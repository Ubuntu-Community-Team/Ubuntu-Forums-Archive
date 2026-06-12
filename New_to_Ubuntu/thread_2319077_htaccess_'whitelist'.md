---
title: "htaccess 'whitelist'"
date: 2016-03-31
forum: New to Ubuntu
---

### Post by Jake_Simmons on 2016-03-31
Hi all!

I was having a little fun with my home ubuntu server (not really for anything special or important), and I 'happened' to stumble across htaccess to secure a web page. This was very fun to try and set up, however I have an 'urge' to make my apache server better! 
I was hoping that someone could help me by providing a way to specify the users (from the .htaccess file) that can access the site (like a whitelist). I don't know if this can be achieved by changing the Required field from 'valid-user' to a username. 

If anyone understands, and can give me a hand, that would be great!

Thanks,

---

### Post by SeijiSensei on 2016-04-01
You can use "Require user username" or, to handle multiple users, put them in an Apache group and use "Require group groupname".  Read this for details: [http://httpd.apache.org/docs/current/howto/auth.html](http://httpd.apache.org/docs/current/howto/auth.html)

Also if you control the server configuration, you should avoid using .htaccess files and put the corresponding directives inside the <Directory></Directory> stanza in the virtual host configuration in /etc/apache2/sites-available/.  For instance,
```

<VirtualHost *:80>
ServerName myserver.example.com
DocumentRoot /path/to/my/site

<Directory "/path/to/my/site">
     AuthType Basic
     AuthName "By Invitation Only"
     AuthUserFile "/usr/local/apache/passwd/passwords"
     AuthGroupFile "/usr/local/apache/passwd/groups"
     Require group GroupName
 
     Options ...
     [other stuff]
</Directory>

</VirtualHost>

```

---

