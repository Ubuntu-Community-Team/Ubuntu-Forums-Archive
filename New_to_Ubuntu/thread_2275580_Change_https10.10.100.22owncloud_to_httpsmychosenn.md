---
title: "Change https://10.10.100.22/owncloud to https://mychosenname.org"
date: 2015-04-27
forum: New to Ubuntu
---

### Post by Theforce32 on 2015-04-27
Hi, having found out that ownlcoud 8.02 and above is not supported on windows platforms, I downloaded and installed ubuntu 14.04 for the first time.  I've followed the instructions to setup owncloud which was surprisingly painless.  Now I want to change my address from [https://10.10.100.22/owncloud](https://10.10.100.22/owncloud) so that when I type [https://mychosenname.org](https://mychosenname.org) that's translated to [https://10.10.100.22/owncloud](https://10.10.100.22/owncloud).  I haven't even got to the stage of making it accessible on the internet (that will come later); right now I want to change it so that users don't have to remember what they consider a long set of numbers followed by /owncloud.

I would really appreciate some idiot proof instructions on how to do this.  Many thanks :p

---

### Post by dino99 on 2015-04-27
a little doc :
[https://gist.github.com/mlgill/195721d3ee6702085ec5](https://gist.github.com/mlgill/195721d3ee6702085ec5)
[http://www.davelachapelle.ca/guides/owncloud-ubuntu-nginx-setup-guide/](http://www.davelachapelle.ca/guides/owncloud-ubuntu-nginx-setup-guide/)
[https://forum.owncloud.org/viewtopic.php?f=17&t=20220](https://forum.owncloud.org/viewtopic.php?f=17&t=20220)

---

### Post by Theforce32 on 2015-04-27
Hi, I made changes to the following files, but its still not working.. 

config.php
<?php
$CONFIG = array (
  'instanceid' => 'ocizz40u3x5d',
  'passwordsalt' => 'YZnA8lwVHs80dlHJQmuFRqKT2.83NO',
  'secret' => 'C/m4ZfYZ8J5AqF58qcV4DfiTo8BkfTDtKqA77sV9bP709AZd',
  'trusted_domains' =>
  array (
    0 => '10.10.10.222','mydomain.org'
),
  'datadirectory' => '/var/www/owncloud/data',
  'overwrite.cli.url' => 'http://10.10.10.222/owncloud',
  'dbtype' => 'mysql',
  'version' => '8.0.2.0',
  'dbname' => 'OwnCloud',
  'dbhost' => 'localhost',
  'dbtableprefix' => 'oc_',
  'dbuser' => 'oc_Systemadmin',
  'dbpassword' => '8z9kbws5v79yum3ta5z1b8u25cqkpt',
  'installed' => true,
  'ldapIgnoreNamingRules' => false,
);






defualt-ssl
<IfModule mod_ssl.c>
        <VirtualHost _default_:443>
                ServerAdmin webmaster@localhost
                servername mydomain.org


        DocumentRoot /var/www/html


                # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
                # error, crit, alert, emerg.
                # It is also possible to configure the loglevel for particular
                # modules, e.g.
                #LogLevel info ssl:warn


                ErrorLog ${APACHE_LOG_DIR}/error.log
                CustomLog ${APACHE_LOG_DIR}/access.log combined


                # For most configuration files from conf-available/, which are
                # enabled or disabled at a global level, it is possible to
                # include a line for only one particular virtual host. For example the
                # following line enables the CGI configuration for this host only
                # after it has been globally disabled with "a2disconf".
                #Include conf-available/serve-cgi-bin.conf


                #   SSL Engine Switch:
                #   Enable/Disable SSL for this virtual host.
                SSLEngine on


                #   A self-signed (snakeoil) certificate can be created by installing
                #   the ssl-cert package. See
                #   /usr/share/doc/apache2/README.Debian.gz for more info.
                #   If both key and certificate are stored in the same file, only the
                #   SSLCertificateFile directive is needed.
                SSLCertificateFile      /etc/apache2/ssl/owncloud.crt
                SSLCertificateKeyFile /etc/apache2/ssl/owncloud.key


                #   Server Certificate Chain:
                #   Point SSLCertificateChainFile at a file containing the
                #   concatenation of PEM encoded CA certificates which form the
                #   certificate chain for the server certificate. Alternatively
                #   the referenced file can be the same as SSLCertificateFile
                #   when the CA certificates are directly appended to the server
                #   certificate for convinience.
                #SSLCertificateChainFile /etc/apache2/ssl.crt/server-ca.crt


                #   Certificate Authority (CA):
                #   Set the CA certificate verification path where to find CA
                #   certificates for client authentication or alternatively one


/etc/hostname
mydomain.org




owncloud.conf
alias /owncloud "/var/www/owncloud/"
<Directory "/var/www/owncloud">
    Options +FollowSymLinks
    AllowOverride All
</Directory>


What am I missing or doing wrong

---

