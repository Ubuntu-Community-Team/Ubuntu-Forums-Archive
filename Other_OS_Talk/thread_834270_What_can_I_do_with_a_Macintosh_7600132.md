---
title: "What can I do with a Macintosh 7600/132"
date: 2008-06-19
forum: Other OS Talk
---

### Post by Bungo Pony on 2008-06-19
So, I inherited this Macintosh 7600/132. It's got Mac OS 9.1 on it. It's kinda neat, but the OS is a bit on the bland side :)

My question: is it worth putting a version of Linux on this thing, or is it more useful with MacOS on it? If it's worth a Linux install, which version would work well?

I tried to see if I could get a live CD to boot on it, but I couldn't do it. I'm guessing there's a few tricks I need to know to get around the OS and the hardware.

---

### Post by Midwest-Linux on 2008-06-19
> **Bungo Pony said:**
> So, I inherited this Macintosh 7600/132. It's got Mac OS 9.1 on it. It's kinda neat, but the OS is a bit on the bland side :)

My question: is it worth putting a version of Linux on this thing, or is it more useful with MacOS on it? If it's worth a Linux install, which version would work well?

I tried to see if I could get a live CD to boot on it, but I couldn't do it. I'm guessing there's a few tricks I need to know to get around the OS and the hardware.

 OS 9 in my opinion is obsolete. However looking at the approximate specs at

[http://www.everymac.com/systems/apple/powermac/stats/powermac_7600_132.html](http://www.everymac.com/systems/apple/powermac/stats/powermac_7600_132.html)

132 Mhz and 16 MB Ram is pretty narrow for a modern distro. I think even Ubuntu 7.04 PPC needs at least 128 MB ram. I highly doubt Puma or Panther. OSX would run on it. But may I suggest the Ubuntu PPC forum and maybe repost there or ask the mods to move the thread for you. 


If you want to attempt Ubuntu 7.04 PPC, use the ALTERNATE INSTALL CD version. I mention the 7.04 because I had the least trouble installing it on a pair of IMacs. If you can increase the RAM to 128MB or better, then 7.04 might run on it. 

 On the positive side there are Linux programs that can run on older PC's which Ram as low as 16 to 30 MB. And I am almost positive that there are lightweight PPC versions of Linux OS than can run on Ram below 50 MB.

---

### Post by Bungo Pony on 2008-06-19
I don't care that it's not Ubuntu running on it. I wanted to try booting my DSL live CD on it, but couldn't figure out how to do it. I think it's the Mac architecture that's preventing me from booting a non-Mac CD on it. In other words, the problem is me not knowing enough about Macs.

I really like the idea of RCA jacks and S-Video on the back of the Mac, and would love to put it to some good use. There also seems to be an internal sound card in the unit.

This particular machine has 48M of RAM in it. The boot time of MacOS is pretty pathetic though.

Any chance of installing FreeDOS on this thing? (Probably not) :D

I may just take it apart for the SCSI drives and install them into an old PC-XT.

---

### Post by bashveank on 2008-06-19
Just keep it around as a neat relic.

---

### Post by kool_kat_os on 2008-06-19
> **bashveank said:**
> Just keep it around as a neat relic.

ya...it will become a collectible...

---

### Post by zmjjmz on 2008-06-19
Maybe you can go for a stripped down old (woody, like DSL) version of DebianPPC.

And I think you hold down C at bhttp://www.alaska.net/~erbenson/doc/mac-fdisk-basics.txtoot for it to get to a CD.

EDIT: I googled Macintosh 7600/132 Linux , got a few interesting links (including something for NetBSD...) among them : [http://linux.derkeiler.com/Newsgroups/alt.os.linux/2004-02/0526.html](http://linux.derkeiler.com/Newsgroups/alt.os.linux/2004-02/0526.html)

EDIT2: #debianppc on irc.freenode.net

EDIT3: Even moar [http://www.alaska.net/~erbenson/doc/mac-fdisk-basics.txt](http://www.alaska.net/~erbenson/doc/mac-fdisk-basics.txt)

EDIT4: Moar links: [http://groups.google.com/group/linux.debian.ports.powerpc/browse_thread/thread/65372ab9968854ef](http://groups.google.com/group/linux.debian.ports.powerpc/browse_thread/thread/65372ab9968854ef)
[http://ubuntuforums.org/archive/index.php/t-474074.html](http://ubuntuforums.org/archive/index.php/t-474074.html)

EDIT5: [http://forums.gentoo.org/viewtopic-p-3754199.html?sid=351efd2d9ae60a1282694dce009619fa](http://forums.gentoo.org/viewtopic-p-3754199.html?sid=351efd2d9ae60a1282694dce009619fa)

---

### Post by K.Mandla on 2008-06-19
I think I had something similar to that a little while ago. It was a functional Internet surfer with 6.06 on it. Mine might have been a a little faster than that, but it could still do a few things.

Need a torrent seeder? Sounds like a candidate to me.

---

### Post by stream303 on 2008-06-20
> **Bungo Pony said:**
> This particular machine has 48M of RAM in it. The boot time of MacOS is pretty pathetic though.

My first apple install was onto a 7500 with NetBSD.  Your 7600 is supported with NetBSD:

[http://www.netbsd.org/ports/macppc/models.html](http://www.netbsd.org/ports/macppc/models.html)

This faq about old-world macs might be worth looking into:

[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

Take a look at the very bottom, and it appears that Edgy (or even post-Edgy) installs from a "server" install might be your best bet.  If it works, this is a great guide for low-mem diy installations:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

With only 48mb on board, you really will be limited to the cli, and possibly a very lightweight X install with a handful of xterms. I've run Dillo as a browser in 48mb before, but in reality I ended up at the cli most of the time.  Actually kind of fun considering how much time you may have spent getting this up and running.

---

### Post by 3rdalbum on 2008-06-20
I used to own a Macintosh desktop from that era. It had a processor upgrade in it - a boost of a massive 32 megahertz for god knows how much money! It also had 80 megabytes of RAM onboard.

Ubuntu is a write-off. I tried it at version 5.10 and didn't even get X running; I recently read that X never ran on those machines. You've got buckley's chance of running X on Ubuntu in a mere 48 megabytes. Debian is a possibility. You won't be able to blow away the Mac OS 9 partition, because you cannot boot Linux or BSD straight from CD on these machines - you need a program called BootX that runs within Mac OS and starts Linux/BSD.

Debian is a possibility. Slackintosh might run. NetBSD will certainly be runnable, and I think this could be your best choice.

Good luck, and remember that Mac OS 9 is still a good operating system, so back it up!

---

### Post by zmjjmz on 2008-06-20
You don't need X :P

---

### Post by Bungo Pony on 2008-06-20
Thanks for all the help, everyone!

The Mac is just basically a toy for me to play with. I won't cry if I mess it up :)

I may try Debian or NetBSD. If I can make good use of the input and output jacks on the back, I'll be happy. But I'd prefer using some form of Linux instead of MacOS. From what I gathered from playing with MacOS, it's even less flexible than Windows.

I would prefer having some form of X running on it and an lightweight GUI. I've used Flux/Openbox before and I'm quite happy with them.

Again, if I can't do anything useful with this thing, the drives go into my PC-XT :)

---

### Post by mips on 2008-06-20
[http://www.archlinuxppc.org/](http://www.archlinuxppc.org/)

I would however try and find some cheap secondhand ram somewhere. Should make a very nice play machine if you can get more ram. I see max ram is 1GB for that machine.

---

### Post by Bungo Pony on 2008-06-20
> **mips said:**
> [http://www.archlinuxppc.org/](http://www.archlinuxppc.org/)

I would however try and find some cheap secondhand ram somewhere. Should make a very nice play machine if you can get more ram. I see max ram is 1GB for that machine.

I missed out on a machine like this for $10 a couple months back. They don't seem to be all that rare, so I should be able to find another one that I can use for the RAM. I don't even know what one of these looks like inside, therefore I don't know if the ram comes in a single module, or if you can simply add to it like the PC. Perhaps I'll open it up on the weekend and see what makes it tick :)

---

### Post by mips on 2008-06-20
> **Bungo Pony said:**
> I missed out on a machine like this for $10 a couple months back. They don't seem to be all that rare, so I should be able to find another one that I can use for the RAM. I don't even know what one of these looks like inside, therefore I don't know if the ram comes in a single module, or if you can simply add to it like the PC. Perhaps I'll open it up on the weekend and see what makes it tick :)

It has 8x 168-pin 5v FPM DIMM sockets.

[http://ubuntuforums.org/archive/index.php/t-135609.html](http://ubuntuforums.org/archive/index.php/t-135609.html)
[http://docs.info.apple.com/article.html?artnum=112367](http://docs.info.apple.com/article.html?artnum=112367)

---

