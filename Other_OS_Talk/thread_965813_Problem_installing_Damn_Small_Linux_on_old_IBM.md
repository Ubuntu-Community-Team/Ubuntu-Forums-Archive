---
title: "Problem installing Damn Small Linux on old IBM"
date: 2008-10-31
forum: Other OS Talk
---

### Post by Felixworks on 2008-10-31
I got an old IBM Aptiva 2180:) from my grandparents that's currently running Windows 3.1(not so well, I might add).  After looking through low-resource distros, I decided DSL is a good choice for the 450 MHZ processor, 16 MB RAM, and ~600 MB hard drive.

I downloaded and burned the ISO to a CD-R and I can't for the life of me figure out how to install it.  I'm not too keen on how to navigate Windows 3.1, as I'm used to a modern desktop GUI, and so I'm not sure if the CD is even showing up.  I went to the BIOS and there seem to be no boot options.  When booting up with the CD in, nothing changes and it acts completely normal.

So what's the problem?  Is it some sort of old-computer "feature" that I would feel stupid for not realizing?:)

---

### Post by zmjjmz on 2008-10-31
I really recommend using BasicLinux, DSL is too much for that oldie.
If you want to boot a CD though (BasicLinux comes on two floppies), look into Smart Boot Manager.

---

### Post by lukjad on 2008-10-31
If you want a really low resourse Live cd/OS, Try SliTaz. It uses 4 ***_megs_*** of RAM once installed to the hard drive. Just something to look into more.

Also, Puppy linux is supposedly **very** good at making old PCs new again.

As for DSL, I can't really help you there. I just thought that a few other light distros may help you choose.

---

### Post by tgalati4 on 2008-10-31
You need to make a DSL boot floppy.

---

### Post by Felixworks on 2008-10-31
Oh is it required that you use floppies on such an oldie?  Hehe I don't wanna dig through all my junk for floppy disks...  The *live* CD function is pretty much unnecessary for me.  Anyway, I'm planning to use that computer for light web browsing(is Youtube even possible???) and perhaps some attempts to code.  On a sidenote, most programming languages will still run on older machines right?

---

### Post by Bungo Pony on 2008-11-01
> I downloaded and burned the ISO to a CD-R and I can't for the life of me figure out how to install it. 

Your PC is newer than my IBM 300GL (which is a 200 MHz machine.) I'm quite surprised that you can't seem to find any boot options in the BIOS for your CD-ROM drive, since my old beast has the option to boot from CD. If your BIOS is anything like mine, the boot options are a bit goofy to get to. Just in case your BIOS is similar to mine, here's what I had to do:

Hit F1 for Config Setup
Goto "Start Options" and hit enter
Goto "Startup Sequence" and hit enter
Change both of the startup devices to CD-ROM and your second to HD.
Save changes and Exit.
Reboot with the CD in the drive, and it should go.

There are two ways to install DSL onto your computer. You can do it while running in DSL itself, however with only 16M of RAM, I probably wouldn't recommend it.

While the CD is booting, you will get a prompt for about 10 seconds or so. At this prompt, type "install" and hit enter. You will end up at a nice text menu that will give you options for installation. Follow the directions, and you should be good to go.

I've got DSL running off a 2G Compact Flash card, and it runs fantastic! It's also really quiet.

> You need to make a DSL boot floppy.

If you don't have a setting in your BIOS to boot from the CD-ROM drive, check your drive. I also believe you need a DOS CD-ROM driver for it to be recognized in Windows 3.1 (try oakcdrom.sys if you actually want to get that working.) You could also try swapping out drives and see if the drive is defective

If all else fails, you may have to make a boot floppy. You can use [Smart Boot Manager]("http://linux.simple.be/tools/sbm") which is useful for many things.

I would recommend against using DSL 4.x. I've found 3.x to be much more user friendly (but then again, I have an odd attachment to Fluxbox and that little mount tool. I also would NOT recommend using any Linux disto other than DSL unless you upgrade your RAM to 128M. I've tried SliTaz (doesn't boot), Puppy (won't run) and a couple others in less than 128M. DSL is really your best choice when it comes to having Linux on a low spec PC. Oh yeah, and you can install DOSBox in DSL, which basically makes it two OSes in one :)

---

### Post by zmjjmz on 2008-11-01
I still stand by BasicLinux, but you will not be able to watch youtube videos, at all.
BasicLinux has a recommended RAM requirement of 12MB, and there's something called loadlin.exe which loads BasicLinux in DOS and it only needs 3MB RAM.

---

### Post by Felixworks on 2008-11-01
Hmm, thanks for the input zmjjmz, but I looked into BasicLinux and it doesn't seem like what I want.  As for Bungo Pony, I'll try and mess around some more with some of those ideas, thanks for all the info!:)

---

### Post by zmjjmz on 2008-11-01
> **Felixworks said:**
> Hmm, thanks for the input zmjjmz, but I looked into BasicLinux and it doesn't seem like what I want.  As for Bungo Pony, I'll try and mess around some more with some of those ideas, thanks for all the info!:)

If you really need that kind of stuff, you could try doing a base CLI install of Debian sid, but even then a 600MB HDD seems a bit small.

---

### Post by darrelljon on 2008-11-01
Have you tried [DeLi]("http://www.delilinux.org/") Linux? [Linux.com review it here]("http://www.linux.com/articles/59489"). The [minimum system requirements]("http://www.delilinux.org/wiki/doku.php?id=announcement:generalnews:releases") for 0.7 are a 386 with 8Mb RAM.

---

### Post by zmjjmz on 2008-11-02
> **darrelljon said:**
> Have you tried [DeLi]("http://www.delilinux.org/") Linux? [Linux.com review it here]("http://www.linux.com/articles/59489"). The [minimum system requirements]("http://www.delilinux.org/wiki/doku.php?id=announcement:generalnews:releases") for 0.7 are a 386 with 8Mb RAM.

Unfortunately, þe latest one (0.8) needs 32MB RAM. (And even þen a swap partition.)

---

### Post by darrelljon on 2008-11-03
> **zmjjmz said:**
> Unfortunately, þe latest one (0.8) needs 32MB RAM. (And even þen a swap partition.)
Don't use the latest version then. Its still probably newer than Basic Linux.

---

### Post by Twitch6000 on 2008-11-03
here is a youtube video that helped me install DSL through terminal.

It works very well.

[http://www.youtube.com/watch?v=PhP17LPOCOU](http://www.youtube.com/watch?v=PhP17LPOCOU)

---

