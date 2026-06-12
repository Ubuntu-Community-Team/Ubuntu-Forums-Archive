---
title: "Removing applications not installed in the default directory"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Poyntz on 2008-11-06
I've installed elinks in /usr/local. The problem with this is that, whilst the application runs, it will not find spidermonkey, and consequently I have no javascript support. I have installed spidermonkey from the source and from debian, both which build and install the application into /usr/ - or so i'm lead to believe from searching the hard disk. There is no config file, making it hard to direct the installation of spidermonkey to /usr/local. Consequently I'm faced with the need to install elinks to the default directory. 

When I install elinks to its default directory, the desired version won't run because installations in the /usr/local directory override installations anywhere else.

So, how do I uninstall elinks from the /usr/local directory?

P.S: I've tried using aptitude, synaptic, apt and deb packager, but had no luck trying to uninstall the /usr/local installation of elinks

---

### Post by Mark_in_Hollywood on 2008-11-08
> **Poyntz said:**
> I've installed elinks in /usr/local. The problem with this is that, whilst the application runs, it will not find spidermonkey, and consequently I have no javascript support. I have installed spidermonkey from the source and from debian, both which build and install the application into /usr/ - or so i'm lead to believe from searching the hard disk. There is no config file, making it hard to direct the installation of spidermonkey to /usr/local. Consequently I'm faced with the need to install elinks to the default directory. 

When I install elinks to its default directory, the desired version won't run because installations in the /usr/local directory override installations anywhere else.

So, how do I uninstall elinks from the /usr/local directory?

P.S: I've tried using aptitude, synaptic, apt and deb packager, but had no luck trying to uninstall the /usr/local installation of elinks

sudo aptitude remove elinks

BUT, before that have you looked for hidden directories?

try

alt-f2

when the box opens, type:

gksudo nautilus

a file manager will open, hunt & peck for your (maybe): /.elinks

---

### Post by pgorillaman on 2008-11-08
Why dont you just symlink spidermonkey into /usr/local?

---

### Post by Poyntz on 2008-11-11
> **Mark_in_Hollywood said:**
> sudo aptitude remove elinks
BUT, before that have you looked for hidden directories?

sudo aptitude remove elinks uninstalled something, but it hasn't uninstalled elinks from /usr/local :/. 

elinks is located in /usr/local/bin. I know this because if I rename the file and try to run elinks from terminal I get: 
> bash: /usr/local/bin/elinks: No such file or directory

Does this help?

> **pgorillaman said:**
> Why dont you just symlink spidermonkey into /usr/local?
I would prefer to install it to the proper directory in case I found out I need to install another program. For every new program I'd have to symlink it to get elinks to work. I'd prefer not to have to worry about this if possible. Thanks for the suggestion though

---

### Post by Mark_in_Hollywood on 2008-11-12
Open a terminal and paste this line:

sudo aptitude remove elinks

---

### Post by Poyntz on 2008-11-14
I discovered a quick fix. Aptitude won't cut it in the way you're stating, but thanks just the same. "elinks" is the terminal alias that runs the elinks application. This is run from /usr/local/bin/. Basically the trick is to rename elinks to something else, then to reinstall the application. The reinstalled application will take over the alias for "elinks" - that's the case at least in a debian or apt install. 

I discovered that the issue I was having was because spidermonkey and elinks only interacted in a limited sense. I don't think it's possible to get a simple text browser like elinks to undertake more advanced javascript functions. In my circumstance it was however bizarre because all I wanted was to login to something (ie, have my form variables stored in a session). Oddly in this circumstance elinks didn't support the storage :/.

P.S: Just like to note that if anyone happens to find a quick fix to uninstalling aps from non-default source installations I would like to hear it

---

