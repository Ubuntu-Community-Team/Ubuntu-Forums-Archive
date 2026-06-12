---
title: "org.chameleon.boot.plist screwup on Mountain Lion"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by firstdefence on 2014-01-27
Hi all, I was trying to sort out my App store and not being able to login, I followed a few suggestions and didn't get very far, then, for some reason I can't quiet fathom, I went into muppet mode and set PCIroot=1 in the org.chameleon.boot.plist file, rebooted and now I can't get into my OS X.

So, I thought I'd get me a live Linux DVD Zorin is the one I had to hand, Mount sda2 and either modify or delete the offending file. Well fate obviously has a different option for me so I'm here.

Okay the story so far in ubuntu...

[LIST]
[*]the partition is HFS+ but its not Journaled
[*]I have installed the HFSprogs, HFSutils and just about any other HFS that I could lay my hands on.
[*]I have used ```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
``` to get a read out of all the info that seems relevant.
[/LIST]

```
NAME   FSTYPE     SIZE MOUNTPOINT                LABEL
sda             931.5G                           
&#9500;&#9472;sda1 vfat       200M                           EFI
&#9500;&#9472;sda2 hfsplus  745.3G /media/live/Mountain Lion Mountain Lion
&#9492;&#9472;sda3 hfsplus  185.8G                           TIME MACHINE
sdc             931.5G                           
&#9500;&#9472;sdc1 hfsplus  465.4G                           Files
&#9492;&#9472;sdc2 ntfs     466.1G /media/live/Music         Music
sdd               1.8T                           
&#9492;&#9472;sdd1 ntfs       1.8T                           Elements
sde             465.8G                           
&#9500;&#9472;sde1 vfat       200M                           EFI
&#9492;&#9472;sde2 hfsplus  465.5G                           Storage
sr0    iso9660    1.6G /cdrom                    Zorin OS 7.1 Core 32
loop0  squashfs   1.5G /rofs                     



```

The sd I need is the Mountain lion (sda2) but no matter how much I try I can't mount it with read write.

Some of the options I've tried (forgive me if I have errors I'm not very up on Linux)

[CODEsudo mount -o remount,rw,force /media/live/Mountain Lion/dev/sda2][/CODE]
This gets me:  can't find /dev/live/sda2 in /etc/fstab or /etc/mtab

```
sudo mount -t hfsplus -o force,rw /dev/sda2 /media/live/Mountain Lion
```
With this I get [I]Only root can do that
[/I]
```
su mount -t hfsplus -o force,rw /dev/sda2 /media/live/Mountain Lion
```
This gets me invalid t option and then the help on options for su

I'm kind of going round in circles now so if anyone could help that would be nice.

TIA

---

### Post by sandyd on 2014-01-27
Firstly Linux doesnt take nicely to spaces in file paths - should be
```

sudo mount -t hfsplus -o force,rw /dev/sda2 "/media/live/Mountain Lion"
```

However, /dev/sda2 is already mounted for you on /media/live/Mountain Lion - browse to that folder and your files should be there

---

### Post by firstdefence on 2014-01-27
Hi thanks for the reply and the "" hint re spaces.

I can easily mount Mountain Lion but its read only.

With Mountain Lion umounted, if I use ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo mount -t hfsplus -o force,rw /dev/sda2 "/media/live/Mountain Lion"[/FONT][/COLOR]
``` I get ```
mount: mount point /media/live/Mountain Lion does not exist
```

If I mount Mountain Lion and use the code above I get ```
mount: /dev/sda2 already mounted or /media/live/Mountain Lion busy
mount: according to mtab, /dev/sda2 is already mounted on /media/live/Mountain Lion
``` It's a kind of catch 22 at the moment :confused:

Could I create /media/live/Mountain Lion and then try mounting into /media/live/Mountain Lion?

---

### Post by firstdefence on 2014-01-27
Mountain Lion is umounted.
 
I tried ```
mkdir /media/live/osx
``` It went to prompt as if it had done the task, so I then ran ```
sudo mount -t hfsplus -o force,rw /dev/sda2 /media/live/osx
``` This resulted in ```
mount: warning: /media/live/osx seems to be mounted read-only.
``` one step closer one step further away.

---

### Post by firstdefence on 2014-01-28
Also tried using the mac flag -s (Single User mode) when booting to mac, this gets you to a command prompt but the files I want to get to are still read only

---

### Post by firstdefence on 2014-01-28
[COLOR=#454545][FONT=tahoma]This is For OS X at a  command prompt not Linux, I've put this here for completeness and as part of the process to find a way to edit the org.chameleon.boot.plist. I originally thought it would be a simple task from Linux but as I have found out, it can be quite convoluted and not as straightforward as it would first appear, still its an upward pointing learning curve [/FONT][/COLOR];)[COLOR=#454545][FONT=tahoma]

Thanks to [Rene at the OSX86.net]("http://www.osx86.net/topic/16519-help-mountain-lion-1082-cant-boot-anymore/") forum for this info

For example if you want to move "your.kext" from /S/L/E to kext_backup, create a kext_backup directory on root.[/FONT][/COLOR]

[COLOR=#454545][FONT=tahoma]Boot with -s (single user) and type:[/FONT][/COLOR]
```
fsck [COLOR=#666600]-[/COLOR]fy
mount [COLOR=#666600]-[/COLOR]uw [COLOR=#666600]/[/COLOR]
mkdir [COLOR=#666600]/[/COLOR]kext_backup
cd [COLOR=#666600]/[/COLOR][COLOR=#660066]System[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#660066]Library[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#660066]Extensions[/COLOR]
mv your[COLOR=#666600].[/COLOR]kext [COLOR=#666600]/[/COLOR]kext_backup
reboot
```
[COLOR=#454545][FONT=tahoma]Boot with boot flag:[/FONT][/COLOR]
[COLOR=#454545][FONT=tahoma]UseKernelCache=No -v[/FONT][/COLOR]

[COLOR=#454545][FONT=tahoma]If you want to edit your "org.chameleon.boot.plist" boot with: [/FONT][/COLOR][COLOR=#454545][FONT=tahoma]-s[/FONT][/COLOR]

```
mount [COLOR=#666600]-[/COLOR]uw [COLOR=#666600]/[/COLOR]
cd [COLOR=#666600]/[/COLOR][COLOR=#660066]Extra[/COLOR][COLOR=#666600]/[/COLOR] 
nano org[COLOR=#666600].[/COLOR]chameleon[COLOR=#666600].[/COLOR]boot[COLOR=#666600].[/COLOR]plist
reboot
```
[COLOR=#454545][FONT=tahoma]nano = small text editor[/FONT][/COLOR]
[COLOR=#454545][FONT=tahoma]fsck = file system check
 
Right off to apply this approach and I'll be back later.[/FONT][/COLOR]

---

### Post by firstdefence on 2014-01-28
I'm back, a little greyer, a lot wiser and a lot happier.
I thought I would give the OS X boot from DVD another crack so...

I booted the OS X Install DVD and waited until I got to the choose your language option, then clicked the circled arrow
[IMG]http://1.bp.blogspot.com/-dUy2x43RqZ8/TzW5kamI7bI/AAAAAAAAAuY/UhMjS6iPQog/s1600/Lion%2Bstep%2B2.png[/IMG]

On the next page I clicked on Utilities and selected Terminal, a greenish window with a command prompt, appears.

I used: ```
Diskutil list
``` to get a read out of all the drives connected, I also noted the drive I was looking fors ID e.g. Disk1s2 this disk has a volume name "Mountain Lion".

I used ```
mount -uw /dev/Disk1s2
``` to mount the disk.

I used ```
Diskutil info
``` to get a detailed read out for the mounted Disk1s2 (Diskutil info wouldn't work until I'd mounted the disk.)

I noted the mount point /Volumes/Mountain Lion/ and used ```
cd "/Volumes/Mountain Lion"
``` to move to the disk (if you have spaces in the volume name you need to use "" 

I used ```
ls
``` to confirm I'd got the right disk, I wanted to see the folders etc

I needed to get into the Extra folder so I used ```
cd Extra
``` to move to that folder

I tried to edit the file using ```
nano org.chameleon.boot.plist
``` this failed with command not found (I'll see if there is another option instead of nano) so instead of editing the file I deleted it, its probably a better idea to back the file up to another place but I'm a risk taker and that's what got me into this trouble in the first place lol

so I used ```
rm org.chameleon.boot.plist
``` and thankfully it was removed... YAY! :-D

I rebooted and removed the DVD and waited what seemed like ages, thankfully it all came back, talk about a sigh of relief. I've now made a few changes to my habits and where I store things and how I back up.

I hope this helps others if they screw up their org.chameleon.boot.plist file.

---

