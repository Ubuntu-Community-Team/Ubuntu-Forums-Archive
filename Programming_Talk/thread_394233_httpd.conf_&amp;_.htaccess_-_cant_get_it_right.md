---
title: "httpd.conf &amp; .htaccess - cant get it right"
date: 2007-03-26
forum: Programming Talk
---

### Post by theorem_hunter on 2007-03-26
i cant seam to get this right. i have apache2 installed, with mysql5.0 & php5.

when i type in my IP or 127.0.0.1, i get:

apache2-default/ 
munin/
webalizer/  

& then 127.0.0.1:8888 i get GNUMP3d,

which is all fine all except that the whole world can now access my music if they have my IP. so i have been trying to restrict acess to those pages by  playing with httpd.conf - which i cant get right & .htaccess - which never seams to make any difference. 

i created a password file like this:

sudo htpasswd -c /home/dimitri/password dimitri 
so that the password file would be in my home directory. 

then i added a .htaccess, file in /var/www/ that looks like this:

AuthType Basic
AuthName "Restricted Files"
# (Following line optional)
AuthBasicProvider file
AuthUserFile /home/dimitri/password
Require user dimitri

^^^ this doesnt make a difference, i have also tried putting this in httpd.conf - but that always gives syntax errors.

i have been reading [http://httpd.apache.org/docs/2.2/howto/auth.html](http://httpd.apache.org/docs/2.2/howto/auth.html) 
but i am obviously doing something very wrong...

any help?
thanks

---

### Post by kidders on 2007-03-26
Hi there,

It's been a while since I've used this feature, but here are some things to check...

[LIST]
[*]Make sure Apache's **AccessFileName** directive is set properly, so that .htaccess files are recognised.
[*]Permissions & ownership of .htaccess files need to be appropriate.
[/LIST]Assuming you can make Apache ask for a password, it will only accept it if...

[LIST]
[*]/home/dimitri/ is **chmod o+x**.
[*]Your password file is readable, at least by www-data.
[/LIST]

> **theorem_hunter said:**
> i have also tried putting this in httpd.conf - but that always gives syntax errors.The syntax of the file itself seems okay... perhaps you were just putting the directives in the wrong place in your config files?

Is any of these suggestion helpful?

---

### Post by Mr. C. on 2007-03-26
The authentication directives need to be in a Directory context if they are on the httpd.conf file.

MrC

---

### Post by theorem_hunter on 2007-03-27
i think every thing is right... its just not asking for a username & password...

relevent things are...

dimitri@OuZo:~$ ls -al
-rw-r--r--   1 dimitri dimitri       22 2007-03-27 22:06 .htpasswd

dimitri@OuZo:/var/www$ ls -al
total 32
drwxr-xr-x  6 root    root  4096 2007-03-27 23:34 .
drwxr-xr-x 18 root    root  4096 2007-03-22 14:05 ..
drwxr-xr-x  2 root    root  4096 2007-03-27 22:43 apache2-default
-rwxrwxrwx  1 root    root    99 2007-03-27 22:45 .htaccess
-rw-r--r--  1 root    root    99 2007-03-27 22:10 .htaccess~
drwxr-xr-x  3 munin   munin 4096 2007-03-27 22:44 munin
drwxr-xr-x  2 dimitri root  4096 2007-03-27 23:45 test-pages
drwxr-xr-x  2 root    root  4096 2007-03-27 22:21 webalizer

the contents of .htaccess is:

AuthUserFile /home/dimitri/.htpasswd
AuthType Basic
AuthName "My Secret Folder"
Require valid-user

i copied it into: apache2-default  munin webalizer > as well as have .htaccess in the /var/www/ folder...

:( im just not winning here...

# Make sure Apache's AccessFileName directive is set properly, so that .htaccess files are recognised.
^^^ how do i make sure of this?

Permissions & ownership of .htaccess files need to be appropriate.
^^^ i think i have taken care of this?

anything else drastic that i am missing out on?

thanks

---

### Post by Mr. C. on 2007-03-27
Look in your web logs in /var/log/apache2 (access and error logs).  You will find they do not show any .htaccess requests, right?  Learn to look for these things.

The default virtual host does not allow overriding options; so .htaccess (authconfig) is not searched.  You need to replace

```
AllowOverride none
```
in the <Directory /var/www/> section of the /etc/apache2/sites-enabled/000-default file, with
```

AllowOverride AuthConfig
```
and then reload the server.

You do not want .htaccess 777.  Make it 644, owned by your or root.  It should not be writable by group or others.

MrC

---

### Post by theorem_hunter on 2007-03-27
thanks Mr. C.

that has worked...

i just need to find where "GNUMP3d" is, so i can block that to!

---

### Post by Mr. C. on 2007-03-27
locate -i GNUMP3d

---

### Post by theorem_hunter on 2007-03-27
thanks, that gave a long list of things

i am amkeing changes to 
/etc/gnump3d/gnump3d.conf

### i want this to only be accessible from my local intranet
### binding_host = `hostname' <<< this did not work
### binding_host = [http://localhost/](http://localhost/) <<< niether did this
### binding_host = OuZo <<< nor did this
binding_host = 10.0.0.4
^^^ but this did

i restarted gnump3d each time with: sudo /etc/init.d/gnump3d restart


is this good? what if my local IP changes...

thanks

---

### Post by Mr. C. on 2007-03-27
binding_host indicates which *interface* the server will listen on.  Only IP addresses work; none of your other settings make sense as IP addresses.

Servers should have static IP addresses, so your concern is mitigated.

MrC

---

### Post by theorem_hunter on 2007-03-27
thanks for clearing that up :)

---

