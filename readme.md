# Certbot plugin for authentication using Nodeup API

This is a plugin for [Certbot](https://certbot.eff.org/) that uses the Nodeup API to allow [Nodeup](https://nodeup.io/)
customers to prove control of a domain name.

## Usage

1. Obtain a NodeUp API token (see [Nodeup API Settings](https://cloud.nodeup.io/settings/api/))

2. Install the plugin using `pip install certbot-dns-nodeup`

3. Create a `nodeup.ini` config file with the following contents and apply `chmod 600 nodeup.ini` on it:
   ```
   # Nodeup API credentials used by Certbot
   api_key = TOKEN
 
   ```
   Replace `TOKEN` with your Nodeup API token and ensure permissions are set
   to disallow access to other users.

4. Run `certbot` and direct it to use the plugin for authentication and to use
   the config file previously created:
   ```
   certbot certonly -a certbot-plugin-nodeup:dns --certbot-plugin-nodeup:dns-credentials nodeup.ini -d example.com
   ```
   Add additional options as required to specify an installation plugin etc.
