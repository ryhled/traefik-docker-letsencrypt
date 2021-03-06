# Traefik with lets encrypt and portainer

Configures Traefik to run in a docker swarm with lets encrypt. Includes portainer to administer the swarm.
Uses commands for traefik configuration.

#### Basic setup (change domain to whatever you want to use)

Traefik API/UI: traefik.swarm.mydomain.com  
Portainer UI: portainer.swarm.mydomain.com  
Demo app: swarm.mydomain.com  

#### Passwords

The default login for traefik API / Web UI is admin / abc123.  
New passwords needs to be encrypted through [HTPASSWORD](http://www.htaccesstools.com/htpasswd-generator).
You also need to escape "$" with "$$" afterwards.

#### LetsEncrypt

* Ensure you use valid domain names for the sites you want to use letsencrypt / acme certificates.
* Ensure that the domain you use has ben configured to point against your docker machines ip address.
* If you happen to use cloudflare to manage your domain and ssl do not work, try disabling cloudflare proxy and see if it helps.

Deploy it by running: `docker stack deploy -c ./docker-compose.yml traefik-services`
where 'traefik' is the name you want your stack to be deployed as (tip: change network prefix in compose file as well if you change).

You can download the acme.json file by running the command `docker cp {containerId}:/acme.json .`.
