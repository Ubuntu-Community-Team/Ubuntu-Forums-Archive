---
title: "Random Problems"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by johngreen12 on 2011-11-15
Hello Ubuntu Community,
I recently switched completely over to ubuntu because I was tired of dealing with windows 7 getting so slow after awhile as well as because of the malware that attacks it.  I love it but I have run into several problems with the system.  I use a desktop with GNOME (Ubuntu 64 bit 10.04 lucid).  The Kernel is 2.6.32-35-generic (#78-Ubuntu SMP Tue Oct 11 16:11:24 UTC 2011).  I listed the problems I've been having below:

[1]  About a week ago it suddenly got extremely slow and it seems to freeze for like 5 or 10 minutes on the login screen.  

[2]  Also, occasionally the shut down option in the menu bar disappears and the tops of the windows sometimes disappear, thus not letting me shrink or close them.  

[3]  About a week ago the update manager stopped working as well.  It said that it needed some access codes to access the update database and I fixed that problem but after that now it says that it can't download all repository indexes. 

[4]  Another issue is with the wireless plugin card not working.  I use an asus wireless plugin to access the internet and it works perfectly with windows but it doesn't with ubuntu.  There is a driver for linux os but the directions are very confusing to me.  I looked up the problem hoping to find a solution online but it seems that everyone else is having the same problem with it.  I also find it very strange that occasionally the wireless card works, and I can connect to the wireless without any issue, but it only does that usually when the windows lose their tops.

[5]  Google gadgets (GTK) doesn't come with the gadgets that it is supposed to.  Also, the igoogle gadgets doesn't work either, even though I put the link for the gadget in.  

[6]  The system freezes periodically which is really annoying and I don't know how to fix it.  

[7]  I use Virtualbox to emulate windows 7 in order to use it for netflix but the sound on the virtual os stopped working.

[8] Another thing is that for the webcam's audio to work I always have to manually change it to the webcam's microphone in the sound settings.  Is there any way to make it just automatically choose to use the webcam's microphone without having to select it everytime?

[9] The weather widget doesn't work.

[10] Rhythmbox scroll down menu in the panel doesn't work anymore.  It used to work a few days ago.

[11] My motherboard has an error display on it that flashes out errors if there's a problem.  Ever since I started using Ubuntu it has constantly had an error on it.  The error is A2.  My mother board is the Foxconn Flaming Blade.  [http://www.newegg.com/Product/Product.aspx?Item=N82E16813186170](http://www.newegg.com/Product/Product.aspx?Item=N82E16813186170)


I really could use some help with these problems.  I use the macubuntu10.04 theme which i believe could be causing some of the problems.  Thank you for taking a look!
Sincerely, 
John Green

---

### Post by Daveth on 2011-11-15
ooo, too many bad things happening there. 1 at a time perhaps. When it went slow, did you do anything substantial? I assume you are running 64 bit virtualbox with windows, yes? I assume you have enough system specs to virtualise that setup? Did it run OK before the slow-down?
Might kick off more views on your problems.

---

### Post by johngreen12 on 2011-11-15
> **Daveth said:**
> ooo, too many bad things happening there. 1 at a time perhaps. When it went slow, did you do anything substantial? I assume you are running 64 bit virtualbox with windows, yes? I assume you have enough system specs to virtualise that setup? Did it run OK before the slow-down?
Might kick off more views on your problems.

Hello Daveth, thank you for the quick response.
Half the time the computer freezes on the splash screen while booting up and when it does actually work it takes a long time loading the login screen.  After the login screen is fully loaded then it takes about a minute for the desktop to load, when before the system slowed down it was almost instantaneous loading up.  

Regarding the virtualbox, it is 64 bit windows 7 and it stopped working before the system slowed down.

Here is the error report from the update manager:
Failed to fetch cdrom://Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)/dists/lucid/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)/dists/lucid/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.


Hope this helps.  What any other system information be useful?

---

### Post by Daveth on 2011-11-18
ah, if I am right it is trying to resolve repositories on the cd when the cd is not present, so it spends ages looking.
Try System/Admin/Software Sources, and, after giving your password, make sure the installable form cd-rom is unchecked. You might also want to check out what else is checked and explore taking the options down and putting them back up.
If this is duff advice, perhaps someone else can help out!

---

### Post by fat yak on 2011-11-18
re point 4 your wireless connection - have you downloaded the driver? and what are the instructions?

---

### Post by johngreen12 on 2011-11-18
> **Daveth said:**
> ah, if I am right it is trying to resolve repositories on the cd when the cd is not present, so it spends ages looking.
Try System/Admin/Software Sources, and, after giving your password, make sure the installable form cd-rom is unchecked. You might also want to check out what else is checked and explore taking the options down and putting them back up.
If this is duff advice, perhaps someone else can help out!

I just tried unchecking the cdrom option but it gave me this error after reloading:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21

Should I uncheck something else?  I attached a picture of the software sources.
When I run the update manager now it gives the same error as the one above.

---

### Post by johngreen12 on 2011-11-18
> **fat yak said:**
> re point 4 your wireless connection - have you downloaded the driver? and what are the instructions?

I use a PCE-N13 ASUS Wireless card plugin (PCI-Express Adapter) and the driver designed for linux users is called RT2860 Wireless Lan Linux Driver.  I've attached the entire driver folder for linux users as well as just the instructions.  I kept getting an invalid file type error when I tried to upload the instructions so I just put it in a openoffice document.

---

### Post by johngreen12 on 2011-11-18
I restarted the computer just now and when it finally loaded up all the window tops were missing.  I attached a picture of what it looks like.  For some reason google chrome seems to be unaffected while every other program can't be closed, moved, or resized with the three options that are normally there.  It's quite frustrating.

---

### Post by LinuxFan999 on 2011-11-18
> **johngreen12 said:**
> I restarted the computer just now and when it finally loaded up all the window tops were missing.  I attached a picture of what it looks like.  For some reason google chrome seems to be unaffected while every other program can't be closed, moved, or resized with the three options that are normally there.  It's quite frustrating.
Could it be because of the customizations you applied to it. Try it with the standard theme and see if it still happens.

---

### Post by johngreen12 on 2011-11-18
> **LinuxFan999 said:**
> Could it be because of the customizations you applied to it. Try it with the standard theme and see if it still happens.

This only happens sometimes though.  I restarted my computer again and the tops came back.

---

### Post by Daveth on 2011-11-19
um, I'm sort of wondering whether a fresh install might overcome your woes. Fast, easy and free. Then work on the base system, see if that works, and keep note of things you change and when.Bit like throwing the towel in, but if it solves your problems...

---

### Post by johngreen12 on 2011-11-19
> **Daveth said:**
> um, I'm sort of wondering whether a fresh install might overcome your woes. Fast, easy and free. Then work on the base system, see if that works, and keep note of things you change and when.Bit like throwing the towel in, but if it solves your problems...

I was thinking that would be easier too.  I'll reinstall ubuntu and see if that fixes the problems.  I doubt that it will fix the error code on the motherboard though because that was like that from the very start.  Do you know what it means?  I tried looking it up online but it didn't come up with anything.

---

### Post by johngreen12 on 2011-11-20
Ok, I just reinstalled the 10.04 LTS system but it's having the same slow boot problem.  I found this article online that suggested that it was a problem with the SATA settings...and that I needed to switch from IDE to something else.  I tried loading it up with all the various settings though and they all behaved similarly...still very slow.  I installed bootchart and I'm going to restart again to see what that shows regarding the start up.

---

### Post by johngreen12 on 2011-11-20
I attached the bootchart log.  I got the idea from [http://ubuntuforums.org/showthread.php?t=1842022](http://ubuntuforums.org/showthread.php?t=1842022)

Any ideas?

---

### Post by johngreen12 on 2011-11-20
Here's a zip file with the log in it if you can't view the one I posted before.

---

### Post by johngreen12 on 2011-11-21
When I install the Macbuntu theme for 10.04 the menu for rhythmbox always disappears after like 1 reboot.  I just uninstalled the theme and now the menu came back.  Does anyone know how to fix this?

The code that I type in is this:
$ wget [https://downloads.sourceforge.net/project/macbuntu/macbuntu-10.04/v2.2/Macbuntu-10.04.tar.gz](https://downloads.sourceforge.net/project/macbuntu/macbuntu-10.04/v2.2/Macbuntu-10.04.tar.gz) -O /tmp/Macbuntu-10.04.tar.gz
$ tar xzvf /tmp/Macbuntu-10.04.tar.gz
$ cd /tmp/Macbuntu-10.04/
$ ./uninstall.sh  (or install)

---

### Post by johngreen12 on 2011-11-21
Well I am using the default theme now but the rhythmbox scrolldown menu still disappears every once and awhile.

---

### Post by Daveth on 2011-11-25
um, a bit pants that the install did not come to anything. What sort of motherboard do you have. I too have read about SATA issues and the need to edit the grub2 files, as detailed in
[HTML]http://www.rommellaranjo.com/content/my-ubuntu-1004-lucid-lynx-linux[/HTML]
You also might want to try upgrading to a newer Ubuntu, non-LTS version that might play better with your system, though if you go too new you will be in Unity-land or the Gnome-shell district!

---

### Post by johngreen12 on 2011-11-28
I was thinking that a newer version of ubuntu might solve the problems too.  That was the next thing I was going to try.  My motherboard is a foxconn flaming blade.  This link gives information about it.  
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813186170](http://www.newegg.com/Product/Product.aspx?Item=N82E16813186170)
I tried using the update manager to get the version upgrade but it didn't work so I'm going to just start from the cd again.

---

### Post by johngreen12 on 2011-11-28
I just installed 10.10 and it had the same slow boot up.  It freezes on the initial login screen for a few minutes and then starts working.

---

### Post by Daveth on 2011-11-28
it might be instructive to look through the dmesg log in var/log and see if there are any obvious errors being thrown up, though I'm hoping someone with more skill might help you interpret the output.
I can find almost nothing on the net about the motherboard and linux; it strikes me more as being a slightly glowing stick  rather than a flaming blade at the moment!

---

### Post by johngreen12 on 2011-11-29
I don't really understand anything in that log so I attached it.  I agree completely with the motherboard being just a glowing stick rather than a flaming blade now lol

I also am having trouble with the direct connection to the internet.  It always seems to be either really fast like it should (25Mb/s) or really slow.  When it is slow generally the other people in my apartment who are using windows don't have the same issue, which makes me think that something is setup incorrectly with the connections in ubuntu.  Besides that, google gadgets still doesn't have anything in it and the sound on virtualbox doesn't work.  I recently tried installing the pandora plugin for rhythmbox and now rhythmbox is incredibly slow.  Reinstalling it did not seem to help.  Other than that all the other problems that came up with 10.04 went away.
[http://www.webupd8.org/2011/05/rhythmbox-pandora-plugin-updated-for.html](http://www.webupd8.org/2011/05/rhythmbox-pandora-plugin-updated-for.html)

---

### Post by johngreen12 on 2011-11-29
I don't know which one has the information in it =/

---

### Post by johngreen12 on 2011-11-29
IT WORKS!!!!  I reinstalled the 10.10 version again but rather than choosing to download the updates while installing the system I chose not to.  That's the only thing that I did differently and now it loads up faster than windows =D  I haven't tested the other problems yet though.  The wireless is still messed up...but I have a feeling that I can't fix that =(  I'm going to update the system...hopefully the slow startup doesn't come back after that...

---

### Post by johngreen12 on 2011-11-29
The startup works really nicely now but now the networking is acting up.  The networking icon in the panel disappeared.

---

### Post by Daveth on 2011-12-04
oh, well done. Have you tried just re-booting your router with the pc on? I often find that works. 
Loaded up XP onto my old computer for my parents- vile experience which took all afternoon...

---

### Post by johngreen12 on 2011-12-24
The network problem I believe is with the driver...I still haven't figured out the solution to the wireless not working.  Hope loading XP on your parents computer went well :)  I've found that OEM is better when putting a different OS on.  No extra applications that you need to remove.

---

### Post by johngreen12 on 2012-01-20
I'll start one thread for every problem in the future.  Thank you for your help Daveth!

---

