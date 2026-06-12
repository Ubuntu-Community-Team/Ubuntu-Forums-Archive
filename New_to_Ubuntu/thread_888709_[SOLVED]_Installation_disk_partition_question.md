---
title: "[SOLVED] Installation disk partition question"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by zzzonked on 2008-08-13
The first time I tried to install Ubuntu, during the disk partition prompt, it gave me 3 options: "guided - resizable", "guided - whole disk" and "manual". I didn't finish the installation and Vista was still intact and useable. Now I'm installing it a second time, without any changes done whatsoever (or so I think), but this time it's only giving me two options: "guided - whole disk" and "manual". Why is this so?

2nd question: If I wanna completely erase Vista now, and very possibly install XP in the future for dual-booting, which option should I pick and how should I partition my disk? Thanks.

---

### Post by shearn89 on 2008-08-13
I'm not sure why it only gives you two options, but I personally feel the best way to do it is to go with manual, and set it up yourself. Be careful though, as you could lose data if you get it wrong. 

I would boot with the cd, then hit alt-f2 and run "gksudo gparted". This will show you all the partitions on your disk, which allows you to erase partitions, resize partitions (CAREFUL!), and create new ones. This would let you wipe the vista partition, create one in it's space for XP, and create another for Ubuntu. I personally have:

10gb for Vista Recovery
30gb for Vista
20gb for Ubuntu (broken down into root, home, and swap. You probs won't need the seperate home partition.)
60gb for Music and Videos

Format the Ubuntu one as ext2 or ext3, the Media one (if you want it) as fat32, and the windows one as ntfs.

Hope this helps! pm me with questions.

EDIT: be warned - moving a partition may cause you to lose data. Backup anything important first, onto DVD or external drive.

---

### Post by snowpine on 2008-08-13
> **zzzonked said:**
> The first time I tried to install Ubuntu, during the disk partition prompt, it gave me 3 options: "guided - resizable", "guided - whole disk" and "manual". I didn't finish the installation and Vista was still intact and useable. Now I'm installing it a second time, without any changes done whatsoever (or so I think), but this time it's only giving me two options: "guided - whole disk" and "manual". Why is this so?

2nd question: If I wanna completely erase Vista now, and very possibly install XP in the future for dual-booting, which option should I pick and how should I partition my disk? Thanks.

I believe the reason the "resize" option no longer appears is because you aborted the first installation after it had already created the new partitions. My hunch is that there are empty partitions on your drive, just waiting for Ubuntu. :)

But before you do anything, take 15 minutes and educate yourself about partitioning--it will save you time and frustration in the long run. Here's a good guide: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by zzzonked on 2008-08-13
Is this [IMG]http://www.psychocats.net/ubuntu/images/partitioning3.png[/IMG] recommended for a first-timer like me? How do I do that? When I clicked manual, it brought me to a window with a list of stuff saying /dev/sda1, /dev/sda2, /dev/sda3 and /dev/sda5, so what am I supposed to do now?

By the way how do you guys recommend I should partition my disk if I've only got about 70GB of hard disk space? I think I want something like th image I posted earlier. When I bought my laptop, it said 80GB on the tech specs, but somehow in Windows, both my C and D drives added up to only 71GB :(

Sorry if these questions seem dumb, but I need a step-by-step guide on what to do 'cause I'm really new to this thing...

Oh, @shearn89: the media partition you were referring to, is it the yellow portion of the image I posted? And the Ubuntu root partition is the cyan portion, and the swap partition the gray portion? Correct me if I'm wrong. I'm just guessing, I have little clue of what's going on now actually.

---

### Post by stoneybroke on 2008-08-13
If you are thinking of installing XP and Ubuntu it would be best to install XP now then Ubuntu this way when you install Ubuntu the boot loader will give you a menu to chose to load between XP or Ubuntu.

If you only install Ubuntu now and later decide to install XP you might have problems because windows wants to use the entire disk, with the above method you can use the free space to install Ubuntu.

Hope that helps

---

### Post by zzzonked on 2008-08-13
Okay I've noted your suggestion, stoneybroke, but thing is, my copy of XP will only be available/accessible in at least a month, it's physically out of reach now. So I'm thinking of installing Ubuntu now and getting rid of Vista altogether. So what do you think I should do?

---

### Post by stoneybroke on 2008-08-13
Well you could always partition the disk now into 2 physical partitions and install Ubuntu on 1 partition for now then later install XP on the other partition, hopefully windows might not like the idea though and try and install itself on the entire disk.

Alternative is to install VMWare follow this link to see how its done [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209) Then you can run both o/s at the same time

---

### Post by zzzonked on 2008-08-13
Okay I tried doing something stupid and now I'm completely lost. How am I supposed to partition my disk? How as in I need a step-by-step guide on what to click and what to type and what to do. I'm curently (on the other computer on which I'm installing Ubuntu) at a window that says "prepare partitions" and down there it has a list of "/dev/sdax" where x is 1, 2, 3 and 5. What do I do now?

Edit: To make my illiteracy clearer, I wouldn't know what to do if you said something like "partition one of them to a fat32 thingy with 10GB" or something like that, I dunno. I'm only comfortable with "select /dev/sda2, on the menu, click [blah blah], then check the box that says [blah blah]", y'know, really explicit step-by-step, I'm sorry but that's just how illiterate I am, or does anyone have a link to a good guide?

---

### Post by sandysandy on 2008-08-13
post output of [COLOR="Red"]sudo fdisk -lu[/COLOR]

(from terminal on ubuntu live CD)

this will help us understand ur existing partitions better.

as far as partitioning with gparted is concerned look here

[www.howtoforge.com/partitioning_with_gparted](www.howtoforge.com/partitioning_with_gparted) 

regards

---

### Post by shearn89 on 2008-08-13
> **zzzonked said:**
> Is this [IMG]http://www.psychocats.net/ubuntu/images/partitioning3.png[/IMG] recommended for a first-timer like me? How do I do that? When I clicked manual, it brought me to a window with a list of stuff saying /dev/sda1, /dev/sda2, /dev/sda3 and /dev/sda5, so what am I supposed to do now?
That is a perfect example, as you're not meant to directly mount windows partitions in linux. Permissions go screwy.

> 
By the way how do you guys recommend I should partition my disk if I've only got about 70GB of hard disk space? I think I want something like th image I posted earlier. When I bought my laptop, it said 80GB on the tech specs, but somehow in Windows, both my C and D drives added up to only 71GB :(
Not sure why you only have 71gb, perhaps for a recovery partition? Windows needs a fair chunk of room, ubuntu doesn't, so maybe 30gb for windows and maybe 15/20 for Ubuntu? The rest could be shared.

> Oh, @shearn89: the media partition you were referring to, is it the yellow portion of the image I posted? And the Ubuntu root partition is the cyan portion, and the swap partition the gray portion? Correct me if I'm wrong. I'm just guessing, I have little clue of what's going on now actually.
It is indeed the yellow portion. You've got all the colours correct.

I can't help to much with the explicit howto, as i haven't used gparted for aaages... hunt around the web, check out [the gparted website]("http://gparted.sourceforge.net/"), and read the howto posted by **sandysandy**.

---

### Post by zzzonked on 2008-08-13
I'm blind. I've been hunting around for 10 minutes but I couldn't find GParted. Is it supposed to be somewhere on the desktop? Or am I missing something? Can someone tell me how to launch GParted in the first place? What's the difference between using GParted to partition my hard disk, and using the installation process to do it?

---

### Post by sandysandy on 2008-08-13
see on the ubuntu live CD panel bar sub menus.

or here

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

i personally prefer to use the gparted live CD.

regards

---

### Post by snowpine on 2008-08-13
> **zzzonked said:**
> I'm blind. I've been hunting around for 10 minutes but I couldn't find GParted. Is it supposed to be somewhere on the desktop? Or am I missing something? Can someone tell me how to launch GParted in the first place? What's the difference between using GParted to partition my hard disk, and using the installation process to do it?

Boot from the Live CD and then look in the System menu for Partition Editor.

---

### Post by shearn89 on 2008-08-13
Using gparted gives you (IMO) a clearer visual representation of what you're doing. As I said before:

> **shearn89 said:**
> ... hit alt-f2 and run "gksudo gparted" ...

This will start the partition editor.

---

### Post by ntu on 2008-08-13
Here is a good Hardy pictorial installation guide:

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron)

---

