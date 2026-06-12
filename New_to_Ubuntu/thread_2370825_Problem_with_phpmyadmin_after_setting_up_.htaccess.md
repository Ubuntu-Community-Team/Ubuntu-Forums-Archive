---
title: "Problem with phpmyadmin after setting up .htaccess"
date: 2017-09-07
forum: New to Ubuntu
---

### Post by vgledhill on 2017-09-07
Hi People.

I have followed this tutorial [https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-16-04)

Everything worked OK until I followed the instructions about .htaccess once I had done this I get an internal server error message when I try to run phpmyadmin

My simple html file and the php.info file work fine.  

Please can you tell me how to interrogate the logs to see what is going wrong?

---

### Post by SeijiSensei on 2017-09-08
The .htaccess file is used by hosting services like Digital Ocean to give its customers some control over Apache without needing root privileges.  If you are in control of the server, any code that would go in an .htaccess file should be placed in the configuration file that defines your virtual server in /etc/apache2/sites-available.  

Inside the <VirtualHost> container for your site you would add something like this:

```

<VirtualHost *:80>
ServerName  phpmyadmin.example.com
DocumentRoot /path/to/phpmyadmin     
     <Directory /path/to/phpmyadmin>
          AuthUserFile /home/me/.htpasswd 
          AuthGroupFile /home/me/.htgroup
          AuthName "My Server"
          AuthType Basic
          require valid-user
    </Directory>
[Other stuff]
</VirtualHost>

```

By default, Ubuntu disables the .htaccess file.

---

