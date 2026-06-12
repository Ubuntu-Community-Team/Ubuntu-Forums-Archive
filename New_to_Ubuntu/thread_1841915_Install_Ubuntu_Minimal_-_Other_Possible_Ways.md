---
title: "Install Ubuntu Minimal - Other Possible Ways"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by avnd on 2011-09-10
Hi!

I want to install Ubuntu Minimal on my very old PC. I downloaded the Natty Minimal CD image from [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD).

It was a 19 MB image. I thought that image when burnt to a CD would have everything necessary to install a minimal Ubuntu environment. I only want to install the bare minimum and setup a user, so that I could boot into the installed OS and then setup my network later and download the packages I want.

The problem I have is that, in the install environment I could only go as far as setting up the network and without setting up the network I am not able to proceed further.

This made me wonder if the minimal image did NOT actually have all that was necessary. (Please correct me if I'm wrong. I'm very confused with this part). Does it only have so much to setup a network and THEN download the bare minimum OS from a server?

I really donot want to setup a network during the install procedure. I read about the APTonCD. That's not what I want either. I want to be able to DOWNLOAD packages after I setup the minimal system.

I would really appreciate if someone could suggest me other ways in which I could setup a bare minimal installation from which to work on.

Thanks.

P.S. I read about the command-line-only install from the Alternate CD. But I don't know 
1. if it is similar to a Minimal CD install.
2. if it would allow me to setup the network AFTER installing the operating system.

---

### Post by whatthefunk on 2011-09-10
If it is an old pc, you may simply be having problems running the install program.  What are your specs?  Id try the alternate install CD.  You will be able to do an install without configuring your network.

---

### Post by Paqman on 2011-09-10
> **avnd said:**
> 
The problem I have is that, in the install environment I could only go as far as setting up the network and without setting up the network I am not able to proceed further.


Are you trying to use wifi? If so, you may want to use a wired connection until you get the system installed. Wifi sometimes requires additional drivers that are difficult to set up from the command line. Your wired network adapter shouldn't need any configuration, so just plug straight into your router and you should be fine.
> 
This made me wonder if the minimal image did NOT actually have all that was necessary. (Please correct me if I'm wrong. I'm very confused with this part). Does it only have so much to setup a network and THEN download the bare minimum OS from a server?


Yes, it contains only enough to boot up, connect to the internet and install packages.

---

### Post by ron999 on 2011-09-10
Hi
As others have said, use your wired network adapter and the Natty 19MB mini iso.
After installation, reboot.
Then you'll see the splash and a _blinking cursor_.
Press **ALT-F1** to bring up the login screen.

Then install a login window and minimal desktop.
For example:-
```
sudo apt-get install gdm gnome-core
```

Then:-
```
sudo service gdm start
```

When it starts up you can add other packages, whatever you like.
```
sudo apt-get install synaptic
```

---

### Post by avnd on 2011-09-10
Thanks for you replies whatthefunk, Paqman and ron999.

@whatthefunk:I> f it is an old pc, you may simply be having problems running the install program I thought the minimal CD would be the most compatible with an old PC. > Id try the alternate install CD I will try the Alternate CD next, mate.

@ron999: > As others have said, use your wired network adapter and the Natty 19MB mini iso.
After installation, reboot.I'm having trouble using my wired network adapter, mate.

@Paqman: > Are you trying to use wifi? I tried using both wireless and ethernet connections. I'll explain in detail the problems I faced. The following is how I went about the whole thing.

I booted into the minimal CD and got as far as setting up the network.>  Wifi sometimes requires additional drivers that are difficult to set up from the command line. At this point the installer actually presented 2 interfaces to me; eth0 and wlan0. Since it presented wlan0 interface, I assumed there was no problem with the drivers (I could be wrong here. Please correct me if I am). I tried the install many times and the following are the different courses I took.

1. I chose wlan0. The installer then said it could not identify any access points and I was asked to enter the ESSID. I did. I temporarily removed the WPA encryption I had on the network to make the install process simpler. So I left the place for the WEP password blank. Then, there was a screen with the installer trying something with DHCP. That step failed. Next I chose the archive and there was a progress bar with 'downloading' shown and then that stopped giving me an error that said something to the tune of 'Your network configuration is faulty or the server is faulty'. I tried with different servers and got the same error. (I use the same wireless card with a Windows Xp, which is pretty slow, on the same machine and that works fine. So I ruled out issues with the hardware).


2. I chose eth0. The installer did the same thing with DHCP but it was always successful with the eth0 thing. But then came the issue with it. I was at a screen which asked me to enter the details of my HTTP proxy (if I used one) in a certain syntax (or leave it blank if I don't use one). The problem was my lack of knowledge about my ISP. I live in India and use a 'Broadband' connection where I dial in with a username and password through the modem and the ethernet line. I guess I'm allotted a certain IP address each time I 'dial in'. So I tried this twice taking 2 courses from here.
  a. I left the HTTP proxy field blank and proceeded. It didn't work.
  b. I entered the data but I'm not certain of the data asked. I was asked for a 'user', 'pass', 'port' and another thing 'host' which I was not sure was to be substituted with something. I took the 'user' and 'pass' to be the username and password assigned to me by my ISP. I left the host as such. I looked around on the web and I found pages suggesting the 'port' was '8080' (although they weren't convincing). It didn't work this time either. 
In both cases I got the same error as the first time saying that either my network configuration or my server was faulty.

I'd be happy if someone could post any more suggestions or help or relevant reference.

Thanks and cheers! :)

---

### Post by whatthefunk on 2011-09-10
What are the computers specs?  Ubuntu may not work well at all on it.  The biggest problem is the DE which is a bit of a ram hog.  Minimal install wont help you much there.  Have you considered Lubuntu?

I installed Lubuntu on the machine Im using now with an alternate install CD.  During my last install, I didnt have the internet and was able to easily select a "Configure network later" option to bypass all the network steps.

---

### Post by jtarin on 2011-09-10
When I first installed Ubuntu (10.04) I did not setup a network choosing to do it later and did not connect to the internet during install. There are more than enough programs on the CD to give you a basic install. You can always go back after install and remove any you don't want or need.

---

### Post by Denver Dave on 2011-09-11
I just purchased "The Official ubuntu Book" and am running the DVD.  From the interface that I'm running, is there a way to:

(1) Create a bootable CD (not a DVD) so I can run Ubuntu on a different PC that has a CD Rom drive but not a DVD?  Might save having to buy an additional PC since the Windows XP installation is crudded up to the point of not being useful.

(2) Create a USB stick that is bootable.   I've seen various utilities mentioned, but not clear if I can do this from the interface that I'm running or how for Ubuntu to recognize the USB drive if I attach it.

Thanks.

---

### Post by pierreyy on 2011-09-11
Hey!

 have you tried using xubuntu? its intended to run on low spec pcs... try it and let us know...

---

### Post by whatthefunk on 2011-09-11
> **Denver Dave said:**
> I just purchased "The Official ubuntu Book" and am running the DVD.  From the interface that I'm running, is there a way to:

(1) Create a bootable CD (not a DVD) so I can run Ubuntu on a different PC that has a CD Rom drive but not a DVD?  Might save having to buy an additional PC since the Windows XP installation is crudded up to the point of not being useful.

(2) Create a USB stick that is bootable.   I've seen various utilities mentioned, but not clear if I can do this from the interface that I'm running or how for Ubuntu to recognize the USB drive if I attach it.

Thanks.

Just download the .iso image and burn it on a normal CD.

---

### Post by Paqman on 2011-09-11
> **avnd said:**
> 
I live in India and use a 'Broadband' connection where I dial in with a username and password through the modem and the ethernet line. I guess I'm allotted a certain IP address each time I 'dial in'. So I tried this twice taking 2 courses from here.
  a. I left the HTTP proxy field blank and proceeded. It didn't work.
  b. I entered the data but I'm not certain of the data asked. I was asked for a 'user', 'pass', 'port' and another thing 'host' which I was not sure was to be substituted with something. I took the 'user' and 'pass' to be the username and password assigned to me by my ISP. I left the host as such. I looked around on the web and I found pages suggesting the 'port' was '8080' (although they weren't convincing). It didn't work this time either. 
In both cases I got the same error as the first time saying that either my network configuration or my server was faulty.


Hmm, it's highly unlikely that you're using an HTTP proxy unless you configured one yourself, or you're connecting through someone else's network (workplace, university, etc). Leaving it blank is the normal thing to do.

I'm not sure what's going on with your connection. Normally with broadband (ADSL) the connection is "always on". Are you sure you've got broadband (ie: can you use the phone and the internet simultaneously?) If you're actually connecting to dialup I'm not sure how you could do that on the minimal install, as I've never used dialup on Ubuntu.

---

### Post by waynefoutz on 2011-09-11
if your a new user, installing the minimal cd can be pretty overwhelming. Even if you get the network problem solved, then what? What desktop environment do you plan to install? If you go the straight Ubuntu route, you'll end up with Gnome and Unity, and pretty much the same end product that you would have had if you installed from the standard cd. 

If you are new, which I assume you are since you are posting in the "for beginners only" section, then I would go with a lighter variation of Ubuntu. Lubuntu, or Peppermint OS, would be a great choice for an ancient machine. Personally, I prefer Peppermint OS over Lubuntu, even though the default theme is pretty ugly. (It can be customized.) Either one will run on just about any system, even 10 year old PCs. If you have an older system than that, try looking at Puppy Linux, which will happily run on that 20 year old 486, though it's not as newbie friendly as an Ubuntu based distro.

---

### Post by avnd on 2011-09-11
@Paqman: The connection I have is not dial-up, mate (I can use my phone simultaneously). I guess broadband's on all the time in most parts of the world and that particular user has a constant IP all the time (?). But here we 'dial-in' each time and get a different IP assigned each time. 

@waynefoutz: The biggest limitation for my install is the 128MB RAM I have. I'm planning to install LXDE. Apparently the graphic installer for Lubuntu needs more RAM than that. The Alternate install CD was giving me issues (I don't think it's even an official version). Plus, I have an even older system which will definitely need this minimal install, so I thought I'd try it with this system first. 
I'm understanding more from the official documentations each day (I guess I'm competent enough to install a DE over a minimal install given good documentation), but I'm not sure if I've graduated out of the 'Beginner' tag.

Thank you for your replies, guys.

---

### Post by waynefoutz on 2011-09-11
> **avnd said:**
> @Paqman: The connection I have is not dial-up, mate (I can use my phone simultaneously). I guess broadband's on all the time in most parts of the world and that particular user has a constant IP all the time (?). But here we 'dial-in' each time and get a different IP assigned each time. 

@waynefoutz: The biggest limitation for my install is the 128MB RAM I have. I'm planning to install LXDE. Apparently the graphic installer for Lubuntu needs more RAM than that. The Alternate install CD was giving me issues (I don't think it's even an official version). Plus, I have an even older system which will definitely need this minimal install, so I thought I'd try it with this system first. 
I'm understanding more from the official documentations each day (I guess I'm competent enough to install a DE over a minimal install given good documentation), but I'm not sure if I've graduated out of the 'Beginner' tag.

Thank you for your replies, guys.


I  wouldn't rule out installing Bohdi Linux on a system like that. 
[http://www.bodhilinux.com/system.php]("http://www.bodhilinux.com/system.php") The Enlightenment window manager is not only fast, it's quite beautiful to look at as well. The minimum requirements are a 386 with 128 megs of ram. And, it's based off of Ubuntu 10.04.

---

