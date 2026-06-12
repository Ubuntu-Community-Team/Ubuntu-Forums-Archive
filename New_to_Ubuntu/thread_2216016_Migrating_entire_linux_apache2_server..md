---
title: "Migrating entire linux apache2 server."
date: 2014-04-09
forum: New to Ubuntu
---

### Post by sskrnguy on 2014-04-09
im trying move a apache2 web server to my own computer. i did NOT make this server originally. the person who orginally made my site isnt longer available,  so im trying to figure this out myself. im currently using linode server. ([www.linode.com](www.linode.com)). 

and this is what i have done so far. 

1. install virtualbox along with ubuntu server edition on my win7 machine. 
2. install lamp on the server along with phpmyadmin
3. copied the entire web content to new server. 
4. export and import the entire database. 
5. bought a new domain and had it point to my ip and its working now. 

my problem comes here, i am not familar with apache2 settings. looks like the original content was installed on /home/ directory instead or /var/www and apache settings are included in /etc/apache2/sites-enabled/oldwebsite/

how to i change these settings so it knows where to look for the contents and also the apache settings. ? 
thanx guys

---

### Post by SeijiSensei on 2014-04-09
Hmm.  I thought we talked about this in PMs.

Here is the configuration file for one of my sites; the website files reside under /home:

```

<VirtualHost *:80>
ServerAdmin     webmaster@cyways.com
DocumentRoot    /home/seiji/sites/somesite/public
ServerName      somesite.example.com
ErrorLog        logs/error_log-somesite
TransferLog     logs/access_log-somesite
CustomLog       logs/referer_log-somesite "%h: %{referer}i -> %U"
CustomLog       logs/agent_log-somesite "%{User-agent}i"

<Directory "/home/seiji/sites/somesite/public">
    Options         All
</Directory>

</VirtualHost>

```

As we discussed in PMs, you will be using a <VirtualHost> statement of the form
```
<VirtualHost 10.10.10.10:80>
```
rather than "*:80" since you will be using IP-based virtual hosting.

Put the site's configuration in a file in /etc/apache2/sites-available/ and use a2ensite to "enable" the site as described in the [Server Guide]("https://help.ubuntu.com/12.04/serverguide/httpd.html").  Remember that the files must be readable by the "www-data" pseudo-user that owns the Apache server process.

---

### Post by sskrnguy on 2014-04-10
i've done exactly what you have told me but when i restart apache2.. i am getting an error. i'll look over the log and send you over pm. again.. i appreciate your help.

---

### Post by sskrnguy on 2014-05-07
ive made the conf file. enabled it by a2ensite . and for testing, ive created as test.com and modified my host file. but its keep showing [h=1]Forbidden[/h][COLOR=#000000][FONT=Times New Roman]You don't have permission to access / on this server.[/FONT][/COLOR]

i did gave read permission to my content directory to www-data user. but its not helping. any suggestions?

---

