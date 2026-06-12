---
title: "[SOLVED] I Cannot find my C drive in Ubuntu"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Daagorath on 2008-05-15
i have Vista and Ubuntu, i cannot find my c drive files from vista in Ubuntu, which has all my stuff on it.. a little help

---

### Post by Xiong Chiamiov on 2008-05-15
Well, of course, there is the mistake that a certain drive is tied to a certain letter, but Windows does that to you...

Anyhoo, if you go to system:/media, does it show up in there?

---

### Post by HotShotDJ on 2008-05-15
> **Daagorath said:**
> i have Vista and Ubuntu, i cannot find my c drive files from vista in Ubuntu, which has all my stuff on it.. a little helpPlaces --> Computer  ... it should be there.  It won't be labeled C: of course.

---

### Post by Daagorath on 2008-05-15
in the computer folder in ubuntu ther is the presario drive and anotther one, but in the other one i dont recogize any of the folders, it doesnt look like any of teh ones i might find in my c drive on vista

---

### Post by Xiong Chiamiov on 2008-05-15
What does kind of folders does it have?  Are they things like boot, etc and home?

---

### Post by HotShotDJ on 2008-05-15
> **Daagorath said:**
> in the computer folder in ubuntu ther is the presario drive and anotther one, but in the other one i dont recogize any of the folders, it doesnt look like any of teh ones i might find in my c drive on vista
The "other one" should be labeled "Filesystem" and that is your Linux file system.  I don't know what you mean by "presario drive" -- is that your CD/DVD drive or is it something else?  What happens when you click on it?

---

### Post by Living2007 on 2008-05-15
When you open GParted, is the Windows partition in front or behind the Ubuntu partition?

---

### Post by DaF101 on 2008-05-15
Okay, what version of Ubuntu are you running? 

You havent lost your windows? can you still boot into Vista?

Your C drive will not show up as C in Ubuntu. Try going into Places > Computer and if you don't see it in there type in at the address bar at the top /media and if its not in there I'm not so sure otherwise.

---

### Post by Daagorath on 2008-05-15
ahh yes, the other one is called filesystem, and it has a bunch ov folders like you said, and the presario one is my computer folder, like for restore or whatever, i have gone to search and typed in a program from my vista one which was Soulseek and it didnt find anything about the program, also, my wireless adapter doesnt work when im loged into ubuntu.. hmm..

thank you guys for the advice, sorry if im not being very clear, im just getting into all ov this computer stuff

---

### Post by Daagorath on 2008-05-15
ya i still can get into vista, thats what im in rite now.

---

### Post by SunnyRabbiera on 2008-05-15
> **Daagorath said:**
> ahh yes, the other one is called filesystem, and it has a bunch ov folders like you said, and the presario one is my computer folder, like for restore or whatever, i have gone to search and typed in a program from my vista one which was Soulseek and it didnt find anything about the program, also, my wireless adapter doesnt work when im loged into ubuntu.. hmm..

thank you guys for the advice, sorry if im not being very clear, im just getting into all ov this computer stuff

well its a good thing you dual boot, you may have to utilize it to get wireless working in ubuntu, as wireless for ubuntu is still a little shaky... mind you its not our fault.

---

### Post by HotShotDJ on 2008-05-15
> **Daagorath said:**
> ya i still can get into vista, thats what im in rite now.Well, at least we know that the partition is there.  I'd like you (when you are back into Ubuntu) open up a terminal (Applications --> Accessories --> Terminal) and type the following:```
sudo fdisk -l
```(that last letter is a lower-case "L") and then post the output.

---

### Post by Xiong Chiamiov on 2008-05-15
> **Daagorath said:**
> ahh yes, the other one is called filesystem, and it has a bunch ov folders like you said, and the presario one is my computer folder, like for restore or whatever, i have gone to search and typed in a program from my vista one which was Soulseek and it didnt find anything about the program, also, my wireless adapter doesnt work when im loged into ubuntu.. hmm..

thank you guys for the advice, sorry if im not being very clear, im just getting into all ov this computer stuff
Aside from what the others said, can you give us some concrete examples of the folders that you see?  If you're not familiar with the windows file structure then you might in fact be looking at your windows partition without knowing it.  If you tell us the names of several of the folders that you see there then we can figure out what it is you're looking at.

---

### Post by Daagorath on 2008-05-15
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52751945

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11297    90743121    7  HPFS/NTFS
/dev/sda2           11298       12161     6940080    7  HPFS/NTFS


thats what came up

---

### Post by HotShotDJ on 2008-05-15
Well... I'm off to bed.  You might want to take a look at [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by subzero316 on 2008-05-15
> **Daagorath said:**
> Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52751945

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11297    90743121    7  HPFS/NTFS
/dev/sda2           11298       12161     6940080    7  HPFS/NTFS


thats what came up


Your vista partitions are detected . The NTFS is the vista partition..

---

### Post by Daagorath on 2008-05-15
yes im off to bed also, if anyone still wants to put things on this subject. im going to check it in the morning, thanks for all ov your help

---

### Post by Xiong Chiamiov on 2008-05-15
> **Daagorath said:**
> Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52751945

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11297    90743121    7  HPFS/NTFS
/dev/sda2           11298       12161     6940080    7  HPFS/NTFS


thats what came up
You're running Ubuntu off of an NTFS partition?  Boy, that's odd, and not something I'd choose to do.  Aside from answering my questions, do what someone else said, and open GParted (it's somewhere in the menu, I'm not familiar with GNOME, or press alt+f2 and type gparted) and tell us what you see there, specifically in which order the partitions are.

---

### Post by nowshining on 2008-05-15
yeah un-like Windows - linux/unix use a diff. file structure - once u get used to it - u'll then realize it's much superior than windows file structure and easier to navigate. :)

---

### Post by Living2007 on 2008-05-15
Ubuntu runs on the files system "ext2" and "Ext3" and also reqires a 2GB Partition under "linux-swap"

---

### Post by ZabiGG on 2008-05-15
Hi there ;)

Presario is probably the disk you're looking for. I have a setup similar to yours, which was already partitioned before my Ubuntu installation due to a very large hard drive...

I am using the Gnome user interface, so it won't work for you if you chose the KDE.

But the first time I clicked on Places (in the panel), both Windows partitions were already there and named 
ACER (my computer's brand)  
DATA

I can "mount" (tell my computer I want to access them) them from there any time by clicking on any one of them and entering my password at the prompt.

I'm not quite sure this will help, but it was worth a try :)

---

### Post by Daagorath on 2008-05-15
some of the files in Filesystem are bin boot cdrom dev etc home host initrd lib lib64 lost + found and so on, i dont know, but im guessing that one guy was rite, that is my vista partition? anyway, i will try that gparted thing again, i tryed the alt f2 thing but it didnt work, i will try again.

---

### Post by Living2007 on 2008-05-15
> **Daagorath said:**
> some of the files in Filesystem are bin boot cdrom dev etc home host initrd lib lib64 lost + found and so on, i dont know, but im guessing that one guy was rite, that is my vista partition? anyway, i will try that gparted thing again, i tryed the alt f2 thing but it didnt work, i will try again.

Vista will have Users, Windows, Program Files; try and find thoes folders

---

### Post by Xiong Chiamiov on 2008-05-15
> **Living2007 said:**
> Ubuntu runs on the files system "ext2" and "Ext3" and also reqires a 2GB Partition under "linux-swap"
or reiser, or XFS, or...

---

### Post by Daagorath on 2008-05-15
ya, my i have GNOME one to, mine is like yours, i have one that is my computer type, and another that says Systemfile, but i cant find anything in the systemfile that i recognize from my c drive on my vista, someone said it might be the vista partition, im not sure if what im looking for might still be on there tho.

---

### Post by Xiong Chiamiov on 2008-05-15
Let's try mounting the drives manually.
```

sudo mkdir /windows1
sudo mkdir /windows2
sudo mount /dev/sda1 /windows1
sudo mount /dev/sda2 /windows2

```
If you get any errors, tell us and continue with the rest of the commands.  After you finish, go to the root directory (/) in your file manager, then take a look at the folders windows1 and windows2.  Do either of them look familiar?

---

### Post by forestpixie on 2008-05-15
Are you running Ubuntu through wubi - I assume that you are as you have no linux files in the fdisk -l output.

Would that explain why the OP doesn't see them and would it be wise to be mounting windows in linux in windows - if you follow my drift.

All that said I know very little about wubi.

---

### Post by Daagorath on 2008-05-15
awesome, i found what i was looking for, thanks, now i just need to know why i wont let me connect to the internet wirelessly on Unbuntu lol, and i guess i need a better graphics card to make all the visuals better or whatever. i got Nvidia gForce go 6800 or some such, you guys dont have to help me with that, but its not good enough is it? ehh.. its worth it tho, im hopeing to learn about all this programming and stuff so i better get to figuring things out.

---

### Post by ZabiGG on 2008-05-15
Sweetie, BREATHE!

You don't have to jump into programming right away.

My advice to you is this: click on the sticky titled "Installing ..." just above the thread list and read it. It will take you a few minutes, I know, but you'll better understand what all of that technospeak is all about, I promise.

If all else fails, I posted my list of favourite links for newbies (heck, I'm still in your shoes) :)

Look right under the line and click on _Look right here_ 

Take your time, take a peek at the basics, and you'll be fine (and up and running in no time!)

Cheers,


Z.

---

### Post by Xiong Chiamiov on 2008-05-15
> **ZabiGG said:**
> Sweetie, BREATHE!


/thumbup

> **Daagorath said:**
> awesome, i found what i was looking for, thanks, now i just need to know why i wont let me connect to the internet wirelessly on Unbuntu lol, and i guess i need a better graphics card to make all the visuals better or whatever. i got Nvidia gForce go 6800 or some such, you guys dont have to help me with that, but its not good enough is it? ehh.. its worth it tho, im hopeing to learn about all this programming and stuff so i better get to figuring things out.

Can you tell us what exactly fixed it?  If it was one of the commands I gave you, then those won't stick when you reboot - that is, until we help you through editing your fstab.

For wireless and graphics problems, I'd suggest searching around first, since they are quite common problems.  I recently had to do some playing around with my geforce 7600, so that's all fresh in my brain if you need help there.

EDIT: Ah sweet, I got a coffe-cup now!  No more lame beans for me!

---

### Post by Daagorath on 2008-05-15
oh lets see... well actually i feel abit stupid... i found the files in the Systemfile thing... and about the graphics card, i tryed to change the visual effects in ubuntu and it said it was unable to change it, so im guessing my video card isnt good enough, and i wouldnt know how to change it because this is a laptop im using.. i tryed upgrading my video card on the nvidia website, i dotn think it changed anything.. anyways, well thanks for all of your guy's help, i have learned some new things tonight, well i need to go to bed, my eyes are herting real bad lol, neways, thanks again

-Daagorath

---

### Post by ZabiGG on 2008-05-15
Hey I got the thanks! lol

Lovely forum helpers, remember -- some newbies are newer than others. Think simple and easy first, then move on to more technical stuff so it's not so scary.

We know you know your Ubuntu :)
But remember the first time you ever laid eyes on a linux or UNIX-like system?

Think back really hard. Then explain it so that the newbie YOU once were would have understood.

Keep up the good tricks and advice. We love you.



The Main Commander of the Newbie Literacy Awareness Center
(just kidding... but it makes some people smile, and that's good!)

Z.

---

