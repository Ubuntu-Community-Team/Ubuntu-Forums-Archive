---
title: "[SOLVED] My script made me lose my panels!"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by dinostabOMG on 2008-08-20
Okay, so on Hardy I wrote a script to mount my Windows partition at startup, and then I put a line in my /etc/rc.local that calls it. Here are the files:

rc.local (my addition only)
```

#mounts windows XP partition in /media/disk/
csh /home/me/.myscripts/mountwinpart.csh

```

mountwinpart.csh (entire file)
```

#
#This script mounts my Windows XP partition in /media/disk/
#To be run at startup. Needs superuser permissions.



mkdir /media/disk/
#This command comes from http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/
mount -t ntfs -o nls=utf8,umask=0222 /dev/sda1/ /media/disk/


```

The next time I started up, the disk was mounted properly but my panels were gone! I have no idea why. I've since commented out that line in rc.local, and the disk doesn't mount, but my panels are still gone! What??

Another minor question: My understanding is that rc.local runs at startup, before you log in - does it run at any other time as well?

One more question: Was it the right idea to put this call in rc.local? I needed the script to be run with superuser permissions to mount the drive, and I came across that solution in my search. If there is another way to do it, I'd like to avoid having to put in my password.

This may not be an *absolute* beginner question but I do feel lost like one!

---

### Post by dinostabOMG on 2008-08-20
An update: so I figured I could run from the terminal (good thing I have a keyboard shortcut to open the terminal):

```
$ gnome-panel
The program 'gnome-panel' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-panel
bash: gnome-panel: command not found

```

gnome-panel is not installed? Isn't it part of the default Ubuntu install? Or am I confusing it with another similar thing?

I am worried that maybe my script did something much larger than I intended, like deleting my installed programs? I have no idea how this could have happened.

---

### Post by dinostabOMG on 2008-08-20
Okay so I just went ahead and installed the panels with apt-get. Fine, I got them back. Now I am getting these errors:

[IMG][/IMG]

Sure enough, when I try to add those manually, I get the same error again.

So I am beginning to think my script was a success and this is an unrelated problem. I uninstalled Evolution from synaptic just before doing all this. I don't see why this would affect the panels, but I guess it does somehow. Fine, I can also see why the Evolution launcher wouldn't work, but why the sound, multiload, user switcher, and trash (not pictured) stop working?

Perhaps this warrants a new thread as it's not really related to the original problem.

---

### Post by dinostabOMG on 2008-08-20
Alright, it looks like I worked through all of this on my own, heh.

With apt-get, i installed fast-user-switch-applet, gnome-applets, and gnome-panel.

I have no idea how they all got removed, though. I only removed evolution via synaptic. I'd be interested in any theories, but the problem is solved.

Thanks for all the help?

---

### Post by lswb on 2008-08-20
> **dinostabOMG said:**
> Okay, so on Hardy I wrote a script to mount my startup, before you log in - does it run at any other time as well?

One more question: Was it the right idea to put this call in rc.local? I needed the script to be run with superuser permissions to mount the drive, and I came across that solution in my search. If there is another way to do it, I'd like to avoid having to put in my password.

This may not be an *absolute* beginner question but I do feel lost like one!

rc.local only runs at startup though I suppose it would be possible to explicitly run it from a shell if you wanted to. Instead of mounting from rc.local, check out the man page for the /etc/fstab file. This is a config file that tells the system which filesystems and partitons to mount at boot time.

As for the panel problem, sometimes an inadvertant mouse click or keypress can have unintended consequences. I think most anyone who has been using a computer for a while, regardless of operating system, has made mistakes like that!

---

