---
title: "Persistent with new daily build??"
date: 2011-06-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2011-06-05
Persistent with new daily update??  I'm running 5 June after having run 4 June in persistent mode - 

Do I have to wipe out casper-rw when there's a new daily build??

Alpha 1 plus, i.e. latest daily build Live mode as booted from .iso with Grub2, is somewhat usable and quick running in memory, 

Does somehow persistent mode realize that something in casper-rw has been updated in the daily build and needs replaced?

Anyway it's working for now and allows me to run latest Oneiric Ocelot without dread install screwing up my triple boot Windoze 7, Natty Narwhal, and reliable Meerkat.

Jerry

---

### Post by fjgaude on 2011-06-06
> **jerrylamos said:**
> Persistent with new daily update??  I'm running 5 June after having run 4 June in persistent mode - 

Do I have to wipe out casper-rw when there's a new daily build??

Alpha 1 plus, i.e. latest daily build Live mode as booted from .iso with Grub2, is somewhat usable and quick running in memory, 

Does somehow persistent mode realize that something in casper-rw has been updated in the daily build and needs replaced?

Anyway it's working for now and allows me to run latest Oneiric Ocelot without dread install screwing up my triple boot Windoze 7, Natty Narwhal, and reliable Meerkat.

Jerry

I see you haven't gotten a reply... question: how do you Live mode boot from an .iso using Grub2, please. <smile>

---

### Post by jerrylamos on 2011-06-06
> **fjgaude said:**
> I see you haven't gotten a reply... question: how do you Live mode boot from an .iso using Grub2, please. <smile>

Booting .iso running pretty well here - given the usual things that don't work on an Alpha.  Look at my thread:

[http://ubuntuforums.org/showthread.php?t=1769956&highlight=boot+.iso](http://ubuntuforums.org/showthread.php?t=1769956&highlight=boot+.iso)

So I boot something reliable like Narwhal, navigate to /boot/iso on /dev/sda1 or wherever you choose, do a zsync, then reboot to test out to see how good/bad the daily build is.

So far persistent is saving my settings O.K. but as usual on an Alpha hang on to your hat.

Enjoy,

Jerry

---

### Post by fjgaude on 2011-06-06
Thank you, Jerry! I'll give it a go, on one of my three hard drives, not one that is bootable.

Sure is nice to have helpful folks like you around.

Some time has passed.

I did it all and it booted up to a point, where it failed to bind, address already in use. Error binding udev-control socket, stopping.

Touching a key I saw many more lines showing how far it got. I'll study to see if I can figure out what the hang up is.

Thanks again, Jerry, for pointing me to the forum messages where all this is being tried out. What a trip! Fun, fun!

---

### Post by jerrylamos on 2011-06-06
> **fjgaude said:**
> 

I did it all and it booted up to a point, where it failed to bind, address already in use. Error binding udev-control socket, stopping.
I don't seem to get that one.  There's lots of complaints as it boots up, and it stops for a while here and there, but does get up eventually.

Jerry

---

### Post by fjgaude on 2011-06-06
I'll keep doing it your way each day with the new daily builds. We'll see what happens.

Nonetheless, the boot iso technique works!

---

### Post by fjgaude on 2011-06-07
Well, the boot grub iso works... but any saved options are not saved on reboot. Is this your experience?

---

### Post by jerrylamos on 2011-06-07
> **fjgaude said:**
> Well, the boot grub iso works... but any saved options are not saved on reboot. Is this your experience?

I have a separate 1G partition formatted ext3 with the label 

casper-rw

Also on booting the 40_custom grub entry includes persistent as follows:
```

menuentry "Ocelot iso on sda1" {
set isofile="/boot/iso/oneiric-desktop-i386.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz boot=casper persistent iso-scan/filename=$isofile noprompt noeject 
initrd (loop)/casper/initrd.lz
} 

```

Seems to save most settings.  I don't know about updates since I'm doing zsync most days.

Jerry

---

### Post by iClouseau88 on 2011-06-07
Hello,

What is "persistent mode"?

Secondly, could you give me link(s) to tips/tutorials on running oneiric daily builds on persistent mode?

Thanks a lot for your help.

---

### Post by jerrylamos on 2011-06-07
Take a look at this:

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

Now a lot of use of persistent is with a 2G USB stick, with two partitions one for boot as made with Ubuntu startup disk creator, and the other formatted ext3 and labelled casper-rw.

I find a folder on the hard drive with the .iso plus a separate casper-rw partition a lot easier and quicker than fussing with USB sticks.

An Alpha can and will trash things, so backup anything you want to save.  My experience the chief thing that trashes my hard drives is "install".  Booting the .iso from the current daily build gets you up and running the latest Ocelot so you can experience the bugs first hand, with less danger of trashing hard drives.

Jerry

---

### Post by fjgaude on 2011-06-07
Will do, and I've been testing Alphas and Betas for a long time. I never install an Alpha. <smile>

As time goes on will keep you posted as to what I'm doing, you do the same.

Thanks again for being.

---

