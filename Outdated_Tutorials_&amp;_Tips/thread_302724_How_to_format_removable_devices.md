---
title: "How to format removable devices"
date: 2006-11-19
forum: Outdated Tutorials &amp; Tips
---

### Post by bodhi.zazen on 2006-11-19
[Size=4] How to format removable devices[/size]

[size=2] Introduction[/size]

[color=blue]This script is for: CujoQuarrel and tedrogers[/color]

[list=number][*]This is a bash script that will unmount, format, and re-mount a removable device.
[*]You can add a menu item/desktop icon/launcher if you like.
[*]Although this is a bash script IT RUNS AS A GUI.
[*]Dependency : The only absolute dependency is **zenity** which is installed with a default Ubuntu (gnome) installation.[/list]

Not to state the obvious, but,

[color=red]**_Caution_: If you format a device/partition you will lose all the data in that partition. You have been warned....**[/color]

[size=2]How to install this script[/size]

[list=number][*]Download the attached file (**Ubuntu_format.txt**).
[*]Save it to /usr/bin as **/usr/bin/format** (you must sudo to do this).
[*]Alternately, as suggested by [color=blue]sebastjanp[/color], you may save the script to your scripts directory.
[*]Make it executable.```
sudo chmod a+x /usr/bin/format
```[/list]

[size=2]How to use this script[/size]
[list=number][*]IMO this script is best run in a terminal:```
gksudo format
```
[*]Start the script with your device **attached and mounted** in /media
[*]You can also manually add a menu item, desktop icon, or launcher.
[indent]_command_: gksudo /usr/bin/format[/indent]
[*]At the end of the script your newly formatted device will be mounted, rw, at **/media/new_format**
[*]You should be able to umount as a user (from the desktop -> eject or in a terminal with pumount **pumount /media/new_format/**), but if you have problems,```
sudo pumount /media/new_format
```

Or, if all else fails:```
sudo umount /media/new_format
sudo rm -r /media/new_format
```[/list]



Enjoy

[img]http://www.laiwa.com/cache/3/1/531045_70x70.gif[/img] [color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by tedrogers on 2006-11-19
Great Howto bodhi.zazen. And thanks for adding my name!

Worked great for me.

---

### Post by sebastjanp on 2006-11-19
Great job bodhi.zazen. I have inputed your script into scripts folder and now when I right click on anything I get a menu which includes format option. And I have tested it and it works. 
Just for a record I have Acer Travelmate 2423 with Edgy on it. 

P.S. Ofcourse I had to make it executable.

---

### Post by Mithrilhall on 2006-12-21
Everything seemed to work for me except....it gets mounted with read-only permissions. I can't write anything to it.

---

### Post by zagu on 2006-12-22
Well, THAT was helpful.  =D>   Thanks, Bodhi.zazen, for that very useful script!  Totally worked for me.

---

### Post by Mithrilhall on 2006-12-23
It worked fine for me on an external hard drive.

The USB memory stick I was having problems with is some junk Microsoft model that has a locking mechanism that will not let me format it with anything other than Fat or NTFS. ](*,) 

BTW...great script.

---

### Post by james23ryco on 2007-11-09
Thank bodhi.zazen it work well for me

---

### Post by gytis on 2007-11-11
Thanks - that is exactly what I was looking for! Great job.

---

### Post by bharadwaj on 2007-11-11
don't we have any graphical interface for formating USB devices?

---

### Post by bodhi.zazen on 2007-11-11
> **gytis said:**
> Thanks - that is exactly what I was looking for! Great job.

This is an old thread and I had all but forgotten about it.

I am glad the script worked for you, you are most welcome.

> **bharadwaj said:**
> don't we have any graphical interface for formating USB devices?

But my script is a graphical :)

---

### Post by dryder on 2007-11-11
Please excuse my ignorance but what is the difference between
> "Save it to [COLOR="Red"]**/usr/bin"**[/COLOR] ...
and 
Alternately, as suggested by sebastjanp, you may save the script to your "[COLOR="Red"]**scripts directory**[/COLOR]".

I thought usr/bin *is* the scripts directory .. ??:confused:

Many thanks
David

---

### Post by CitroenC4 on 2007-11-11
Thanks for the great script! But I have a problem using it. If I format my card in a digital camera some cameras use FAT32. If this is the case when I try to format it, the script seems to run but does not actually format anything. Any idea why? With a card that has been formated in a camera that uses FAT it works great.

---

### Post by johnraff on 2007-11-13
> **dryder said:**
> what is the difference between
"Save it to /usr/bin" ...
and
save the script to your "scripts directory".

First, I'd like to join in the chorus of thanks for this script. It's just what *I* was looking for too... ;)

dryder, your "scripts directory" refers to a directory in your own folder rather than the system /usr/bin folder .
That way you can play around with it without having to use *sudo* all the time. 
Just make a new folder /home/*your username*/scripts (call it whatever you like) and put the format script in there.
Once it's been made executable, you can call it up with: ```
gksudo ~/scripts/format
```

bodhi.zazen, I *did* have to use sudo to pumount the media/new_format disk as it had "not been mounted by you". Since the format script is run as root that seems reasonable enough...

---

### Post by dryder on 2007-11-13
Thanks johnraff,

I had already made my own private scripts folder as you suggest but I interpreted the post as meaning another *system* folder that already existed ... my mistake.

From the accolades I have no doubt this is a script I will find very useful so will install it.

Many thanks.

David

---

### Post by johnraff on 2007-11-14
er... ah... maybe I spoke too soon. :(
When I ran the script it *seemed* to work perfectly, but when I finally found out how to check the file system of a mounted device (you can look at /etc/mtab)  it turned out the usb stick I thought I'd formatted in ext3 was still fat32.
Hmm... tried the script again and this time there was some "superblock error" (I think it was) and the stick couldn't be mounted at all!
Finally running ```
sudo mkfs.ext3 /dev/sda1
``` got the stick formatted OK 

[but  it mounted as /media/disk-1 as there was still a mysterious /media/disk hanging around, which I had to delete with sudo as it belonged to root. That done, everything now seems OK with the stick, but not with the script... ] (edit: please ignore this section- I made that /media/disk folder myself!)

Bodhi.zazen, can you enlighten us? :) 
Is it possible some of the commands the script depends on might have changed a bit since last year?

---

### Post by bodhi.zazen on 2007-11-14
> **johnraff said:**
> er... ah... maybe I spoke too soon. :(
When I ran the script it *seemed* to work perfectly, but when I finally found out how to check the file system of a mounted device (you can look at /etc/mtab)  it turned out the usb stick I thought I'd formatted in ext3 was still fat32.
Hmm... tried the script again and this time there was some "superblock error" (I think it was) and the stick couldn't be mounted at all!
Finally running ```
sudo mkfs.ext3 /dev/sda1
``` got the stick formatted OK but  it mounted as /media/disk-1 as there was still a mysterious /media/disk hanging around, which I had to delete with sudo as it belonged to root. That done, everything now seems OK with the stick, but not with the script...

Bodhi.zazen, can you enlighten us? :) 
Is it possible some of the commands the script depends on might have changed a bit since last year?

OK, thanks. My script needs to be run as root , so from the command line either gksu format (or if you prefer sudo format).

The script uses mkfs.ext3

I will look at it tonight, it may be that the mount point or device changed for you ?

---

### Post by johnraff on 2007-11-15
:embarassed-face: Hmmm sorry to drag you away from testing the Heron possibly for no reason. As my edit above shows, that mysterious "disk" folder I'd made myself while trying to mount the messed-up stick...
> **bodhi.zazen said:**
> The script uses mkfs.ext3
I will look at it tonight, it may be that the mount point or device changed for you ?
I formatted the stick OK with the same mkfs.ext3 command that the script uses, so the only difference with the time I used the script might be that that  time I tried to add a "label". (which gets put in with the "-L" option it seems) Maybe I tried to add a label which is illegal and messed things up?
Are there restrictions on what you can put in at that point in the script?
(Er... what's the "label" for anyway???)

---

### Post by bodhi.zazen on 2007-11-15
> **johnraff said:**
> :embarassed-face: Hmmm sorry to drag you away from testing the Heron possibly for no reason. As my edit above shows, that mysterious "disk" folder I'd made myself while trying to mount the messed-up stick...

I formatted the stick OK with the same mkfs.ext3 command that the script uses, so the only difference with the time I used the script might be that that  time I tried to add a "label". (which gets put in with the "-L" option it seems) Maybe I tried to add a label which is illegal and messed things up?
Are there restrictions on what you can put in at that point in the script?
(Er... what's the "label" for anyway???)

LOL

A label is a name you give to a disk, it is optional.

If you set a label you can then mount by label, so 

mount LABEL=xxx /media/xxx

where xxx = the label you gave.

So if you gave a label of USB,

mount LABEL=USB /media/USB

see this link : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by johnraff on 2007-11-15
Thanks for that link to an information-packed page!

For some reason, on my box, while
```
ls /dev/disk/by-id -lah
```
and
```
ls /dev/disk/by-uuid -lah
```
work OK,
```
ls /dev/disk/by-label -lah
```
gives an error message "ls: /dev/disk/by-label: No such file or directory"

I tried formatting the stick with your script again, both with and without setting a label, and this time it seemed to work fine. 

As to why there were problems before, the only guess I had left was that that time the stick was being changed from vfat to ext3. I tried reformatting it back to vfat, with a label, and that worked too, so did going back to ext3 again, either with or without label!

So everything's cool - I guess the first problems must have been because I tried to use a long label with spaces in it. :)

Thanks again for a really useful script.
Most usb sticks you can buy in the shops will likely be formatted for Windows, so a utility like this to easily reformat them in a file system that supports permissions (and works with rsync) would be a welcome addition to the basic Ubuntu system maybe?

---

### Post by bodhi.zazen on 2007-11-15
Thanks for the follow-through, it saves me the time from de-bugging my script.

---

### Post by kelvin spratt on 2007-11-15
There is always KMFORMAT for kde 4 works perfect for me on Gutsy E17 format anything to any format but does not partition, Or use Gparted live does not matter if the stick is accidentally  write protected still formats and partitions, I use Gparted live to partition and format 4gb sticks and then install Gutsy live in persistent mode its the only way that 100% reliable

---

### Post by Thesisoftwilight on 2008-11-05
it would be nice if it were a .deb that we could just install and it would add a shortcut to the menu.....  (sory i've been a windows user for years, im finding it hard to remember all these txt comands <cp instead of coppy>)

---

