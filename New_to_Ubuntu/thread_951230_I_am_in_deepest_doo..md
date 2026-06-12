---
title: "I am in deepest doo."
date: 2008-10-17
forum: New to Ubuntu
---

### Post by General Douchebag on 2008-10-17
I am currently on a Macbook Pro. I, using OS X Leopards' Boot Camp, also installed Windows Vista Business, foolishly giving the sole OS I intended to use only 25GB of space. I have since, to acquire space, unwittingly deleted the Mac half of my laptop. Up until I tried to install Ubuntu, it wasn't a big deal. I still had to wait for the white screen before Windows began to load, and I still had to be subjected to the irritating noise Macs make when they start, like someone's lying on a church organ. I have now realised that since my Mac has no BIOS, I cannot use this to boot from the CD and install Ubuntu. Nor can I use the commands for Mac's EFI, because I no longer have Mac. I would call this a serious mistake, but had I not deleted Mac, I'd only be able to dedicate 5MB to Ubuntu, which simply wouldn't work at all either. Can anyone offer any advice?

---

### Post by Keen101 on 2008-10-17
> For Ubuntu, which is based on Debian Linux, the bootstrap loader - the program that decides which OS you want to boot - the program that controls that first few seconds of your computer startup is called yaboot and it's actually a project that lives at [http://penguinppc.org/bootloaders/yaboot/](http://penguinppc.org/bootloaders/yaboot/).

To modify yaboot so that the default operating system is actually Mac OS X isn't too hard. There&#65533;s a great yaboot reference document online at the yaboot site. It turns out that the change is trivially simple: in the file /etc/yaboot.conf on the Linux side of things, you simply needed to add the line defaultos=macosx.

The second - and critical - step is to actually install the new bootstrap loader configuration file, and that&#65533;s done with ybin -v which figures out where the new configuration file should be moved and does it.

And keep your eyes open as you go along: the most amusing line in the entire process is the output statement &#65533;Blessing /dev/hda6 with Holy Penguin Pee&#65533;. Only in the world of Linux! 

Those mac systems have a different program to a BIOS. I don't know much about them, but there should still be a way to install ubuntu. try to put the CD into your drive, and power on the Apple Mac. Hold the 'c' key until the live-cd of Ubuntu is loaded.

---

### Post by General Douchebag on 2008-10-17
The thing is, I accidentally deleted the mac partition, so those hotkeys for the EFI don't work.

---

### Post by Keen101 on 2008-10-17
we'll i don't know much about macs, but i will keep trying to help you.

have you tried holding down just the option key on boot up to show available boot options?

if that doesn't work, try to restart your computer, hold down Command-S while it is booting up. If this command works it should get you to a bash like shell prompt for macs. you may be able to then use some commands.

--------------------

if there is absolutely no way to access any mac terminal or bios type thing, then you could try installing ubuntu on windows with WUBI. I've heard that after a wubi install, there is an option to install ubuntu to a dedicated partition.

i also heard you could fix one mac through the firewire port on another mac.
[http://macamour.com/blog/2007/11/07/installing-os-x-via-the-target-disk-mode/](http://macamour.com/blog/2007/11/07/installing-os-x-via-the-target-disk-mode/)

---

### Post by friendofpugs on 2008-10-17
Dude, poo is right. You've got one expensive paper weight now. :(

---

### Post by General Douchebag on 2008-10-17
Not really, I just can't change the boot order. I suppose, if the advice doesn't work (I haven't tried it yet, I'm burning the CD again at 1x, just in case.) then I'll just have to live without Ubuntu.

---

### Post by schiznik on 2008-10-18
try a mac forum maybe? as far as I understand EFI from my G4 powerbook (dual boots OSX & ubuntuPPC), is that it is like the bios (as in on a chip), but fancier. I have yaboot on there, and EFI certainly runs *before* yaboot does the OS selection.

It'd be stupid to have a "broken"/unbootable computer just from deleting the primary OS...

Have a look at [http://refit.sourceforge.net/](http://refit.sourceforge.net/)

---

### Post by General Douchebag on 2008-10-18
I just held down Op, and it showed the Ubuntu CD! But then the keyboard locked up and I just get trapped at the language select screen.

---

### Post by mkvnmtr on 2008-10-18
Why can't you backup everything you need on you windows os and then reinstall the Mac os from the disks? Then you can proceed to install Windows and Ubuntu like you want. When you finish you will be using yaboot to startup. Then if space is a problem you can reformat the Mac partition for use as a shared partition.

---

### Post by General Douchebag on 2008-10-18
I have nowhere to back up to, and I've figured out how to access the CD. All I have to do is hold op, the same as when I was running Boot Camp. But now that I'm on the main page, it won't let me install it. When I select install or run from CD the disk just whirs and then stops, but nothing else happens.

---

### Post by Keen101 on 2008-10-18
I hate to say it, but the alternate install cd might work better.

Anyway, don't give up.

These might help. I'm sure there are more if you look too. There is also a genuine mac forum here on ubuntu forums too.

[http://modular.math.washington.edu/macbook/](http://modular.math.washington.edu/macbook/)

[http://ubuntuforums.org/showthread.php?t=198453](http://ubuntuforums.org/showthread.php?t=198453)

---

### Post by ppc_guy on 2008-10-19
While never having a macbook pro, you are dealing with a truly "new world" machine. So you still have openfirmware.. Or mac's answer to bios. When I installed Ubuntu on a pwnd G4 I had to flash the pram a few times. To do this power on a hold apple-option-p-r @ the same time. Let the computer bong a few times. Then restart, from there you need to get into openfirmware. To do this when powering the machine on hold apple-option-o-f. Once you are into the whitesceen black text world type boot cd and see what happens. Either A. You will be able to boot from the Ubuntu iso disk there, or it will fault out.. No worries either way. If it does fault, reboot and hold c. See if the ubuntu disk boots. Took a few times for me. Also as a side note, in loading ubuntu on many old and new world macs I've found that CD-R's don't play well for some reason and don't ask me why CD-RW's burned SLOW seems to be the key.

As always, your mileage may vary,
ppc_guy
----------------------------------------------------------------------
When you are Sierra-Oscar-Lima. I'm Hotel-Tango-Hotel.
----------------------------------------------------------------------

---

