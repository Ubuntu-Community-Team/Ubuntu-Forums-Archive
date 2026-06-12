---
title: "32 vs 64 bit? and Ubuntu vs kubuntu and other virsions of linux"
date: 2010-08-17
forum: Recurring Discussions
---

### Post by Ta1}s0n on 2010-08-17
Hey, first of all i would like to introduce my self because this is my first post ( out of many hopefully :D ).
so my name is Ariel, hello everyone.

it is quite hard to ignore the fact that most people prefer linux for some reasons, so i thought to my self:
what's so special about it?

i did my little research and figured that Ubuntu is probably the best Desktop linux there is.

now i would like to know:

[LIST=1]
[*]What is the difference between Ubuntu and Kubuntu (and other similar OS's?) 
[*]I would like to have both linux and windows on my pc, i heared about a concept or something like that which is called **"Dual booting"**, i would be glad to have any reference about how it works, or how i could get it to work :).
[*]what should i use, 64 bit or 32 bit OS? do 32 bit programs work on 64 bit linux?
[*]Pros and Cons of ubuntu verses other linux OS?
[*]what does UNIX mean? is it like linux? same kernel or what? i really couldnt figure it out :p
[*]is there anything else important for me to know before installing Ubuntu on my personal pc \ laptop?
[/LIST]

hopefully i would get a reply soon, i'm quite excited to be experiencing linux for the first time!:D

thanks in advance, Ariel!

---

### Post by techunit on 2010-08-17
> **Ta1}s0n said:**
> Hey, first of all i would like to introduce my self because this is my first post ( out of many hopefully :D ).
so my name is Ariel, hello everyone.

it is quite hard to ignore the fact that most people prefer linux for some reasons, so i thought to my self:
what's so special about it?

i did my little research and figured that Ubuntu is probably the best Desktop linux there is.

now i would like to know:

[LIST=1]
[*]What is the difference between Ubuntu and Kubuntu (and other similar OS's?)
[*]I would like to have both linux and windows on my pc, i heared about a concept or something like that which is called **"Dual booting"**, i would be glad to have any reference about how it works, or how i could get it to work :).
[*]what should i use, 64 bit or 32 bit OS? do 32 bit programs work on 64 bit linux?
[*]Pros and Cons of ubuntu verses other linux OS?
[*]what does UNIX mean? is it like linux? same kernel or what? i really couldnt figure it out :p
[*]is there anything else important for me to know before installing Ubuntu on my personal pc \ laptop?
[/LIST]

hopefully i would get a reply soon, i'm quite excited to be experiencing linux for the first time!:D

thanks in advance, Ariel!

The difference between Ubuntu and Kubuntu is the window manager. Ubuntu uses Gnome and Kubuntu uses KDE, which is better? I would try Ubuntu first. 

You should try WUBI. You can download it from [wubi-installer.org]("http://wubi-installer.org/") It allows you to dual boot Windows and Ubuntu with minimal effort. You can remove it as a windows application if you get tired of it. While this not true dual booting, it is a heck of a lot easier and a better idea for new users. I run the[ Ubuntu Video Tutorials blog on wordpress]("http://ubuntuvideotutorials.wordpress.com") so you can check that out and get and idea of how to use wubi. Specifically [here is the wubi guide]("http://ubuntuvideotutorials.wordpress.com/install-ubuntu/install-in-windows/") I have created. 

No Most applications turn into fairy dust and drift away in 64bit.

Sorry couldn't resist. Now for a real answer. Most 32bit programs will work unless they require driver integration. So many programs won't work. You can use a method with apt to install 32bit programs by force but most applications you won't have a problem with. Actually the real problem you are likely to run in to is flash in firefox. In 64bit Ubuntu Firefox 64bit installed, exciting right. Well not really, it can cause you alot of trouble trying to get flash to work, but if you have 4gbs of ram then it is so worth it.

Unix is proprietary, linux is Open, not always true but it sums it up pretty well, correct me if I am wrong, there are some Open-Source Unix Oses ex. openBSD. Linux has the linux kernal, Unix has a proprietary kernel. I hope this helps. Please understand that my understanding of Unix is limited.

---

### Post by techunit on 2010-08-17
Ok now thats a start for you. Pro's:
1. Lack Of Malware and Viruses (they do exist mind you)
2. Free Software
3. Easy to use
4. Free support
5. Open-Source
6. Best Visual Effects
7. Fast as a bat out of hell
8. It is free
9. Customizable
10. there are so many more but I would fill three pages.

Cons:
1. There are none Just Kidding there are some
2. Poor support for ATI video cards. You should be fine with the open-source driver though so not a real problem
3. Poor support for windows programs
4. Slowly developing gaming community
5. I could go on but there are so many cons I could fill a page...
Note there are probably more pros but I have had a fairly productive relationship with Ubuntu and I have not had many problems.

---

### Post by Zeike on 2010-08-17
> **Ta1}s0n said:**
> Hey, first of all i would like to introduce my self because this is my first post ( out of many hopefully :D ).
so my name is Ariel, hello everyone.
Hello!

> it is quite hard to ignore the fact that most people prefer linux for some reasons, so i thought to my self:
what's so special about it?
Lots of wonderful wonderful things!  What gets most people is that it is free & open source!  It is also very secure and there aren't really any modern viruses.  It is very customizable, and in many cases can be *very* fast.

> i did my little research and figured that Ubuntu is probably the best Desktop linux there is.
Very subjective.  But we like Ubuntu quite a bit around here ;)

> now i would like to know:

What is the difference between Ubuntu and Kubuntu (and other similar OS's?)
Kubuntu is an Ubuntu spin that comes with a different desktop environment.  This means the visual appearance is different, as well as a lot of things about the desktop you interact with all the time.  What it really comes down to is personal preference.
Ubuntu comes with GNOME
Kubuntu comes with KDE
Xubuntu comes with XFCE

> I would like to have both linux and windows on my pc, i heared about a concept or something like that which is called **"Dual booting"**, i would be glad to have any reference about how it works, or how i could get it to work :).
When installing Ubuntu you'll be given the option to set this up.  Just make sure not to accidentally overwrite windows and you'll have a dual boot.

> what should i use, 64 bit or 32 bit OS? do 32 bit programs work on 64 bit linux?
If you have hardware that supports 64 bit you should really take that option.  Most programs come with 64bit versions (and the vast majority of the ones that don't can still be used on 64bit).  Like what was mentioned above, flash can be a problem, but then again it works fine without any issue for many users.

> Pros and Cons of ubuntu verses other linux OS?
Ubuntu is probably the most noobie-friendly no-nonsense distro out there (with the exception of maybe some Ubuntu-derived distros like Mint).  It comes with a generic configuration so it can run out of the box on most hardware.  This leads to the cons, which is that it is slightly more 'bloated' than other distros and can have a larger footprint.  Some people say its harder to customize as well.  But if you're just starting out with linux I really suggest Ubuntu (or maybe Mint)

> what does UNIX mean? is it like linux? same kernel or what? i really couldnt figure it out :p
UNIX was an operating system developed in the 60s at Bell Labs.  It was really wonderful at the time.  It has given rise to several lines of descendant operating systems that draw many ideas from UNIX.  Here is a neat graphic: [http://upload.wikimedia.org/wikipedia/commons/1/11/Unix-history.svg](http://upload.wikimedia.org/wikipedia/commons/1/11/Unix-history.svg) .  BSDs, OS X, and Solaris are all directly derived from UNIX.  Linux is not directly derived from UNIX, but was built to be similar and compatible with UNIX.

Not all UNIXes are proprietary.  Some are, some aren't, some are somewhere in between.

A 'kernel' is just the core part of any operating system.  UNIX, BSD, OS X, Linux, and Windows all have different kernels.

> is there anything else important for me to know before installing Ubuntu on my personal pc \ laptop?
[/LIST]
You should try it out with the liveCD to make sure your hardware works before installing it!

Windows programs you need will likely *not* run in Linux.

Also, don't be afraid to ask questions.

---

### Post by Smart Viking on 2010-08-17
> **Ta1}s0n said:**
> 

[LIST=1]
[*]What is the difference between Ubuntu and Kubuntu (and other similar OS's?)
[*]I would like to have both linux and windows on my pc, i heared about a concept or something like that which is called **"Dual booting"**, i would be glad to have any reference about how it works, or how i could get it to work :).
[*]what should i use, 64 bit or 32 bit OS? do 32 bit programs work on 64 bit linux?
[*]Pros and Cons of ubuntu verses other linux OS?
[*]what does UNIX mean? is it like linux? same kernel or what? i really couldnt figure it out :p
[*]is there anything else important for me to know before installing Ubuntu on my personal pc \ laptop?
[/LIST]
 
1) Ubuntu uses the gnome Desktop enviroment(DE), kubuntu uses KDE DE, and xubuntu uses the xfce4 DE. 
2) When you install from the live CD, you will get the option to install windows and linux side by side, it is pretty safe to use this option.
3) 32Bit makes things easier in my experience. The difference isn't so big, your call.
4) Ubuntu have good support, many programs to choose from, user friendly, feature rich. Ubuntu is good for new users because of that, but when you get more experienced with Ubuntu i encourage you to try other things as well.
:)

---

### Post by alaukikyo on 2010-08-17
> **techunit said:**
> Ok now thats a start for you. Pro's:
1. Lack Of Malware and Viruses (they do exist mind you)
2. Free Software
3. Easy to use
4. Free support
5. Open-Source
6. Best Visual Effects
7. Fast as a bat out of hell
8. It is free
9. Customizable
10. there are so many more but I would fill three pages.

Cons:
1. There are none Just Kidding there are some
2. Poor support for ATI video cards. You should be fine with the open-source driver though so not a real problem
3. Poor support for windows programs
4. Slowly developing gaming community
5. I could go on but there are so many cons I could fill a page...
Note there are probably more pros but I have had a fairly productive relationship with Ubuntu and I have not had many problems.


i think he was asking ubuntu vs other linux distros :)

---

### Post by tripmix on 2010-08-17
1. ubuntu comes with the gnome while kbuntu comes with kde, both are graphical user interfaces or GUIs for short. gnome focuses on usability I think, personally I prefer kde for its configurability. It's just a matter of taste really.
2. You can easily get a dual-boot system by installing windows first on one partition then ubuntu second on another partition, grub (ubuntu boot loader) will automatically detect your windows. Installing windows second and it becomes a little more complicated.
3. Use 32bit, 64bit was still buggy when I tried it last and although it's a lot better than windows 64bit many apps still have trouble installing/compiling on 64bit linux and closed source apps like flash are hopeless.
4. I don't know what UNIX stand for but I know they tried to sue linux for stealing their code and lost :D
5. Not really, you can always try it live before you install anything. Just remember you must have at least 2 partitions or disks to dual boot, one for windows and one for linux. While installing it will ask you if you want to auto-partition or do it manually, you must choose manually or it will use the whole disk and erase anything on it. You can split one drive into several partitions even while they are in use and have data on them with apps you can find on the internet, some that come to mind are imagemagick(win, not free), parted(*nix) and I think vista and 7 comes with a app that can do that too.

Hope that helps and welcome to linux.
EDIT: Damn, can't believe I spent 9min typing that :D

---

### Post by uRock on 2010-08-17
> **alaukikyo said:**
> i think he was asking ubuntu vs other linux distros :)
Maybe he/she didn't want to speak negatively of other distros. Nothing wrong with stating experience with Ubuntu if it might help the OP in his/her Linux endeavors.

---

### Post by techunit on 2010-08-17
> **uRock said:**
> Maybe he/she didn't want to speak negatively of other distros. Nothing wrong with stating experience with Ubuntu if it might help the OP in his/her Linux endeavors.
thank you, I am a user of many Linux Distros and I run Ubuntu / Linux Mint / Debian / Maemo / Edubuntu / Kubutnu / Xubuntu. I was just trying to make his first time with Ubuntu a good experience the first time. I have only been a member of the forum for a short while now but been running linux since O7.

On another note does repeating what I said first make it any more useful? Just wondering. I understand it can concrete his belief but I think it is becoming a little excessive. New input good, missed info good, repeat correct imput should have a limit.

---

### Post by Scooter_X on 2010-08-17
> **Ta1}s0n said:**
> 
[LIST=1]
[*]is there anything else important for me to know before installing Ubuntu on my personal pc \ laptop?
[/LIST]

 

Some things I wish I would've known about and done the first time around when I installed ubuntu in a dual-boot fashion are these:

1) Don't do wubi. I know someone else posted to try it, but it wound up breaking stuff and I almost lost a bunch of data because I didn't know how to retrieve it when my computer locked up.

2) partitioning - you can partition your hard drive so that basically you have a section for windows, a section for ubuntu, and a big section in between for all your data. That's especially helpful for WHEN you break ubuntu and need to start fresh again, you can install it as if brand new without worrying about having to reformat the entire drive. Just reinstall the broken stuff and leave your documents and such alone.

3) it's going to take time to learn what you need to learn. Dig around in the forums, ask smart questions when you can't find anything about what you need to learn (or just don't understand) and you'll pick it up. I was really frustrated when I started just because I didn't understand tons of the jargon. You'll get it tho.

If you need help on partitioning go ahead and say so. I can point you to some items that should help and give further advice, as many others can do as well.

Good luck!

---

### Post by sydbat on 2010-08-17
> **techunit said:**
> You should try WUBI. You can download it from [wubi-installer.org]("http://wubi-installer.org/")No. Unless this has changed drastically with 10.04, after downloading and burning the Ubuntu ISO, just pop it in while running Windows. It will ask if you want to install Ubuntu as a program inside Windows via wubi. No need to download anything else.

> Most 32bit programs will work unless they require driver integration. So many programs won't work. You can use a method with apt to install 32bit programs by force but most applications you won't have a problem with. Actually the real problem you are likely to run in to is flash in firefox. In 64bit Ubuntu Firefox 64bit installed, exciting right. Well not really, it can cause you alot of trouble trying to get flash to work, but if you have 4gbs of ram then it is so worth it.Never had a problem installing and running 32bit OR 64bit apps on my 64bit installs...and I've been running 64 bit Ubuntu for years. Go through Synaptic and all dependencies are taken care of, including making sure 32bit apps run properly.


> **tripmix said:**
> 3. Use 32bit, 64bit was still buggy when I tried it last and although it's a lot better than windows 64bit many apps still have trouble installing/compiling on 64bit linux and closed source apps like flash are hopeless.Read what I wrote above. 64bit is just fine. Maybe 6 years ago it was less stable, but today...

---

### Post by techunit on 2010-08-17
> **tripmix said:**
> 1. ubuntu comes with the gnome while kbuntu comes with kde, both are graphical user interfaces or GUIs for short. gnome focuses on usability I think, personally I prefer kde for its configurability. It's just a matter of taste really.
2. You can easily get a dual-boot system by installing windows first on one partition then ubuntu second on another partition, grub (ubuntu boot loader) will automatically detect your windows. Installing windows second and it becomes a little more complicated.
3. Use 32bit, 64bit was still buggy when I tried it last and although it's a lot better than windows 64bit many apps still have trouble installing/compiling on 64bit linux and closed source apps like flash are hopeless.
4. I don't know what UNIX stand for but I know they tried to sue linux for stealing their code and lost :D
5. Not really, you can always try it live before you install anything. Just remember you must have at least 2 partitions or disks to dual boot, one for windows and one for linux. While installing it will ask you if you want to auto-partition or do it manually, you must choose manually or it will use the whole disk and erase anything on it. You can split one drive into several partitions even while they are in use and have data on them with apps you can find on the internet, some that come to mind are imagemagick(win, not free), parted(*nix) and I think vista and 7 comes with a app that can do that too.

Hope that helps and welcome to linux.
EDIT: Damn, can't believe I spent 9min typing that :D
I don't think it is fair to say that 64bit is buggy. I run 64bit every day not a problem, even flash works. Saying stuff like this can set a new user on a bad path of frustration and unease.

---

### Post by sydbat on 2010-08-17
> **Scooter_X said:**
> Some things I wish I would've known about and done the first time around when I installed ubuntu in a dual-boot fashion are these:

1) **Don't do wubi**. I know someone else posted to try it, but it wound up breaking stuff and I almost lost a bunch of data because I didn't know how to retrieve it when my computer locked up.

2) partitioning - you can partition your hard drive so that basically you have a section for windows, a section for ubuntu, and a big section in between for all your data. That's especially helpful for WHEN you break ubuntu and need to start fresh again, you can install it as if brand new without worrying about having to reformat the entire drive. Just reinstall the broken stuff and leave your documents and such alone.

3) it's going to take time to learn what you need to learn. Dig around in the forums, ask smart questions when you can't find anything about what you need to learn (or just don't understand) and you'll pick it up. I was really frustrated when I started just because I didn't understand tons of the jargon. You'll get it tho.

If you need help on partitioning go ahead and say so. I can point you to some items that should help and give further advice, as many others can do as well.

Good luck!Good advice...especially the wubi part. 

Wubi is only good for testing purposes. A proper install of a Linux distribution *on its own partition(s)* is always the best thing to do.

---

### Post by techunit on 2010-08-17
> **sydbat said:**
> No. Unless this has changed drastically with 10.04, after downloading and burning the Ubuntu ISO, just pop it in while running Windows. It will ask if you want to install Ubuntu as a program inside Windows via wubi. No need to download anything else.

Never had a problem installing and running 32bit OR 64bit apps on my 64bit installs...and I've been running 64 bit Ubuntu for years. Go through Synaptic and all dependencies are taken care of, including making sure 32bit apps run properly.


Read what I wrote above. 64bit is just fine. Maybe 6 years ago it was less stable, but today...
The new wubi installer will download the iso for you so you don't have to burn it to a disk, only difference.

---

### Post by sydbat on 2010-08-17
> **techunit said:**
> The new wubi installer will download the iso for you so you don't have to burn it to a disk, only difference.Ahh. Thanks.

---

### Post by techunit on 2010-08-17
> 1) Don't do wubi. I know someone else posted to try it, but it wound up  breaking stuff and I almost lost a bunch of data because I didn't know  how to retrieve it when my computer locked up.There is nothing wrong with WUBI and scaring the guy won't help either, just because you had a bad experience doesn't mean that he will to. Were trying to encourage the guy not scare him away. If something goes wrong, I will at lease help the guy, not that he will.

---

### Post by techunit on 2010-08-17
What are we supposed to tell him. That if he is in windows he needs to try to partition his computer with the terribly unreliable Windows Disk Manger so he doesn't break it then boot from the Live CD install it and find out he doesn't like it. or can we tell him how to try it. WUBI is a good choice if you want to give it a try. These guys have had problems with it, and that doesn't matter. I have installed wubi on over 15 computers with no problems. I have installed Ubuntu with no problems more times than I can remember. You will probably not have any problems with WUBI and it is a good place to start.

---

### Post by linux18 on 2010-08-17
he posted an hour ago, he's probably reading through all of the posts now, and came to the realization that ubuntu also has great community support.

---

### Post by techunit on 2010-08-17
> **linux18 said:**
> he posted an hour ago, he's probably reading through all of the posts now, and came to the realization that ubuntu also has great community support.
Or really terrible support. My god there are people posting the same things and whats worse scaring him away from a viable way of trying Ubuntu. WUBI while by no means permanent is a great way to try it.

---

### Post by borth92 on 2010-08-17
I have found Ubuntu 64-bit to be the fastest, and you can run a window manager like compiz to get aero style effects if you cannot live without them. There is a flash player bug with compiz and Ubuntu 64-bit, but my company made a how-to guide to fix it.

[http://www.wikihow.com/Fix-Compiz-YouTube-Bug](http://www.wikihow.com/Fix-Compiz-YouTube-Bug)
(remember to hit pause by the live feed or the site can scroll very slow)

Cheers,
Infinity Group

---

### Post by philinux on 2010-08-17
Moved to Recurring Discussions forum.

---

### Post by Scooter_X on 2010-08-17
> **linux18 said:**
> ubuntu also has great community support.
> **techunit said:**
> Or really terrible support.

Yes, but *community* support nonetheless. If WUBI worked fine for you on a bunch of computers, then great. Maybe it is a good way to go. My experience was otherwise. A tough part about community support is that there's always a different angle on any issue, and there's many different routes that are suggested. But then again that's what makes community support a good thing. People can pick and choose what advice they follow. As for scaring people away, it seems to me that our new community member will be just fine judging by the questions he's asking. How do the people who know a ton about anything get to where they are unless they figure out how to wade through the irrelevant and come out on the top?

Not trying to bash here, just want to say that there's going to be differing opinions. Let him decide what he wants to do from what we give him.

---

### Post by Ta1}s0n on 2010-08-17
Wow, first of all thanks a lot everyone. 
Ubuntu definitely has a great community support and thats a huge plus in my decision compared to other OS-s!:D

i kinda got the answer for most of my questions thanks to you all.
yet, still i have some questions un answered and i fill even more confused :?

about the Dual booting and the partitions part when i install my ubuntu.
if i do not use "Wubi" or any other program to help me install ubuntu ( which i have yet to understand what it is used for, i didnt read the manual given nor downloaded it ) : 

Will the ubuntu installation help me install the ubuntu OS successfully without any 3rd party program?
it will automatically show me my partitions and will allow me to separate them freely inside the installation it self? 
and also, will it install a Dual booting program automatically without me needing to do anything while installing?
(According to the comments, it will work only if my Windows OS is allready installed, so i considered that term)

the fact that i use WIN 7 on my computer changes anything about the automatic dual booting?

and the last thing i found out on the internet, there are several different kinds of file systems, in windows its FAT32 or NTFS
what about linux? and which should i use?

Thanks again for the great help given before :)

---

### Post by tjktyler on 2010-08-17
If you have more than 4GB of RAM but don't or can't use a 64bit OS, search for "linux-generic-pae" in Synaptic. PAE means Physical Address Extension, and allows the OS to address more memory than a normal 32bit implementation allows.  [Wikipedia has a great article]("http://en.wikipedia.org/wiki/Physical_Address_Extension") that explains it in more detail for the technically inclined. 

I hope this helps figure out the 32 vs 64bit puzzle.

---

### Post by Scooter_X on 2010-08-17
> **Ta1}s0n said:**
> Wow, first of all thanks a lot everyone. 
Ubuntu definitely has a great community support and thats a huge plus in my decision compared to other OS-s!:D

i kinda got the answer for most of my questions thanks to you all.
yet, still i have some questions un answered and i fill even more confused :?

about the Dual booting and the partitions part when i install my ubuntu.
if i do not use "Wubi" or any other program to help me install ubuntu ( which i have yet to understand what it is used for, i didnt read the manual given nor downloaded it ) : 

Will the ubuntu installation help me install the ubuntu OS successfully without any 3rd party program?
it will automatically show me my partitions and will allow me to separate them freely inside the installation it self? 
and also, will it install a Dual booting program automatically without me needing to do anything while installing?
(According to the comments, it will work only if my Windows OS is allready installed, so i considered that term)

the fact that i use WIN 7 on my computer changes anything about the automatic dual booting?

and the last thing i found out on the internet, there are several different kinds of file systems, in windows its FAT32 or NTFS
what about linux? and which should i use?

Thanks again for the great help given before :)

Wubi basically is ubuntu but installed and somehow magically ran from within windows, though you still pick which OS you want to run at startup. So, you need windows to be running properly to be able to use Wubi. It's basically so you don't have to mess up your windows installation AT ALL to try out Ubuntu. (though I had a bad experience)

The ubuntu installation works great. No 3rd party programs required, really. For some reason I can't remember, but the installer should also help you do your partitions. But you could get a copy of something called 'gparted' and put it on a CD and boot from it to manage your partitions and move stuff around as you need. That's what I have used on a couple of occasions. How big is your hard drive anyway?

The reason people tell you that if you already have windows on your computer then dual-boot should be easy, is because of your little "dual-booting program". It's called Grub, and it is installed automatically with ubuntu, whether or not you are going to dual-boot. It's required. I don't understand the super profound-ness of it all, but basically, if you install ubuntu first, then install windows, then the "dual-booting program" that's installed with windows will overwrite the "dual-booting program" (grub) that is the one that allows you to dual-boot, and your ubuntu install will seem to disappear. Otherwise, grub is installed sortof in place of the windows "dual-booting program" and still allows you to boot up either windows or ubuntu. 

File systems. Ubuntu and Windows both are able to understand fat32 (i believe) as well as NTFS. When you install windows, you'll pick a partition that you want and tell it to just install, and it will. I don't know which filesystem it uses or whatever, but it does what it needs. When you install Ubuntu, you should tell it to use 'ext4' (that's what I use anyway), and your big partition for the combined should be in either fat32 or NTFS so that both OS-s can understand what's there. It doesn't really matter which one you pick, to my knowledge. The only problem I ever had was that I couldn't install Steam on my NTFS partition because apparently they don't get along... not sure why. I'd try fat32 next time just to see.

I don't think I've left anything out, let me know if any of this makes sense. (And anyone should feel free to correct me on any of the technicalities of what I posted)

---

### Post by Ta1}s0n on 2010-08-17
thus you are saying that installing ubuntu alone in a new partition will automatically install properly the required dual boot?

also, you suggest i use EXT4 as my filing system for linux?
can windows read this kind of file system? or is it just linux that can read NTFS?

i find it more appealing NOT to use wubi at first, let the installation deal with the dual booting sounds more convenient, Thanks for the decision though! if this would not work, i would use Wubi :smile:

well, now i believe im ready to go! and install and experience ubuntu, thanks everyone for the help :)

ill try the 64 bit, hopefully i wont get that famous Flash player problem, which i understand it is quite rare?
if im mistaking please do correct me 
if not, im ready to take off! 8-)


**Edit:** Oh and i have 1T ( 1000 GB ) size of an hard disk, and 6 GB RAM - thats why i wanted the 64 bit, but i guess there is another solution to get my RAM going on, even on a 32 bit OS :D

---

### Post by uRock on 2010-08-17
Windows will not be able to read the Linux file system, but Ubuntu will be able to read the Windows partitions.

---

### Post by Scooter_X on 2010-08-17
> **Ta1}s0n said:**
> thus you are saying that installing ubuntu alone in a new partition will automatically install properly the required dual boot?

Yep

> also, you suggest i use EXT4 as my filing system for linux?
can windows read this kind of file system? or is it just linux that can read NTFS?uRock said it. (thanks for simplifying by the way) I like to have 3 different partitions tho. One for each OS and another for Data.

> well, now i believe im ready to go! and install and experience ubuntu, thanks everyone for the help :)Great!


> Oh and i have 1T ( 1000 GB ) size of an hard disk, and 6 GB RAM - thats why i wanted the 64 bit, but i guess there is another solution to get my RAM going on, even on a 32 bit OS :DOk cool, either way you've got plenty of space, not like you have to strategize super hard to plan the size of your partitions.

---

### Post by techunit on 2010-08-17
No do not let Ubuntu automatically partition your computer it will break windows 7. While it isn't to hard to fix you need to partition it using the Windows Disk Management tool so you don't risk damage.

---

### Post by Ta1}s0n on 2010-08-18
> **techunit said:**
> No do not let Ubuntu automatically partition your computer it will break windows 7. While it isn't to hard to fix you need to partition it using the Windows Disk Management tool so you don't risk damage.

everyone said that the installation will do that for me, wouldnt it?

---

### Post by Scooter_X on 2010-08-18
well, I did realize a couple things since yesterday.

The installer's partitioner (in advanced options somewhere when you're doing the installer) I don't know much about how great it would be to shrink and grow and move around partitions where data already exists. If it works at all, it may be risky. It works great for a fresh install though. But you want to keep your windows partition. I used Gparted the first time I had to shrink my windows7 partition so I had room for the other partitions I needed and it worked just fine. I don't know anything about the windows disk management tool either. I would assume it would be just fine to use it though.

When I'm talking about GParted you know what I'm referring to, right? It's a live CD that you put in, it boots up a partitioning program and that's it. From there you can edit your partitions. It will take awhile, mind you. Hours. Many of them. Have you ever played with your partitions before?

---

### Post by CraigPaleo on 2010-08-19
> **Ta1}s0n said:**
> everyone said that the installation will do that for me, wouldnt it?

It will. Choose to install on free space. The installer will partition it for you. You DO NOT want to try to partition it manually unless you are sure you know what you're doing.

---

### Post by Scooter_X on 2010-08-19
> **CraigPaleo said:**
> It will. Choose to install on free space. The installer will partition it for you. You DO NOT want to try to partition it manually unless you are sure you know what you're doing.

Yea, but I think he wants 1 partition for windows, 1 for ubuntu and 1 for data

---

### Post by techunit on 2010-08-19
> **Scooter_X said:**
> Yea, but I think he wants 1 partition for windows, 1 for ubuntu and 1 for data
Do understand what I was talking about now? There is a very specific method to dual booting and you need to know what you talking about. I still think he should have tried Ubuntu first with WUBI

---

### Post by techunit on 2010-08-19
> **Ta1}s0n said:**
> everyone said that the installation will do that for me, wouldnt it?
No! Using the Default installer to shrink Windows 7 will break it temporarily! You could fix it if you have the Windows 7 Install CD. But a simpler way of doing it is to shrink windows with the Windows Disk Manager, from there you can shrink windows safely! I am a veteran of 3 Dual Boots covering several different kinds of OSes. I currently Dual boot Ubuntu and Windows Vista. I hope this helps..

---

### Post by techunit on 2010-08-19
> **Scooter_X said:**
> well, I did realize a couple things since yesterday.

The installer's partitioner (in advanced options somewhere when you're doing the installer) I don't know much about how great it would be to shrink and grow and move around partitions where data already exists. If it works at all, it may be risky. It works great for a fresh install though. But you want to keep your windows partition. I used Gparted the first time I had to shrink my windows7 partition so I had room for the other partitions I needed and it worked just fine. I don't know anything about the windows disk management tool either. I would assume it would be just fine to use it though.

When I'm talking about GParted you know what I'm referring to, right? It's a live CD that you put in, it boots up a partitioning program and that's it. From there you can edit your partitions. It will take awhile, mind you. Hours. Many of them. Have you ever played with your partitions before?
You can not use Gparted To Shrink Windows 7 without breaking it it. And gparted is bundled with Ubuntu

---

### Post by Ta1}s0n on 2010-08-19
what about if i start fresh?
new clean computer, with nothing installed over it :D

---

### Post by Scooter_X on 2010-08-20
> **techunit said:**
> Do understand what I was talking about now? There is a very specific method to dual booting and you need to know what you talking about. I still think he should have tried Ubuntu first with WUBI

Can you stop antagonizing now? You're getting really annoying.

---

### Post by techunit on 2010-08-20
> **Scooter_X said:**
> Can you stop antagonizing now? You're getting really annoying.
Sorry I am really just trying to help this guy... and making sure people know what there telling this person is incorrect is probably the wrong way of handling it. Sorry. We are all trying to help but there has been alot of miss information regarding the subject.

---

### Post by techunit on 2010-08-20
> **Ta1}s0n said:**
> what about if i start fresh?
new clean computer, with nothing installed over it :D
Well first what have you done.. If you haven't started anything then you should look at the following. 

To resize the windows 7 partition safely [look at this guide]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/")

Ok now that you have made room for Ubuntu You can install Ubuntu in the free space simple as that.

For a guide on Dual Booting [This guide does]("https://help.ubuntu.com/community/WindowsDualBoot") a pretty good job explaining the many steps.
Really hope this helps.

---

### Post by NightwishFan on 2010-08-20
I would follow the above advice to resize Windows safely. From experience I have had problems with Gparted but not the Ubuntu installer.

---

### Post by Scooter_X on 2010-08-20
> **techunit said:**
> Sorry I am really just trying to help this guy... and making sure people know what there telling this person is incorrect is probably the wrong way of handling it. Sorry. We are all trying to help but there has been alot of miss information regarding the subject.

I don't mind people telling me I've done something wrong or am incorrect in how I'm explaining stuff, especially here in the forums. Just wishing you'd handle it differently.

Anyway, straying from the subject. Back on topic everyone. ;)

---

