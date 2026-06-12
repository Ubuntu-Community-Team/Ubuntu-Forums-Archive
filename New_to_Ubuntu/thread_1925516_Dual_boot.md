---
title: "Dual boot"
date: 2012-02-14
forum: New to Ubuntu
---

### Post by dep0 on 2012-02-14
Hi, I am already using ubuntu 10.04 LTS and i would like to install windows (for some rpg-games i cannot find on linux) without unistalling ubuntu.
I haven't done it before so i don't know how it will work if i simple run the windows cd.

---

### Post by KingYaba on 2012-02-14
Before you install Windows try using WINE without needing to install Windows [http://www.winehq.org/](http://www.winehq.org/). Your games might work but I haven't had 100% success so I dual boot. 

Just know that installing Windows after Ubuntu will stop GRUB from showing up at boot. See more on that and how you can recover GRUB here: [http://ubuntuforums.org/showthread.php?t=1752186](http://ubuntuforums.org/showthread.php?t=1752186)

To install Windows you need to partition your hard drive. Do this by booting up into a live session either from your CD or USB flash drive. GParted is the program that can partition your hard drive. Be sure to backup your data before you do this. Once your hard drive is partitioned, boot up the Windows disc and install Windows on the partition you just created. When Windows is installed, again, it'll stop you from using GRUB so you'll have to go back into a live session and use the link I just gave on restoring GRUB.

---

### Post by jerrrys on 2012-02-14
Never done it, but looks doable

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=install+windows+after+ubuntu&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=install+windows+after+ubuntu&sa=Search&cof=FORID:9)

[https://www.google.com/search?client=ubuntu&channel=fs&q=install+windows+after+ubuntu&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=install+windows+after+ubuntu&ie=utf-8&oe=utf-8)

---

### Post by sadaruwan12 on 2012-02-15
It's doable but the issue is after installing the windows system it over rights the Linux boot loader GRUB and that makes your ubuntu install unusable. Because windows never want to share it resources with another competitor.

To get your Ubuntu back you need to get your hands dirty.

I also use windows games but in I use crossover linux which is a paid version of wine but you can get a smiler program called play on linux which will make installing games or software very easy.

Before doing a dual boot consider the above options first. If that fails then move to the dual boot as a last resort.

If you really want to do that then here are some guides to help you with the GRUB recovery.

[Link 1]("http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7")

[Link 2]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

[Link 3]("http://askubuntu.com/questions/83771/recovering-grub-after-installing-windows-7")

[Link 4]("http://askubuntu.com/questions/84641/grub-rescue-prompt-after-using-hp-recovery-manager-to-reinstall-windows-7")

[Link 5]("http://www.makeuseof.com/tag/how-to-spell-check-with-the-firefox-dictionary/")

[Link 6]("http://www.mydigitallife.info/firefox-spell-checker-not-working-due-to-missing-dictionary/")

Hope this helps.

---

### Post by dep0 on 2012-02-15
Is play on linux free software or do i have to pay to download it? 
It looks like a good alternative way than trying to get my grub back after dual booting.
Thank's all for offering so many othrer solutions.

---

### Post by sadaruwan12 on 2012-02-15
It's a fully featured free software you don't have to pay anything. And also have very good community.

This is a very good alternative compared to the dual boot option where you have do much more work to get it working.

---

### Post by dep0 on 2012-02-15
Ok, thanks sadaruwan12 __ and all the rest. I will try play on linux and if i find any difficulty i will ask you again.
Hope you're still here to reply.
If all goes well i will mark this thread as solved.
Thanks again for all the recommendations.

---

### Post by Mark Phelps on 2012-02-15
Not to dampen your enthusiasm ... but ... you REALLY need to use the WineHQ link in post #2 to check out the rating for every game (and version) you want to play.  Wine, even with Play On Linux, is not a "miracle cure", especially with Windows Games, as those often require 3D hardware acceleration (which may not be available for the video hardware you have) as well as DirectX support (which may not be available in the video drivers you're using).

---

### Post by Cavsfan on 2012-02-15
I too have windows 7 and Ubuntu 10.04 installed. But, like **sadaruwan12** stated, you have to install windows first.
If you have a USB drive you can backup your important stuff onto and install windows and then install Ubuntu.
Clean installs are best. 

If you are any thing like my son playing MW2 and other games from Steam, they will not run under wine as we have tried.

Good luck and if you get the 2 OSs installed, check out the tutorial in my signature for creating a maintenance free menu with a 
nice picture of your choice. There are several example screens; my current one being the last post. 
I just have Ubuntu, Ubuntu Recovery and Windows 7 as the only 3 options.
What is nice is the menu never changes even when a new kernel is installed.

---

### Post by varunendra on 2012-02-16
> **dep0 said:**
> Hi, I am already using ubuntu 10.04 LTS and i would like to install windows (for some rpg-games i cannot find on linux) without unistalling ubuntu.
Not a problem. This is how I do it: [http://ubuntuforums.org/showpost.php?p=11656462&postcount=4](http://ubuntuforums.org/showpost.php?p=11656462&postcount=4)

Quick and safe.

---

### Post by jasonrisenburg on 2012-02-16
honestly before you do anything ,make sure you have all the documents that are important to you backed up in case something goes wrong. I have had a few friend who have used linux for a while not back up and lose everything.

---

### Post by Cavsfan on 2012-02-16
**varunendra**, That is great post! I didn't even know that was a possibility.
I think I'll bookmark that for future reference.

And as **jasonrisenburg** stated back up anything you don't want to lose.

---

### Post by varunendra on 2012-02-17
> **Cavsfan said:**
> **varunendra**, That is great post! I didn't even know that was a possibility.
Thank you :)

However, after reading that post again, I realized I forgot to mention the obvious risk of 'resizing' partitions, and thus suggesting to back up the data first. I'm going to do it now.

Thanks for the encouragement, I wouldn't have looked back at it otherwise.

---

### Post by Cavsfan on 2012-02-17
You are welcome! Glad I could contribute!
Since I have to dual boot, I have always resized my partitions in windows 7 after extensive, 
time consuming defragmentation. I use Defraggler and would always see
the user journal file in the last cluster. Making it impossible to shrink my existing windows partition. 
I finally found a way to delete **C:/$Extend/$UsnJrnl:$J:$DATA** which does not defragment and after 
a while becomes huge with many fragments.

What is nice about Defraggler is that you can see what is in each cluster, so when you see you have 
your windows files at the start of the drive and nothing from there to the end of the drive, you know it will shrink.

It can safely be deleted with this command "**fsutil usn deletejournal /n c:**"
It is recreated by windows and is just window's way of keeping track of it's files, etc.

After doing this, I was able to shrink my windows partition by 100GB which is what I used to install Ubuntu.

Let us know how it goes. I have always gone with a clean install after windows was installed.
I tried to do an upgrade once and it went well for a while, then something happened and I had to backup my stuff and do a clean install.

Luckily I have a 1TB USB drive that I can back almost anything on to.
Also, I prefer the LTS versions as they are really stable and work well with my printer, camera, etc. 
I am looking forward to Ubuntu 12.04 LTS Precise Pangolin with 5 years of support. :)

---

