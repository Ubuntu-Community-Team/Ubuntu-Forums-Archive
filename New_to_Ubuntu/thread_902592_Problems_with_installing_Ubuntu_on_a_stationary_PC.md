---
title: "Problems with installing Ubuntu on a stationary PC"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by Edgewalker_001 on 2008-08-27
My mther's old PC recently went through a hard drive crash and came back from the store two days ago with a new hard drive installed, but no OS, I tried to install ubuntu from an old live CD.

Anyhow, when I try to install, the GRUB screen comes up as usual, then the bouncing bar loading screen, and after that it seems to crash to terminal with the message: 
"BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)"

And then it starts displaying a parade of error messages once every few seconds, saying something about some four number/letter driver not working and asking me to try another one, now I've used ubuntu for almost half a year, but I'm still not exactly good at the command line, so basically, what should I do? 

The live cd worked on that same computer before, so whatever is wrong has to be tied to one of the two new components, the new hard drive or the new flatscreen monitor that's plugged in.

The old hard drive is supposed to still be inside, set to primary slave.

---

### Post by perlluver on 2008-08-27
> **Edgewalker_001 said:**
> My mther's old PC recently went through a hard drive crash and came back from the store two days ago with a new hard drive installed, but no OS, I tried to install ubuntu from an old live CD.

Anyhow, when I try to install, the GRUB screen comes up as usual, then the bouncing bar loading screen, and after that it seems to crash to terminal with the message: 
"BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)"

And then it starts displaying a parade of error messages once every few seconds, saying something about some four number/letter driver not working and asking me to try another one, now I've used ubuntu for almost half a year, but I'm still not exactly good at the command line, so basically, what should I do? 

The live cd worked on that same computer before, so whatever is wrong has to be tied to one of the two new components, the new hard drive or the new flatscreen monitor that's plugged in.

The old hard drive is supposed to still be inside, set to primary slave.

Sounds like it installed it on the old drive, and not the new one.

---

### Post by Hospadar on 2008-08-27
Try removing the old drive, if it's broken, it may well be causing problems.  After you've removed it and verified that the computer boots without it, try installing linux on the new drive, shut off the machine, reconnect the old drive, start up the machine and see what happens.  If things still don't work, try checking the jumpers on the old drive to verify that the drive is set to slave, and if that *still* doesn't work you probably just won't be able to use the old drive.

---

### Post by Edgewalker_001 on 2008-08-27
I just checked the BIOS setup screen, and apparently it only lists one hard drive, not two. The big problem for me is that I don't know which one of the hard drives is the new one and which is the old one, they do tend to look a lot alike...

As for the jumpers I thought of that too, when I checked them I can see that on one of the drives the jumper is set all the way to the left and on the other it is set all the way to the right, but there is no helpful little sticker put on that says which way means "master" and which means "slave"... I guess I really am a noob at this =P

So is there some universal code for jumper placement?

---

### Post by Hospadar on 2008-08-27
Typically the master drive will be at the very end of the big ribbon ide cable and the slave will be on the middle connector.  If you arn't sure, you could of course just try disconnecting each drive one at a time.

As for jumper settings, I doubt that is your problem, but if there's no helpful sticker you might just have to try every combo unless maybe you can find a manual from the manufacturer somewhere (unlikely) that tell you how to do it.  Sometimes drives have the same jumper settings, but often different manufacturers and models have totally different settings.  I've seen jumpers all over the place.

Here's a little guide on attaching IDE drives. [http://www.mikeshardware.com/howtos/howto_connect_ide_hd.html](http://www.mikeshardware.com/howtos/howto_connect_ide_hd.html)

Alternatively, you might also want to see what happens with no drives at all attached.  Assuming the problem is with your drive(s) the livecd should boot just fine with no drives at all attached (obviously you wouldn't be able to install but you might be able to isolate your problem)

---

### Post by Edgewalker_001 on 2008-08-27
I tried removing one of the drives (Pulled the power cable) and now it's installing perfectly, I'll try reformatting it and installing Ubuntu right away.

Ummm... One thing, the drive I removed was the end one, so the one I'm reformatting right now might be the old one...

Is the master drive *always* at the end of the cable?

---

### Post by lazyart on 2008-08-27
> **edgewalker_001 said:**
> i tried removing one of the drives (pulled the power cable) and now it's installing perfectly, i'll try reformatting it and installing ubuntu right away.

Ummm... One thing, the drive i removed was the end one, so the one i'm reformatting right now might be the old one...

Is the master drive *always* at the end of the cable?

yes.

---

### Post by Edgewalker_001 on 2008-08-27
Well, on the plus side this means the old drive isn't as toasted as everyone thought, but on the minus side it means the whole installation problem lies with the new drive.

So if I install Ubuntu on the old drive, how should I get the new drive to work with it?

---

