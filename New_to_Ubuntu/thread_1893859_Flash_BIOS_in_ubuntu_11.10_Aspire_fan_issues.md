---
title: "Flash BIOS in ubuntu 11.10 Aspire fan issues"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by Yanook on 2011-12-11
Hi everyone, this is probably just newbie noise, but...

I've installed ubuntu 11.10 on my acer aspire 5715z and it's grrreat but because of a design flaw, the aspire's fan only works with windows. Therefore my system overheats and the machine clicks off after 30 mins.

I heard that:
a) you can solder the fan wire to the usb power supply - I don't want to do this as I'm afraid it will burn out the fan.

b) you can try to update your bios from a CDRW pretending to be a floppy. I have acquired a freedos iso and the latest bios from acer (that actually downloads!), but the files are too big to fit on an iso image of a floppy.

c) you can use GRUB to update your bios, as explained in a great post on this forum (flash bios - the ubuntu way), but it also says here that grub2 users cannot follow the instructions given. I checked and I have grub 2. I looked at the manual but understand not a lot.

Can anyone help me? I am an absolute beginner 24 hours into my first ubuntu install and I still can't get up and running. 

:confused:

Thanks in advance...

---

### Post by Frogs Hair on 2011-12-11
Hello and Welcome 

I would rule out the first possible solution unless the work is done by a shop and that may void any warranty .

My user built desktop has an Asus board and they have different methods for updating the Bios depending on the board . I recently updated mine with an external floppy . 

Some Asus boards use update software that is only Windows compatible and can not run with Wine . 

Here is a method I found but make sure there is some benefit to updating the Bios . Asus has release notes that describe the updates . 

[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

---

### Post by Yanook on 2011-12-11
Thanks!

Sadly, I tried that method, but the Acer BIOS files are 1.5 MB total. They don't fit on a disk image...

So am I off to the welding shop, or is there another way? ;)

---

### Post by lechien73 on 2011-12-11
Have you tried a 2.88Mb boot disk instead? You can download one from here [http://www.fdos.org/bootdisks/](http://www.fdos.org/bootdisks/). Remove the DOS folder to make some room, and then try following the instructions at the previous link ([http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)).

---

### Post by Mark Phelps on 2011-12-11
You're asking to completely trash your PC -- since badly flashing a BIOS is one of the few things that can actually trash a PC, turning it into an electric "brick".

The problem you're most likely running into is a know bug with the recent Ubuntu kernel versions.  If you're patient, this will eventually be solved.

If you keep thrashing around like this, you'll end up with a useless piece of junk.

---

### Post by Glenn nl on 2011-12-11
I hope you are using Chromium so you can translate this in a click: [https://sites.google.com/site/computertip/biosflitsen](https://sites.google.com/site/computertip/biosflitsen)

---

### Post by Yanook on 2011-12-11
> **Mark Phelps said:**
>  The problem you're most likely running into is a know bug with the recent Ubuntu kernel versions.  If you're patient, this will eventually be solved.

Thanks Mark - I'd rather not toast my laptop on our first journey into Linux land - but where is the discussion of the known bug? If I could follow it, I'd feel better about waiting it out. Otherwise, everything I've read seems to indicate that the problem is with the aspire series, not with ubuntu... or do you know otherwise?

---

### Post by Yanook on 2011-12-11
> **lechien73 said:**
> Have you tried a 2.88Mb boot disk instead? You can download one from here [http://www.fdos.org/bootdisks/](http://www.fdos.org/bootdisks/). Remove the DOS folder to make some room, [/url]).

Thanks man,

Running...

*gibbers...sweats...

That's got it! BIOS is V1.42, ubuntu works like a dream and so does the system fan. Don't know how to thank you. Definitely endorsing your job app...

woo-hoo!:D

---

### Post by lechien73 on 2011-12-11
Yay!! Cool :D I'm glad it worked for you.

Thanks too for the comment in the membership thread. I want to be able to give back a bit more to the community, so the support is appreciated.

If you get chance, could you mark this thread as [SOLVED] using the **Thread Tools** menu at the top of the page?

Thanks again...enjoy your new installation :)

---

