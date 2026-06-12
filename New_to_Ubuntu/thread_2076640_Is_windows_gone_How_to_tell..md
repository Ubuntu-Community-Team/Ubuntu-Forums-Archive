---
title: "Is windows gone? How to tell."
date: 2012-10-26
forum: New to Ubuntu
---

### Post by Rpm90001 on 2012-10-26
I have to apogize in advance.  Up till 3 days ago I never heard of Ubuntu, and have a few questions that may be very noobish.   Our church gave my kids a nice computer that was donated, and they were very excited to set it up.   When we turned it on, It did not look like windows.  Turns out to be ubuntu.   

1) I have done hrs of reading and searching but could not find my answers.  How do I figure out of the last owner  erased windows or just added Ubuntu?   If I hit esc during start up, it shows a few options, but nothing that says windows..    I would like to get windows back on this maching for the kids, but would be nice to have the dual boot option because Ubuntu looks interesting.  Anyways...how do I tell if windows is gone.  

2) the computer has a wireless card in it,  I can't find a way for it to search for our wireless signal.  I found what're it should be, but it does not show my signal.   

3) if windows is gone,  can I get a windows disk and just reinstall windows? Boot from the cd.   Any issues to expect?

Thank you for any help.

Geo

---

### Post by linuxvstheworld on 2012-10-26
Yeah, getting the Windows 7 disc should be fine. just boot via CD, remove the partitions on the hard drive, and install Windows.

You may want to try Ubuntu on a test laptop sometime, it's pretty neat. :D

---

### Post by Pilot6 on 2012-10-26
When system is booting press and hold SHIFT key. You will see grub menu. If there is Windows, then you can boot into it.
Why do you think there was Windows on this comp?
If there is no Windows you can buy it and install.
Regarding wireless problems you need to provide more details to get help.

---

### Post by Bashing-om on 2012-10-26
Rpm90001; Hi ! Welcome to the forum.

A certain way to see if windows exist on the system is to look at the partitioning.
ctl+alt+t will activate a command line terminal;
in this terminal type the terminal code:
```
sudo fdisk -l
```shucks...as the system is donated ...you most likely do not have the password to use "sudo" ....
Here are easy instructions to reset your password in Ubuntu::
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
and get all of you indoctrinated to the wonderful world of ubuntu.
[INDENT]kind regards <== BDQ

[/INDENT]

---

### Post by Rpm90001 on 2012-10-26
Well the frot of the computer says windows xp, so I figured it originally was xp.   What info is needed to help me get the wireless working, I would like to try Ubuntu for a while. I will post what ever I can,  please talk in small words... Im not an expert.

Thank you for any help.


Geo

---

### Post by Old_Grey_Wolf on 2012-10-26
Are you able to login to the computer?

Are you able to run the sudo fdisk -l command that Bashing-om suggested? That will tell us if Windows XP is still on the computer.

You will not be able to set up the wireless in Ubuntu if you do not have the Ubuntu user password.

Alternatively:

Since there is noting on the computer that you need to save you may want to consider downloading Ubuntu and doing a fresh install. Download website and instructions are at [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

You probable want to read about burning a DVD or USB and trying Ubuntu without installing it (half way down the webpage on the right). I recommend trying it out before installing it.

---

### Post by deadflowr on 2012-10-26
> **Old_Grey_Wolf said:**
> Are you able to login to the computer?

Are you able to run the sudo fdisk -l command that Bashing-om suggested? That will tell us if Windows XP is still on the computer.

You will not be able to set up the wireless if you do not have the password .

Alternatively:

Since there is noting on the computer that you need to save you may want to consider downloading Ubuntu and doing a fresh install. Download website and instructions are at [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

You probable want to read about burning a DVD or USB and trying Ubuntu without installing it (half way down the webpage on the right). I recommend trying it out before installing it.

+1 
I personally, would do a fresh install of either Ubuntu, or Windows. You never know what might have been put on it, and installing it yourself saves you the time trying to figure out which version you're running, among other things.
For possible help with your WIFI, here:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

For Ubuntu Documentation here:
[https://help.ubuntu.com/]("https://help.ubuntu.com/")

These are the currently supported versions of Ubuntu. Hopefully, one of these versions will be the right one loaded onto your system.

But yes, a fresh clean reinstallation is probably the best thing to do. It is quite quick with Ubuntu, and very simple.

---

### Post by Old_Grey_Wolf on 2012-10-26
> **deadflowr said:**
> 
For Ubuntu Documentation here:
[https://help.ubuntu.com/]("https://help.ubuntu.com/")

These are the currently supported versions of Ubuntu. Hopefully, one of these versions will be the right one loaded onto your system.

For clarification, the 8.04 release is only supported for the server release. It has already reached end-of-life for desktop release.

---

### Post by Rpm90001 on 2012-10-26
Thank you all.

I was able to reset the password,  I did a search a few nights ago..that went well and now in the system.  I'm actualy updating Ubuntu now, I see updates and just hit it, I guess I don't have much to lose..

I will post a cell picture I took of a few screens in the next post.

Thank you all for the help.

Geo

---

### Post by Rpm90001 on 2012-10-26
Still updating.... Here is a picture of the screen before update,

[IMG]http://file.walagata.com/w/rpm9001/ubuntu2.jpg[/IMG]

  [IMG]http://file.walagata.com/w/rpm9001/ubuntu1.jpg[/IMG]

---

### Post by Barney-R on 2012-10-26
I'm still a comparative Ubuntu newbie, Rpm90001, so I hope I "speak" your language.

Whichever computer you've got, you can always install a new operating system, whether it's Windows or one of the many flavours of Linux. Just put an installation CD or DVD in the drive and re-boot (shut down and restart).

If you just want a single operating system, whichever one it is, let it clear everything out and go for a clean install.

Ubuntu IS different to Windows, and it can take a while to get used to, but it's worth it in my opinion. I won't be going back.

Here are a few of my reasons.

Cost.

All Linux versions are free, and in my opinion, Windows is over-priced and too restrictive. Also, there's no need to waste money on M$ Office because Linux comes with Open Office pre-installed.

If you need additional software, Windows users usually have to pay for it, or they may risk "dodgy" downloads from unknown sources. Linux has literally thousands of applications kept in secure "repositories" and available through the software center. Best of all, with only a few exceptions, they're free.

You can create as many Linux CDs as you like to share with friends.

Security.

Linux is designed with security in mind. It may not be perfect, but you don't have to scan every day for viruses and spyware, and the "ports" aren't wide open to hacking/cracking like they are in Windows.

I wouldn't say Linux is "immune" to viruses and other forms of attack, but it's pretty close. I do a virus scan a few times a **year** (not every day like I used to when I had Windows) and all it ever picks up on is the occasional "phishing" e-mail, which I delete anyway.

Versatility.

There is very little Windows can do that Linux can't, and I believe I'm right in saying a basic installation of Linux can do things Windows can't or won't.

Freedom to experiment.

Those who have the necessary programming skills can download the source code and alter it in any way they want, even creating new "distros" (versions) if they think their modifications warrant a new release, though I believe these may need to be approved in some way prior to an official release.

---

### Post by MG&amp;TL on 2012-10-26
Er...you've got Mepis on there as well by the looks of it...I would do a fresh install of something like Xubuntu or Lubuntu (XP-vintage machines tend not to run later Ubuntu releases so well). 

Depends what you want, but another distro you don't use will use hard disk space.

---

### Post by Bashing-om on 2012-10-26
you are presently running "lucid lynix" version 10.04. [kernel version 2.6.32-38]
This version also is approaching "End Of Life" ...Will no longer have official support after upcoming April....
As a new user ..might be behooving to learn the new desk top interface ( radical take off from 10.04) as presented in the current LTS (long term support) 12.04.

Reaffirm: installation is simple, and quick. -> great/direct/responsive support !
another point ...in ubuntu .....There are no secrets
[INDENT]just my opinion ==> BDQ

[/INDENT]

---

### Post by Rpm90001 on 2012-10-26
OK,  I did an update and everything seems to be running well.   I have a wireless card and would like to get that working.  Where do I start?   No wireless shows under networking.

Here is a new screeen shot using the code given in a previous post.

[IMG]http://file.walagata.com/w/rpm9001/6902752.png[/IMG]

[IMG]http://ubuntuforums.org/<IMG SRC=&quot;http://file.walagata.com/w/rpm9001/6902752.png&quot;><br><br>[/IMG]

---

### Post by Bashing-om on 2012-10-26
as you are now aware the output of "fdisk" proves nothing other than linux (ubuntu) exist on the system.

Wireless not my strong point ..but, simple thing first -> top bar on the 10.04 screen left endward ...two opposing arrows (icon) ...click on the arrows -> network manager...ensure networking is enabled.
These links will provide the needed instruction for troubleshooting your wireless connection:
reading is good for you.
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices)
[https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections)

I remind you again, as you have questions, ask !
[INDENT]try'n to help <== BDQ

[/INDENT]

---

### Post by Rpm90001 on 2012-10-27
Thank you im off to do some reading.

---

### Post by Bartender on 2012-10-27
Congratulations on installing Ubuntu!
However, from the pictures you sent, I'm guessing that you picked the wrong option when you installed it.  It appears to me that Mepis is still on there.

IIRC about four or five steps into the installation CD you get a choice to wipe the drive & start over, install to existing partition, create a new partition, or 'something else'. The best choice for you would have been to wipe the drive clean and start over.

- sda1 appears to be Ubuntu.  Yay!
- sda2, at the far end of the HDD, appears to be swap.  A little weird, but not the end of the world.
- sda3 is an extended partition, which contains sda5 & sda6.  sda5 & sda6 appear to be another Linux installation (the OS on 5 and another swap on 6).  I'm guessing that's Mepis.  It's taking up half the drive.  You could use that space.

I know, it's frustrating to start over.  You could try deleting the entire Extended partition, then expanding sda1 into the free space.

I wouldn't do that from the Ubuntu CD because you have to deal with unmounting.  I'd use a stand-alone partitioner like GPartedCD.

The simplest option would probably be to boot from the Ubuntu CD, then pick the 'wipe the drive and start over' option.

You mentioned that the PC had a Windows XP sticker.  I don't think you said what model PC you've got?  For many many years, a person could call HP or Dell and ask for a replacement recovery disc.  Recovery discs generally cost about $20, and it wasn't a big deal to get them.  However, all or most of the big box manufacturers won't sell you an XP CD anymore.  If it came with Vista, you can still buy a recovery CD, but not XP.  Besides, XP support ends early 2014, so exploring the new frontier is probably your best bet with this old PC.

That or buying a copy of W7, then hoping you can find drivers for the old equipment.

Another thing about XP - the big box manufacturers sent millions of PC's out the door with 512 MB of RAM.  XP uses most of that RAM just to run itself.  If this box only has 512, Linux is going to run much snappier.

I'd suggest trying out Lubuntu.  It's a lighter-weight desktop.  I've got an old Pentium 4 PC with 2GB of RAM inside.  The 12.04 Ubuntu Desktop is sluggish.  I've had umpteen versions of Ubuntu on this PC and 12.04 feels the slowest that I can recall.  I went into Ubuntu Software Center and installed "lubuntu-desktop".  It runs much snappier now.  There are directions for this operation all over the net.  It's pretty easy.

One more thing, and this is just a maintenance issue.  If I were you, I'd replace the CMOS battery while I had my head under the hood.  The CMOS battery is the coin battery on the motherboard.  They usually die at about 5 to 7 years.  Before they go completely kaput, your PC will start doing very weird things.  Sometimes you can pop the old battery out and get the new one in before the BIOS chip loses all its settings and goes back to default, but usually not.  So it's a good idea to go thru the BIOS and see if there are any settings that you want to check after replacing the battery.  From what I've seen, most PC's have their BIOS still set to the defaults after many years of use because most people don't know how to go into BIOS.

Go to the manufacturer's website and root around for the PC's manual.  HP and Dell and etc. usually will have a fairly detailed .pdf describing BIOS settings.  This is a good reference to have in any case, but especially if you're going to replace the battery.

EDIT: Regarding the wi-fi card, your best bet may be to google around on Newegg or what have you and find a PCI wi-fi adapter that has good Linux feedback.  If the card doesn't have native support, I wouldn't suggest messing with it.  Not for someone who's new to this and just wants the PC to work.

---

### Post by Rpm90001 on 2012-10-27
Thank you for the info.   I'm gave the kids my ine to use, I would like to try this os out for a while.  I looked in to afactory recovery disk, but they are no longer avaiable.   I would like to start fresh and do as suggested with a fresh install.   I did update online,.  How do I get a disk to do a fresh install?

I will change the battery, I did test it, it's a bit over 3v.

I believe the last owner had some computer knowledge, so I don't know if anything was upgrades.   Is there a way to see on screen what the specs are?

The tag on the computer says HP Pavilion a1000y (PU128AV) CTO Desktop PC

Thanks for sticking with me on thei.  Once I get a fresh start,  things will be much smoother.

So I want a fresh start... Get a umbuntu disk?   Download?  I never had a cd,  I just went to update from the desktop.

Thanks everyone

---

### Post by cmcanulty on 2012-10-27
If it is a pretty old version I would definitely download 12.04.1 to a DVD or USB and do a fresh install and for sure make a / partition of around 10 to 15 GB and a swap of a few GB and a separate /home partition for the rest. That way you can do clean installs and upgrades without endangering your settings and documents. Then no danger of old issues or files messing you up. Do 12.04 not 12.10 as 12.04 is a 5 year support release

---

### Post by nothingspecial on 2012-10-27
You can download Ubuntu from here

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

You will probably get a faster smoother experience with Lubuntu

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Installation process is the same.

If you need more help, start a new thread with a descriptive title.

---

### Post by Bartender on 2012-10-27
Oh, I see, I missed a few things the first time through.  You didn't install Ubuntu from a CD, you went online and let the servers update you from the previous version to the newest.

Sorry, I missed that the last time around.

I'm +1 with nothing special - I'd just go to Lubuntu and avoid Ubuntu.

This is hard to grasp at first, because it's foreign to the Windows experience, but you can install several different desktop environments on a Linux PC even though there's only one operating system in the background.  If a person wanted to, they could install the Kubuntu, Ubuntu, Lubuntu, and Xubuntu desktops to one PC.  Then you simply log out of one, and log into another.  For the most part, the programs that are installed to the OS are available in each desktop.

I wouldn't do that myself.  I'm just saying that it's possible.  

Lubuntu is a "lighter-weight" desktop that doesn't need as much computing horsepower as the Ubuntu (Unity) desktop.

There are about a gazillion guides to making an installation CD.  Read a few of them just to get a feel for it.

Follow nothing special's link to Lubuntu.  Pick the one I circled in the screenshot below.

Save to your Desktop is probably easiest.  Once it's done, if you open Brasero and point it to the download, it should do the rest.  Brasero will see that it's an .iso and do the right thing.  Be sure to pick a slow burn speed!  4X or so on an old PC like yours.

You could also save that download to a thumbdrive and burn it on a friend's PC.  If someone has a fast, modern Windows PC, install ImgBurn to it, plug in your thumbdrive, copy/paste the download to their desktop, and have them make you a bootable disc.  Creating a bootable disc is _not_ the same as copying the data to a CD!!!

Then all you gotta do is boot from the CD, wait for it to come up, and install to the entire drive.  

If the Pavilion _doesn't_ boot from the CD you'll have to turn the PC off, go into BIOS and change the boot order.  This is a simple thing for anyone who's done it a few times.  It can be very frustrating if you've never messed around in BIOS before.  You may not have to go into BIOS and change the boot order - that Pavilion may have a "quick-boot" option in BIOS.  If it does, there's a certain key, usually one of the F keys, that stops the bootup process and gives you the option of booting from whatever devices the BIOS thinks it can boot from.  This is easier than going into BIOS and changing the boot order, but the Pavilion may not have that option.

As I suspected, the HP Pavilion came with [512 MB RAM]("http://reviews.cnet.com/desktops/hp-pavilion-a1000y-customizable/4505-3118_7-31396088.html")

Here's a real [easy way]("http://howtoubuntu.org/how-to-find-out-how-much-ram-is-installed-in-ubuntu/") to check your current RAM

I think you'll be pleased with a fresh install of Lubuntu.  I was a little nervous about using it since it's a "lighter-weight" desktop environment but the experience has been positive so far.  Lubuntu will feel more "familiar" than Unity.

Here's the [website for your PC]("http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&dlc=en&product=461232").  From there you can get manuals and specs.

---

### Post by Bartender on 2012-10-27
Whoops

Here's the screenshot that was supposed to be in the post above...

---

