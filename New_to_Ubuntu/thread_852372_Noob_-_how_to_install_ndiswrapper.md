---
title: "Noob - how to install ndiswrapper?"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by itsjareds on 2008-07-07
Sorry if this has been asked. I just switched from windows to Linux and I'm really confused..

I tried following the instructions for installation in ndiswrapper, and it says to set the directory to the ndiswrapper directory.

How do I do that? I tried using ```
cd /home/jared/ndiswrapper-1.53
``` but I got an error that said ```
Error: file:///home/jared%20cd%20/home/jared/ndiswrapper-1.53 not found.
```

Or something along those lines.

Im having a lot of trouble and it's annoying to have to keep logging out of ubuntu and starting up windows to look at help files.

Help is much appreciated :)

---

### Post by bodhi.zazen on 2008-07-07
ndiswraper is in the repositories

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

Unless there is a reason you need to compile.

---

### Post by itsjareds on 2008-07-07
Ok, I'll try that.

Thanks

---

### Post by estyles on 2008-07-07
When I was trying to set up my wife's wireless card, I came across about a half dozen different tutorials.  For some reason all except one start off with having you compile ndiswrapper (well, the reason may be that this solution isn't distro-specific), and I believe that it won't compile correctly under vanilla Ubuntu, due to dependencies - I definitely wasn't and probably still am not equipped to figure out all the dependencies and get it to make.  As a newb, it took me a long time to figure out that things generally *aren't* that difficult in Ubuntu, and found ndiswrapper in the repositories, and it only took me about a half hour to figure out the rest of the procedure and got it working.

---

### Post by itsjareds on 2008-07-07
I tried what you said, entered it into the terminal. Is something supposed to come up after that?

In the help file it says to go to System > Administration > Windows something or other

It's not there :(


By the way, i don't have internet access yet on Ubuntu.

---

### Post by walkerk on 2008-07-07
```
sudo apt-get install ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9 ndisgtk
```

Now you need to download your NICs Windows drivers (from your laptops support site)

Once done, run ```
ndisgtk
``` and install the driver. (it's and .inf file)

---

### Post by Folith on 2008-07-07
Hello everyone, I'm having problems installing ndiswrapper as well.  However, I have little to no experience with Linux.  :(

Basically, my friend and I installed Feisty Fawn on his laptop.  He has a Dynex Wireless G Network Adapter (USB dongle.)  I know this is one of the worst adapters we could possibly have, and I read that I pretty much need ndiswrapper in order for it to work.  However, we have no idea what we're doing when it comes to installing something.  We have "ndiswraooer-1.52.tar.gz" sitting on the desktop and we really don't know what to do from here.  Any help would be greatly appreciated.  :)

---

### Post by itsjareds on 2008-07-07
I did the first thing you said. Already have the driver in a folder.

When I did the last thing, run```
disgtk
``` it gave me an error saying the same thing in the first post.

---

### Post by chalewa on 2008-07-07
> **itsjareds said:**
> I did the first thing you said. Already have the driver in a folder.

When I did the last thing, run```
disgtk
``` it gave me an error saying the same thing in the first post.

```
ndisgtk
```

---

### Post by itsjareds on 2008-07-07
> **chalewa said:**
> ```
ndisgtk
```

sorry thats what I meant, I did that because i wrote it all down and copied it.

---

### Post by chalewa on 2008-07-07
which error did you get when you ran it?

---

### Post by itsjareds on 2008-07-07
> **Folith said:**
> We have "ndiswraooer-1.52.tar.gz" sitting on the desktop and we really don't know what to do from here.

Is it on your windows desktop or linux?

I just extracted on windows, then put those files on a CD.. much easier for an idiot like me.

---

### Post by itsjareds on 2008-07-07
> **chalewa said:**
> which error did you get when you ran it?

```
Could not locate file "file:///home/jared/ndiswrapper".
File could not be found.
```

Like i said earlier, i don't know how to change the directory i'm in.

---

### Post by Folith on 2008-07-07
Oh, wow, "ndiswraooer."  -_-  Haha.

It's on the Linux desktop already.  What can I do with it once I burn it?  Any recommended tutorials?

---

### Post by chalewa on 2008-07-07
> **itsjareds said:**
> ```
Could not locate file "file:///home/jared/ndiswrapper".
File could not be found.
```

so you type ndisgtk into the terminal and that is what it shoots out at you?

---

### Post by itsjareds on 2008-07-07
> **chalewa said:**
> so you type ndisgtk into the terminal and that is what it shoots out at you?

Yes

---

### Post by chalewa on 2008-07-07
> **itsjareds said:**
> Yes

that's really bizarre...

did you run this command 

```
sudo apt-get install ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9 ndisgtk
```

---

### Post by itsjareds on 2008-07-07
> **Folith said:**
> Oh, wow, "ndiswraooer."  -_-  Haha.

It's on the Linux desktop already.  What can I do with it once I burn it?  Any recommended tutorials?

Found this on the ndiswrapper site.
Enter this in terminal:
```
tar -zxvf ndiswrapper-1.53.tar.gz
```

---

### Post by itsjareds on 2008-07-07
> **chalewa said:**
> did you run this command 

```
sudo apt-get install ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9 ndisgtk
```

Yes

Nothing came up after I clicked enter. Was something supposed to happen?

---

### Post by chalewa on 2008-07-07
> **itsjareds said:**
> Found this on the ndiswrapper site.
Enter this in terminal:
```
tar -zxvf ndiswrapper-1.53.tar.gz
```

ok here is my advice to you...

get rid of this ndiswrapper-1.53 folder that is in your home folder. my reason for it is this.

1) you are trying to compile an older verision of ndiswrapper
2) you are trying to compile software when there is a version in the repositories built for use in ubuntu.

---

### Post by chalewa on 2008-07-07
> **itsjareds said:**
> Yes

Nothing came up after I clicked enter. Was something supposed to happen?

yea, it should install ndiswrapper for you. 


are you copy/pasting that into a brand new terminal?


edit: well at the very very very least, it should ask you for your root password.

---

### Post by itsjareds on 2008-07-07
Didn't know it was already installed when I downloaded it. So if I delete this folder, will running ndisgtk work?

> are you copy/pasting that into a brand new terminal?

Yes. I press alt+F2 when ubuntu first starts up, then write what you gave me.

---

### Post by appi2012 on 2008-07-07
Frolith: 
in ubuntu, generally, when you install something, you use Applications -> Add-Remove. However, since you do not have a working internet connection, and i'm guessing since you have fiesty fawn, you don't have a hardy cd, you won't be able to use that (it needs to have access to a database containing ndiswrapper, either online or a cd. gutsy gibbon had ndiswrapper on the cd, but I don't think feisty did)

to install from source, which works for all programs made for linux (not just the ones that are in a repository), you double click on the archive (the tar.gz file) which opens the archive manager. in the archive manager click extract, and save it to your desktop. Then open a terminal (Applications -> Accessories -> Terminal) and type:```
cd desktop/[replace this with the name of the ndiswrapper folder on your desktop]
```
this command changes where the terminal is working to your the newly created ndiswrapper folder.
Then type:
```
./configure
make
sudo make install
```

if that works, type:
```
ndiswrapper -l
``` (to list all your drivers that have been installed. 
(There shouldn't be anything there)
then, copy all the .sys and .inf files from the windows driver cd, into another folder in your home folder. 
then type:
```
cd ~/folder that has your driver
```
```
sudo ndiswrapper -i [your inf file]
```
```
sudo ndiswrapper -l
```
now it should say:
driver installed, device present
```
sudo ndiswrapper -m
```
```
sudo modprobe ndiswrapper
```
that should start the driver, and in a few minutes, you'll have a working internet connection.

---

### Post by Folith on 2008-07-07
itsjareds, it returned this:  

"tar: ndiswrapper-1.52.tar.gz: Cannot open: No such file or directory

tar: Error is not recoverable: exiting now

tar: Child returned status 2

tar: Error exit delayed from previous errors"

---

### Post by chalewa on 2008-07-07
> **itsjareds said:**
> Didn't know it was already installed when I downloaded it. So if I delete this folder, will running ndisgtk work?

yea it should definitely work provided that you have run this command and gotten everything to install

```
sudo apt-get install ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9 ndisgtk
```


just make sure that you type that into a brand new terminal.




edit: wait, you do have a working internet connection on the computer you are trying to install ndiswrapper on right?

---

### Post by itsjareds on 2008-07-07
> **Folith said:**
> itsjareds, it returned this:  

"tar: ndiswrapper-1.52.tar.gz: Cannot open: No such file or directory

Replace ndiswrapper-1.52.tar.gz with your version of ndiswrapper.

---

### Post by itsjareds on 2008-07-07
> **chalewa said:**
> edit: wait, you do have a working internet connection on the computer you are trying to install ndiswrapper on right?

No. That's the whole reason for me trying to install ndiswrapper :\

This computer does have an internet connection, but I have to log off Ubuntu and load up WinXP to read this forum.

---

### Post by chalewa on 2008-07-07
> **itsjareds said:**
> No. That's the whole reason for me trying to install ndiswrapper :\

This computer does have an internet connection, but I have to log off Ubuntu and load up WinXP to read this forum.

haha ohhh now it all makes sense to me. 

i am going to link you to the necessary packages that you need. from there, if you can put them on a cd or something from winxp, and then put them on your desktop within ubuntu, we will be able to get this problem all fixed.

[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb)

[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb)

[http://mirrors.kernel.org/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.3-1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.3-1_i386.deb)

---

### Post by Folith on 2008-07-07
appi2012, it keeps saying there is no such file or directory?  I'm typing the name of it exactly

itsjareds, 1.52 is the version I have.  I'm typing the name exactly :(

Thanks for all the help so far though guys, because I'm sure I'm just missing something really stupid and simple >_>

---

### Post by cariboo on 2008-07-07
Is there any way you can set up a wired connection between your laptop and your wireless router?

Jim

---

### Post by Folith on 2008-07-07
Yeah, he can still get online using a direct wired connection to a router.  It's just that his wi-fi is currently disabled until we can fix this, so he has to be at a router to do anything.

---

### Post by bodhi.zazen on 2008-07-07
We are making this more complicated then it already is :twisted:

First, too many people are giving confusing directions.

Second, ndiswrapper is in the repos, there is no need to compile it.

Third, you need to identify your wireless card and find the appropriate windows driver (ie .INF file). In general use the Windows XP driver and not the Vista driver.

===================

As to how to ndiswrapper, see this page :

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

If you have no internet connection, download and install the .deb

For specific directions, google search your wireless card to find the exact driver you need.

---

### Post by appi2012 on 2008-07-07
connect to the router, and then:
```
sudo apt-get install ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9 ndisgtk
```
just do that and then follow the rest of my instructions starting from:
```
ndiswrapper -l
```

that should work.

---

### Post by itsjareds on 2008-07-07
OK.

I have gotten the ndiswrapper to finally work. \\:D/

I entered in all the information for my internet, including my WPA password. It still wont connect; is there anything I have left to do?

---

### Post by itsjareds on 2008-07-07
anyone? :confused:

i'm almost done :(

---

### Post by bodhi.zazen on 2008-07-07
> **itsjareds said:**
> OK.

I have gotten the ndiswrapper to finally work. \\:D/

I entered in all the information for my internet, including my WPA password. It still wont connect; is there anything I have left to do?

Start by disabling wireless security for a minute, easier for testing. Once you get a connection, reactivate your security.

Make sure the router is not dis allowing you based on MAC.

Use the gui (network manager). You may need to reboot.

If you prefer, open a terminal and :

```
sudo modprobe ndiswrapper
sudo dhclient wlan0
```

If you want to configure your wireless card, from the command line, use iwconfig (see man iwconfig).

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by Frak on 2008-07-07
OK, since nobody seems to understand this (I'm too lazy to check)

NDISWRAPPER FILES ARE IN THE **MAIN **SECTION OF THE REPOSITORIES!

That means, that all the appropriate files **are on the installation disc**. Just insert the disc, add it to your sources through the administration menu, then open synaptic and install it.

---

### Post by itsjareds on 2008-07-07
> **bodhi.zazen said:**
> Make sure the router is not dis allowing you based on MAC.

I have both Windows XP and Ubuntu on the same computer with the same wireless card. I'm not an expert, so would the MAC address still be ok? My router does allow the card for XP.

---

### Post by bodhi.zazen on 2008-07-07
> **itsjareds said:**
> I have both Windows XP and Ubuntu on the same computer with the same wireless card. I'm not an expert, so would the MAC address still be ok? My router does allow the card for XP.

should be fine then.

Again, if dhclient does not work, take the router out of the equation for a minute (by disabling security).

Once you connect, re-enable security, see the links I gave you.

Like all of wireless, security is hit and miss.

---

### Post by anewguy on 2008-07-07
Maybe someone a little more expert than me can give you a good tutorial for this:  if you are running 7.0x I suspect that wpa-supplicant may not be running - it may not even be installed.

To verify that wpa could be your problem, direct connect to your router and enter its' setup.  Temporarily disable wep, wpa, etc., and just run as an open router.  Try connecting to it wirelessly with no security and see if it connects.  If so, I would suspect WPA.  I know my old DSL modem would never work right with WPA of any type running, but my new cable modem works just fine with WPA.

Remember after this test to reset the security on the wireless side of your router!  :)

Also, I'm seeing more and more of these "can't use my wireless so how do I install ndiswrapper" type of questions.  Has anyone written a "generic" tutorial for getting wireless working if you don't have an internet connection?

---

### Post by Folith on 2008-07-07
Alright, I think I got it installed..  But I cannot find .inf and .sys files for this specific device anywhere.  The website just offers a .exe for windows, instead of the drivers themselves.  If anyone could tell us which drivers would work for the Dynex Wireless G USB Adapter, it'd be appreciated.

---

### Post by itsjareds on 2008-07-07
I don't have access to my router because it's on my dad's comp, and he keeps it password protected.

---

### Post by anewguy on 2008-07-11
> **Folith said:**
> Alright, I think I got it installed..  But I cannot find .inf and .sys files for this specific device anywhere.  The website just offers a .exe for windows, instead of the drivers themselves.  If anyone could tell us which drivers would work for the Dynex Wireless G USB Adapter, it'd be appreciated.

Run the .exe via wine, then using the file browser navigate to ~/.wine/drive_c and search for the folder the .exe unpacked into.  you'll find your .inf and .sys files in that folder - just copy them to where ever you want for use with ndiswrapper (you could even just use them right from that folder).

---

### Post by youthforlinux on 2008-07-11
just run ```
unzip (name of executable).exe
```

Also if you don't have any internet connection I know that from Edgy on they have ndiswrapper on the install cds and that ndisgtk is not on the alternate cd...but if ubuntu does not detect an internet connection on install it should enable the cd repo, which will allow you to easily install ndiswrapper.

---

### Post by youthforlinux on 2008-07-11
> **itsjareds said:**
> I don't have access to my router because it's on my dad's comp, and he keeps it password protected.


The router or the computer, because if it is only the computer and that router is on the same network, then you can acess it when you are in windows....

---

### Post by Folith on 2008-07-14
Alright, I have an idea that I didn't even think of before.

My biggest problem right now is that I'm not familiar enough with Linux to navigate around and find files, or use Wine correctly.

Idea:  One of my computers runs Windows XP.  Is there any way I can get the .inf and .sys files out of that .exe on the windows xp computer?  I can then just flash-drive them over to the laptop and install them with ndiswrapper.

Here's the page with the .exe, if that helps.

[http://www.dynexsupport.com/product/?pid=DX-BUSB](http://www.dynexsupport.com/product/?pid=DX-BUSB)

---

### Post by itsjareds on 2008-07-16
It isn't in another folder within the driver's installation folder? 

For my netgear adapter, I found my driver in C:\Program Files\NETGEAR\wpn111\Driver


That included everything i needed :)

---

### Post by Frak on 2008-07-17
> **Folith said:**
> Alright, I have an idea that I didn't even think of before.

My biggest problem right now is that I'm not familiar enough with Linux to navigate around and find files, or use Wine correctly.

Idea:  One of my computers runs Windows XP.  Is there any way I can get the .inf and .sys files out of that .exe on the windows xp computer?  I can then just flash-drive them over to the laptop and install them with ndiswrapper.

Here's the page with the .exe, if that helps.

[http://www.dynexsupport.com/product/?pid=DX-BUSB](http://www.dynexsupport.com/product/?pid=DX-BUSB)
Use Peazip(my favorite)/7zip/WinRAR/WinZIP to decompress the archive. That's all you need to do.

---

