---
title: "Desktop wi-fi adapter - please help!"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by MikeSz on 2008-04-28
Sorry in advance for this, I know im probably not supposed to do it....

I have a thread here in the networking section [http://ubuntuforums.org/showthread.php?t=772602](http://ubuntuforums.org/showthread.php?t=772602)
problem is I just cant get this thing working and no one seems to have any ideas - can anyone help me set it up?

Its a Buffalo Wireless-G 125* USB2 wi-fi adapter - I know it works as I have it working in Windows, but I also have this machine dual booting Ubuntu 7.10 64 bit edition - My dad doesnt want to use windows really apart from the odd game - he wants to use ubuntu so can anyone please help me get it going?  I have no idea if Ubuntu is even seeing it - all I can say is that there are no wireless networks detected...

---

### Post by mwf on 2008-04-28
OK, you may not like this but here it goes: getting wireless to work with Linux is like gambling in Vegas. Others may give you lots of cool things to do to make it work but, in my experience, none of these things actually work for me!

I'd suggest you run down to Wal-Mart or Target or whatever and buy a cheap USB Broadcom wireless device. This is what I use, its relatively common and Linux automatically sees it with no muss or fuss. Great reception, no problems.

---

### Post by AndrewTheArt on 2008-04-28
I think you're in luck in terms of getting this working.

First of all, get this computer attached to the Internet in some fashion (probably a wired Ethernet connection). You either need to do that OR figure out how to enable the installer CD as a software source. The reason you need to do either of these things is because you need to install additional software that does not come with Ubuntu by default to get the wireless going. You also need to download the Buffalo drivers onto your computer. I'd say, the easiest option is to connect a weired connection so you can get the software and the drivers without issues.

First of all, download the Buffalo drivers [here]("http://www.buffalotech.com/support/getfile/?U2KG125S.zip"). Right click on the file, press "Extract Here" and remember the folder where you extracted everything (probably the Desktop).

Now, figure out how to install software on your machine (by connecting to the Internet and enabling an Internet repository, or by enabling the CD). [Here's]("https://help.ubuntu.com/community/Repositories/Ubuntu") a good guide for that kind of stuff. If you went the wired connection route, you need to change some options in Synaptic. Look at the guide for more info.

Once you can install software, open a terminal (Applications->Accessories-> Terminal) and type in -

```
sudo -i
apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
cd /home/your_user_name/Desktop/U2KG125S (for example, just wherever you extracted the drivers)
ndiswrapper -i NETG125S.INF
```Just to check, type in

```
ndiswrapper -l
```You should see something like "Driver installed".

Finally, execute these commands

```
modprobe ndiswrapper
echo "ndiswrapper" >> /etc/modules
```After a reboot (you HAVE to reboot), your wireless should work. You should see available wireless networks in the network manager (left click on the network icon in the system tray).

Good luck!!!

---

### Post by MikeSz on 2008-04-28
Hi AndrewtheArt - I have my laptop and a USB memory stick if thats any use?  Cant really do a wired connection at the moment, id have to go and get an Ethernet cable (which isnt a huge problem) - I do however have the buffalo drivers on my memory stick and a copy of both the 7.10 and 8.04 live CD's.  Is your solution still do-able?  I dont mind doing the messing about if you can go through it step by step...

Cheers for the help

---

### Post by MikeSz on 2008-04-28
Ok, I have Ndiswrapper-1.52.tar.gz and the buffalo drivers on my memory stick - I take it I can install ndiswrapper on to the desktop and then run the rest of what you've typed above?  How do you install a tar.gz file?

---

### Post by AndrewTheArt on 2008-04-28
Gotta run, but go here!!!

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by AndrewTheArt on 2008-04-29
Any updates?
As a small note, you're going to need to install build-essential from the CD, as you can't really compile the C compiler from source :P (Just makes no sense :lolflag:)

---

### Post by MikeSz on 2008-04-30
I get this....

tony@tony-desktop:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
tony@tony-desktop:~$ ndiswrapper -l
netg125s : invalid driver!
tony@tony-desktop:~$ modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory
tony@tony-desktop:~$ sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
ndiswrapper-common is already the newest version.
ndiswrapper-common set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tony@tony-desktop:~$ cd /home/tony/wifi/U2KG125S
tony@tony-desktop:~/wifi/U2KG125S$ ndiswrapper -i NETG125S.INF
driver netg125s is already installed
tony@tony-desktop:~/wifi/U2KG125S$ ndiswrapper -l
netg125s : invalid driver!
tony@tony-desktop:~/wifi/U2KG125S$

---

### Post by AndrewTheArt on 2008-04-30
Try

```
sudo aptitude install linux-ubuntu-modules-`uname -r`
```Then try ndiswrapper install again.

---

### Post by anewguy on 2008-05-01
You also need to get back to a clean slate in ndiswrapper before continuing.  In a terminal window do the following:

sudo ndiswrapper -l <= lower case "L"
 
 for each driver returned from above:

sudo ndiswrapper -e xxxxxx <= where xxxxxx is the driver name returned above

Repeat this until nothing is returned.  You will then be at a clean state again.  Now try installing your driver again with ndiswrapper -i.  Your safest bet is to "cd xxxxxx" where "xxxxxx" is the folder the driver files are in (should be at least .inf and .sys maybe more) BEFORE doing the ndiswrapper -i.  This eliminates any path problems.  Believe me, ndiswrapper will "install" (maybe I should say it used to not return an error) if you installed something with the wrong spelling, incorrect path, etc..  That's why I always tell everyone to get back to a clean slate first.

Also, for those interested, rather than compile ndiswrapper, if you have the livecd you can manually install it from there:

(1) Put the disk in the drive and reply "cancel" to the "a volume with software packages has been detected" screen.  Wait for the file browser to come up.

(2) Click on pool, then main, then "n", then ndiswrapper.  You'll find the .deb's for ndiswrapper common and the utils there and can just click each .deb and the package manager will start for it.  Saves needing to download source, compile it (in my experience I've never needed to actually compile ndiswrapper from source).

:)

---

### Post by MikeSz on 2008-05-06
> **AndrewTheArt said:**
> Try

```
sudo aptitude install linux-ubuntu-modules-`uname -r`
```Then try ndiswrapper install again.

Can I just ask, am I typing the above exactly as it appears or do I need to substitute 'uname...' with the applicable user name? 

so far no joy, though Il try all this again toniht when I can get the unit onto the internet via cable.

---

### Post by shifty_powers on 2008-05-06
type the command as is. uname -r is to get the version number of your linux kernel iirc...

---

### Post by MikeSz on 2008-05-08
Ok - still no joy sorry - Below is my output from terminal.  I removed all the previously installed versions and tried from scratch - you can see below what happens...

tony@tony-desktop:~$ sudo aptitude install linux-ubuntu-modules-`uname -r`
[sudo] password for tony:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
tony@tony-desktop:~$ cd /home/tony/wifi/U2KG125S
tony@tony-desktop:~/wifi/U2KG125S$ sudo ndiswrapper -l
tony@tony-desktop:~/wifi/U2KG125S$ sudo ndiswrapper -i NETG125S.INF
installing netg125s ...
forcing parameter IBSSGMode from 0 to 2
tony@tony-desktop:~/wifi/U2KG125S$ sudo ndiswrapper -l
netg125s : invalid driver!
tony@tony-desktop:~/wifi/U2KG125S$ 

Any ideas????

---

### Post by MikeSz on 2008-05-12
bump...

---

### Post by MikeSz on 2008-05-13
does anyone have any ideas?  Or am I going to have to et a new USB wi-fi stick??

---

### Post by trucker33377 on 2008-05-13
> **MikeSz said:**
> does anyone have any ideas?  Or am I going to have to et a new USB wi-fi stick??
Hi have you looked in the wireless forms there is a sticky that show what wifi's you can use also a link to wifidoc's. I'm not real good with linux but i have had some luck there. if you can't get on with what you have at least it tell's you what will work. just take your time before you buy anything. getting the right windows driver can be tricky. ndiswrapper should work.
also another thing you might try. if burning cd's is ok is a diff linux distro. I just got a new gateway laptop hardy wouldnt work with wireless but linux puppy 4.0 did. so i knew there was a way. i went back to ubuntu gutsy and it found the wireless right off.

---

### Post by MikeSz on 2008-05-16
Ok, this is quite simply driving me mad now :(:(

Ive been out and bought a Belkin wireless G+ USB adapter to see if usig a different brand would make an difference.  It hasnt.  Not even the slightest.  Ubuntu still wont recognise it.  Iv e tried going through the process of installing the windows driver with NDisWrapper but I get the same message when I type Ndiswrapper -l 'Invalid driver'

So I am at a complete loss and I cant believe that there isnt a way of making these things work!!!  How do all the laptops get on??

---

### Post by shifty_powers on 2008-05-16
did you look here to see if it is supported by ubuntu?

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

i would look here and make sure you get one that is supported within the kernel.

And i'm afraid that, yes wireless can be a bit of a nightmare still with linux and ubuntu. But, in fairness, it has imporved beyond all recognition since i started using 6.06. If it's a pain now, imagine what it used to be like ;) tbf, i find wireless a joy to use now, in fact i getter wireless peformance from ubuntu than windows ;)

also, are you sure you're using the right river file? iirc, you need to use the *.inf file, as this is the actual driver.

also look here

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by MikeSz on 2008-05-20
Thanks for those links - I think I am just going to have to bite the bullet and get another new one from the list and see if I can return one of the ones Ive bought already.

I have been using the *.inf files - there is only one or possibly two *.inf files, and certainly only one for the Buffalo stick.  I dont think my Ndiswrapper is working properly as, although it lets me install a driver using 'ndiswrapper -i whatever.inf', when I do a 'ndiswrapper -l' it shows the driver, but says its invalid!!!  Ive tried removing all the previous ones, starting again and still get the same.  So perhaps its something much more complicated.  Would upgrading the machine to 8.04 make any difference?  I tried the wi-fi stick using the 8.04 live disc and it didnt work - though I didnt bother installing it.

---

### Post by Myglaren on 2008-05-20
I don't know if this will help but the other day my internal telephone extension net went down.  Had to relocate the router to the prime socket which meant that the Ethernet is no longer connected. No problem with the laptops (wireless - autodetected everything and just connected) but this machine has always been Ethernet wired.

I have a D-Link wireless dongle, never previously used.  Stuck it in a USB port and expected a popup that it had been 'seen' by Ubuntu.  Zilch - did modprobes and the like (You will realise that I am relatively clueless about all this)

Right clicked on the network manager icon in the system tray, got a few options there, one to add a new (wireless) network.  Followed the links and was prompted to enter the name of the network device (BTHomeHub-A3DB) then the encryption key.  Had to repeat it a few times due to cluelessness and entering incorrect data but five minutes later it was up and running, is almost as quick as the Ethernet network.

There was no downloading or installing of anything to do.  The dongle itself is still invisible as far as the desktop is concerned but that is not a problem (to me anyway) the whole thing just works fine and was as simple to get going as Windows, once I discovered (more by accident than anything else) how to go about it.

---

### Post by MikeSz on 2008-05-20
Do you know, I havent even looked at anything like that :)  Il give it a try soon and let you know what happens - you may be absolutely spot on and it may just need a bit of manual faffing about!

---

### Post by shifty_powers on 2008-05-20
btw, have you looked at this bug on launchpad?

[https://bugs.launchpad.net/ubuntu/hardy/+source/linux-source-2.6.22/+bug/140511](https://bugs.launchpad.net/ubuntu/hardy/+source/linux-source-2.6.22/+bug/140511)

might give you some insightinto what is going on ;)

---

### Post by MikeSz on 2008-05-22
> **AndrewTheArt said:**
> I think you're in luck in terms of getting this working.

First of all, get this computer attached to the Internet in some fashion (probably a wired Ethernet connection). You either need to do that OR figure out how to enable the installer CD as a software source. The reason you need to do either of these things is because you need to install additional software that does not come with Ubuntu by default to get the wireless going. You also need to download the Buffalo drivers onto your computer. I'd say, the easiest option is to connect a weired connection so you can get the software and the drivers without issues.

First of all, download the Buffalo drivers [here]("http://www.buffalotech.com/support/getfile/?U2KG125S.zip"). Right click on the file, press "Extract Here" and remember the folder where you extracted everything (probably the Desktop).

Now, figure out how to install software on your machine (by connecting to the Internet and enabling an Internet repository, or by enabling the CD). [Here's]("https://help.ubuntu.com/community/Repositories/Ubuntu") a good guide for that kind of stuff. If you went the wired connection route, you need to change some options in Synaptic. Look at the guide for more info.

Once you can install software, open a terminal (Applications->Accessories-> Terminal) and type in -

```
sudo -i
apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
cd /home/your_user_name/Desktop/U2KG125S (for example, just wherever you extracted the drivers)
ndiswrapper -i NETG125S.INF
```Just to check, type in

```
ndiswrapper -l
```You should see something like "Driver installed".

Finally, execute these commands

```
modprobe ndiswrapper
echo "ndiswrapper" >> /etc/modules
```After a reboot (you HAVE to reboot), your wireless should work. You should see available wireless networks in the network manager (left click on the network icon in the system tray).

Good luck!!!

Bit of progress - managed to get one of the drivers I foind on buffalo's website that related to the wireless-G usb stick.  I also found an Ndis wrapper installation utility on in the repo's as well.  I have managed to install a driver, but the commands you suggested I type dont seem to do much...I get this:

tony@tony-desktop:~$ modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory
tony@tony-desktop:~$ echo "ndiswrapper" >> /etc/modules
bash: /etc/modules: Permission denied
tony@tony-desktop:~$ sudo echo "ndiswrapper" >> /etc/modules
bash: /etc/modules: Permission denied
tony@tony-desktop:~$

---

### Post by MikeSz on 2008-05-22
> **MikeSz said:**
> Bit of progress - managed to get one of the drivers I foind on buffalo's website that related to the wireless-G usb stick.  I also found an Ndis wrapper installation utility on in the repo's as well.  I have managed to install a driver, but the commands you suggested I type dont seem to do much...I get this:

tony@tony-desktop:~$ modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory
tony@tony-desktop:~$ echo "ndiswrapper" >> /etc/modules
bash: /etc/modules: Permission denied
tony@tony-desktop:~$ sudo echo "ndiswrapper" >> /etc/modules
bash: /etc/modules: Permission denied
tony@tony-desktop:~$

Also, that final bit of code you asked me to tpye - ive looked up the directory and the last bit, the /nd bit, doesnt exist - ive attached a screenshot for you to see...is this perhaps where its going wrong?  I suspect this is really close to working now as I have a driver that is actually installed, I just cant seem to find away of getting on a wireless network!!

---

### Post by shifty_powers on 2008-05-22
heh, afraid i am very busy at the moment, as i am writing an essay, a very important one that i need to finish by 4mp tomorrow.

however, has anyone actually suggested using ndisgtk?

this is the gui frontend for ndiswrapper, and i've used it in the past and it has made my life much easier ;)

```
sudo ap-get install ndisgtk
```

then go system>administration>windows wireless drivers....

---

