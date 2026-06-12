---
title: "I Need A Tiny Linux Distro For A Machine That Otherwise Has No Hope"
date: 2008-02-07
forum: Other OS Talk
---

### Post by k1dicarus on 2008-02-07
Hey Everyone,

I just have a question for those of you who enjoy challenges:

I have scoured the internet and chased my tail for hours now trying to find the best small linux distro for my mother-in-law's laptop ((and more importantly, how to install...)). It is an old Dell Latitude. Terrible computer. This thing has no CDROM, a 2GB HD, 128MB RAM, and a P3 750MHz processor. It does have a floppy drive, however (Score!). It also has 1 USB port ((I have a 2GB USB flash drive I can try to work with)). And some ridiculous person installed XP on it!

Anyway, I've been thinking about installing DSL on it. DSL seems like a very nice distro for what you get. ((Does anyone disagree? Have any suggestions?)) I'll also probably need some help with making a boot floppy if anyone here is familiar with that because the computer's BIOS doesn't support USB booting ((are there any other methods?)).

I hope I'm posting this in the right place, and thanks SO MUCH for your help and attention, folks!

Icarus

---

### Post by exploder on 2008-02-07
Why not try putting Fluxbuntu or the Mint Fluxbox Community Edition beta on the  flash drive and install ?

Both of these should run fine with the hardware and it would be very functional.

---

### Post by Andrew Stone on 2008-02-07
Well, this forum is only for Ubuntu, so you haven't really posted to the right place,  However, let me say that the stripped down Xubuntu is still a bit heavyweight for your system.  It requires 192 meg.  I evaluated DSL, but did not like it because it was just too custom.  I couldn't install the stuff I needed due to lack of package manager support, use of 2.4 kernel etc.  DSL is for REALLY small computers

I would try zenwalk ([www.zenwalk.org](www.zenwalk.org)).  It has a nice desktop and package management system (it's slackware), and uses the 2.6 kernel.  I am happily running it on a Gateway P2 400mhz with 96MB ram.

---

### Post by K.Mandla on 2008-02-07
> **k1dicarus said:**
> Hey Everyone,

I just have a question for those of you who enjoy challenges:

I have scoured the internet and chased my tail for hours now trying to find the best small linux distro for my mother-in-law's laptop ((and more importantly, how to install...)). It is an old Dell Latitude. Terrible computer. This thing has no CDROM, a 2GB HD, 128MB RAM, and a P3 750MHz processor. It does have a floppy drive, however (Score!). It also has 1 USB port ((I have a 2GB USB flash drive I can try to work with)). And some ridiculous person installed XP on it!

Anyway, I've been thinking about installing DSL on it. DSL seems like a very nice distro for what you get. ((Does anyone disagree? Have any suggestions?)) I'll also probably need some help with making a boot floppy if anyone here is familiar with that because the computer's BIOS doesn't support USB booting ((are there any other methods?)).

I hope I'm posting this in the right place, and thanks SO MUCH for your help and attention, folks!

Icarus
It shouldn't be too hard to do. See if Smart Boot Manager will allow you to boot from that USB port, even if the BIOS won't. Also, there are PCMCIA adapters that you can connect to a CDROM, and possibly get an external CD drive going that way. If either of those is true, you're golden.

And if worst comes to worst, you can pull out the hard drive and transplant it into another machine to get you started. 

Does it have a network connection? Can you boot across a network? Some of the old laptops supported PXE boots; my I8000 does and I think my old CPx did too.

Don't forget there are installers that will work from within Windows, which means you could install any garden-variety Linux with XP as an accomplice. :twisted:

After that it's just a choice of which distro you want. DSL is underweight for that, unless you happen to prefer it. Some people will tell you Xubuntu is a good fit; personally I won't run Xubuntu on anything slower than 1Ghz now that it's so fat.

After that you might try Wolvix or Mepis AntiX, or you could build it yourself from a minimal Ubuntu installation. Feel free to ask questions, there are thousands of folks here willing to offer tips. Cheers and good luck!

---

### Post by Pogeymanz on 2008-02-07
I would recommend DSL anyway. Your processor and RAM can handle bigger distros, but your HD cannot. Even fluxbuntu will take 1.3GB, whereas DSL will take a lot less. It will run like lightning with DSL, though. I think you can install it from within Windows, but I've never done it myself.

---

### Post by init1 on 2008-02-07
> **k1dicarus said:**
> Hey Everyone,

I just have a question for those of you who enjoy challenges:

I have scoured the internet and chased my tail for hours now trying to find the best small linux distro for my mother-in-law's laptop ((and more importantly, how to install...)). It is an old Dell Latitude. Terrible computer. This thing has no CDROM, a 2GB HD, 128MB RAM, and a P3 750MHz processor. It does have a floppy drive, however (Score!). It also has 1 USB port ((I have a 2GB USB flash drive I can try to work with)). And some ridiculous person installed XP on it!

Anyway, I've been thinking about installing DSL on it. DSL seems like a very nice distro for what you get. ((Does anyone disagree? Have any suggestions?)) I'll also probably need some help with making a boot floppy if anyone here is familiar with that because the computer's BIOS doesn't support USB booting ((are there any other methods?)).

I hope I'm posting this in the right place, and thanks SO MUCH for your help and attention, folks!

Icarus
Yeah the specs aren't too bad, i've gotten a few distros running on an older laptop. The issue is the lack of CD drive. There are a few floppy distros that can mount USB drives. You may be able to run one of those and then install a distro from a tar achieve on a USB drive. 
The other option is FreeDOS. It's really much lighter than you need on such a computer, but it'll run great and only needs a floppy drive. You can play quite a few games on it. If you would like I could make a floppy image for this purpose. 
[www.freedos.org](www.freedos.org)

---

### Post by Midwest-Linux on 2008-02-08
> **k1dicarus said:**
> Hey Everyone,

I just have a question for those of you who enjoy challenges:

I have scoured the internet and chased my tail for hours now trying to find the best small linux distro for my mother-in-law's laptop ((and more importantly, how to install...)). It is an old Dell Latitude. Terrible computer. This thing has no CDROM, a 2GB HD, 128MB RAM, and a P3 750MHz processor. It does have a floppy drive, however (Score!). It also has 1 USB port ((I have a 2GB USB flash drive I can try to work with)). And some ridiculous person installed XP on it!

Anyway, I've been thinking about installing DSL on it. DSL seems like a very nice distro for what you get. ((Does anyone disagree? Have any suggestions?)) I'll also probably need some help with making a boot floppy if anyone here is familiar with that because the computer's BIOS doesn't support USB booting ((are there any other methods?)).

I hope I'm posting this in the right place, and thanks SO MUCH for your help and attention, folks!

Icarus


750 Mhz  processor is more than what several of my computers have. Add a CD/RW Drive, throw another 384 MB RAM in there and add a 40 GB hard drive and then wireless , now you have a great computer for Linux or  XP.

---

### Post by dptxp on 2008-02-08
use puppy linux.

---

### Post by kerry_s on 2008-02-08
i would go for a debian custom install. it would be more up to date than dsl, you can choose what goes in it, you only have to install it once and it can be kept updated with apt-get or synaptic.
[http://www.debian.org/releases/stable/i386/index.html.en](http://www.debian.org/releases/stable/i386/index.html.en)
[http://cdimage.debian.org/debian-cd/current/i386/iso-cd/debian-40r2-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/current/i386/iso-cd/debian-40r2-i386-businesscard.iso)

might help more-> [http://www.pendrivelinux.com/2007/11/21/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/2007/11/21/use-a-floppy-to-boot-usb-pendrive-linux/)

if it were me, i would pull the drive, borrow a laptop to install with, then put the drive back, done.

you want to at least give her the same functions your taking away, otherwise just leave xp, but trim it down.

---

### Post by hellion0 on 2008-02-08
I'll second the Debian custom install. All you need is one floppy to start and a network connection to finish. Was that HD space a typo, though? Only TWO gigs? People usually are giving away drives with more space than that...

---

### Post by KCPokes on 2008-02-08
Honestly those specs aren't horrible.  I have a 266Mhz laptop that is still running, so you definitely have some options.  

Personally I'm not a huge fan of DSL or Puppy.  I'd consider a Debian install or Arch.  I am a big fan of Arch as you get from it what you put into it.  Its a bit of a challenge to get it set up, initially, but the results are worth it.  It is what brought my 266 back to life.

---

### Post by edd07 on 2008-02-08
Come on! That computer's not bad at all! :-P
I've installed Ubuntu (yes, GNOME and all) on a very similar computer, only difference was the HD space, mine had 3GB. Of course, it was kind of unusable, but Xubuntu ran pretty fast. Evend with compositing (this slowed it down, but it was usable).

So, you've got a lot of options, the only problem I see is the HD. Maybe you could use the HD for OS only and use that 2GB USB stick of yours for data.

Good Luck

---

### Post by Bungo Pony on 2008-02-08
I'd go with TinyFlux. It's a really nice distro, shouldn't take up too much HD space, and I believe it can be put onto a flash drive.

Following that, I'd probably go with DSL. Puppy would also work, but I'm personally not a big fan of it.

You could also do yourself a favor and pick up an external CD-ROM drive instead of farting around with flash drives. I find my external drive useful for computers with no CD rom drive. I bought mine used for $4. It's a 8x read, 4x write (yeah, a burner!) and it works great. You may have to dual boot with DOS to get it working though. I haven't used it to install Linux (yet), but who knows what the future holds!

---

### Post by timzak on 2008-02-08
> **k1dicarus said:**
> Hey Everyone,

I just have a question for those of you who enjoy challenges:

I have scoured the internet and chased my tail for hours now trying to find the best small linux distro for my mother-in-law's laptop ((and more importantly, how to install...)). It is an old Dell Latitude. Terrible computer. This thing has no CDROM, a 2GB HD, 128MB RAM, and a P3 750MHz processor. It does have a floppy drive, however (Score!). It also has 1 USB port ((I have a 2GB USB flash drive I can try to work with)). And some ridiculous person installed XP on it!

Anyway, I've been thinking about installing DSL on it. DSL seems like a very nice distro for what you get. ((Does anyone disagree? Have any suggestions?)) I'll also probably need some help with making a boot floppy if anyone here is familiar with that because the computer's BIOS doesn't support USB booting ((are there any other methods?)).

I hope I'm posting this in the right place, and thanks SO MUCH for your help and attention, folks!

Icarus

Those are very interesting specs.  I have a Dell Inspiron laptop with only a 650Mhz P3, but it has a CD drive, 9GB HD, and 384MB RAM.  Gutsy runs fine on it (I disabled some items in Sessions and Services so it only uses ~110MB at startup).  I agree with the others that the HD is the main bottleneck.  If you could fit Gutsy on there, it would run okay.  Is upgrading the HD an option?  Maybe borrow an external CD to do the install?

---

### Post by k1dicarus on 2008-02-08
You guys have been a huge help. So much information! I'm going to go over all these options and try some things, and then I'll post the results.

Thanks again,
Icarus

---

### Post by VCSkier on 2008-02-08
I would recommend Mepis AntiX.  With those specs, I think fluxbox would be the ideal window manager, and I think AntiX is the most complete implementation of it.  Fluxbuntu would be good for too, but I don't think its quite as complete as AntiX yet.

---

### Post by whitefang5412 on 2008-02-08
I would try puppy linux. I have a fairly old 4 year old desktop. I'm either going to install windows vista on it or puppy linux. Chances are puppy linux, even though my plans my change around. Just depends on what I can do with a 64 bit version of ubuntu. Try puppy linux for sure.

EDIT: I forgot to mention gOS if the person doesn't mind having most of thier things saved online, and it doesn't have such a crappy looking desktop to boot.

---

### Post by anticapitalista on 2008-02-09
You could try the antiX-base (178MB) version for more control over what you want to install or the 'full' version (310MB)

---

### Post by Chilli Bob on 2008-02-09
Puppy would fly on that machine, plus it's easier to use out of the box than anything else I've tried.

---

### Post by DJiNN on 2008-02-10
antiX or TinyMe. Both really lightweight, but have all the progs that you could need, & if they're not installed  already they're only an "apt-get" away. :)

---

### Post by chris4585 on 2008-02-12
PCFluxOS is pretty good and lightweight

---

### Post by andrewjoy on 2008-02-15
I would go for vector linux its slackware based and runs realy well its also designed for lower end system i got it working on a 96mhz P1 but that was an older version if it.

[http://www.vectorlinux.com/](http://www.vectorlinux.com/)

Try out VL - Lite but the normal version works jsut fine.

---

