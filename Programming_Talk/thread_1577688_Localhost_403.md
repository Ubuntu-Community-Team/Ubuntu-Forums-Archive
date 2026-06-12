---
title: "Localhost 403"
date: 2010-09-19
forum: Programming Talk
---

### Post by ApocalypeX on 2010-09-19
So my localhost works perfectly just to clarify, I have multiple sub directories and files working on it. I've been on Windows a bit and working there on a project. When I copied the files over to my D drive and then on Ubuntu copied the files over to my www folder it gives me a 403 when I try to view the web pages. But I can open the files and edit them etc.

Any ideas as to how I can get permission and why this happened?

---

### Post by dwhitney67 on 2010-09-19
> **ApocalypeX said:**
> So my localhost works perfectly just to clarify,

That's assuring.
> **ApocalypeX said:**
> I have multiple sub directories and files working on it.

Whatever.
> **ApocalypeX said:**
> I've been on Windows a bit and working there on a project.  When I copied the files over to my D drive and then on Ubuntu copied the files over to my www folder it gives me a 403 when I try to view the web pages.

Who owns the files?  You or root?

> **ApocalypeX said:**
> But I can open the files and edit them etc.

Typically, when users at home interface with Windows, they unknowingly use a privileged account for all of the day-to-day dealings.  Whereas this is also possible under Linux/Unix, it is discouraged, and not setup by default.

So when you say "I" in the statement above, to whom are you referring to?  Is it your regular user account or is it "root" (via sudo)?
> **ApocalypeX said:**
> 
Any ideas as to how I can get permission and why this happened?
The "localhost 403" error is quite common; I'm surprised you could not Google for a solution.  I'm no expert, but I believe it has something to do with either file or directory permissions.

On my system, all folders are owned by root:root; permissions are 755.  All files are also owned by root:root, and their permissions are 644.

You can fix the permissions by fixing all of the directories and files at your web-server's base document directory.  Assuming this is /var/www, perform the following:
```

sudo find /var/www -exec chown root:root {} \;     # changes ownership
sudo find /var/www -type d -exec chmod 755 {} \;   # changed dir perms
sudo find /var/www -type f -exec chmod 644 {} \;   # changes file perms

```


P.S.  The Apache Web Server's document root is set within /etc/apache2/sites-enabled/000-www.  I personally have setup this file to point to a similar file in /etc/apache2/sites-available, which I have edited to use a non-default document root.  It's contents are something like:
```

<VirtualHost *:80>
        ServerAdmin **you@email.com**

        DocumentRoot **/path/to/www/html**
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory **/path/to/www/html/**>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
...

```

---

