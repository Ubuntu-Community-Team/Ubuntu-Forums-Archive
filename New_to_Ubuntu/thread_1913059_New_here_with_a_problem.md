---
title: "New here with a problem"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by winscar on 2012-01-21
Hello,

I'm new to this forum and completely new to Ubuntu. I recently installed the Ubuntu version 11.4 onto my sister's computer(I believe it's this version) and I'm trying to install applications needed for Linksys AE2500 to work on it. 

I searched the web and realized I needed an application called wine in order to install it. Problem is, I think most of the guides and responses I read requires internet connection which unfortunately I don't have. 

I propose a solution to this. Provide an executable wine file that I can download onto my computer and then transfer it over to my sister's computer to run. Sadly, I couldn't find such thing.

The guides I have read states that I need to type in statements in the terminal to gain stuff from the package. I done it couple times but it keeps stating the file cannot be found. Here's the reference: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Can someone please tell me how to get wine and install it? I'm so confused. I need it to install the Linksys AE2500 Dual-Band Wireless-N USB Adapter CD which is a .exe file so my sister can finally surf the web on her new computer.

Much appreciated,
Thanks. :D

P.S. Just as I was able to submit this thread it said it doesn't have a prefix. I don't know what prefix to choose so if I pick something wrong, please excuse me.

---

### Post by Double.J on 2012-01-21
Hi there, 
Welcome to the forums!

I'm afraid I don't know anything about usb wireless as I've never had one, but [this binary package]("http://pkgs.org/ubuntu-11.04/ubuntu-multiverse-i386/wine1.0_1.0.1-0ubuntu14_i386.deb.html") should work for getting wine.

If it generates any dependencies you don't have, look them up on pkgs.org

Hope it helps :)

---

### Post by grahammechanical on 2012-01-21
If you do not mind me saying it I think you are going in the wrong direction. We do not use wine to install Windows drivers. That is what you are trying to do, is it not?

When you buy an item of hardware to use with Windows the maker has to supply a driver for Windows to use the hardware. That does not happen with Linux.

Sometimes we use something called Ndiswrapper to use a Windows driver to get a wireless adapter to work. Here is the link for you to read about it.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

I am not sure that it is necessary for the device that you are using. So, let us start from the beginning. How do you know that Ubuntu is not recognising this USB wireless device?

Please remember that we cannot see what you are seeing on the computer screen. You have to tell us. Do you see a network icon in the top panel? It can look like a segment of a circle (no connections), four curves (arcs) radiating upwards (trying to make a connection) and two arrows going in opposite directions (a wired connection). What do you see when you click on it?

This will give us a clue. I am asking these things because you say that you are new. We have no way of knowing how much or how little you know.

Here is a link to the wireless trouble shooting guide.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Here is a link to another thread where others had the same problem.

[http://ubuntuforums.org/showthread.php?t=1805830&page=4]("http://ubuntuforums.org/showthread.php?t=1805830&page=4")

Do not give up hope. Keep reading all the way down to page four. It might have the solution for you.

Regards.

---

### Post by anewguy on 2012-01-21
Indeed, wireless drivers don't go in wine - they won't work in that even if they did install, which is extremely doubtful, they would be restricted to just wine - they would not be visible to Linux and its' applications.

There are a couple of things we need for more information:

- open a terminal window

- type:

lspci > ~/dwetest.txt [press enter]

lsusb >> ~/dwetest.txt [press enter]

lshw -C network >> ~/dwetest.txt [press enter]  this will scroll a few lines by, mainly on top of each other, and then return the information we need

ifconfig >> ~/dwetest.txt [press enter]

iwconfig >> ~/dwetest.txt [press enter]

The single ">" on the first command ask that the output be put in a new file - in this case dwetest.txt.  The double ">" {>>} in the rest of the commands ask the the output be appended to a file - in this case dwetest.txt.

Attach the file in a reply back here.

In the mean time, there are a few things worth trying:

- if you can hard-wire your computer to the router, do so, then do the following in a terminal window:

sudo apt-get update

sudo apt-get upgrade

- go to additional (it might say restricted) drivers, wait for it to load, then if a driver shows select "enable" or "install" (I don't recall what the exact instance is)

This is to try to get a native driver loaded and running for it.

If that fails, there is indeed ndiswrapper, a tool that is used to let linux uses windows networking drivers.  This is normally used as a tool of last resort, since native drivers are preferred, but there is nothing wrong with using it.  If you decide you want to do that, just post back as I can give you some step-by-step easy to follow instructions that will be current - including using ndisgtk, the graphical front-end to ndiswrapper so you don't have to do a bunch of typing to get it to work.

Just reply back - if you want to use ndiswrapper it's no problem and I'll get you through it quickly.  Let's just see if we can find a native driver first!

Dave ;)

---

### Post by sandyd on 2012-01-21
> **winscar said:**
> Hello,

I'm new to this forum and completely new to Ubuntu. I recently installed the Ubuntu version 11.4 onto my sister's computer(I believe it's this version) and I'm trying to install applications needed for Linksys AE2500 to work on it. 

I searched the web and realized I needed an application called wine in order to install it. Problem is, I think most of the guides and responses I read requires internet connection which unfortunately I don't have. 

I propose a solution to this. Provide an executable wine file that I can download onto my computer and then transfer it over to my sister's computer to run. Sadly, I couldn't find such thing.

The guides I have read states that I need to type in statements in the terminal to gain stuff from the package. I done it couple times but it keeps stating the file cannot be found. Here's the reference: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Can someone please tell me how to get wine and install it? I'm so confused. I need it to install the Linksys AE2500 Dual-Band Wireless-N USB Adapter CD which is a .exe file so my sister can finally surf the web on her new computer.

Much appreciated,
Thanks. :D

P.S. Just as I was able to submit this thread it said it doesn't have a prefix. I don't know what prefix to choose so if I pick something wrong, please excuse me.
No drivers. Uses BCM43236 Chipset
You will have to wait for the linux devs to add it into the kernel via brcmfmac. Rather, its the USB support they need to add to brcmfmac. Their apparently testing it out [right now]("http://www.spinics.net/lists/linux-wireless/msg83256.html")

---

### Post by anewguy on 2012-01-22
Sounds like ndiswrapper/ndisgtk may be the only thing left to try.

Please be aware of the following prerequisites:

- you need the .inf and .sys files that make up the driver from Windows

- they must be Windows XP drivers

- the driver and ubuntu architecture must match - 32 bit Ubuntu and 32 bit drivers, 64 bit ubuntu and 64 bit drivers.


Now to get started:

[LIST=1]
[*]Copy the .inf and .sys files that make up the driver to a folder such as windrivers within your home folder
[*]Install ndiswrapper:
[LIST]
[*]boot up ubuntu as normal
[*]put the Livecd in the drive - you may get a message about a software source being found - just cancel that
[*]use the file explorer and navigate to the LiveCD
[*]navigate to the /pool/main/n folder.  You should see 2 folders:  ndisgtk and ndiswrapper.
[*]navigate to the ndiswrapper folder.  You should see 2 files:  ndiswrapper common and ndiswrapper utilities.
[*]Double-click the ndiswrapper common file to start it's installation.  This should call up the software center with the package selected and it should start installing.  Wait for this to finish.
[*]Repeat the above on ndiswrapper utilities file and wait for it to complete.
[*]Navigate back to the /pool/main/n/ndisgtk folder
[*]Double-click the ndisgtk file and wait for the installation to finish.
[*]At this point you have the driver files needed and you have ndiswrapper and the gui'd front end ndisgtk ready to use.
[/LIST][*]Now open Windows Drivers - this starts ndisgtk.  
[*]Select new (or maybe it's add)
[*]Point it to the folder containing the .inf and .sys files that make up your driver
[*]Click OK (or add or whatever the verbage actually is) and should return saying the device is loaded and ready for use.
[*]Close out of ndisgtk.
[*]Click on the network manager icon and be sure Enable Wireless is checked.
[*]It may take a minute or 2, but you should see available wireless networks in network manager.[/LIST]

I hope that helps.  Please post back with the results.

Dave ;)

---

### Post by sunewbie on 2012-01-22
try [portable software center]("http://www.webupd8.org/2011/12/portable-software-center-create-custom.html")

also have a look at the signature of @cortman

[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

scroll down to second thread. Notice 3 links?? . they could be og help to you.

but first you need to find a driver for Linux (debian / ubuntu) and you need ot manually download it.

---

### Post by anewguy on 2012-01-23
> **sunewbie said:**
> try [portable software center]("http://www.webupd8.org/2011/12/portable-software-center-create-custom.html")

also have a look at the signature of @cortman

[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

scroll down to second thread. Notice 3 links?? . they could be og help to you.

but first you need to find a driver for Linux (debian / ubuntu) and you need ot manually download it.

See the ending comments from sandyd's post above - there is no driver.  That's why I recommended trying ndiswrapper.  It's not a sin to use it ;)

---

### Post by sunewbie on 2012-01-23
> **anewguy said:**
> See the ending comments from sandyd's post above - there is no driver.  That's why I recommended trying ndiswrapper.  It's not a sin to use it ;)

Oh yes :) I remember, I had to install ndiswrapper for wireless LAN on 9.1 Karmic. It worked very well, better than driver in XP :)

---

### Post by winscar on 2012-01-24
> **anewguy said:**
> Indeed, wireless drivers don't go in wine - they won't work in that even if they did install, which is extremely doubtful, they would be restricted to just wine - they would not be visible to Linux and its' applications.

There are a couple of things we need for more information:

- open a terminal window

- type:

lspci > ~/dwetest.txt [press enter]



Typed in but nothing is shown on the Terminal.

>  lsusb >> ~/dwetest.txt [press enter] Again, typed in but nothing appears on the Terminal.

> lshw -C network >> ~/dwetest.txt [press enter]  this will scroll a few lines by, mainly on top of each other, and then return the information we needIt says: 

WARNING: you should run this program as a super-user.
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

> ifconfig >> ~/dwetest.txt [press enter]Typed in, nothing appears.

> iwconfig >> ~/dwetest.txt [press enter]It says:

lo                no wireless extensions.

eth0             no wireless extensions.

> 

The single ">" on the first command ask that the output be put in a new file - in this case dwetest.txt.  The double ">" {>>} in the rest of the commands ask the the output be appended to a file - in this case dwetest.txt.

Attach the file in a reply back here.

In the mean time, there are a few things worth trying:

- if you can hard-wire your computer to the router, do so, then do the following in a terminal window:

sudo apt-get update

sudo apt-get upgrade

- go to additional (it might say restricted) drivers, wait for it to load, then if a driver shows select "enable" or "install" (I don't recall what the exact instance is)

This is to try to get a native driver loaded and running for it.

If that fails, there is indeed ndiswrapper, a tool that is used to let linux uses windows networking drivers.  This is normally used as a tool of last resort, since native drivers are preferred, but there is nothing wrong with using it.  If you decide you want to do that, just post back as I can give you some step-by-step easy to follow instructions that will be current - including using ndisgtk, the graphical front-end to ndiswrapper so you don't have to do a bunch of typing to get it to work.

Just reply back - if you want to use ndiswrapper it's no problem and I'll get you through it quickly.  Let's just see if we can find a native driver first!

Dave ;)Thanks for your help. What's a native driver?

---

### Post by anewguy on 2012-01-24
Nothing would show in the terminal - I had you redirect the output to a file - dwetest.txt.  Please post back here and attach that file.  Just copy to a removable media, such as a USB stick, and bring to the machine you are posting from.

However, from Sandyd's post there is no native (in other words, written for linux) driver.  That's why I typed in everything in post 6.  Please follow it.

---

### Post by winscar on 2012-01-24
> **anewguy said:**
> Sounds like ndiswrapper/ndisgtk may be the only thing left to try.

Please be aware of the following prerequisites:

- you need the .inf and .sys files that make up the driver from Windows

- they must be Windows XP drivers

- the driver and ubuntu architecture must match - 32 bit Ubuntu and 32 bit drivers, 64 bit ubuntu and 64 bit drivers.



Well, I did a complete hard wipe. I don't know if my Windows XP files and drivers are still here. I don't know how to check >.<

> 


Now to get started:

[LIST=1]
[*]Copy the .inf and .sys files that make up the driver to a folder such as windrivers within your home folder
[/LIST]



Hmm... I'm a bit confused. Where's this .inf and .sys files?


> 


[LIST=1]
[*]Install ndiswrapper:
[LIST]
[*]boot up ubuntu as normal
[*]put the Livecd in the drive - you may get a message about a software source being found - just cancel that
[*]use the file explorer and navigate to the LiveCD
[*]navigate to the /pool/main/n folder.  You should see 2 folders:  ndisgtk and ndiswrapper.
[*]navigate to the ndiswrapper folder.  You should see 2 files:  ndiswrapper common and ndiswrapper utilities.
[*]Double-click the ndiswrapper common file to start it's installation.  This should call up the software center with the package selected and it should start installing.  Wait for this to finish.
[*]Repeat the above on ndiswrapper utilities file and wait for it to complete.
[*]Navigate back to the /pool/main/n/ndisgtk folder
[*]Double-click the ndisgtk file and wait for the installation to finish.
[*]At this point you have the driver files needed and you have ndiswrapper and the gui'd front end ndisgtk ready to use.
[/LIST]
 
[*]Now open Windows Drivers - this starts ndisgtk.
[*]Select new (or maybe it's add)
[*]Point it to the folder containing the .inf and .sys files that make up your driver
[*]Click OK (or add or whatever the verbage actually is) and should return saying the device is loaded and ready for use.
[*]Close out of ndisgtk.
[*]Click on the network manager icon and be sure Enable Wireless is checked.
[*]It may take a minute or 2, but you should see available wireless networks in network manager.
[/LIST]

I hope that helps.  Please post back with the results.

Dave ;)

When you mention the LiveCD is it the wireless adapter CD or the ndiswrapper? If it's the ndiswrapper, I guess I will need to burn some data onto a disk for my sister's computer.

Once again, thanks for your assistance :P

---

### Post by winscar on 2012-01-24
> **anewguy said:**
> Nothing would show in the terminal - I had you redirect the output to a file - dwetest.txt.  Please post back here and attach that file.  Just copy to a removable media, such as a USB stick, and bring to the machine you are posting from.

However, from Sandyd's post there is no native (in other words, written for linux) driver.  That's why I typed in everything in post 6.  Please follow it.

Oh... I get it. I will get the file now. Give me a moment. :D

EDIT: I got the file.

---

### Post by anewguy on 2012-01-24
Please, follow post 6.  The livecd is the media you installed ubuntu from - be it a USB stick of the ISO or a burned CD of the ISO.

If you don't have the Windows driver anymore, see if the owner has any driver disk that may have come with the PC and check to see if you can find the wireless driver on it.

If not, go to the manufacturers' website and download it.

The driver may come as a zip file, a self-extracting compressed file, etc., so you may need to unpack it before you can find the files.

Once you have the driver you will find the .inf and .sys files.

---

