---
title: "Activating a script via web/network"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by Targettio on 2011-12-22
Hi, I am not sure if this is an absolute beginner question, but I am sure there is an easy fix.

I have a script that runs on my 10.04 server called [sorttv](http://forum.xbmc.org/showthread.php?t=75949) which sorts my media (tv/films/music). But currently I have to use ssh to access the server and manually activate the script, which is a bit of a pain.

The server also runs apache, so I would like to set it up so I could activate the script via a webpage (which I can then access with python from xbmc).

So I created a simple cgi script 

```

#!/usr/bin/perl

exec ('/home/****/sorttv/sorttv.pl');

```

The problem is, the webpage then changes to to the first few lines of the script output (which is ok, it implies the script is running and I can always use Location to set the user back to the right page). But the bigger problem is the script doesn't actually run. It's like it stops as soon as it has output the first few line which end up the webpage.

I assume I have to tell apache that the sorttv script is an offline process so it just activates the script and leaves it alone?

Any help would be great, thabks

---

### Post by MartijnNL on 2011-12-22
Wouldn't is be easier to use '[cron]("https://help.ubuntu.com/community/CronHowto")' and run the script automatically at specific intervals?

---

### Post by Lars Noodén on 2011-12-22
Or as another alternative you could create a [SSH key](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) which does only one thing, running your script.  When you load the key onto the server you just add [font=Courier New]Command="/home/targettio/sorttv/sorttv.pl"[/font] to the front of it.  

The manual page for [sshd](http://manpages.ubuntu.com/manpages/oneiric/en/man8/sshd.8.html) has the full list of options for the authorized_keys file.

---

### Post by Targettio on 2011-12-22
Both good points.

I did think about using cron, but it would be annoying to have to wait for 30-60mins for it to run again and I didn't want it to run every 5mins as that would be overkill 99% of the time.

The ssh key is a nice idea, I didn't know you could do that. I will read some more about it.

As I said in the OP, the eventual aim is to get to a point where XBMC can request that the script is run via a python addon. So if it is possible, I would like to get to a point where I can launch the script via a webpage.

---

