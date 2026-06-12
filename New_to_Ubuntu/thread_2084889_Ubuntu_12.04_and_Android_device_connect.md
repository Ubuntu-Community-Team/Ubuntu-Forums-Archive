---
title: "Ubuntu 12.04 and Android device connect"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by Danixu on 2012-11-16
Hi friends, first of all: i'm totally new in Ubuntu, and there are a lot of things that i don't know, and maybe this problem is one of that things.

Well, i've an Xperia S mobile with android 4.0.4 installed, and i can't connect it to Ubuntu 12.04. I've tried with a lot of manuals, including this one: 

[http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access)

and i can't do it, always get the same error:

Transport endpoint is not connected

The phone is working fine and i've tested on windows seven and works. I only get that error on Ubuntu.
I did it work one time (only connecting like a pendrive), but i don't remember if was in Ubuntu 12.10 or 12.04.

Thanks in advance :)

---

### Post by cortman on 2012-11-16
I've had that same problem and have tried many things- still no solution. I'm afraid it's broken AFAIK- good news is that Jelly Bean seems to play much nicer with Linux.

---

### Post by Danixu on 2012-11-16
Then bad news for me... Sony decides to leave the Xperia S without updates (Is the last sony mobile that i buy)... :???:

---

### Post by centaurusa on 2012-11-16
> **Danixu said:**
> Well, i've an Xperia S mobile with android 4.0.4 installed, and i can't connect it to Ubuntu 12.04.

If your Android device supports the Software Data Cable app, connecting to an Ubuntu machine via a wireless link is simple.  See:
[URL="http://linuxnorth.wordpress.com/2012/04/23/a100-to-ubuntu-file-transfer/"]
http://linuxnorth.wordpress.com/2012/04/23/a100-to-ubuntu-file-transfer/ [/URL]

and

[http://linuxnorth.wordpress.com/2012/04/24/software-data-cable-addendum/](http://linuxnorth.wordpress.com/2012/04/24/software-data-cable-addendum/)

---

### Post by Danixu on 2012-11-16
> **centaurusa said:**
> If your Android device supports the Software Data Cable app, connecting to an Ubuntu machine via a wireless link is simple.  See:
[URL="http://linuxnorth.wordpress.com/2012/04/23/a100-to-ubuntu-file-transfer/"]
http://linuxnorth.wordpress.com/2012/04/23/a100-to-ubuntu-file-transfer/ [/URL]

and

[http://linuxnorth.wordpress.com/2012/04/24/software-data-cable-addendum/](http://linuxnorth.wordpress.com/2012/04/24/software-data-cable-addendum/)


Yeah FTP is a solution, but really don't need to transfer files to phone. I can share folders with samba and then copy that folders with mobile explorer. The problem is speed, wifi speed is slower than cable (i've the PC connected to wifi too).

---

### Post by cbanakis on 2012-11-16
I had this problem with my Galaxy S3.

My problem, was because the Galaxy S3 uses EXFAT file system, and Ubuntu does not natively support EXFAT.

If your problem is the same as mine...

Open terminal.  (Ctrl+Alt+T)

And Type in the following.
```

sudo apt-add-repository ppa:relan/exfat
sudo apt-get install fuse-exfat
```

It will prompt you for your password after you enter the first line.
When you type your password.  It will not show any visual confirmation that you are typing anything.  Just trust that it received your password, and hit enter.
(Does not show *'s like most password prompts)

Assuming your problem is the same as mine, after you restart the computer, it should recognize your phone the same way it does with a flash drive.

---

### Post by Danixu on 2012-11-16
> **cbanakis said:**
> I had this problem with my Galaxy S3.

My problem, was because the Galaxy S3 uses EXFAT file system, and Ubuntu does not natively support EXFAT.

If your problem is the same as mine...

Open terminal.  (Ctrl+Alt+T)

And Type in the following.
```

sudo apt-add-repository ppa:relan/exfat
sudo apt-get install fuse-exfat
```It will prompt you for your password after you enter the first line.
When you type your password.  It will not show any visual confirmation that you are typing anything.  Just trust that it received your password, and hit enter.
(Does not show *'s like most password prompts)

Assuming your problem is the same as mine, after you restart the computer, it should recognize your phone the same way it does with a flash drive.

Doesn't work :(
Maybe part of problem is exFAT, because have a 32GB storage, but still the problem.


With a lsusb i get:
```
Bus 001 Device 005: ID 0fce:0169 Sony Ericsson Mobile Communications AB 
```and with a mtp-detect i get:
```
Device 0 (VID=0fce and PID=0169) is a SONY Xperia S.
   Found 1 device(s):
   SONY: Xperia S (0fce:0169) @ bus 1, dev 5

```and shows a lot of info about mtp device like supported formats, then the phone is detected by OS...

EDIT: before used a lot of times the "android-connect" and "android-disconnect" i saw the phone content, but i've tried to disconect and reconect again and don't work :S

---

### Post by cbanakis on 2012-11-16
MTP could also cause problems.

Phones used to use UMS mode (USB Mass Storage) to connect to computers.

But now they use MTP.

It caused some problems for me, so I installed an app on the phone called "Easy UMS", which allows me to switch the phone to UMS when its connected.

But my phone is rooted (Jailbroken), and that app does not work unless the phone has been rooted.

---

### Post by Danixu on 2012-11-16
> **cbanakis said:**
> MTP could also cause problems.

Phones used to use UMS mode (USB Mass Storage) to connect to computers.

But now they use MTP.

It caused some problems for me, so I installed an app on the phone called "Easy UMS", which allows me to switch the phone to UMS when its connected.

But my phone is rooted (Jailbroken), and that app does not work unless the phone has been rooted.

Maybe one day i root the phone. Thanks for info ;)

Edit: i made it work, i've mounting and unmounting the device a lot of times, then Ubuntu started to read pone info. Take some time to read the device, but works. It's a temporary solution.
Edit2: Works very slow... maybe one day i get an unofficial Jelly Bean or Key Lime update with better linux compatibility.

---

### Post by cbanakis on 2012-11-16
Yeah, it seems very slow with mine too, but it works.

I can't say for certain, but it seems like wifi is faster.

If you install "ES File Explorer" on your phone, you can browse your local network via wifi through all your shared network files.

And copy files onto your phone that way.

Its kinda nice to be able to copy music and such onto your phone while your in bed.

---

### Post by Danixu on 2012-11-16
> **cbanakis said:**
> Yeah, it seems very slow with mine too, but it works.

I can't say for certain, but it seems like wifi is faster.

If you install "ES File Explorer" on your phone, you can browse your local network via wifi through all your shared network files.

And copy files onto your phone that way.

Its kinda nice to be able to copy music and such onto your phone while your in bed.

I'ts the program that i use ;)

For music, i've a lot of music in "Google Music" cloud, then i open the google play music app and i select the music to download. It's a little slower than WIFI, but i only need the phone and a WIFI point to manage my music.

---

### Post by Joe 1 on 2012-11-18
> **cbanakis said:**
> I had this problem with my Galaxy S3.

My problem, was because the Galaxy S3 uses EXFAT file system, and Ubuntu does not natively support EXFAT.

If your problem is the same as mine...

Open terminal.  (Ctrl+Alt+T)

And Type in the following.
```

sudo apt-add-repository ppa:relan/exfat
sudo apt-get install fuse-exfat
```

It will prompt you for your password after you enter the first line.
When you type your password.  It will not show any visual confirmation that you are typing anything.  Just trust that it received your password, and hit enter.
(Does not show *'s like most password prompts)

Assuming your problem is the same as mine, after you restart the computer, it should recognize your phone the same way it does with a flash drive.

Hi cbanakis,
I've installed Ubuntu 12.10 and it doesn't detect my sony experia arc Android phone. I've followed your advice here but the second command doesn't go through:
E: Invalid operation insall

Thank you,
Joe

---

### Post by Danixu on 2012-11-18
> **Joe 1 said:**
> Hi cbanakis,
I've installed Ubuntu 12.10 and it doesn't detect my sony experia arc Android phone. I've followed your advice here but the second command doesn't go through:
E: Invalid operation insall

Thank you,
Joe

You have to do a "sudo apt-get update" before the second command.
I see that you have written "insall" instead "install", and maybe that's the problem too.

---

### Post by cwsnyder on 2012-11-18
@ Joe 1: Unstated in your previous posting, you need the line **sudo apt-get update** between the two lines, as in ```
sudo apt-add-repository ppa:relan/exfat
sudo apt-get update
sudo apt-get install fuse-exfat
```

---

### Post by Joe 1 on 2012-11-19
Still doesn't work. 
After the second command I've got```
Ign http://ca.archive.ubuntu.com quantal-backports/universe Translation-en_CA
Fetched 209 kB in 14s (14.8 kB/s)
W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by carl4926 on 2012-11-20
When you connect the device, does the device offer an option for MTP or PTP (or if you look in the settings on the device, can you set it to PTP)
That should let you access the DCIM folder using Nautilus

---

### Post by Danixu on 2012-11-20
> **carl4926 said:**
> When you connect the device, does the device offer an option for MTP or PTP (or if you look in the settings on the device, can you set it to PTP)
That should let you access the DCIM folder using Nautilus

I've tried to found that option but i think that my mobile don't have it

---

### Post by carl4926 on 2012-11-20
> **Danixu said:**
> I've tried to found that option but i think that my mobile don't have it

If it's using android
It would be strange for it not to have that option.

Usually when you connect the device the USB connection is detected and you can pull open the connection from the top of the screen

---

### Post by Danixu on 2012-11-20
> **carl4926 said:**
> If it's using android
It would be strange for it not to have that option.

Usually when you connect the device the USB connection is detected and you can pull open the connection from the top of the screen

Maybe Sony disabled that option, because when i connect to USB i can see the connection in notifications, but when i try to open that notification the mobile does nothing. I've tried to found in settings but don't appear where have to be.

---

### Post by carl4926 on 2012-11-20
Well Sony don't have a good rep in the Linux world, they have a habit of making things vendor locked and generally difficult

---

### Post by cwsnyder on 2012-11-20
@Joe 1: You will first have to amend your /etc/apt/sources.list, either using synaptic ( >> Settings menu >> Repositories) or by using **sudo nano /etc/apt/sources.list** to remove your CD-ROM from your repository list, so that you can update your repository availability listing to download new packages.  Then you can try again.

---

### Post by cbanakis on 2012-11-20
I can't think of anything else.

My Galaxy S3 is working in 12.04 after adding exfat support.

Sorry

---

### Post by Joe 1 on 2012-11-21
> **carl4926 said:**
> When you connect the device, does the device offer an option for MTP or PTP (or if you look in the settings on the device, can you set it to PTP)
That should let you access the DCIM folder using Nautilus

I can choose between MTP and MSC in the USB connection mode. I've tried both settings. I've downloaded Nautilus but I don't see how it can help here. 

I guess I'll have to buy an adaptor and then I can take the micro SD card out ot the phone and connect it to the P.C. directly.

BTW, my OS is Ubuntu 12.10

Lots of thanks for the reply.

---

### Post by Joe 1 on 2012-11-21
> **cwsnyder said:**
> @Joe 1: You will first have to amend your /etc/apt/sources.list, either using synaptic ( >> Settings menu >> Repositories) or by using **sudo nano /etc/apt/sources.list** to remove your CD-ROM from your repository list, so that you can update your repository availability listing to download new packages.  Then you can try again.

Thanks cwsnyder, did that. Now the commands went through nicely.

Still no luck with my phone though.

Thanks again.

---

### Post by Joe 1 on 2012-12-02
Good news. It works now. the last update from ubuntu fixed that I guess.

---

### Post by Danixu on 2012-12-03
> **Joe 1 said:**
> Good news. It works now. the last update from ubuntu fixed that I guess.

Thanks for info ;)

I'll try another day, because from now i'm using Windows 8, because some things like Phone, and h264 video acceleration, don't works on ubuntu, and its a problem with a 1080p films, in a core2duo... and i've to repair grub.

---

### Post by Joe 1 on 2012-12-04
I have problems with sound and video all the time. 

What I've found that fixed that is:
in the ubuntu software centre I go to:
edit>software sources>additional drivers
and choose the proprietary driver from nvidia.

---

### Post by Danixu on 2012-12-04
> **Joe 1 said:**
> I have problems with sound and video all the time. 

What I've found that fixed that is:
in the ubuntu software centre I go to:
edit>software sources>additional drivers
and choose the proprietary driver from nvidia.

Thanks for info, but my problen is ATI, not the Ubuntu.
Both of drivers (propietary of ATI and ubuntu driver) works fine with graphic card, but don't have h264 HW decoding support, ATI added support to Radeon HD4000 and above (UVD2), and i've an HD3650 (UVD+). Im using windows for this, some videos go slow, even in youtube...

---

### Post by BigFatTony on 2012-12-19
use this great script / ppa:
[http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html]("http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html")
worked for me, my ubuntu 12.10 and my one x on Jelly Bean 4.1.1.
it updates libmtp, adds an unity-mount-unmount-launcherscript and go-mtpfs. (had to reboot)

now it's fast and stable.

---

### Post by Danixu on 2012-12-19
> **BigFatTony said:**
> use this great script / ppa:
[http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html](http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html)
worked for me, my ubuntu 12.10 and my one x on Jelly Bean 4.1.1.
it updates libmtp, adds an unity-mount-unmount-launcherscript and go-mtpfs. (had to reboot)

now it's fast and stable.

Thanks for info friend ;)

---

### Post by LinuxNubian on 2012-12-30
I have found that Android Ice Cream Sandwich 4.x.x will not connect to Linux due to A's abandonment of Mass Transfer Protocol in ICS.   Adding ExFat sounds interesting, but what finally got my Linux box to connect to Android 4.0.1-4.0.4 (ICS) was Eclipse [https://www.eclipse.org/](https://www.eclipse.org/), a software developing application. Eclipse seems to only run in 32 bit, but after installing some dependencies, I got it working on my 64 bit Lubuntu and files are transfering via USB again!!! There must be a more direct way, but Eclipse is working well for me. This bug is a real bugger...Ubuntu and Android are both built on Linux kernals, so WTF? Anyway, hope this helps somebody. Cheers

---

### Post by seafury on 2013-04-29
Hi 

I had similar problem.

Change MTP to PTP.

I changed it by tapping the usb icon on the device opens up screen you might  see MEDIA Device(MTP) with little tick box, just tick camera(PTP) and should be able to browse the device.

I am running Ubuntu 12.04.

Hope it helps

---

### Post by rirchse on 2013-05-13
Dear All,

I have a Samsung Galaxy Grand GT-I9082 and I have a Laptop installed {ubuntu 11.04(natty) that is 'Zorin 5.1} OS'.
 I have created a hotspot connection in wifi device of my laptop for connection throwing. 
It's working nicely with my Nokia E52 and others Mobile phone, Laptops, but I can't find the wifi connection with Samsung Galaxy Grand GT-I9082, "Sony-android 4.0" and others Tablet device these are installed android OS. 

"Please help me....................... I have tried many things on the web, can't find any good information."

---

### Post by braufrau on 2013-11-11
I haven't seen anyone mention Airdroid as a solution.
[www.airdroid.com](www.airdroid.com)

Works well on Firefox, woudn't go into LAN mode on Chrome for me.
Reasonably quick. Wont copy folders but will copy multiple files.

And does lots of other groovy things as well, no MTP or UMS required.

---

### Post by alphacrucis2 on 2013-11-11
> **braufrau said:**
> I haven't seen anyone mention Airdroid as a solution.
[www.airdroid.com](www.airdroid.com)

Works well on Firefox, woudn't go into LAN mode on Chrome for me.
Reasonably quick. Wont copy folders but will copy multiple files.

And does lots of other groovy things as well, no MTP or UMS required.

Yep the Airdroid app works well. The downside is that using wifi, it isn't as fast as a USB connection if you have a lot of data to transfer.

---

