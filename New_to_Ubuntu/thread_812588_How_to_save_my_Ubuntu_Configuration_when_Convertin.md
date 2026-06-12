---
title: "How to save my Ubuntu Configuration when Converting from Vista to XP"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by cforput on 2008-05-30
Hi,
I tried this in a different forum but didn't get much help so I am trying it here. I bought a new laptop that came with Vista. Before I realized just how bad Vista is, I installed Ubuntu as a dual boot. I have 1 program that forces me to still use Windows but Vista just isn't working for me so I want to put XP on my laptop. 

Well, I spent days, no probably weeks, getting my ubuntu configuration set up so everything works well. In some cases, I have no idea what I did, it just works. I'm a newbie if you can't tell.

Well, I am wondering if there is a way to take an image of my Ubuntu configuration, then wipe out Vista, install XP then put my Ubuntu image back on.

Anyone have any ideas for this newbie?

Thanks in advance for the help. Oh yea, keep it simple too if you can!

---

### Post by powerpleb on 2008-05-30
> **cforput said:**
> Hi,
I tried this in a different forum but didn't get much help so I am trying it here. I bought a new laptop that came with Vista. Before I realized just how bad Vista is, I installed Ubuntu as a dual boot. I have 1 program that forces me to still use Windows but Vista just isn't working for me so I want to put XP on my laptop. 

Well, I spent days, no probably weeks, getting my ubuntu configuration set up so everything works well. In some cases, I have no idea what I did, it just works. I'm a newbie if you can't tell.

Well, I am wondering if there is a way to take an image of my Ubuntu configuration, then wipe out Vista, install XP then put my Ubuntu image back on.

Anyone have any ideas for this newbie?

Thanks in advance for the help. Oh yea, keep it simple too if you can!

If you install XP over Vista on the same partition you shouldn't have to make an image of Ubuntu. You may need to reinstall GRUB, however, because XP will wipe out your MBR. 

This can be done from a Live CD:
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by oedha on 2008-05-30
since you're dual boot...it means win and ubuntu on different partition right ?
if so...
just install XP on vista partition....it will wipe vista
then after that you have to recover the grub...to recall your ubuntu...

---

### Post by cforput on 2008-05-30
OK. The only grub I know about is a something you use for bait when you fish. I will give this a try. It seems logical. Wish me luck and thanks for the help.

---

### Post by hyper_ch on 2008-05-30
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by bumanie on 2008-05-30
GRUB stands for GRand Universal Bootloader. It is the 'thing' that enabled you to dual boot and choose which OS to use. It will happily work with windows' bootloadder, but windows is unforgiving when it comes to other/rival bootloader's and overwrites grub files that were put into the mbr. Reinstalling grub is done via the live cd. There are plenty of tutorials about how to do it. Just make sure that you install xp over the vista partition and you will have no problems. If you are unable to reinstall grub, make another post to the forum and someone will help you.

---

