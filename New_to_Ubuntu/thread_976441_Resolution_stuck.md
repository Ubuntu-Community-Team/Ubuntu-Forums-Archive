---
title: "Resolution stuck"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Mazehero55 on 2008-11-09
Usually I have this problem when I first install Ubuntu but all I have to do is install EnvyNG and my resolutions are fixed.
But not now, I did a fresh install of Ubuntu to 8.10 instead of upgrading thinking that it would give me less problems, wrong.

My resolution will not go higher then 800x600 no matter what. I've tried many things that I've found here(I used search). but they're not working.
I tried adding in the modes manually into xorg.conf. And installing displayconfig.gtk to fix it there. But now whenever I change anything in it it gives me a message when I try to start that something's wrong with my xorg! And I have to go back to a backup.
I work in graphics, I need a higher resolution. How come suddenly it's not working when it worked fine for all other versions?

Please reply soon, I'm completely lost.

thank you

---

### Post by mapes12 on 2008-11-09
This worked for me: [http://ubuntuforums.org/showpost.php?p=6086662&postcount=8](http://ubuntuforums.org/showpost.php?p=6086662&postcount=8)

What graphics card do you have and can we have a look at your xorg.conf file please?

---

### Post by Mazehero55 on 2008-11-09
Yeah I tried that. 
I went back and uninstalled the drivers and completely made my xorg the default. 
I went through that process several times, and now it's at least showing it on the nvidia settings. It wasn't before, but now suddenly it is after like 4 driver re-installations. 
Sometimes I think computeers like to just screw with us.
How would it make a difference whether I installed my driver once or four times????

well thanks man. This was getting pretty annoying.

---

### Post by Kellemora on 2008-11-09
Hi Maze

I'm not a programmer by any stretch of the imagination, hi hi....

But this is what appears to be happening to me, and it IS duplicatable.

Some configuration files are stored as BINARIES and it takes like three times of rebooting within a short time frame for the Binaries to be overwritten with the current configuration.

A good example of this is the Samba configuration file smb.conf
You can make changes to it until your blue in the face and it isn't going to make much difference if you are using Gnome.
Nautilus stores the Samba configuration file in /var/lib/samba
This file cannot be edited by humanoids its Binary.

When you boot up, the pooter reads THIS configuration file.
If you shut down and boot up again a second time within a short time, it will read the smb.conf instead for this session.
Next time you boot up, your back to square one again, because it's back to reading the binary config file.
But if you shut down a third time in a short time frame, the binary file is overwritten with the current smb.conf session.
So then after that, things start working right and seem to stay that way.
Or at least until the next time the Binary Configuration file gets updated.

The way I explained it may not be what's actually happening, but its how it appears to me as to what is happening inside the BLACK SMOKE Filled little 80 leg BUGS on the circuit board. hi hi.....

TTUL
Gary

---

