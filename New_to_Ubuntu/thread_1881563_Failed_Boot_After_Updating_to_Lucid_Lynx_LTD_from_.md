---
title: "Failed Boot After Updating to Lucid Lynx LTD from Hardy Heron LTD"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by Samsonator on 2011-11-15
Hello there.  First off, let me quickly thank everyone in the community for the help I've received over the years. I still haven't got a solid grasp on everything, and I couldn't immediately find a thread already on this--so please redirect me to any links of someone experiencing the same problem, rather than cause any redundancies.  Anyway, here's what's going on,

I have a studio 1535 and I'm running Hardy Heron and tiny xp.  Before this problem started I installed hardy heron on multiple partitions (quite accidentally), so I still have a partition running HH (without all my files and whatnot, just a partition I didn't use, the partition I SHOULD have tried updating to LL with).  So I updated to LL  on my main partition, and when all was "said and done" and I went to do that first reboot I was given this for a message::

libudev: udev_monitor_new_from_netlink: error getting socket

init: ureadahead main process (2952)

init: mountall main process (2964) killed by ABRT signal

A maintenance shell will now be started

root@sam-laptop:~#

Any thoughts?  Thanks in advance, and I apologize if this is the wrong forum and/or a redundant topic.         --Sam

---

### Post by Bucky Ball on 2011-11-15
Open the working Hardy, open a terminal and run:

```
sudo update-grub
```That should pick up all installs and allow you to boot into Lucid. See if it makes a difference. Not sure if you are getting the option to choose the Lucid upgrade from the grub list at boot or not. The ureadahead message ignore. 

When you get to the maintenance shell, what happens when you input:

```
startx
```?

ps: LTS (long-term support) rather than LTD ... ;)

---

### Post by Samsonator on 2011-11-15
Thanks Bucky.  I am not seeing Lucid Lynx in the grub menu amongst the kernals , just Hardy Heron, including the one I tried to update.  I ran the grub update which I had tried before I think, and rebooted and tried to no avail.  start x in the terminal produces: 

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.

I don't know where else to put it, in gnome it produced a list of items/phrases and using the command line in the grub menu it didn't recognize the command.  Would it be easier to try a fresh install and recover my files from the old partition somehow?

Good call on the LTS,maybe I was thinking about that canadian ltd....

---

### Post by Bucky Ball on 2011-11-15
Hmmm. See, it's hard to know which install is actually producing the grub list when you boot. That is obviously the partition you need to update grub on and then it will pick up Lucid and add it. Probably you first (main) install which is the one you can't get to boot. You could try installing Boot-repair and running it in the working install which would give control of the grub to the working Hardy install. That is available in Synaptic Package Manager.

* I wouldn't go for a reinstall just yet ... ;)

---

### Post by Samsonator on 2011-11-16
Do you mean SASH - stand alone shell?  that's what comes up when I search for boot repair with all the repositories checked.  I installed it but don't really know where to go from there.

---

### Post by Bucky Ball on 2011-11-16
Ok. I use Xfce, so bit different to your Ubuntu setup, but try System>Administration>Boot Repair and run it ... It should give the grub to the install you are running it from (remember this) and find and add the Lucid install.

---

### Post by Samsonator on 2011-11-21
I don't think boot-repair can be installed/run on hardy heron...

---

### Post by Bucky Ball on 2011-11-21
> **Samsonator said:**
> I don't think boot-repair can be installed/run on hardy heron...

Yes it can, not a problem. Not sure where the heck you got that from. If for some absolutely unknown reason you're having a problem you can even download boot-repair ISO, make a CD, boot from that and fix your grub.

Boot repair is independent of the release you're using. Please supply the proof for your claim. ;)

---

