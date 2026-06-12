---
title: "Stani's Python Editor v0.7.5.c crashes all the time"
date: 2005-12-22
forum: Programming Talk
---

### Post by futz on 2005-12-22
Stani's Python Editor v0.7.5.c (the one in the repositories) is great, but it crashes at the drop of a hat with no warning, and if you haven't saved recently it takes your work with it :(  :mad: #-o :evil: 

Has anyone been successful at installing the new v0.8.1.c version? I got that installed fine, but it wants wxPython 2.5.4.1 or better, which I can't seem to get installed correctly. Ended up going back to spe 0.7.5.c and saving often!

---

### Post by kudu on 2005-12-22
I have 0.8.1.b installed at the moment and it appears to be working just fine. No problems with wxPython etc. I haven't messed with 0.8.1.c yet since I just got done with installing b and it's working so no need to fix it...yet.

Cheers!

---

### Post by futz on 2005-12-22
I just now realized that I had been trying to install it on the Fedora4 box right beside this Ubuntu box, and not on this box. I just finished installing it on this box, and you're right, it works fine.

Sometimes I forget where I am... :mrgreen:

---

### Post by oldmanstan on 2005-12-23
what is the package name for that app? i couldn't find it in the repositories, i have universe enabled, etc.

---

### Post by futz on 2005-12-23
[QUOTE=oldmanstan]what is the package name for that app? i couldn't find it in the repositories, i have universe enabled, etc.[/QUOTE]
I'm not exactly sure - I'm sitting at the windoze box this morning. 

But get the newer one anyway at [http://www.stani.be/python/spe/](http://www.stani.be/python/spe/)

It's easy to install, and its dependency (wxpython) is already installed in Ubuntu, or if it's not it's available easily from the repos.

To install (going from memory), cd to the temporary directory where you unpacked the files, type 'sudo python setup.py install' (without the apostrophes). After install you can delete the temp directory.

If it squawks about any dependencies, you might have to go grab em from the repos and install again.

It's a nice python editor, but save often. The new version still crashes occasionally. Just silently disappears for no apparent reason.

---

### Post by fct on 2005-12-25
Package name for ubuntu: spe

---

### Post by stani on 2006-01-20
[QUOTE=futz]It's a nice python editor, but save often. The new version still crashes occasionally. Just silently disappears for no apparent reason.[/QUOTE]

Hi,

Can you describe when the latest version crashes? Known issue is the browser in the sidebar. I've been working hard to port SPE to Ubuntu (see [http://pythonide.stani.be/blog](http://pythonide.stani.be/blog)) and I'd like to fix any stability issues. Please report them to me directly. Any bug wich crashes SPE will get high priority. I'll release soon SPE 0.8.1.e which should be optimized for Ubuntu. So if you have comments, they can be taken into account.

I would discourage everybody to use SPE v0.7.5.c, it is very old. SPE will from now on release .deb packages which will make it much more easy to install: ```
sudo dpkg -i spe.deb
``` (I think).

I'm also looking for some experienced Ubuntu users (I'm totally newbie) to help me out with certain things about Ubuntu.

Thanks,
Stani

[http://pythonide.stani.be](http://pythonide.stani.be)

---

### Post by stani on 2006-07-18
Read my [howto install latest wxPython & SPE (Feature rich Python IDE)]("http://www.ubuntuforums.org/showthread.php?t=218001&highlight=wxpython").

---

