---
title: "Installed, rebooted, stuck on boot screen"
date: 2021-08-08
forum: New to Ubuntu
---

### Post by mumbletypeg on 2021-08-08
Thanks to you, Ubuntu Was working well until I tried to reboot my computer, whereupon it got stuck in my ASUS boot screen. Ubuntu shows it is trying to load for a few seconds then freezes. 
Was trying to get it to list my second internal 5TB before I called it a day. I have no clue but maybe that screwed it up?

I’ve seen advice on similar problems with Asus, to change Bios settings?

I have tried over and over to load via the USB but nothing.Now my iPhone is my computer.

---

### Post by grahammechanical on 2021-08-08
I am going to ignore your first comment.

If the computer is stuck on the ASUS boot screen then the problem is happening before the Linux boot loader is loading. So, why do you say 

> Ubuntu shows it is trying to load for a few seconds then freezes.

What have you done? How long has this second internal 5TB drive been in that machine? Is it being recognised by the BIOS/UEFI? What drive is Ubuntu on? Is UEFI set to load an OS from the second internal 5TB drive?

---

### Post by mumbletypeg on 2021-08-08
> **grahammechanical said:**
> 
If the computer is stuck on the ASUS boot screen then the problem is happening before the Linux boot loader is loading. So, why do you say 

“…Ubuntu shows it is trying to load for a few seconds and then freezes”
1.
2.What have you done? How long has this second internal 5TB drive been in that machine? 3. Is it being recognised by the BIOS/UEFI? 4. What drive is Ubuntu on? 5. Is UEFI set to load an OS from the second internal 5TB drive? 6. 

1. I describe it like that because the Ubuntu icon is it the bottom of the screen, showing the ASUS. A kind of spinning circle shows above it, for say 30 seconds, before the circle disappears and the screen  freezes. -I should figure out how to share a picture.
2. “What have I done?” - Unsure.  In previous post titled: “How to get file manager to list 2nd internal HDD”- I attempted to follow advice on using ext/stab   
To get my 5TB internal listed in reboot. I had no idea of what I was doing.As another poster said  in that thread, I am a windows guy.
3. The second internal has been there for two years.
4. Yes. Bios lists it. It was recognized by windows before too. My difficulty was Ubuntu did not recognize it, for whatever reason.
5. Ubuntu is on my 1 TB internal “C: Drive” I formatted this drive during installation of Ubuntu.
6. No. The one terabyte drive is set to load after flash etc.

---

### Post by mumbletypeg on 2021-08-08
I should add that I believe I may have deleted the partition contents on the 2 partition operating system drive. The second partition Ubuntu on it. I should also say that I don&#8217;t care about my former installation and would happily reformat the one terabyte drive and reinstall Ubuntu on it.

---

### Post by tea for one on 2021-08-09
> **mumbletypeg said:**
> Ubuntu Was working well until I tried to reboot my computer, whereupon it got stuck in my ASUS boot screen. Ubuntu shows it is trying to load for a few seconds then freezes. 
> **grahammechanical]What have you done?  [COLOR="#0000FF"] Good question[/COLOR][/QUOTE]
[QUOTE=mumbletypeg said:**
> I should add that I believe I may have deleted the partition contents on the 2 partition operating system drive. The second partition Ubuntu on it 
The information in the last quote should have been provided in the original post.
Notwithstanding, the possibility of further _missing_ information, [COLOR="#0000FF"]mumbletypeg[/COLOR] has kindly provided the correct solution as follows:-
> **mumbletypeg said:**
> I should also say that I don’t care about my former installation and would happily reformat the one terabyte drive and reinstall Ubuntu on it 

Often quoted in these forum pages:-  [highlight]Details matter[/highlight]

Anyway, I hope that the OP will reply soon with the report of a successful re-installation.

---

### Post by sudodus on 2021-08-09
- Have you got a USB drive, that can be booted with Ubuntu, for example the drive that was used to install Ubuntu the first time? If it is new enough, try booting from it and start the installer.

- But you should also take the chance to download a newer version of Ubuntu, for example Ubuntu 20.04.x LTS, where x is the 'point release number'. Then make a USB boot drive (in Windows with Rufus, in Ubuntu with the Startup Disk Creator), boot from it and start the installer.

*I think you will be able to identify the two internal drives, and install Ubuntu where you want it,* when you are running the installer from a USB pendrive.

---

### Post by ajgreeny on 2021-08-09
Let's see exactly what we're dealing with here.
See Boot-Repair in my signature below and from a live Ubuntu system run the Boot-Info script, then copy back here the pastebin link you are given.

Do not run any repair at this stage or you may make matters even worse, but just run the script.  That should give us a lot more detailed info with which to help you.

---

### Post by yancek on 2021-08-09
>  My difficulty was Ubuntu did not recognize it, for whatever reason.
5. Ubuntu is on my 1 TB internal “C: Drive” I formatted this drive during installation of Ubuntu. 

One possibility is that it is an ntfs partition and you left windows hibernated.  Linux systems will not mount a hibernated.What filesystem did you format it as?  The default for Ubuntu is ext4. I don't think Ubuntu is on any partition labelled as C drive by windows.  That would be a partition and windows does not give drive label names such as "C" or "D" to Linux partitions.

---

### Post by mumbletypeg on 2021-08-09
> **sudodus said:**
> - Have you got a USB drive, that can be booted with Ubuntu, for example the drive that was used to install Ubuntu the first time? If it is new enough, try booting from it and start the installer.

- But you should also take the chance to download a newer version of Ubuntu, for example Ubuntu 20.04.x LTS, where x is the 'point release number'. Then make a USB boot drive (in Windows with Rufus, in Ubuntu with the Startup Disk Creator), boot from it and start the installer.

*I think you will be able to identify the two internal drives, and install Ubuntu where you want it,* when you are running the installer from a USB pendrive.

TY sudodus,
Initial installation was with Ubuntu 20.04LTS. Still have a USB drive. Have tried to restart computer with it in the USB slot.Computer behaves the same as when I try to boot it without the USB drive attached. In short I cannot boot my computer either with or with out the Ubuntu 20.04LTS USB drive.

If I had another operating system to install that would work, I would use it. I have access to another computer that is not mine and I’m thinking about taking another thumb drive to it, to mount Linux Mint and give that a try. I am writing this with my smart phone. Does not seem to have a setting to make me smarter.

---

### Post by mumbletypeg on 2021-08-09
> **ajgreeny said:**
> Let's see exactly what we're dealing with here.
See Boot-Repair in my signature below and from a live Ubuntu system run the Boot-Info script, then copy back here the pastebin link you are given.

Do not run any repair at this stage or you may make matters even worse, but just run the script.  That should give us a lot more detailed info with which to help you.

TY moderator ajgreeny,
I will do as you advise, when I get access to a second computer in the early AM PST. I will post pastebin link it gives me.Makes a lot of sense to me. :-)

---

### Post by mumbletypeg on 2021-08-09
> **yancek said:**
> One possibility is that it is an ntfs partition and you left windows hibernated.  Linux systems will not mount a hibernated.What filesystem did you format it as?  The default for Ubuntu is ext4. I don't think Ubuntu is on any partition labelled as C drive by windows.  That would be a partition and windows does not give drive label names such as "C" or "D" to Linux partitions.
TY yancek, 
My apologies for miss leading you. Currently my UEFA bios utility refers to my boot drive as: Ubuntu (P1: Toshba…)

---

### Post by mumbletypeg on 2021-08-09
Update: I did some looking to find out why my computer would not boot from my USB drive. I saw in my computer&#8217;s Bios, when attempting to force a boot directly to USB drive, the following, &#8220;Secure boot is an able to prevent on trusted operating systems from loading during the system start up. To launch the EFI shell, please disable the secure boot option or acquire digital signature for the EFI shell file and store it on a USB flash drive.&#8221; 
more research told me to delete secure boot keys to disable secure boot.I did so and was able to reboot to flash which started a new install. 
I click-checked- install third-party software for graphics and Wi-Fi.
My installation appears to be stalled although the little circle showing activity that&#8217;s controlled by my pointer. The problem seems to be as a notation says &#8220;not available because there is no Internet connection.&#8221; I guess I&#8217;ll just leave it for another couple of hours. 

much thanks for all the kind advice and ideas you&#8217;ve given me, this means a lot.

---

### Post by sudodus on 2021-08-10
I think your problem right now is that the wifi does not work in your live system booted from USB.

- If you do not check 'install third-party software for graphics and Wi-Fi' you should be able to make a complete installation with wifi. Afterwards you can connect via wired internet (ethernet cable) and then it is possible to download and install the third-party software for graphics and Wi-Fi.

- The alternative is to run the whole installation when connected to the internet via wire (ethernet). then you can install third-party software for graphics and Wi-Fi directly.

---

### Post by mumbletypeg on 2021-08-10
Thank you and great advice sudodus,
I just wrote a long response to you but writing on this iPhone resulted in it getting lost, so I&#8217;ll try again.
in short, I followed all your advice and have an active ethernet connection but nothing worked. I did as you said and try to basic install without checking for updates or third-party software. This resulted in more progress. I got to the purple cat screen with the install window asking me, &#8220;who are you?&#8221; I filled it in, set it to log in automatically but this stalled too. All the purple progress circles filled up but it stalled. I tried again with the same result. I am truly stuck now, again.
I don&#8217;t know what else to do but attempt to download the software the moderator said would produce script that would help in the analysis of my problem. I imagine I&#8217;ll have to go back-and-forth to get it posted. That said, I am heartened by myself he wonderful supportive community, all the the help offered Ubuntu is.

---

### Post by mumbletypeg on 2021-08-10
Hey! -I rebooted again and my screen was a black: GNU GRU version 2.04
 it says: &#8220;Minimal BASH-lke line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completion.
grub>_&#8221;
Any advice on what I can do with this?

---

### Post by mumbletypeg on 2021-08-11
How to get use GRUB Rescue boot and repair link? Guess not? I&#8217;m going to try a guide I found. What could go wrong? Ha

---

### Post by sudodus on 2021-08-11
Sorry, but your installed system is still not good. And I think you saw the problem already (when you noticed that the installer got stuck, could not finish correctly).

I agree that it would be a good idea to try with **Boot Repair** as suggested by the moderator @ajgreeny. Boot live "Try Ubuntu" into the USB installer drive, install Boot Repair and run it from there.

Edit: Before we continue it would be good to know more about your computer, so if possible, please specify

- Brand name (ASUS) and model number of the computer
- Brand name and model number of the graphics chip/card
- Brand name and model of the wifi chip/card
- Size of RAM

---

### Post by mumbletypeg on 2021-08-11
> **ajgreeny said:**
> Let's see exactly what we're dealing with here.
See Boot-Repair in my signature below and from a live Ubuntu system run the Boot-Info script, then copy back here the pastebin link you are given.

Do not run any repair at this stage or you may make matters even worse, but just run the script.  That should give us a lot more detailed info with which to help you.
Had a screwup, before I could write out the link the screen went and in trying to find the script, I initiated boot repair. Stopped it and generated another script.

    [https://paste.ubuntu.com/p/WSzshvBK2H/](https://paste.ubuntu.com/p/WSzshvBK2H/)
ASUS desktop model? 
Processor Intel core I 7–6700 CPU at 3.4 0GHZ
Ram 16 GB, graphics card: NVIDA GeForce GTX960

---

### Post by sudodus on 2021-08-11
Until you have installed a proprietary nvidia driver, you should use the [boot option](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808) **nomodeset**

That should bring you to a [low resolution] graphic user interface, and later on you can find information how to get a suitable proprietary driver for you graphics card.

---

### Post by mumbletypeg on 2021-08-11
> **sudodus said:**
> Until you have installed a proprietary nvidia driver, you should use the [boot option]("http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808") **nomodeset**

That should bring you to a [low resolution] graphic user interface, and later on you can find information how to get a suitable proprietary driver for you graphics card.

Thank you as you sudodus,
currently my hard drive route to grub. Not modeset is not a recognized command. I can use my flash drive and boots to boot repair. I don’t know how to use boot option -nomodeset. Advice?

---

### Post by mumbletypeg on 2021-08-12
Still stuck. Boot Repair-&#8220;Boot successfully repaired.&#8221; URL: [http://paste.Ubuntu.com/p/YS3zcvtCqi/](http://paste.Ubuntu.com/p/YS3zcvtCqi/) 
Yet rebooting to disk again results in black screen with grub command. That is, no GUI. 
It&#8217;s been awhile since anyone advised me. What&#8217;s up with that? Should I give up and reinstall Windows? Guess that&#8217;s what the silence means. Deep sigh.

---

### Post by sudodus on 2021-08-12
Boot from your live USB, mount the **root partition** (or **boot partition** if you have a separate boot partition) of your internal drive and edit the file grub.cfg of the internal system. This partition has an **ext4** file system in a standard installation of Ubuntu.

Explanation: Run [FONT=Courier New]**lsblk -f**[/FONT] to identify the device letters for the root partition of the internal system. It might be /dev/sda2 (or /dev/nvme0np2 if an nvme drive). If sda2 replace x with a and n with 2 in the command line below. There might be another letter for example b and another digit for example 5. You must use the correct letter and digit in order to mount the correct partition.

```

sudo mount /dev/sdxn /mnt
sudo nano /mnt/boot/grub/grub.cfg

```

One line in each menuentry starts with 'linux' and ends with '---'. Put 'nomodeset' near the end like so:

```

linux some other text nomodeset ---

```

Save the file and exit. Now please try booting into the installed system again.

---

### Post by mumbletypeg on 2021-08-14
> **sudodus said:**
> Boot from your live USB, mount the **root partition** (or **boot partition** if you have a separate boot partition) of your internal drive and edit the file grub.cfg of the internal system. This partition has an **ext4** file system in a standard installation of Ubuntu.

Explanation: Run [FONT=Courier New]**lsblk -f**[/FONT] to identify the device letters for the root partition of the internal system. It might be /dev/sda2 (or /dev/nvme0np2 if an nvme drive). If sda2 replace x with a and n with 2 in the command line below. There might be another letter for example b and another digit for example 5. You must use the correct letter and digit in order to mount the correct partition.

```

sudo mount /dev/sdxn /mnt
sudo nano /mnt/boot/grub/grub.cfg

```
One line in each menuentry starts with 'linux' and ends with '---'. Put 'nomodeset' near the end like so:

```

linux some other text nomodeset ---

```

Save the file and exit. Now please try booting into the installed system again.
Thank you Sudodus,
Your noble scholarly guidance impresses on many levels. 
Unfortunately I couldn’t get my USB to successfully boot. I clicked on try Ubuntu, and my screen went black with white script speeding down it. I tried and tried again and again, no luck. I checked in on the computer and no was a working USB with Ubuntu live on it. I can only guess my computers UEFI Was somehow blocking it. I’m also guessing the only option I’ve got that I can figure out, is setting up my computer to dual boot. I’m going to start by reinstalling windows.

---

### Post by sudodus on 2021-08-14
"... white script speeding down it ..." indicates that Ubuntu is starting, so UEFI is not stopping it. Instead there is some other problem, probably some hardware, typically for the graphics or wifi, that is missing a working driver.

---

