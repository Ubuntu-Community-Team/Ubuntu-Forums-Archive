---
title: "Fedora or PCLinuxOS"
date: 2007-10-18
forum: Other OS Talk
---

### Post by voteforpedro36 on 2007-10-18
So I'm downloading Gutsy right now, plan on updating Fiesty when I can (tonight maybe tommorow). And since I'm gaining access to a CD burner for this weekend (great timing, eh?), I figured I'd try another distro that I maybe could dual boot. Since I've downloaded both Fedora 7 and PCLinuxOS, I figure it may as well be one of those. I can, however, use another one if I must (or it's suggested). So, basically, which one? Here's what I really want:

-It doesn't have to be all GUI. It's not my main computer anyway, I want to learn something. Besides, if I get too confused I'll boot into Ubuntu anyway.

-I can't have to use the internet, I don't have wireless.

-I want to be able to play music, install games, do interesting stuff (very narrow selection now, right?)

-On a side note, can I possibly have a guide to dual booting?

Btw, I don't want to try both. I just want an answer, lol. I already am going to burn 7.10, the reason I'm actually able to use it (CD of some song or crap), and another distro. I don't want to use 4 CD's.

Thanks for the time ;).

---

### Post by igknighted on 2007-10-18
> **voteforpedro36 said:**
> So I'm downloading Gutsy right now, plan on updating Fiesty when I can (tonight maybe tommorow). And since I'm gaining access to a CD burner for this weekend (great timing, eh?), I figured I'd try another distro that I maybe could dual boot. Since I've downloaded both Fedora 7 and PCLinuxOS, I figure it may as well be one of those. I can, however, use another one if I must (or it's suggested). So, basically, which one? Here's what I really want:

-It doesn't have to be all GUI. It's not my main computer anyway, I want to learn something. Besides, if I get too confused I'll boot into Ubuntu anyway.

-I can't have to use the internet, I don't have wireless.

-I want to be able to play music, install games, do interesting stuff (very narrow selection now, right?)

-On a side note, can I possibly have a guide to dual booting?

Btw, I don't want to try both. I just want an answer, lol. I already am going to burn 7.10, the reason I'm actually able to use it (CD of some song or crap), and another distro. I don't want to use 4 CD's.

Thanks for the time ;).

Wow... I'm not sure you could have picked two more different distros.  I'll highlight both:

**Fedora:** An intermediate distro (in other words they do not go out of their way to make it easier for new users), Fedora is very similar to Debian in that it includes ONLY free software.  No non-free codecs, no non-free video or wifi drivers, and no other proprietary apps.  Fedora does some very advanced hardware detection (much nicer than Ubuntu, IMHO).  Fedora also looks much nicer right out of the box (again, IMHO).

**PCLOS:** This is a distro designed for new users, more so than Ubuntu.  Non-free drivers and codecs are included by default.  It uses older packages (it is about the same as last fall's mandriva release).  The repositories are very slow if you want to update/install new software.  To be totally honest, you would be much better off downloading Mandriva One 2008 instead.  Newer packages, better supported distro and you still get the drivers and codecs (plus compiz fusion and mettisse if you choose).  The config tools are the same for both distros, and are pretty much the best config tools available.

---

### Post by voteforpedro36 on 2007-10-18
Alright, might as well try Mandriva. I'm downloading it now. Do you care to explain (or point me somewhere) how to set up a dual boot with it? Sorry, I have about no idea how to do it. I do know that I need to have more than one partition, which I don't think I do. 

Thanks for the answer though.

---

### Post by igknighted on 2007-10-18
You could just install it the default way and it should automatically add Ubuntu to its own grub.  There are more advanced ways that will save you trouble later on (say, like the next kernel release).  I don't have time to do a step by step right now, but if you can wait till later tonight I would be more than happy to post a how-to (or if someone else beats me to it, go for it).

---

### Post by voteforpedro36 on 2007-10-18
So, if I just do a default install, it won't wipe Ubuntu out?

And I'd like to do the complicated way, it is about learning more, right?


Yup, I'll wait. No hurry.

---

### Post by DreadPirateRoby on 2007-10-19
> -I can't have to use the internet, I don't have wireless.

-I want to be able to play music, install games, do interesting stuff (very narrow selection now, right?)

Are you saying that you won't have an available Internet connection on this machine?  If that's the case, I don't see how you can expect to be installing many games or have decent codec support by using just a single CD. Maybe you should take a look at something like sabayon which comes on a live DVD.

Otherwise, Make sure you install Mandriva first then Ubuntu (both PCLOS and Mandriva/Mandrake have had trouble seeing other linux installations).

When it comes to partitioning the drive in mandriva, choose to use custom disk partitioning. Next, select the partition you want mandriva to go to and set it's mount point to "/".

When it becomes time to install Ubuntu , just tell it to use the other partition as "/" and you should be able pick to boot either one when you restart.

Note: If you feel up to it, it may be a good idea to actually create four partition on your drive and use both a "/" and "/home" partition for Ubuntu and Mandriva. In this case, your personal files will be stored on "/home" while system files will be on "/". Either "/" shouldn't have to be any bigger than 10GB while your home partions can be as big as you like.

---

### Post by SunnyRabbiera on 2007-10-19
personally I would take Pclinux as its hands down the best RPM distro out there, apt makes a lot of difference

---

### Post by voteforpedro36 on 2007-10-19
Ok, now I'm more confused. I think instead of of updating Fiesty, I will do this:

Install Mandriva, on one partition. How big should I make this partition?

Install 7.10 on a different partition. Same question as above.

Have a seperate /home folder on another partition. This means I have to back up, which I know will be slow seeing as how I will have to use a 1GB USB drive for 4.1GB of info in /home/*my user* that I have in a tarball ready to go already. Is it alright that I just copied my user folder instead of home?

Will that work? And how do I make seperate partitions like that? How do I make Ubuntu and Mandriva see that /home folder instead of the one they both will make?

Sorry for all the questions.

EDIT: Oh, about what I said earlier (not having internet): It's a pain, but it's been working so far. Instead of downloading codecs and that, I just use a program for the Windows computer I'm typing from to convert it instead. I successfully installed some games and emulators too. I'll be fine, no need to worry about that.

---

### Post by dca on 2007-10-19
> **igknighted said:**
> Wow... I'm not sure you could have picked two more different distros.
 
+1

---

### Post by voteforpedro36 on 2007-10-19
Alright, time to just do it.

Right now I'm in Mandriva Live CD, I'm going to make four partitions, two for Mandriva and Ubuntu, one for /home/, the two OS's mount points will be /, but on different partitions. What is the fourth one for? 

Where should the mount point be for the partition that will hold Mandriva, and where for Ubuntu? One should be /, but what should the other one be?

Sorry for all the rants and whatnot, but I just started kind of understanding DreadPirateRoby's post. Any advice/answers?

---

### Post by DreadPirateRoby on 2007-10-19
I was saying that you should have a separate home and "/" partition for each. You could share the same home partition between Mandriva and Ubuntu, but it doesn't sound like a good idea. If you're having trouble with this,  you don't necessarily "need" to have separate partitions for home and "/". It just might end up making things easier for you down the road.

-You could have both distributions reside entirely on their own partition for a total of two partitions on the drive. (Simple now, but not the best in the long run)
-You could have a / and /home partition for Ubuntu and stuff all of Mandriva into a single partition for a total of three. (A decent compromise )
-You could set a / and /home for each for a total of four. ( The "proper" way)

Don't set or change the mount point for partitions that you won't be using in mandriva. You'll do that in Ubuntu. 

Since you'll probably be spending most of your time in Ubuntu, the home partition for that should be what takes up most of your drive. If you use a separate home partition for Mandriva it will only need to be big enough to hold settings files and other things unique to the user. I usually can get away with just 5GB in that case, but your millage may vary.

---

### Post by voteforpedro36 on 2007-10-20
Well, I believe I have screwed it up more. I only have two partitions I think, one for Mandriva one for Ubuntu :/. Is there a way I can access files from one to the other? I'm guessing I have to mount something, but I know Mandriva is on /dev/hda1 (I believe that's where it is, I know it's partition 1), and Ubuntu is partition 3.

And you said I'd be booting into Ubuntu, hope there's no good reason. I've found Mandriva better (maybe since it's something new...), especially with Amarok.

---

### Post by igknighted on 2007-10-20
> **voteforpedro36 said:**
> Well, I believe I have screwed it up more. I only have two partitions I think, one for Mandriva one for Ubuntu :/. Is there a way I can access files from one to the other? I'm guessing I have to mount something, but I know Mandriva is on /dev/hda1 (I believe that's where it is, I know it's partition 1), and Ubuntu is partition 3.

And you said I'd be booting into Ubuntu, hope there's no good reason. I've found Mandriva better (maybe since it's something new...), especially with Amarok.

The drive should be sda1, not hda1.  Run fdisk -l as root to see what the partitions are named.

---

### Post by voteforpedro36 on 2007-10-20
```
 Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1337    10739421   83  Linux
/dev/hda2            4583        4864     2265165    5  Extended
/dev/hda3   *        1338        4582    26065462+  83  Linux
/dev/hda5            4724        4864     1132551   82  Linux swap / Solaris
/dev/hda6            4583        4723     1132519+  82  Linux swap / Solaris


```

That's from Ubuntu when running fdisk -l. (Sorry if the formatting is odd) 

So, I know I need to go

sudo mount -t ext3 /dev/hda1

But that's missing the device. In other words, how exactly do I mount it?

Sorry for the noobishness.

---

### Post by DreadPirateRoby on 2007-10-21
Older IDE drives will show as hda. There's no problem there.

I feel like an idiot for forgetting to talk about swap partitions. It would be better to have a single swap partition at the beginning of the drive, but what you have now wont kill you. It's just not ideal. I am really sorry about that.

> sudo mount -t ext3 /dev/hda1

If you're on the live cd, **don't** mount anything from the command line. It's not the same as doing it from the installer.

Ubuntu should always place all the partitions on the desktop once that you install it. Even if it doesn't show there, you should be able to reach the other partition through Places>Media in the gnome-panel. Otherwise, you need a "folder" to mount the drive to.   

```
mkdir /media/mandriva

sudo mount /dev/hda1 /media/mandriva
```

You'd eventually have to edit a text file to make that stick, but we'll cross that bridge when we come to it.

Setting the ubuntu partition to always mount in Mandriva can be done in the Mandriva control center. I think it's something like Mount Points>Create Delete..>Toggle Expert Mode>*select drive*>Options>uncheck noauto. 

Defaulting to mandriva sounds like it might be a minor inconvenience. You'll have to edit a text file some where or try to install Ubuntu's grub to it's own partition and then add an entry for it in Mandrivas' menu by using MCC. 

Having Ubuntu take up most of your drive might also be a problem now. Earlier, I said that you would probably want to give more space to where you'd be spending most of your time. Still, this just boils down to the space that will get eaten up as you install various apps and where you want to keep the files you bring over.

---

### Post by voteforpedro36 on 2007-10-21
Thanks. I'll have to try that here in a sec, will edit back.

I'm not defaulting to Mandriva. Sadly, installing Ubuntu second brought the text-only Grub, instead of the Graphical (pretty) one that came with Mandriva...

I'll edit back.

So, it worked. I can now access my files from Mandriva in Ubuntu. Sadly I have to run Nautilus as sudo, or Rhythmbox as sudo, but that's alright. I'm happy.

Thanks for all your help.

---

