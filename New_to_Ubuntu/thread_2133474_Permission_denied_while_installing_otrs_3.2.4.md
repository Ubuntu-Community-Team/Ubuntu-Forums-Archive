---
title: "Permission denied while installing otrs 3.2.4"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by jj99 on 2013-04-08
Hi ,
I am new to Ubuntu platform. I am trying to install OTRS but when i try to set permissions for web server user and otrs user to have permissions on the directory I got the following error:
**bash:bin/otrs.SetPermissions.pl: Permission denied**

---

### Post by WWielbert on 2013-08-07
Try : [http://ownlinuxnotes.wordpress.com/2012/01/22/install-and-configure-otrs-in-ubuntu/](http://ownlinuxnotes.wordpress.com/2012/01/22/install-and-configure-otrs-in-ubuntu/)

These are steps i followed today and otrs works fine for me


wget [ftp://ftp.otrs.org/pub/otrs/otrs-3.2.9.tar.gz](ftp://ftp.otrs.org/pub/otrs/otrs-3.2.9.tar.gz)


cp otrs-3.2.9.tar.gz /opt/


cd /opt


tar -xzvf otrs-3.2.9.tar.gz


ln -s /opt/otrs-3.0.3 /opt/otrs


useradd otrs
passwd otrs
usermod -d /opt/otrs otrs


usermod -g www-data otrs


sudo apt-get install mysql-server apache2


cd /opt/otrs


sudo ./bin/otrs.CheckModules.pl | grep Not


sudo aptitude search libdatetime-perl libnet-dns-perl libwp-useragent-determined-perl


sudo aptitude install libdatetime-perl libnet-dns-perl libwp-useragent-determined-perl


sudo bin/otrs.SetPermissions.pl --otrs-user=otrs &#8211;otrs-group=otrs --web-user=www-data --web-group=www-data /opt/otrs


sudo ln -s /opt/otrs/scripts/apache2-httpd.include.conf /etc/apache2/sites-available/otrs.conf


sudo ls /etc/apache2/sites-available/


sudo /etc/init.d/apache2 reload


sudo a2ensite otrs.conf


sudo /etc/init.d/apache2 reload


[http://local/otrs/installer.pl](http://local/otrs/installer.pl)


It did not work at this moment. Hence, i followed the remaining from [http://wiki.otterhub.org/index.php?title=Installation_on_Ubuntu_Lucid_Lynx_(10.4)](http://wiki.otterhub.org/index.php?title=Installation_on_Ubuntu_Lucid_Lynx_(10.4))


cd /opt/otrs/kernel
cp config.pm.dist config.pm
cp config/genericagent.pm.dist config/genericagent.pm


Modify the ENVVARS file


Add # in front of 


#export Apache_run_user=www-data
#export Apache_run_group=www-data


Below that type :


#export Apache_run_user=otrs
#export Apache_run_group=otrs


Restart Apache and you should be able to complete the registration

---

