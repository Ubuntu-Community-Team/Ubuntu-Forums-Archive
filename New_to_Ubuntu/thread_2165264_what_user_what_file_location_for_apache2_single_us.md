---
title: "what user what file location for apache2 single user development box?"
date: 2013-08-04
forum: New to Ubuntu
---

### Post by 1888software on 2013-08-04
I installed the LAMP stack and the apache server runs.
[COLOR=#008000]$ sudo tasksel install lamp-server[/COLOR]
The installation directory is the default /var/www/ folder and it is owned by root.

I hope to use the LAMP install for developing and testing websites. When the website development code runs satisfactorily, I'll ftp it to the actual production web server on the cloud. So, my local LAMP stack is just for development and I will be the only user, and a single virtual host is all i need. 

In the filesystem, I eventually want to use /home/Documents/folder1.com, /home/Documents/folder2.com, /home/Documents/folder3.com and so on. 

What I did
[COLOR=#008000]$ sudo mv /home/Documents/folder1 /var/www/[/COLOR]

LOGGED IN AS HOME USER
[COLOR=#008000]index.html in /var/www/ loads index.html[/COLOR]
[COLOR=#ff0000]index.html in /var/www/folder1/ does not load[/COLOR]

LOGGED IN AS SUPERUSER
[COLOR=#ff0000]index.html in /var/www/ does not load[/COLOR]
[COLOR=#ff0000]index.html in /var/www/folder1/ does not load[/COLOR]

The Firefox web browser error for "does not load" is:
[COLOR=#ff0000]Unable to connect
        
Firefox can't establish a connection to the server at localhost.[/COLOR]

I looked in the apache error log and there were no errors for today.

QUESTIONS
What location should the working files (/home/Documents/folder1.com etc etc) be in? I'll need to access them frequently.
What user should I be using to work on files in the root owned /var/www/ folder? superuser or non root regular account user?

**[COLOR=#0000cd]What solution makes it easiest for me to work without the constant issue of permissions in the /var/www/ folder on my development box?[/COLOR]**

Thank you for any pointers in the right direction.

---

### Post by Lars Noodén on 2013-08-04
If you are the sole user of your web server, then it is enough to take ownership of the /var/www hierarchy using [chown](http://manpages.ubuntu.com/manpages/raring/en/man1/chown.1.html).  Then you will be able to make any edits you wish to folders and files within that directory.

```

sudo chown -R 1888software /var/www/

```

If you plan to have additional users helping with the editing and such, then you will need to use group permissions instead.

---

