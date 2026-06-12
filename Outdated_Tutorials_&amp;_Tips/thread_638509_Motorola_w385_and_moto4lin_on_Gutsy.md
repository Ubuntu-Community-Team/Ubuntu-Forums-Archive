---
title: "Motorola w385 and moto4lin on Gutsy"
date: 2007-12-12
forum: Outdated Tutorials &amp; Tips
---

### Post by joeerror on 2007-12-12
Hello,

So I looked all over the place and couldn't find out why when I plugged my phone w385 in I didn't get the /dev/ttyACM0, I had deduced that could be tied to why moto4lin and my phone just generally hated each other as well. It kind of drove me insane getting it to work, so in my attempt to save the sanity of at least one other person, this is what I did:

First, I installed the moto4lin package with apt-get.
```

$~sudo apt-get install moto4lin
```
Then, I tried everything I could find in a bunch of forums, wikis, and whatnot.
```
Used Google a bunch. Did a lot of trial and error.
```
Ended up doing this:

```
$~lsusb
```

Which returned:
```

Bus 003 Device 005: ID 1058:0903 Western Digital Technologies, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 020: ID [COLOR="Red"]22b8:2b44[/COLOR] Motorola PCS 
Bus 001 Device 001: ID 0000:0000 
``` 

The red numbers are apparently vendor and product id numbers:

```

~$sudo modprobe usbserial vendor=0x[COLOR="Red"]22b8[/COLOR] product=[COLOR="Red"]0x2b44[/COLOR]
```

Which ends up changing the product number to 2b41 and giving me a /dev/ttyUSB0 and /dev/ttyUSB1.
So I tell moto4lin that it's on /dev/ttyUSB0, that the AT Vendor and Product is 22b8 and 2b44, and the p2k Vendor and Product is 22b8 and 2b41. It can't find the phone model, and I've only tried to put ringtones on. I'll throw one of those edit marks on here if I come across any issues. Lemme know if it works. Or also, if I did this for no reason.

---

### Post by mindmark on 2008-01-04
thanks a lot that worked great, I just got that phone the other day. I didn't try transferring ring tones yet but pictures worked fine. There are ways to load the usbserial driver with that type of device automatically with udev or something. I think I did it with wacom tablets before, I'll post it if I figure it out

---

### Post by uuser on 2008-01-17
I'm trying to do this with a Moto W490. How did you know what the P2K numbers were?

---

### Post by jim.stanley on 2008-01-23
I've tried joeerror's steps and while it connects, that's about all it can do - it not only can't get phone model, but drive name, file count, or anything else.

Could this have something to do with the fact that it's a Verizon phone and they lock it down?  I'd love to be able to get my images - and ringtones would be great!

Thanks in advance

Jim Stanley

---

### Post by joeerror on 2008-01-26
Sorry for lagging guys. I'm kind of a skitzo when it comes to my internet behavior, anyways. In attempt to touch up...

uuser: with moto4lin settings->preferences->update list showed me the same numbers as with lsusb, in my case after I sent the initial modprobe lsusb then showed different numbers then moto4lin did, so I just punched in the new numbers that lsusb gave me for the p2k info and it worked.

jim: I would imagine so, my phone is through metropcs and thus cdma. The features I have access to even with moto4lin are very few. Just pictures and ringtones. I would hope at some point there's eventually better support, I'm not familiar with seem editing but perhaps there's some of those hardcore phone guys that may be able to help a bit more then myself.

---

### Post by louman on 2008-01-27
> I've tried joeerror's steps and while it connects, that's about all it can do - it not only can't get phone model, but drive name, file count, or anything else.

Could this have something to do with the fact that it's a Verizon phone and they lock it down? I'd love to be able to get my images - and ringtones would be great!

Thanks in advance

Jim Stanley
I was having the same problem, it was a permissions problem. Try running moto4lin with sudo. That did the trick for me :)

---

### Post by jim.stanley on 2008-01-28
Wow, that worked!  Thanks.

It also helps when you click the Update List button, too. <g>

Jim Stanley

---

### Post by jim.stanley on 2008-01-28
Wow, I'm really enjoying the access to the phone, and am especially happy that I can get to areas that Verizon doesn't allow its vendors to access.

So.... next questions:

From what I can glean from searching around, sudo modprobe loads a usbserial into the kernel.  I kind of assume that the usbserial with the vendor ID's enable something, but am not sure what it is, and also why do the ID's change when you execute the modprobe?

Also, it looks like it's possible to create a rule in /etc/udev/rules.d to automatically execute the modprobe when the phone is plugged in?  There's a file in rules.d called 90-modprobe.rules that you could possibly add on to.   Has anyone tried that?  I can give it a go when I have some time (a rare commodity), 

Thanks to all again.

Jim Stanley

P.S.  Have noted the images from the camera can get really pixellated - they wouldn't have some sort of algorithm that smooths things out?

P.P.S.  Where's the contact list?  Haven't searched for it thoroughly, but.....

---

### Post by adam_r on 2008-01-29
i use KRZR K3 andi did everything right, but when it tries to connect to /dev/ttyACM0 it connects and unpluggs the phone! what do i do?

---

### Post by joeerror on 2008-01-29
With the info from the beginning of individual rule files, and this ([http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)) guide to udev rules this is what I've done.

In the 20-names.rules file what looked like:

```

# Other USB devices, commonly grouped under /dev/usb
KERNEL=="auer[0-9]*",                   NAME="usb/%k"
KERNEL=="cpad[0-9]*",                   NAME="usb/%k"
KERNEL=="dabusb[0-9]*",                 NAME="usb/%k"
KERNEL=="hiddev[0-9]*",                 NAME="usb/%k"
KERNEL=="legousbtower[0-9]*",           NAME="usb/%k"
SUBSYSTEMS=="usb", KERNEL=="lp[0-9]*",  NAME="usb/%k"

```

Now looks like:

```

# Other USB devices, commonly grouped under /dev/usb
KERNEL=="auer[0-9]*",                   NAME="usb/%k"
KERNEL=="cpad[0-9]*",                   NAME="usb/%k"
KERNEL=="dabusb[0-9]*",                 NAME="usb/%k"
KERNEL=="hiddev[0-9]*",                 NAME="usb/%k"
KERNEL=="legousbtower[0-9]*",           NAME="usb/%k"
# For my motorola w385
KERNEL=="ttyUSB[0-9]*",                 NAME="usb/%k"
# Done with the w385 for now.
SUBSYSTEMS=="usb", KERNEL=="lp[0-9]*",  NAME="usb/%k"

```


This was to help my brain organize things a bit, and to play with udev rules. I now have /dev/usb/ttyUSB0 and /dev/usb/ttyUSB1

Then I did this: 

```

udevinfo -a -p $(udevinfo -q path -n /dev/usb/ttyUSB0)

```


Which gave me a lot of info, I just ended up using this info:

```

ATTRS{product}=="Motorola W385"

```

I then added to close to the end of the 90-modprobe.rules:

```

# w385 stuff..
ATTRS{product}!="Motorola W385", GOTO="w385_end"
RUN+="/sbin/modprobe usbserial vendor=0x22b8 product=0x2b44"
LABEL="w385_end"

```

Which seems to work... Now for the permissions.

This I appended to 40-permissions.rules:

```

#w385 stuff...
KERNEL=="ttyUSB[0-9]*",                 GROUP="usb"
KERNEL=="ttyUSB[0-9]*",                 MODE="0666"

```

Ok, so now I think I have udev calling the modprobe for the device and creating /dev/usb/ttyUSB0 with permissions for users in the group usb to access it. I think. So then I:

```

sudo invoke-rc.d udev restart

```

Success! udev is doing what I want it to.

Then I run moto4lin, reconfigure it, and bam! It doesn't work. all the udev stuff looks to be correct... but I seem to have broken my **** somehow. Anyways, baby steps...

Oh, and also, I did add a group called usb, and put myself in it.

---

### Post by jim.stanley on 2008-02-05
Hmmmm..... now I can copy MIDI files and they play, but they won't set as ringtones.  Is there some sort of flag or file format trick that Verizon uses to distinguish files?  I noticed the supplied files seem really small - do they compress them in some way?

Jim Stanley

---

### Post by joeerror on 2008-02-05
According to the folks at howardforums there's a couple of files you have to delete from you phone it's like tones.db and something else.db in order for them to work completely I forget what the files are right now, but I can check they're definitely listed over at howardforums.com. Any luck on udev stuff?

---

### Post by jasex on 2008-03-07
Has anyone got this to work with a W490?


Please post the steps you followed

---

### Post by JJNova on 2008-05-01
I stumbles across this from a web search, so I want to add some information regarding my experience on Hardy Heron , Ubuntu 8.04 LTS

In order to get any of the preferences to take, I had to use 
```

$~gksudo moto4lin

```

Using this method, the terminal wont output errors. Using just sudo, moto4lin wouldn't recognize model, name, drives, or anything else. Using gksudo , only the model isn't recognized.Everything else worked smoothly (aside from kjava)

Thank you very much. You helped me figure it all out.

---

### Post by mohtasham1983 on 2008-06-06
> **jim.stanley said:**
> Wow, that worked!  Thanks.

It also helps when you click the Update List button, too. <g>

Jim Stanley

Didn't work for me. I guess they have a new way of locking their phones.

---

### Post by neuro4848 on 2008-06-20
Not sure how far you got with your situation but I got it to work like a champ...

From what I understand with moto4lin is that you have to configure it as a regular user THEN gksudo moto4lin to actually USE the product.

Given that, I just created an udev rules (10-local.rules) with the following content:

```
# w385 stuff..
SUBSYSTEMS=="usb",ATTRS{product}=="Motorola W385",GROUP="usb",MODE="0660"
RUN+="/sbin/modprobe usbserial vendor=0x22b8 product=0x2b44"
```

Then, I fire up "gksudo moto4lin" and it works like a champ!

Thanks for your help!

---

### Post by catoodubhagain on 2009-01-07
I'm new to Ubuntu, I use Intrepid Ibex, I have a Boost Mobile w385 that has no sim card so i guess it is CDMA.  How would i set up everything in moto4lin?.

all i know is this Bus 001 Device 003: ID 22b8:2b44 Motorola PCS 


Please tell it to me stupid style because I don't know what a lot of this stuff is.

Thanks, Cato

---

### Post by kalos on 2010-02-27
> **neuro4848 said:**
> From what I understand with moto4lin is that you have to configure it as a regular user THEN gksudo moto4lin to actually USE the product.


That explains why I couldn't get it to work. Instead, I just modified my ~/.qt/moto4linrc file with the settings that joeerror describes. (I guess I ran moto4lin once as a regular user and it created that file?) That worked well enough for me.


Oh, and for ringtones, the files you need to delete are "MyToneDB.db" and "TmpTneDB.db" in /a. Then Reboot ([source]("http://moto4lin.sourceforge.net/wiki/W385")). I had to put the files in /a/motorola/shared/audio/Uploaded/ for it to work. (This folder was created when I previously uploaded files with my Mac.)


**Edit**: I just tried this again on a new install and it took me a while to figure it out again. Here's the step-by-step:

**Modprobe**

[LIST=1]
[*]I don't know if these steps are required. If so, do them with your phone plugged in.
[*]Get your phone ids: ```
$ lsusb | grep Motorola
```
[*]This  gives you some bus information that ends with AAAA:BBBB Motorola PCS.  Remember AAAA and BBBB.
[*](You may have to run ```
$ sudo  modprobe usbserial vendor=0xAAAA product=0xBBBB
```)
[/LIST]


**Initial Setup**

[LIST=1]
[*]Plug in your phone!
[*]Get moto4lin
[*]Run moto4lin as a normal user. Close it without doing anything.
[*]You now have a config file in ~/.qt/moto4linrc
[*]Run ```
$ sudo moto4lin
```
[*]Click Preferences
[*]Click Update List
[*]Select your phone from the list
[*]Click Set as AT Device
[*]Click Set as P2k Device
[*]Click OK
[*]Click Connect/Disconnect
[*]moto4lin will start connecting and probably say that it cannot get the phone model. That's okay.
[/LIST]

**Ringtones**

[LIST=1]
[*]Now that we're connected, you can upload files.
[*]Click Update list to get the File Manager to get the file list from the phone
[*]Navigate to /a/motorola/shared/audio
[*]If this folder doesn't exist, you're using a different phone than I am. Check [here]("http://moto4lin.sourceforge.net/wiki/") for info on your phone.
[*]In Upload path, enter /a/motorola/shared/audio/Uploaded
[*]Click Create
[*]Navigate to /a/motorola/shared/audio/Uploaded
[*]Click Upload
[*]Select the files you want and OK
[*]Now you have files on there, but they need to get added to the database
[*]Navigate to /a
[*]Select "MyToneDB.db" and "TmpTneDB.db"
[*]Click Delete
[*]You may need to Reboot your phone
[*]Now you should have new ringtones/alarm sounds in your list! (At the bottom)
[/LIST]

---

### Post by kalos on 2010-11-23
Update to this: I'm now on Maverick (10.10) and the ACMdevice setting is defaulting to /dev/ttyACM0, which doesn't exist. (verify with [FONT="Courier New"]ls /dev[/FONT] and see that there are no acm devices)

I did this to find there is a ttyUSB0:
```

# disconnect phone
ls /dev > /tmp/devnothing.txt
# connect phone
ls /dev > /tmp/devwithphone.txt
diff /tmp/dev*.txt
```

My output showed three new devices: serial, ttyUSB0, and ttyUSB1. 

I modified my config file ~/.qt/moto4linrc so the first section looks like this:

```
[device]
cfgACMdevice=/dev/ttyUSB0
cfgATproduct=2b44
cfgATvendor=22b8
cfgAutoConnect=0
cfgDetachDriver=0
cfgP2Kproduct=2b41
cfgP2Kvendor=22b8

```

---

