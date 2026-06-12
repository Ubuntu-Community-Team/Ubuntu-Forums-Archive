---
title: "First time Ubuntu Installation - Nothing happens?"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by skcgirl on 2012-11-17
Hello - My apologies if this is posted somewhere, but I really need some help... I'm brand new to the Linux world and have been trying to get my system properly set up for the best possible Ubuntu installation for a while now. 
I have a fairly brand new computer with Windows 7 and installed a second brand new hard drive specifically for Linux so I can have a dual boot senerio preserving my Windows operating system as the primary and running Linux on a separate hard drive.
So I put the Ubuntu DVD in the CD-ROM drive, reboot my computer, select 'Install Ubuntu', select a language and then nothing happens after that?? My monitor goes blank and the computer just sits there doing nothing. What could be causing that?? I don't even get to the part of selecting/preparing disk space... Any help would be greatly appriciated! Thanks in advance!!

---

### Post by deadflowr on 2012-11-17
When you get to the install ubuntu screen, press F6 and select nomodeset. then hit ecsape, and then click install ubuntu.
Hope this helps.

---

### Post by uclugLee on 2012-11-17
Will the machine boot up in Windows 7 and see the second hard drive?  If so, at least we know the bios is seeing the second hard drive.

---

### Post by skcgirl on 2012-11-17
Thank you so much deadflowr and uClugLee!! Pressing F6 and changing that setting worked perfectly!!! Is it better in my case to chose the first installation option of 'Install Ubuntu alongside Windows 7' or go with 'Something else'?

---

### Post by carl4926 on 2012-11-17
> **skcgirl said:**
> Thank you so much deadflowr and uClugLee!! Pressing F6 and changing that setting worked perfectly!!! Is it better in my case to chose the first installation option of 'Install Ubuntu alongside Windows 7' or go with 'Something else'?

If you choose install along side, the installer will do it all for you.

Something else lets you manage the partitioning, which I always use, but it may be to difficult for a new user.

But first, please, if you didn't already, go back to windows and make a backup of anything really important and then defrag windows. I say this, because Ubuntu will shrink some free space of the windows partition.

You should also know that many windows installs will not readily permit a Linux install. So if you have Ubuntu booted now, open a terminal and enter this

```
sudo fdisk -l
```

You should know that is a lower case L, not a number 1

Post the result here

---

### Post by skcgirl on 2012-11-18
Hi carl4926, Thank you so much for this information. I was so sure I knew what my plan was but now that I've started the installation process, I'm kind of nervous since I'm not incredibly comfortable setting up partitions :confused:
Thankfully I have everything backed up just in case... 
This is probably a stupid question, but how do I open a new terminal from the installation screen? Do you know if go ahead and choose the option to install Ubuntu alongside Windows, if it will give me the choice to install Ubuntu on a separate drive letter since I want to run it on a second hard drive instead of running it on my Windows drive or will it automatically install it on my first, primary drive?

---

### Post by DuckHook on 2012-11-18
+1 to carl4926 re: backing up first. This is a must-do to avoid trouble.

"something else" will give you the option to install on your second HD, whereas "install alongside" will shrink the Windows partition and install on your first disk (which contains Windows).

---

### Post by carl4926 on 2012-11-18
> **skcgirl said:**
> Hi carl4926, Thank you so much for this information. I was so sure I knew what my plan was but now that I've started the installation process, I'm kind of nervous since I'm not incredibly comfortable setting up partitions :confused:
Thankfully I have everything backed up just in case... 
This is probably a stupid question, but how do I open a new terminal from the installation screen? Do you know if go ahead and choose the option to install Ubuntu alongside Windows, if it will give me the choice to install Ubuntu on a separate drive letter since I want to run it on a second hard drive instead of running it on my Windows drive or will it automatically install it on my first, primary drive?

You need to have booted the cd and opted to Try Ubuntu before installing. This lets you actually try the system live before installing it.
The desktop will look something like this
[https://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10/1_installme.jpeg](https://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10/1_installme.jpeg)

The very top button of the toolbar on the left is called 'Dash' and from there if you type: term
In the search field you should see the terminal launcher

*Yes, you can install to a different HD, that is ideal. Using the live CD  you can use a application called Gparted to setup the partitions on the additional HD
Personally I would create partitions on the spare HD like this:

swap = 2 x your RAM
ext4 = 25GB will be used as /
ext4 = all the remaining space or as big as you can for /home

Have a look at this, it may help a little
[https://docs.google.com/open?id=0B3e0lLG3OdqEbXhQRmpPUlI5LTA](https://docs.google.com/open?id=0B3e0lLG3OdqEbXhQRmpPUlI5LTA)

---

### Post by skcgirl on 2012-11-18
Ok great, that helps a lot, sounds like I need to go with the 'something else' installation.... thank you guys so much!! alright, now it's giving me an error message saying 'no root file system is defined. Please correct this from the partitioning menu'....
 
I have one partition created, should I go ahead and select the 'use as: Ext4journaling file system' and make it the 'root mount point'?
 
I'm so sorry to be bugging you with all these questions....

---

### Post by carl4926 on 2012-11-18
> **skcgirl said:**
> it's giving me an error message saying 'no root file system is defined. Please correct this from the partitioning menu'....
 
I have one partition created, should I go ahead and select the 'use as: Ext4journaling file system' and make it the 'root mount point'?
 
I'm so sorry to be bugging you with all these questions....

Yes
Ideally if you can. Create a 
ext4 of 25 GB for / (root)
ext4 for /home
and a SWAP

see my prev post
Gparted is easier. The use the something else option to point to the new partitions
(You will need to quit the installer for now, to use Gparted)

Then make sure Grub is set to sda
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png)

---

### Post by skcgirl on 2012-11-18
Ok sorry I must have just missed your last post Carl which answered my last question about what partitions to set up... thanks again everyone, you guys are absolutley great and very kind to be so helpful with newbies like me lol!  I will check out those links!!

---

### Post by Swagman on 2012-11-18
Here's my Partition list.
I Thought I had Win7 on a seperate drive but evidently I don't
. There is another drive (200gb) which we use as a backup.

Main drive is 1Tb

Dunno what the /boot option was but it sounded technical so I gave it some space !!

[img]http://img839.imageshack.us/img839/1364/partitions.jpg[/img]

---

### Post by carl4926 on 2012-11-18
> **Swagman said:**
> Here's my Partition list.
I Thought I had Win7 on a seperate drive but evidently I don't
. There is another drive (200gb) which we use as a backup.

Main drive is 1Tb

Dunno what the /boot option was but it sounded technical so I gave it some space !!

[img]http://img839.imageshack.us/img839/1364/partitions.jpg[/img]

/boot is not a requirement, but can be used.

It's a bit odd though........

---

### Post by skcgirl on 2012-11-18
I'm so glad this thread is still open... Apparently when I installed the new 1T second HD, I partitioned the whole drive as one so when I tried to get the installer to lower the partition size it said it would take a 'long' time to resize. So I closed out and removed the partition on the 2nd drive so it's completely unallocated and hopefully now I should be able to add those partitions the next time just fine. 
 
One more questions... and I'm sorry if this is a redundent question but I just want to make sure I understand about the bootloader/GRUB location... So just to recap, currently I have 2 hard drives, the first one (/dev/sda) has Windows 7 and the second one (/dev/sdb) is where I want Ubuntu to be installed so they're separate. In one of the screenshots, it says to install the Ubuntu GRUB on the Windows (/dev/sda) as the device for the bootloader installation, correct? That makes sense I guess because how will the system know to boot Linux on the second drive if it already has instructions to boot Windows on the first. Please don't think I'm trying to second guess anyone, I just want to make sure since I'm totally new at this and have very little prior knowledge of Linux. 
 
Thanks again for your help, I really mean it.

---

### Post by carl4926 on 2012-11-18
> it says to install the Ubuntu GRUB on the Windows (/dev/sda) as the device for the bootloader installation, correct? 

Yes

Advanced users might switch the HD boot order in the BIOS though to make what is now sda be sdb
Then install Linux to the new sda
This protects the windows HD MBR

Personally I never bother, and just leave windows HD as sda
And install grub to sda

Grub will boot windows either way, no problem

---

### Post by Bartender on 2012-11-18
Jeepers. I woulda given Windows a bit more space.  Rule of thumb is when you get to less than 20% free space the OS will start getting in its own way and performance will suffer...

---

### Post by skcgirl on 2012-11-18
> Yes

Advanced users might switch the HD boot order in the BIOS though to make what is now sda be sdb
Then install Linux to the new sda
This protects the windows HD MBR

Personally I never bother, and just leave windows HD as sda
And install grub to sda

Grub will boot windows either way, no problem 
 
WE HAVE LIFT OFF!! :D THANK YOU, THANK YOU, THANK YOU!!!!!!!!!!!!!!!!!
You were absolutley right about everything Carl!! I used the GParted tool and followed your partition scheme and set the GRUB to the first hard drive and it let's me boot to either Windows or Linux with no issues whatsoever!! Yay!! 
 
It's really hard to do these things if you don't know people around you personally who's ever done it before so again, thank you for all you do!!!
 
It's definitely worth it to take the extra time to ask questions and with this incredibly awesome and newbie friendly forum, I didn't feel more like a total idiot than I already did LOL. 
 
Best regards!!!

---

### Post by carl4926 on 2012-11-18
> **skcgirl said:**
> WE HAVE LIFT OFF!! :D THANK YOU, THANK YOU, THANK YOU!!!!!!!!!!!!!!!!!
You were absolutley right about everything Carl!! I used the GParted tool and followed your partition scheme and set the GRUB to the first hard drive and it let's me boot to either Windows or Linux with no issues whatsoever!! Yay!! 
 
It's really hard to do these things if you don't know people around you personally who's ever done it before so again, thank you for all you do!!!
 
It's definitely worth it to take the extra time to ask questions and with this incredibly awesome and newbie friendly forum, I didn't feel more like a total idiot than I already did LOL. 
 
Best regards!!!

You are most welcome
And I hope you enjoy Ubuntu 
x

---

### Post by DuckHook on 2012-11-18
> **skcgirl said:**
> It's really hard to do these things if you don't know people around you personally who's ever done it before so again, thank you for all you do!!!

Welcome to Linux. We've all had to come out of the starting gate at some point in the past, so your questions are normal and appreciated. For my part, one of the most wonderful things about Linux is its user community--always welcoming and willing to help. Hope you enjoy your Ubuntu experience and always feel free to ask for help from the wonderful people here.

---

### Post by doja on 2012-11-18
> **DuckHook said:**
> Welcome to Linux. We've all had to come out of the starting gate at some point in the past, so your questions are normal and appreciated. For my part, one of the most wonderful things about Linux is its user community--always welcoming and willing to help. Hope you enjoy your Ubuntu experience and always feel free to ask for help from the wonderful people here.

+1
Welcome to Linux. I'm also newbie, maybe one step ahead to you, but once you come through you will see that the install is not so difficult. 
Don't give up and you will be rewarded.

---

### Post by skcgirl on 2012-11-20
Sorry I'm just now responding. Everything is going great, I'm totally LOVING this new OS experience!! My eyes are open to a whole new world and I've barely touched my Windows PC since I started using Linux a couple of days ago. This is all so wonderful, I don't know why I was so afraid of breaking the PC chains.  I'm so grateful again for everyone's help during this process and kind, welcoming words.  What an incredible environment with an great cause. Thanks again.

---

### Post by carl4926 on 2012-11-20
Looks like we have you converted :-)

---

### Post by skcgirl on 2012-11-22
You sure did! I'm never going back \\:D/Thanks again Carl!! =D>

---

### Post by skcgirl on 2012-11-22
I may need to post this in a different thread, but do you know if there's a way to remote into my Windows PC (my work email is locked down in some Microsoft 2010 Outlook Web application) if I'm already logged into my Linux desktop instead of restarting the computer and choosing Windows from GRUB?
It's no big deal but was just wondering....

Thanks again~

---

### Post by Takanakathehacker on 2012-11-22
> You sure did! I'm never going back \\:D/Thanks again Carl!! =D>Lol give it a week or two, guarenteed you'll start to get annoyed.  

We all fall the first time we try to make the jump. 

Trust ;)

---

### Post by coldcritter64 on 2012-11-22
> **skcgirl said:**
> I may need to post this in a different thread, but do you know if there's a way to remote into my Windows PC (my work email is locked down in some Microsoft 2010 Outlook Web application) if I'm already logged into my Linux desktop instead of restarting the computer and choosing Windows from GRUB?
It's no big deal but was just wondering....

Thanks again~
With your setup only one OS can run at a time, if you have Linux booted you can't "remote" into your (non-booted) Windows system on the same hardware.

With regard to > I may need to post this in a different threadYou can press the "report abuse" button on your post I quoted above and request the moderators split out these two posts to a new thread. The button is not only for reporting actual abuse of the CoC, but for anything the moderators need to deal with (like this :)).

Regards coldcritter64.

---

### Post by Vaphell on 2012-11-22
if you need to use windows programs from time to time, look into virtualization.
in let's say virtualbox you can create a fake computer and install system on it. The result is that you have 2nd system (guest) running inside your main system (host).

It requires a rather beefy machine though, because it will have to split its resources between the host and the guest systems.

---

### Post by skcgirl on 2012-11-22
> Lol give it a week or two, guarenteed you'll start to get annoyed.  

We all fall the first time we try to make the jump. 

Trust :wink:
Lol that's encouraging, thanks for your honesty [Takanakathehacker]("http://ubuntuforums.org/member.php?u=1757339") ;)

>  With your setup only one OS can run at a time, if you have Linux booted  you can't "remote" into your (non-booted) Windows system on the same  hardware. 

Ahh I didn't think about that when doing the installation, I had my heart dead-set on doing it this way and didn't research the remote-access factor. Oh well. Thanks coldcritter64 for your help and fast response. 

>  if you need to use windows programs from time to time, look into virtualization. in let's say virtualbox you can create a fake computer and install  system on it. The result is that you have 2nd system (guest) running  inside your main system (host). It requires a rather beefy machine though, because it will have to split its resources between the host and the guest systems. 

Very cool, thanks vaphell! I'm currently running on VPN on my work laptop and thought maybe there was some way to use that technology for home but after getting this information, looks like it's not as easy as I thought it would be in reality lol. Thanks again!!

---

### Post by Takanakathehacker on 2012-11-22
Well it is a tricky learning curve dude/dudette, i had a kind of mentor to help me through the first few months or so, at which point i was more than half-tempted to return to the ways of the windows. 

As you say the people on this forum/fellow linux users, are generally more than inclined and willing to help you with anything linux/ubuntu related.

---

### Post by skcgirl on 2012-11-22
Dudette :), having a mentor is a big plus, unfortunately I don't have that benefit which makes this all the more challenging but that's why I'm glad I have you guys/gals to help! :) I'm study cybersecurity and my professor says learning Linux is a huge must so that's what brings me here. Hopefully by saying that I didn't just incriminate myself ;)

---

### Post by skcgirl on 2012-11-22
And somehow my bean status now shows "Spilled the Beans" LMOL!!! So very true and quite awesome at the same time :D

---

### Post by doja on 2012-11-22
It's true, installing Ubuntu is (a great but) only the first step that follow many others.
There will be for sure some difficulties that will  temp you choose your old OS.
But don't give up, there is always some solution.

As for your personal data:
shift them to one partition with NTFS format ( without OS) and  you can reach them from both operating systems because Linux can use this M$ format.


Emails in Outlook:
If you install Thunderbird under Windows you can import your data from Outlook directly into Thunderbird. Then export them to a file. Restart a computer with Ubuntu and import them there again into Thunderbird. (I did it only for contacts but I think for emails it is the same game.)

[http://support.real-time.com/tbird/outlook_import.html](http://support.real-time.com/tbird/outlook_import.html)

I don't think you need virtual machine for reading emails. 

But from now on you have to look always after the format you use to save your data so you are able open them in both OS. Before I switched to Ubuntu I used M$ office 2003 and the Libreoffice can open them. But it can be different by M$ office 2010.

---

### Post by skcgirl on 2012-11-23
Thank you so much Doja, I didn't know I could install Thunderbird under Windows, very good to know. I will definitely check out the link. I have M$ 2010 and was wondering the compatibility level of LibreOffice. I emailed myself a LibreDoc and was disappointed not to be able to open it on my iPhone and was wondering if there was a LibreDoc to Word conversion option out there but hadn't delved too much into that yet. 
It's good to know what to expect after the "honeymoon" is over ;) Thanks again.

---

### Post by Vaphell on 2012-11-23
libre office uses .odt by default but you can use ms formats. There is a caveat though - libre office is let's say 99% compatible with MSO and breakage can happen from time to time. Latest .docx/.xlsx/.whateverx formats are especially troublesome (not enough time to iron out all kinks), you are safer with older formats like .doc (you can select them in 'save as'). Yes, now you have to pay attention to such details ;-)
In case you send docs somewhere and you don't need editing, you can export to pdf. That format is widely recognizable and the most bulletproof as it doesn't depend on some obscure, minute settings of the office suite that can vary from computer to computer.

---

### Post by carl4926 on 2012-11-24
> In case you send docs somewhere and you don't need editing, you can export to pdf.+1

I often use this option in LO when sending documents to friends and or family.

---

### Post by doja on 2012-11-24
On this format-story you can actually recognize the difference between open source philosophy and  the one of M$ and other companies. Windows runs on the most PC's. Many people don't even  know that there is an alternative (except for Mac in recent years).
   
 M$ created a system that the most people use and they try to protect it (It's their money).  It should work like a black box and you should get everything prepared as long as you pay. They are not interested on competition with others. That means that they don't give their formats free so nonM$ applications can use them. That you can open M$O formats with Libreoffice is due nice people from open source community who decrypt them and include them in the Libreoffice. This is the reason while the newest formats are always troublesome and you are on the better side to use the older ones. On the other hand M$ don't want include open source formats in their applications. They try to make it difficult to use something else then M$ products.

 An other example is the format for HDD. I wrote to you you can shift your data to a partition with NTFS format because Linux can use it. But why should M$ include the ext3,ext4,... in they products and make it easy for you using Linux?

 An other example are the drivers for hardware. If you buy hardware component (Graphic card, Wlan card, &#8230;) there is always driver for M$ but there is also always the question if it runs under Linux. The reason is that the hardware producers don't bother with the drivers for Linux. Once (and I believe in it) when the Linux will be used by more and more people the hardware producers will have the, at this time missing, interest to prepare they products also for Linux (It's their money).

 The same for software.

 And that is what this community is also about &#8211; help each other to overcome such obstacles.
 The obstacles described are not caused by Linux, but if you use Linux you have to deal with them.

 But as I wrote about Thunderbird, many applications known and used in Linux world are possible to use also in  windows micro-cosmos.
 So I used already under Windows Firefox, Thunderbird, Gimp...You can install under Windows Openoffice. (I actually don't know the difference between Libre- and Openoffice. They should work the same way.)

So you can try this applications at first step by step under Windows. Then, when you know them you substitute them for non freeware applications (and kick out the M$O & Co.) so that you use Windows only as a platform. And in the final step you kick also the platform away and start working with OS for adults. :-D

 If you switch to open source formats you free yourself from the dependency on M$ & co.

---

### Post by doja on 2012-11-24
One additionally tip. If you use also calender under Outlook you can alternatively use calender under Thunderbird.

Find under add-ons in Thunderbird Lightning application and install it to Thunderbird.

Under the add-ons you find also provider for google calender, so you can synchronise your calender with other calender applications.

---

