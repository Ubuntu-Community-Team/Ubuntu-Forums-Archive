---
title: "How To: Dual Boot Vista and Linux"
date: 2006-07-09
forum: Outdated Tutorials &amp; Tips
---

### Post by molly_001 on 2006-07-09
This instruction page allows you to dual boot Vista and Linux onto a machine with a single hard drive, and which is dedicated for that purpose.

The page also includes links to a post by confused57 on how to dual boot onto two separate, physical drives.  (Keeping the two OS on separate drives.)

Soon, the page will include a guide on dual booting Vista and Linux onto a single drive which already contains Linux -- and keeping your previous Linux install in the process.  (courtesy of Loffe)

As well as, soon, an instruction manual to triple-boot Vista, XP, and Linux (courtesy of testube_babies)

The page is in my sig below.

---

### Post by domino on 2006-07-10
Thanks for the how-to, although i think it would have been better to post it here and left a link to your forum.

What if I installed vista and dapper on HD1, with HD0 already populated with WinXP (hda1) and another OS (hda2)? Should I just disconnect HD0 before installing vista and dapper on HD1? 


Please disregard the statement below:

[COLOR="White"]I also plan on installing dapper FIRST using the text mode version and install GRUB on hdc1, install vista on hdc2. Then use a 3rd party boot loader. I'm not sure what will happen when I install Vista last. Worst case scenario is that it would muck up HD1 MBR. In that case, installing your method would be the more logical.[/COLOR]

---

### Post by molly_001 on 2006-07-10
> **domino said:**
> Thanks for the how-to, although i think it would have been better to post it here and left a link to your forum.

Good idea.  After my other contributors (Loffe & testube_babies, as above) have finished their work, I'll be able to post a full set of instructions here.  When completed, the page will have four sets of directions for 4 different outcomes, as above.  In the meantime, users can find the forums here: [B][http://tinyurl.com/rjv57](http://tinyurl.com/rjv57)

[/B]Nonetheless, the eventual page may too large to post here, so I might end up keeping it as a link-only when referenced to in these forums, such as Herman does with his dual boot instructions.

> **domino said:**
>  What if I installed vista and dapper on HD1, with HD0 already populated with WinXP (hda1) and another OS (hda2)?

It's a good question, but not having tried that particular set-up, I don't know the answer.  However, you will find some great clues to achieve your answer in the thread here:  **[http://tinyurl.com/kr8x2](http://tinyurl.com/kr8x2)**  (This link also appears on my dual boot page, courtesy of confused57.)

> **domino said:**
>  Should I just disconnect HD0 before installing vista and dapper on HD1?

Sounds like a reasonable idea, but it did not work out pretty for [this]("http://tinyurl.com/kfxca") guy or [this guy]("http://tinyurl.com/zbxvt").

---

### Post by domino on 2006-07-10
My experience is that managing multiple Operating Systems can get confusing if you don't have a good handle on hard drive perameters and partition information for boot.ini, grub/lilo, and the BIOS. It's easier to have a 3rd party boot manager like Acronis if I was to play with beta OS installs.

I use Acronis for this system so i'm hoping it picks up Vista after I install it. My disk config is as follows:

HD0:

WinXP: (hda1)
OS X: (hda2)

HD1:

Vista: (hdc1)
Dapper: /boot (hdc2) | /root (hdc3) | swp (hdc5) | /home (hdc6)
FAT32: (hdc7)

---

### Post by ace2005 on 2006-07-10
Well i tend to install a lot of things at the same time and i would say install windows XP first, use its installer to partition the disk in the way you want so when you come to installing dapper you tell it to just format the partitions that were already created. Then i'd install vista telling it which partition to use and allowing it to take over as boot loader and then i'd install dapper and it can take over from vista's loader. Then to get to Vista you'd have to pick vista's boot loader in grub and then pick vista at vista's boot loader. This is what i would do, but i'm not interested in vista enough to try it.

---

### Post by molly_001 on 2006-07-14
A link on the dual boot Vista Linux page (see signature below) has been added to point to Loffe's new instructions on "dual boot Vista and Ubuntu, and KEEP previous Ubuntu install"

link below in my signature

Thank you.

---

### Post by molly_001 on 2006-07-27
The site in my signature now includes instructions and/or links to:

* dual boot Vista and Ubuntu 6.06

* dual boot XP and Ubuntu 6.06

* triple boot XP, Vista, and Ubuntu 6.06 (thanks testube_babies)

* dual boot Vista or XP and Ubuntu over a previous Ubuntu install, without the need to reinstall Ubuntu (thanks Loffe)

* dual boot over two physical hard drives  (thanks confused57)

---

### Post by greyham on 2006-07-28
hi thanks for the post but just a question, i plan to upgrade the vista BETA2 to RC1. If i do this will it destroy the Ubuntu Partition? and why do i have vista on the second partition - does it matter and which partition has all my filles, because i want to access the same ones from both os'es

Than Greyham

---

### Post by turner23x on 2010-12-10
hey guys im also trying to install dual boot Vista and Linux (with vista installed first). I see that the guide isnt available on this thread here anymore, Does anyone have an updated guide. much thanks for any help

---

### Post by wilee-nilee on 2010-12-10
> **turner23x said:**
> hey guys im also trying to install dual boot Vista and Linux (with vista installed first). I see that the guide isnt available on this thread here anymore, Does anyone have an updated guide. thanks

Hows about some actual help just to make sure your safe.;)

---

### Post by turner23x on 2010-12-10
i read a lot of guides still cant get it to work right

---

### Post by wilee-nilee on 2010-12-10
> **turner23x said:**
> i read a lot of guides still cant get it to work right

Lets start with this we have a bootscript that there is a link to in my signature. This will give us a bunch of text that tells us what is where and a good toolset to work with. So download the script drag it to the desktop this is in Ubuntu, live cd or install, and run this command in the Ubuntu terminal. Just copy and paste it, it is easier.
```
sudo bash ~/Desktop/boot_info_script*.sh 
```

A new text file will appear come back and open a new reply window; and first click on the **#** in the reply panel and copy and paste all the text from that generated file in the code tags and we can get to the heart of the matter.

---

