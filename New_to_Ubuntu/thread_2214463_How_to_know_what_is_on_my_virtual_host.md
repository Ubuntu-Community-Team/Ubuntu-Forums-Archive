---
title: "How to know what is on my virtual host"
date: 2014-04-01
forum: New to Ubuntu
---

### Post by SV2B on 2014-04-01
I subscribed an ubuntu virtual server. I access it. It responds. Now I would like to know what is installed on it, where, and how to upgrade what is there and add applications. Is there a guide, a tool simply documented to obtain that without adding tons of things on the machine I will do not know further on how to remove. I am accessing from a window machine. I would only like to understand the machine, the tools and the scripts I need to manage Apache, Postfix, MediaWiki. 
Thank you!

---

### Post by TheFu on 2014-04-01
Welcome to the forums.

Your question is like when an alien from another planet arrives here and asks, "tell me everything I need to know about Earth, but don't waste my time."

Linux is like a new world - especially to someone with only MS-Windows knowledge. Sometimes things seem the same, but underneath, they are not.  Linux/UNIX have very different philosophies from Windows, so understanding that is the first step.

Each of those programs has multiple books written JUST FOR THEM alone. They are like different countries.

Start with help.ubuntu.com to learn what you seek.  I'd start with a beginning CLI tutor, then learn file/directory permissions. This is before touching any of those programs - permissions are the center of all Linux/UNIX security and shouldn't be ignored.

Use ssh/sftp for everything. Avoid other tools.  WinSCP is a good GUI too and putty is the ssh client.
Use ssh-keys over the internet - NEVER passwords after the initial login.  On a linux desktop, ssh-copy-id will handle the push easily. Don't know how to do it from windoze - sorry.

If you are brand new, it would be better to load up virtualbox on Windows and load an Ubuntu desktop inside a VM to get used to it.  Starting with a server will have an extremely steep learning curve.  With the desktop there is a nice GUI, access to multiple windows to read man pages, ssh into the server, copy/paste commands, google for answers ... it is just so much nicer.  The select/paste blows away copy/paste, IMHO too.

Don't forget to learn about security, locking down postfix, apache, and any webapps. There are some commonly used settings in online "how-tos" that are highly non-secure and will get your box pwoned.  

If you don't really want to learn this stuff - why not just pay an expert a few $K to setup the machine and $100-200/month to run it?

---

### Post by SeijiSensei on 2014-04-01
I always suggest starting with the [Ubuntu Server Guide]("https://help.ubuntu.com/12.04/serverguide/C/index.html").

---

