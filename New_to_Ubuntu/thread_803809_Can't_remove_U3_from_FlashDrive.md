---
title: "Can't remove U3 from FlashDrive"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by mishathegoat on 2008-05-22
Heya everyone I have a very annoying problem.

I bought a 2G Flash Drive. I dunno how but whenever I plug it in, it loads a virtual cd called "U3 System" as well as the actual drive itself. I'm pretty sure the stupid virtual cd built into my flash drive is preventing me from booting off of it..

I can't get rid of it! Any ideas?

---

### Post by rickh57 on 2008-05-22
I had one of these from SanDisk, and I ran [U3 Launchpad Removal]("http://www.u3.com/uninstall/") to get rid of it.

---

### Post by mishathegoat on 2008-05-22
I can't..

I messed with the partitioning/formatting with fdisk and mkfs and Windows XP won't recognize it anymore. The launchpad uninstaller can't locate it (It says) Also tried Active KillDisk..

Is there another way to remove it?

---

### Post by HotShotDJ on 2008-05-22
> **mishathegoat said:**
> Is there another way to remove it?Unfortunately, there is no other way.  You must have access to a Windows machine AND have administrative privileges on that machine in order to remove the U3 software.  I had quite an animated conversation with the tech-support people at SanDisk about this problem.  I eventually borrowed a colleague's laptop for the purpose.

---

### Post by mishathegoat on 2008-05-22
Heh so what should I do? I do have access to an XP Machine but my partitioning/formatting makes it not recognize it.. Is it dooooooomed?

---

### Post by HotShotDJ on 2008-05-22
> **mishathegoat said:**
> Heh so what should I do? I do have access to an XP Machine but my partitioning/formatting makes it not recognize it.. Is it dooooooomed?What I would do is put it back in its packaging, grab the receipt, and bring it back to the store where you purchased it and return it as a defective item (unable to remove unwanted software).  Tell them you'd like to exchange it for one without U3... the exact same SKU will be fine as long as THEY remove the unwanted software.  Make sure they know that you expect the same high quality service and support that they give to their Windows customers (and that Linux customers are firm, but as polite as can be!!!)

---

### Post by stchman on 2008-05-22
> **mishathegoat said:**
> Heya everyone I have a very annoying problem.

I bought a 2G Flash Drive. I dunno how but whenever I plug it in, it loads a virtual cd called "U3 System" as well as the actual drive itself. I'm pretty sure the stupid virtual cd built into my flash drive is preventing me from booting off of it..

I can't get rid of it! Any ideas?

Yes, you need a Windows machine with admin rights along with the U3 uninstall program.  Windows does have a few uses to me:

Gaming.
Flashing firmware (if .exe only)
Renaming drives.
Removal of U3 cr@p.

Can't think of anything more.

---

### Post by mishathegoat on 2008-05-22
I shoulda known better than to use any software with a "Geek Squad" logo on it. I just couldn't resist how cheap it was..

But, man, there's GOTTA be a way to get that crud off of the flash drive. I do have all the packaging but I'd rather try and figure out how to fix this myself. I've already had to go back to BestBuy yesterday to return a crappy TV Tuner (Called Pinacalle or something)

(I'll post any useful info I might find elsewhere as well)

---

### Post by mishathegoat on 2008-05-22
I did it!

**Here is my strange solution (But it's all I've got):**
I plugged the Flash drive into my laptop. Booted Active KillDisk. Pressed F10 and chose the option "One Pass Zeros (quick, Low Security)" to wipe the Flash drive. I pulled it out half-way through (Should've waited till it finished) and plugged it into my XP SP2 machine. Windows recognized it. Downloaded the U3 Uninstaller tool. The Uninstaller located it and uninstalled the U3 software yay!

---

### Post by Efros on 2008-05-22
Moral of the story don't buy Sancrap. I had one of these that would crash explorer whenever I plugged it in. Eventually managed to format it and get rid of the U3 bollox on a 98SE machine, they are useful for some things!

---

### Post by snares on 2010-07-26
For anyone that just ran a Google search and clicked on the thing that came up. To remove the U3 partition simply open Synaptic and install u3-tools. if you like terminal that's

```
sudo apt-get install u3-tool
```

the open terminal and run

```
sudo u3-tool -p 0 /u3/location
```

for me the u3 drive was at /dev/sg3 it should say at the bottom when you run 

```
u3-tool -h
```

what dev locations you are working with. worked like a charm for me. hope it will for you. BTW this is on Ubuntu Maverick Dev build but should work on Lucid too.

cheers
5n4r35

---

### Post by COKEDUDE on 2011-01-24
> **snares said:**
> For anyone that just ran a Google search and clicked on the thing that came up. To remove the U3 partition simply open Synaptic and install u3-tools. if you like terminal that's

```
sudo apt-get install u3-tool
```

the open terminal and run

```
sudo u3-tool -p 0 /u3/location
```

for me the u3 drive was at /dev/sg3 it should say at the bottom when you run 

```
u3-tool -h
```

what dev locations you are working with. worked like a charm for me. hope it will for you. BTW this is on Ubuntu Maverick Dev build but should work on Lucid too.

cheers
5n4r35


This worked perfectly for me. If you are following this guide step by step then also reformat you flash drive afterwards. This deletes the hidden partition on your flash drive and then leaves like a 5 mb unpartitioned space. So if you want to use that extra space then you need to reformat your flash drive. 

Here are the man pages for any questions. 

[http://manpages.ubuntu.com/manpages/lucid/man1/u3-tool.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/u3-tool.1.html)

---

### Post by COKEDUDE on 2011-02-10
I was wrong. It just looks like its gone. Save yourself a lot of high blood pressure and use the windows tool. 

[http://u3uninstall.s3.amazonaws.com/U3Uninstall.exe](http://u3uninstall.s3.amazonaws.com/U3Uninstall.exe)

---

### Post by COKEDUDE on 2011-02-10
If you wanna try this it might work. 

```
# ./u3_tool -u /dev/sg3
```

[http://u3-tool.sourceforge.net/](http://u3-tool.sourceforge.net/)

---

### Post by Mossfoot on 2011-06-09
Synaptic package manager says the U3 tool is installed, but I get 

mossfoot@HP-G60:~$ sudo u3-tool -p 0 /u3/sr1
sudo: u3-tool: command not found

Whazzup?

(edit) Oh. Underline, not hyphen. back to the venn diagram.

---

### Post by kherring7383 on 2011-06-09
SanDisk does make some good products, but to me, the U3 utility is useless. Generally it's the first thing to go especially when I use it on both Windows and Ubuntu.

---

### Post by Mossfoot on 2011-06-15
> **kherring7383 said:**
> SanDisk does make some good products, but to me, the U3 utility is useless. Generally it's the first thing to go especially when I use it on both Windows and Ubuntu.
 I have a question going in a new thread "**Trying to locate U3 System device name".** How do I find the device so I can destroy the U3? 
 
Right now, I'm torn between burning the thumb drive with a butane torch or simply pounding it into scrap.

---

### Post by uRock on 2011-06-15
> **Mossfoot said:**
> I have a question going in a new thread "**Trying to locate U3 System device name".** How do I find the device so I can destroy the U3? 
 
Right now, I'm torn between burning the thumb drive with a butane torch or simply pounding it into scrap.

Why not remove the software and move on? [http://kb.sandisk.com/app/answers/detail/a_id/2550/~/removing-u3-launchpad-on-a-pc](http://kb.sandisk.com/app/answers/detail/a_id/2550/~/removing-u3-launchpad-on-a-pc)

---

### Post by Mossfoot on 2011-06-15
uRock, if you had read what you linked to, you would see that it provides instructions only for removing the software using MicroSoft, and requires admin access. I do not have admin rights on any MS machine. 
 
"Remove and move on" is precissly what I want to do.

---

### Post by uRock on 2011-06-15
> **Mossfoot said:**
> uRock, if you had read what you linked to, you would see that it provides instructions only for removing the software using MicroSoft, and requires admin access. I do not have admin rights on any MS machine. 
 
"Remove and move on" is precissly what I want to do.
I did read the link.

To find the media, insert the drive, then go in your menus to **System> Administration> Disk Utility**, then click on your USB drive and you will see its address listed by "Device." In my instance you will see it is */dev/sdf*
[ATTACH]195205[/ATTACH]

---

### Post by Mossfoot on 2011-06-15
Sorry, I don't see anything related to Linux on that page and I only have admin rights to my own computer, running Ubuntu 9.10
 
Palimpsest Disk Utility shows /dev/sr1 mounted at /media/U3 System. That's a 101MB file, ISO 9660. 
 
but **u3_tool -u /dev/sr1**  and **u3_tool -u /media/"U3 System"** both  return "unknown device name" when I plug that in. I've tried both with the fake CD unmounted and I've tried **u3_tool -u /media/"U3 System"** with the fake CD mounted. 
 
So, that's where I'm sitting now. It looks like I have the right path, but the U3 Tool returns an error saying I have the wrong path. 
 
(side note. It seems that there are different versions of U3 tools, one started by "u3_tool" the other by "u3-tool". Just to set aside that possible confusion.)

---

### Post by uRock on 2011-06-15
> **Mossfoot said:**
> Sorry, I don't see anything related to Linux on that page and I only have admin rights to my own computer, running Ubuntu 9.10

My last post was aiding in using the info given in this thread. I used a Windows machine to remove the U3 junk from my USB.

Looking in Synaptic Package Manager I only see u3-tool. I am using Ubuntu 10.10 on this machine.

---

### Post by Mossfoot on 2011-06-15
I started a new thread as soon as I realized I had a different problem. The other thread is:
 
[http://ubuntuforums.org/showthread.php?t=1779105](http://ubuntuforums.org/showthread.php?t=1779105)

---

### Post by malspa on 2011-07-27
If this helps anyone, I have a Memorex TravelDrive that had the U3 stuff on it, so I tried u3-tool in Ubuntu Lucid to see if I could get it removed. Here's what happened (after some trial and error):


Inserted the flash drive. I checked System > Administration > Disk Utility. The drive was shown at /dev/sdc and the volume at /dev/sdc1.

Ran the following commands, which basically just gave me a look at things, I guess:

```
steve[~]$  sudo u3-tool -i /dev/sdc1
Total device size:   1.88 GB (2017984512 bytes)
CD size:             4.09 MB (4292608 bytes)
Data partition size: 1.88 GB (2013691904 bytes)
steve[~]$  sudo u3-tool
Not enough arguments
u3-tool 0.3 - U3 USB stick manager

Usage: u3-tool [options] <device name>

Options:
	-c                Change password
	-d                Disable device security
	-D                Dump all raw info(for debug)
	-e                Enable device security
	-h                Print this help message
	-i                Display device info
	-l <cd image>     Load CD image into device
	-p <cd size>      Repartition device
	-R                Reset device security, destroying private data
	-u                Unlock device
	-v                Use verbose output
	-V                Print version information

For the device name use:
  '/dev/sda0', '/dev/sg3'
```

The second command was obviously incorrect as it did not contain any options or a device name, but note the device names shown at the end of the output.

Then, I ran the following command:

```
steve[~]$  sudo u3-tool -p 0 /dev/sg3

WARNING: Loading a new cd image causes the whole device to be whiped. This INCLUDES
 the data partition.
I repeat: ANY EXCISTING DATA WILL BE LOST!

Are you sure you want to continue? [yn] y
steve[~]$
```

So, I opened GParted and saw that all that was left was a FAT16 partition (1.88 GB) and about 4 MB unallocated. I unmounted the FAT16 partition and then resized it to take up the rest of the drive.

Next, I took a look at things again with this command:

```
steve[~]$  sudo u3-tool -i /dev/sdc1
Total device size:   1.88 GB (2017984512 bytes)
CD size:             0.00B (0 bytes)
Data partition size: 1.88 GB (2017984512 bytes)
```

So, looks like u3-tool worked and the U3 part is gone. "Thank you!" to everyone who helped out in this thread.

---

### Post by redbikemaster on 2011-07-27
I just stuck mine  in a nearby Mac (mom and dad's) and ran Mac's Disk Utility on it, One-Pass Erase.

---

### Post by malspa on 2011-07-27
> **redbikemaster said:**
> I just stuck mine  in a nearby Mac (mom and dad's) and ran Mac's Disk Utility on it, One-Pass Erase.

Nice! A friend of mine simply took his to work and used a Windows computer there to get rid of it. 

No Mac or Windows computers here, and I wouldn't be able to use a Windows computer at work for this, so u3-tool it is. Quite simple now that I know what to do, though. Whatever works.

---

