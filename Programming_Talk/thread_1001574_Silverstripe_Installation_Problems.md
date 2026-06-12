---
title: "Silverstripe Installation Problems"
date: 2008-12-04
forum: Programming Talk
---

### Post by stefanadelbert on 2008-12-04
I'm having serious problems installing Silverstripe (both 2.2.3 and 2.3.0 RC2) on Intrepid.

I have LAMP stack installed as follows:
[LIST]
[*]apache 2.2.9-7ubuntu3
[*]mysql  Ver 14.12 Distrib 5.0.67, for debian-linux-gnu (x86_64) using readline 5.2
[*]PHP 5.2.6-2ubuntu4 with Suhosin-Patch 0.9.6.2 (cli) (built: Oct 14 2008 20:18:13)
[/LIST]

When installing Silverstripe in /var/www (or anywhere else for that matter), is get an error from the installer as follows:

```

Friendly URLs are not working. This is most likely because mod_rewrite isn't configuredcorrectly on your site. Please check the following things in your Apache configuration; you may need to get your web host or server administrator to do this for you:

    * mod_rewrite is enabled
    * AllowOverride All is set for your directory

```

mod_rewrite is installed and enabled. I find it under Loaded Modules when running phpinfo() and the Silverstripe installer claims to be happy that mod_rewrite is enabled too.

I've put the directive below into the /etc/apache2/httpd.conf file (which is included by apache.conf) and also straight into apache.conf and then restarted apache.

```

<Directory /var/www>
AllowOverride All
</Directory>

```

None of this has helped. Has anyone run into the same problems? I'm convinced that it's some small setting somewhere that will get it working.

Thanks
Stef

---

### Post by stefanadelbert on 2008-12-04
I got a reply for a Silverstripe user on their forums and his advice was to add the following to the Apache config file (apache.conf or httpd.conf)

```
<IfModule mod_rewrite.c>
RewriteEngine On
</IfModule>
```

I'll post back if this works.

Stef

---

### Post by MundoMuerto on 2009-05-27
I just ran into this myself while trying to install silverstripe into a subdirectory of /var/www. My best guess is that the AllowOverride directive doesn't automatically apply to subfolders since using a more specific path worked for me. Adding the following to /etc/apache2/httpd.conf allowed silverstripe to install without errors:

```

<Directory /var/www/test>
AllowOverride All
</Directory>

```

In this case I had uploaded all of the silverstripe files to the 'test' directory.

---

### Post by davidm2010 on 2009-10-20
Has anyone gotten SilverStripe to install? I can get it to install, but can't get the modules (this case event_calender) to install. I am having difficulty using the /dev/build function. 
 
I am using Ubuntu 9. PHP 5 ans mySQL from a LAMP install. Any help would be appreciated.
 
Dave

---

