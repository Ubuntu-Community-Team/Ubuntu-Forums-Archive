---
title: "where to look for updates on Ubuntu"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by Pshemas on 2012-12-30
Hello there! I've decided to try Ubuntu - made a bootable USB and played with it for a while. Got to admit I love it! The default desktop is great (the  only small criticism so far is "locked"/non-customizable  app bar , but I can understand that).
Getting back to Windows is a pain, feels wrong in a way ;) . I can't abandon Win completely due to applications I have to work with(fe cad apps) and hardware (for example brother label printer) , but for daily workshop use for me and the rest of the team I'd like to set up Ubuntu on our computers.
This will be a good option when Webb Apps feature will start working correctly. I've found out currently there are issues with it (I was able to make some of them work , through Synaptic reinstall and update, but some , like Gmail are still broken).

But where can I get the info that those are fixed? Browsing several sites would take too much time. Is there some sort of newsblog etc I could track? I know for most of you this may sound silly - but heck, for absolute begginner as me all the Ubuntu (and not only Ubuntu, but Linux in general) resources seems really spread out.

Also can  anyone can you recommend a website for a begginner? For example I'd like to have a working copy on USB (not installer style, which forces me to reinstall, resetup everything after each boot) so I could play and tweak the things without affecting my hdd.

---

### Post by Pjotr123 on 2012-12-30
> **Pshemas said:**
> Also can  anyone can you recommend a website for a begginner?

You might find this helpful:
[https://sites.google.com/site/easylinuxtipsproject/](https://sites.google.com/site/easylinuxtipsproject/)

---

### Post by Cheesemill on 2012-12-30
There are two ways you can set up an installation on USB that remembers your changes, either a Live USB with persistance or a full installation.
At the moment you have a Live USB install but without persistance, which is why all of your changes are lost when you reboot.

For pros & cons see C.S.Camerons post here:
[http://ubuntuforums.org/showpost.php?p=10293555&postcount=2](http://ubuntuforums.org/showpost.php?p=10293555&postcount=2)

---

### Post by gordintoronto on 2012-12-30
Gmail works just fine through a browser.

In my experience, Brother printers work very nicely in Linux. However, I assume there is an application which prints labels?

Many times when there is a bug in Ubuntu, it is posted in launchpad. If you can find the bug there, you can subscribe to any updates.

---

### Post by superDave972 on 2012-12-31
Is dual-booting your computer with Ubuntu and W7 an option? It seems like running Ubuntu off a LiveUSB would be really slow...

---

### Post by Pshemas on 2012-12-31
Thx for the help guys, the links are really useful :) .

Did the install on my USB - but humbly admit I did it in a stupid way.  I've used Wubi hoping it would create a bootable USB... Yeah, I know - RTFM :D . So now I have an install on USB (non-bootable) and a modified Windows Boot Manager, that asks with which system to run on startup.
So I'll have to clean the boot options and reinstall Ubuntu. Which method of installing would you recommend? Through virtualmachine on Win7?

Also I've noticed that this install performance is noticably inferior (slower) than the bootable Live USB (the one with no persistance - no saving of modifivations and with the installer). Is it normal? Or is it caused by the way I've installed Ubuntu through Wubi? Is there a way to improve the speed, so it would match Live USB?

@superDave972: atm it is not an option. My idea is to have a system I could take with me and play a little bit with it, familiarize with it :) . If/ when I start to feel comfortable with it (should be easy - I already love it) dual-boot may be an option, but still I'm also thinking about some sort of install on a removable device. This way the folks that need to use computer in my workshop could simply have a pendrive / usb drive etc they would plug in and run the system with all the settings they need and the one they could take home etc.
Also note that in the workshop I won't need to use any high performance apps. Most of the times it will include using web browser, libre writer, some sort of IM and hopefully label priter if I'll be able to make it run on Linux. So there's a chance USB wil do just fine :) .

@gordintoronto: I figured out I'll simply set up thunderbird for mail. Even though I'm not huge fan of mail programs and prefer simplified UI that gmail offers it should do the trick - well until I find solution that suits me better.

As for label printer - I don't mean regular printer, rather device like [[COLOR=SandyBrown]this one[/COLOR]]("http://www.brother-usa.com/labelprinter/modeldetail.aspx?PRODUCTID=QL550#.UOGkcdHfu5k"), used specifically to print labels. A real shame it has no linux drivers - at least I haven't found any. For Win it comes with all the drivers and a handy app to make labels, generate barcodes on them (if needed) and so on. Having it in Ubuntu would mean I would have a perfect solution :) .

---

### Post by audiomick on 2012-12-31
Hi. A couple of thoughts:

It is entirely possible that a dual boot install would run faster than what you have now. Normally, a proper install will run faster than the live environment from a USB. I have to admit, I didn't quite understand how you have installed now.

The situation you describe in your workshop, where every one has their own OS on a stick, is a classic case for USB with persisintence. Remember though, that this will mean a re-boot every time someone else wants to use the machine. It may be more convenient to have a proper install with a user account for everyone.

I have no idea about label printing in Linux, but a quick search turned up these, and I am quite sure it is possible. You are not the only one who wants it... ;)
[http://archive09.linux.com/feature/119566]("http://archive09.linux.com/feature/119566")
[http://blogs.scansource.com/label-printers-and-labeling-software-for-linux-os/]("http://blogs.scansource.com/label-printers-and-labeling-software-for-linux-os/")
Linked from near the end of that
[http://www.kbarcode.net/]("http://www.kbarcode.net/")

[http://www.godexintl.com/news_content.aspx?id=60]("http://www.godexintl.com/news_content.aspx?id=60")

As I said, no experience with any of that, but it should give you a place to start looking.

---

### Post by Pshemas on 2012-12-31
@audiomick: :) , ok so to straighten things up:

My first try with Ubuntu was by downloading iso with ubuntu installer (from [here](http://www.ubuntu.com/pre-download?distro=desktop&bits=32&release=latest)) and burning this ISO on usb drive. Then upon launch I've chosen "try without installing" option. Worked suprisingly nicely and quite fast, but the changes and all the stuff I did were not being saved.

2nd try - downloaded Windows installer for Ubuntu Desktop (wubi.exe), launched it in Win7 and when asked where to install Ubuntu I've chosen USB drive. Hoped that it will result in bootable USB (again - yeah, I know...). But I got non-bootable USB and a modified windows boot manager (upon system start I can choose whether to boot windows or ubuntu). So I can't take the USB and run it on other computer (non-bootable USB). But the modifications are being saved. Surprisingly though the system seems slower than it was during the 1st try. Thus I'm wondering whether it is because dumb install I did, or settings. Any ideas?

And as mentioned proper hdd install is not an option I currently consider. I know I can create couple of accounts. But the apealing option is that I could take the USB drive and have MY system, with my setup on any machine anywhere , not being bound to a specific PC.
I'm not sure it is good idea and whether it will work - I'd like to give it a try though. From the first tries it seems it will work great :) .
But heck, that might be mostly due to the fact I'd rather not game , run videos etc on such usb-installed system.

Maybe later I'll do hdd install on my home computer as I totally fell in love with Unity UI . EVen now instead of booting Windows I run Ubuntu for web surfing and so on. Got to admit that if there were apps I need to use on Linux I'd switch completely. Sadly this is not going to happen - at least in foreseeable future (Zbrush, Rhino etc won't have Linux versions and there are no viable alternatives - with 3d Coat being an exception). Still for regular "office" work it does the trick so well!

Did some further search on Brother QL-500. It looks there are linux drivers, but they seem tricky to use for unexperienced user. I found several reports where people were not able to use them without tweaks. Also the app for making the labels is missing - but there are some templates for Libre Office. So I'd propably try installing those when I'll get some experience :) .
Thx for the link to kbarcode - heck, it looks very similar to the brother label app. Defnitely if I could make it work along with the drivers I'd have exactly what I need :) .

---

### Post by oldfred on 2012-12-31
Not real familiar with wubi, but flash drive is slow writing & USB ports are slower than SATA ports.

I have a full install in my 16GB flash drive, but installed in 8GB and left 8GB for data. A bit slower loading, but Linux caches recent tasks in RAM, so if you have a fair amount of RAM it still will be usable. You do want to make some settings to reduce writes similar to a SSD, although flash drives are slower. 

       With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)

            Full install of 12.04 to 64GB USB device C.S.Cameron post #3
[http://ubuntuforums.org/showthread.php?t=2092077](http://ubuntuforums.org/showthread.php?t=2092077)
Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)


Actually an install to an external device is the same as to any second device, internal or external. But you have to use manual install or Something Else so yo get the option on where to install the grub2 boot loader. Otherwise any auto installs will default to sda and you will not have a separately bootable flash drive.

Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

With SSD or Flash drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.

---

### Post by audiomick on 2013-01-01
> **oldfred said:**
> ... - now alternative (text based) installer....
I believe I read that the alternate installer is not being offered anymore, which I consider to be a pity.
Edit: just had a look in relation to another thread. It seems there is one available for 12.04, but not for 12.10


@pshemas: As Fred has already indicated, it is pretty certain that the way you have installed will not run very fast.

You seem to be getting a good grip on things. Look at those links that Fred posted. It seems an install  on a USB device will work for you. Just remember that you have to get Grub on the USB device so it will be found when you tell the computer to boot from there, and leave the windows mbr intact on the machine so it can be found when the machine is not booting from the USB device.

---

### Post by mike555 on 2013-01-01
once you get it installed try "gLabels" program , to make labels.

---

### Post by Pshemas on 2013-01-02
wow, thx guys, lot of info here :) .
Can't wait to try those tips. Will play with those during the weekend.

---

### Post by Pshemas on 2013-01-05
Ok, run the installer again :) .

Partitioning went easy and the system started. Then I wanted to turn off journaling. But as I'm no familiar with the way Linux connects devices I did not know what should I type in "sudo tune2fs" command . But I remembered I got such info when partition manager has been running. So I run installer again (yeah, I forgot I could use a dash search) just to check it (turned out to be sdc2). But as the installer has been running I thought I'll start from scratch and install the whole thing again .
So repartitioned the USB drive, waited for installer to finish , rebooted and ....

Well , now I'm getting this message upon booting "/boot/grub/i386-pc/normal.mod" not found" . 
Any ideas  howto fix it? My first thought was that I should clean the mbr of the usb drive but I'm not entirely sure howto do it - and whether in fact it is needed ;) .

As a side note - in the post by Cameron it is suggested to use ext2 for 2nd linux partiton.  I'm courious - why ext2?

---

### Post by Pshemas on 2013-01-06
Ok, after another repartitioning an reinstalling the things went worse - the system won't boot from the USB at all. Also I've noticed that there 1MB of free space has been left on the beggining of the USB flash drive.
ATM will try Rescatux - maybe I'll be to fix mbr with it. If that won't work I'll see what happens if I "burn" USB Live USB.
But got to admi I'm close to giving up - mostly due to lack of time to try figure this one up.

edit: Quick update on things. I was unable to boot Rescatux (I've used Universal USB Installer to record it on one of the flashdrives) - the mbr has been modified, but I get some error upon boot. And note I used different flashdrive than the one I'd like to have Ubuntu on (well, otherwise it wouldn't make sense, would it ;) ? ).  
Ok, so I've got back to the drive I want to install Ubuntu on and tried using the USB Installer to burn Live USB . The first time I did it I was able to do it without issues. But now I can't make it bootable. So I guess that during using ubuntu partitioneer something went wrong, some sort of change has been made that prevents making this flashdrive bootable. ANy ideas ?

---

### Post by oldfred on 2013-01-06
We regularly see users with flash drives that do not work. Some are user error or the download of the ISO was not correct, some have BIOS that do not work with flash drives, some flash drives just do not seem to work, or may work on one system but not another. That may be BIOS settings but I have not seen anything conclusive. 

I have Microcenter or Kingston flash drives and they all have worked on both of my older (about 6 yrs) systems.

Many suggest ext2 for flash as that does not have a journal. Ext4 has other improvements and someone did post that it was better to use ext4 with journal off than use ext2. But not sure if a big issue.

---

### Post by Pshemas on 2013-01-06
Thx Fred! Got to admit I'm getting tired.

IMO the issue is mbr/partition related , not BIOS related. As mentioned the first time I did the install it worked. Also I can select USB as a boot device.

I'm trying to figure out what I did. I suspect that the first time I did the install I simply removed the big fat32 partiton and then made 4 partitions as in the posts by Cameron.
The 2nd time I propably clicked "New Partiton Table" and this is when the problems started. The USB become completly unbootable - neither install, or LIVE USB made with ["Universal USB Installer"]("http://www.pendrivelinux.com") worked.

Also I've noticed that the structure of the partitons changed - I got some free space I was unable to allocate.

I've been able to get one big partiton again by using Bootice utility  and setting USB-FDD mode. The result was a tad different though -  USB become bootable. But with it I can't make any extra partitions (as expected in fdd mode). So it is only viable for Live USB installer, not for regular USB install.

This result made me somewhat more optimistic. Thought that setting USB-HDD mode with multiple partitons may finally resolve the problem. Sadly it does not. I've been able to make partitions , set the boot loader installation to "sdc" , but sadly after install the system is still non-botable - so the boot manager does not install correctly.

You know , waiting 20 minutes for the system to reinstall only to see it is not working is kinda frustrating.
I hoped that maybe I could use simply some type some sort of command that would only try to reinstall boot managaer on a chosen disc , not the whole system. This would allow me to play with the settings in a reasonable way. 
I found one tutorial that suggested installing mbr package and using it for this purpose. But when I try:
[B]apt-get install mbr
[/B]I get the info that the package can't be found.... ARGHHHH.....

Will propably try reinstalling final 2-3 times . If that won't work I quit. With my current knowledge further attempts will be a waste of time.

BTW - when I got a usb-fdd mode and made a LIVE USB  I used the persistance option. But either I did something wrong or simply don't get it - the settings I've changed have not been saved.

---

### Post by mastablasta on 2013-01-06
> **Pshemas said:**
> 
I hoped that maybe I could use simply some type some sort of command that would only try to reinstall boot managaer on a chosen disc , not the whole system. .

there is! there is even a GUI tool fo rit called boot repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

why are you trying to stick it on USB? just set up an empty partition in windows and install there. select to install next to windows and all partitioning and such is handeled for you. it should also be handled for you if oyu want to install it to USB flahs disk. only in this case you need to tell it to put the GRUB (bootmanager) to USB drive. otherwise it will put it on your main drive and you will need to have USB in even if you want to boot into windows.

if you want to just try it out more extensively you can use virtual box.

oh and if you want to make you own mix/setup and then distribute it to other computers you need to install it to hard disk and then make the changes you want to make and the use *remastersys* to create your very own version of "ubuntu".


have a look- installing (inlcudes side by side install): [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
virtual box install: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

also have a look at community made manual (seem y signature for instructions)  to learn a bit more about the OS and how it all works.

there are other interfaces besides default Unity/gnome. Kubutnu for example has KDE interafce which looks & feels preety much like windows. especially in classic view. it also has high customisation options. this goes for Xubuntu (featuring XFCE) as well. most customisations in Xubuntu can be done using right click and selecting porpperties. yup it's that easy....

---

### Post by Pshemas on 2013-01-06
@mastablasta: thx :) .
As mentioned earlier I want an USB install as I want to get a pocket system I could take with me. Don't need a fixed install atm :) .

As for GUI - yeah I know about alternatives. I'm not too fond about KDE. For me (and no pun intended, it is just my personal opinion) making a windows gui clone does not make much sense. If I have wanted Windows I'd use Windows :) .
In fact what drawn me to Ubuntu was Unity GUI - it is different but in a good way, IMO much cooler and more effective.
At one time I'd also like to give Gnome 3 a shot as it also looks different, with some cool functionality. In the end I think it will be a choice between Unity and Gnome for me - will see which works better for my needs.

After playing with Bootice settings I've been able to install Ubuntu on USB :) ! YAY! 
There were issues upon boot - I got an info that dev for /home folder (partition with ext2) can't be mounted. But I was able to mount it by going into manual mode and using commandline commands :) .
Noticed that what previously was sdc now is sdb .
Ok, so now I'll try to tune the performance and disable journalling on sdb2. When I run **sudo tune2fs -O ^has_journal /dev/sdb2** I'm getting info that I can do it only when filesystem is unmounted. So I guess I have to boot from other disc and try this command from it, right?

---

