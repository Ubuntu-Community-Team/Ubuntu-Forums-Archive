---
title: "Disable dangerous functions in LAMP"
date: 2018-11-02
forum: Programming Talk
---

### Post by dam034 on 2018-11-02
Dear users,

I use a virtual host on a dedicated server.

In this virtual host folder I have a website.
I want to create a sub-folder where the users can upload what they want. This sub-folder will be a symbolic link to the real path name (in another partition).

Since the users can upload files to attack my server, I want to disable everything that can be dangerous, including PHP.

Now the configuration is this, taken from the virtual host file configuration in sites-available:
```
<Directory /srv/panomnia/>
Options Indexes FollowSymLinks
AllowOverride All
Require all granted
</Directory>
```
In the panomnia folder, there is a sym link to another folder, which will contain the files uploaded by the users.
Now I want to disable PHP (and everything that can be dangerous) in /srv/panomnia/uploads/ folder, so that the users can only list the folder and visit/download the files.

How is it possible?

Thanks

---

### Post by luca31 on 2018-11-03
Hi, you can disable the php handler on per directory base...

```
<Directory /srv/panomia/upload>
AllowOverride none
Options -Indexes -FollowSymLinks
<FilesMatch "\.php$">
Require all denied
      SetHandler none
</FilesMatch>
</Directory>
```

Not sure if you should use the real directory path as the Directory argument instead of the symlink.

Greetings

Luca

---

### Post by dam034 on 2018-11-03
I don't want to disable the index or followsymlinks functions, but I simple want to disable PHP library and other dangerous libraries which can execute scripts on my server.

I don't want to deny php files to users, but to serve them without executing them.

Is it possible?

Thanks

---

### Post by luca31 on 2018-11-04
SetHandler application/x-httpd-php-source

---

### Post by dam034 on 2018-11-04
I don't know what I have to do with "SetHandler application/x-httpd-php-source". Have I to write in <Directory>?

Can you write an example?

Thanks

---

### Post by luca31 on 2018-11-04
test

---

### Post by luca31 on 2018-11-04
Sorry I'm having trouble on the forum.. try something like

```

<Directory  /srv/panomia/upload>
AllowOverride none
<FilesMatch "\.php$">
SetHandler none
</FilesMatch>
</Directory>

```

php files will be shown in the index page, but if required it will
not be parsed by the engine. The user will be able to download the code.

if you prefer you could also show the php code on the web with the php handler 


```

<Directory  /srv/panomia/upload>
AllowOverride none
<FilesMatch "\.php$">
SetHandler application/x-httpd-php-source
</FilesMatch>
</Directory>

```

Consider also to read the [security tips]("http://httpd.apache.org/docs/2.4/misc/security_tips.html") and to deploy a mod_security policy to improve the overall security

regards

Luca

---

