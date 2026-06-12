---
title: "&quot;Operating system not found&quot; after &quot;successful&quot; install."
date: 2014-01-28
forum: New to Ubuntu
---

### Post by fred_xii on 2014-01-28
So, I'm new to Linux.  I want obedient computers, and I already use mostly open-source software on Windows as-is (Keepass, Firefox, Thunderbird, LibreOffice, etc - I'm cheap, what can I say).  The whole NSA thing has really creeped me out of the idea of using non-free operating systems for much longer, so I'm giving Ubuntu a try.

I'm trying to install it on a Fujitsu Lifebook P1510D - an older swivel-tablet type design, very small, with a Pentium M ULV 1.2 GHz processor, 1 GB of RAM, and a 30 GB IDE hard drive.  I figure it's a perfect old machine to pair with a fresh install of the latest Ubuntu, but I am having no luck whatsoever.  I've tried installing both Ubuntu 12.04 LTS AND Ubuntu 13.10, and both seem to get through the installation process just fine (and, in fact, booting the Live CD shows the hard drive partitioned with files copied to it) - yet when they reboot and try to boot the OS natively from the hard drive, I get the same error:

"Operating System not found."

I have not tried to install Windows, I suppose I could give it a shot, but what on Earth could be causing this?  I've even tried the [boot-repair option]("https://help.ubuntu.com/community/Boot-Repair"), and I checked my flags in GParted.  Help me, Ubuntu Forums, you're my only hope.

---

### Post by Ubi_one_2014 on 2014-01-28
regarding this error, i have seen it before. In both cases the HD needed to replaced by a new one.

do not hang me up on this. maybe some more exprienced users have better answers

---

### Post by robin7 on 2014-01-28
My thoughts as well.  In my case it was simply a loose connection between the HDD and the motherboard.  BIOS can't load the HDD so it doesn't see the operating system.

---

### Post by fantab on 2014-01-28
Yes there seems to be some problem with your HDD.
I assume you can boot from Ubuntu Live DVD/USB, if so, then post the output of the following after booting from Live Ubuntu:
```
sudo parted -l
sudo fdisk -l
```

Also, there is a utility called 'Disks' in Ubuntu Live. Open it and run SMART tests on your HDD and see what it has to say about your HDD.

> Pentium M ULV 1.2 GHz processor, 1 GB of RAM, and a 30 GB IDE hard drive

Now, that is relatively a low spec machine and it will find Ubuntu heavier to run. Your machine will be better off with Lubuntu or Xubuntu.

---

### Post by Bucky Ball on 2014-01-28
> **fantab said:**
> 
Now, that is relatively a low spec machine and it will find Ubuntu heavier to run. Your machine will be better off with Lubuntu or Xubuntu.

+1. Ubuntu will probably not be the most pleasant computing experience on those specs. ;)

---

### Post by fred_xii on 2014-01-28
Well, I learned something!  Ubuntu has a much more robust built-in HDD testing/monitoring tool than Windows, which is grand!  But, I'm still no closer to solving the issue.  I ran both the "Short" and "Extended" self-tests, and the program reports "Disk is OK, one bad sector."  I think the HDD is just fine.  :/

---

### Post by robin7 on 2014-01-28
Just for grins and giggles, try reinstalling Ubuntu.  There have been times when my first "successful" install "didn't take."

---

### Post by whitesmith on 2014-01-28
Because you're working with minimum features, you might consider a different distro. For example: [http://distrogue.blogspot.com/2007/05/linux-lite-small-distros-for-old.html](http://distrogue.blogspot.com/2007/05/linux-lite-small-distros-for-old.html)

---

### Post by fred_xii on 2014-01-28
> **robin7]Just for grins and giggles, try reinstalling Ubuntu.  There have been times when my first "successful" install "didn't take."[/QUOTE]

I've actually installed it *three times* now, I installed 12.04 LTS twice, and then thought maybe it was an issue with that release, so I downloaded, burned, and installed 13.10.  I'm going to install Windows 7 Home Premium 32-bit *juuuuuuust* to make sure that the thing can, in fact, boot an operating system -- otherwise I may have been leading you all on (I didn't mean it!).

[QUOTE=whitesmith said:**
> Because you're working with minimum features, you might consider a different distro. For example: [http://distrogue.blogspot.com/2007/05/linux-lite-small-distros-for-old.html](http://distrogue.blogspot.com/2007/05/linux-lite-small-distros-for-old.html)

I think I'm going to, but I also want to use a distro that's more common and well-supported.  I'm downloading Lubuntu 13.10 now, failing that I guess... I'll try Linux Mint 16 Cinnamon?

---

### Post by fred_xii on 2014-01-28
Never mind, apparently the hard drive was disabled as a boot device in the BIOS (evidently, an exclamation mark preceding the device in the boot selection menu meant it was disabled, though Fujitsu's in-BIOS documentation was all of zero help).  I am so sorry.  I don't even know how that could've happened... the person who gave this machine to me isn't REMOTELY tech savvy...

EDIT:  Also, I should very much like to thank you all for your quick responses and suggestions -- I will undoubtedly be posting more questions here, as I'm wading away from the warm, familiar waters of Windows to Linux.  I know my way around Windows.  I am a lost child in Linux.

---

### Post by king.of.random on 2014-01-28
I was just about to suggest checking your bios.... you beat me to it :D Don't worry about wasting peoples time as your tread may solve someone else's problem in the future; so in some way you have already contributed!!

Yes learning a new operating system can be difficult but you will gain a lot of confidence of using your computer and the whole process is totally rewarding when you suddenly find you have the skills to help others. Good luck with your journey :)

---

### Post by robin7 on 2014-01-28
Hey **don't be sorry!!**  You've done nothing wrong.  In fact you've reminded us not to overlook the simple little things that might be obvious to a computer geek, but Ubuntu is not a "geek's distro!"  We just happen to be lucky enough to have some geeks here.

Just do everyone a favor and mark this thread SOLVED so others with the same issue can spot it and learn from it.

---

### Post by fred_xii on 2014-01-28
I have marked it as "Solved," and I made sure I had the make/model of my computer in the first post so that some Google/Bing/DuckDuckGo Warrior might find help with his or her Fujitsu P1510D in the future.  In any case, I'm pretty surprised at how well Ubuntu runs on it, I mean, it doesn't *fly* per se, but considering it's specs, it's actually pretty dang responsive.

---

### Post by Bucky Ball on 2014-01-29
The water will soon warm up. Great to hear you're having some success.

Enjoy the forums, the learning curve and the OS. ;)

Remember to post a new thread for any new questions in the appropriate sub-forum.

---

