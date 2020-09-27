# Apache2 Webserver Docker Container for AARCH64, ARMv7l, X86 and X64

For hosting static HTML websites.

## Required Docker Image

The Docker Image **ws-apache-base-\<ARCH\>** will automaticly be downloaded from the Docker Hub.  
The source for the image can be found here [https://github.com/tsitle/dockerimage-ws-apache\_base](https://github.com/tsitle/dockerimage-ws-apache_base).

## Docker Container usage

To start the Docker Container simply run `$ ./dc-ws-apache.sh up`.  
When the file `docker-compose.yaml` doesn't exist it will be created for you.  
You can edit the file afterwards if you wish to customize it.

To stop the container run `$ ./dc-ws-apache.sh down`

## Docker Container configuration

- CF\_PROJ\_PRIMARY\_FQDN [string]: FQDN for website (e.g. "mywebsite.localhost") (default: empty)
- CF\_SET\_OWNER\_AND\_PERMS\_WEBROOT [bool]: Recursively chown and chmod CF\_WEBROOT? (default: false)
- CF\_WWWDATA\_USER\_ID [int]: User-ID for www-data (default: 33)
- CF\_WWWDATA\_GROUP\_ID [int]: Group-ID for www-data (default: 33)
- CF\_ENABLE\_CRON [bool]: Enable cron service? (default: false)
- CF\_LANG [string]: Language to use (en\_EN.UTF-8 or de\_DE.UTF-8) (default: empty)
- CF\_TIMEZONE [string]: Timezone (e.g. 'Europe/Berlin') (default: empty)
- CF\_ENABLE\_HTTP [bool]: Enable HTTP for Apache? (default: true)
- CF\_CREATE\_DEFAULT\_HTTP\_SITE [bool]: Create default HTTP Virtual Host for Apache? (default: true)
- CF\_ENABLE\_HTTPS [bool]: Enable HTTPS/SSL for Apache? (default: false)
- CF\_CREATE\_DEFAULT\_HTTPS\_SITE [bool]: Create default HTTPS/SSL Virtual Host for Apache? (default: true)
- CF\_SSLCERT\_GROUP\_ID [int]: Group-ID for ssl-cert (default: 102)
- CF\_DEBUG\_SSLGEN\_SCRIPT [bool]: Enable debug out for sslgen.sh?
- CF\_CSR\_SUBJECT\_COUNTRY [string]: For auto-generated SSL Certificates (default: DE)
- CF\_CSR\_SUBJECT\_STATE [string]: For auto-generated SSL Certificates (default: SAX)
- CF\_CSR\_SUBJECT\_LOCATION [string]: For auto-generated SSL Certificates (default: LE)
- CF\_CSR\_SUBJECT\_ORGANIZ [string]: For auto-generated SSL Certificates (default: The IT Company)
- CF\_CSR\_SUBJECT\_ORGUNIT [string]: For auto-generated SSL Certificates (default: IT)
- CF\_APACHE\_TIMEOUT [int]: Number of seconds before receives and sends time out (default: 300)

## Using cron

If you'd like to use cron you'll also need to copy the file `mpcron/crontab-template` to
`mpcron/<USERNAME>`.  
E.g. for installing a crontab for the user "www-data" copy the file to `mpcron/www-data`.  
Then uncomment the mountpoint for that file in the `docker-compose.yaml`.
