---
title: "Can't read automounted partition."
date: 2009-08-18
forum: Philippine Team
---

### Post by frustphil on 2009-08-18
Need help from the config experts.
I have a separate ext4 partition on the same disk where all my files are saved.
I edited /etc/fstab so it would automount and grant me rw of that partition. Here is my fstab:

> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=ed7ae163-362f-4458-8578-0c05f2a4305a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=70afcdb6-13aa-41b1-966d-0feb2f0b7795 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
**/dev/sda8       /home/user_name/Media ext4 rw,user,auto,exec,sync  0       0**
The line in bold font is my added config. 
The problem is that when I navigate to /home/user_name/Media I don't see any files. If I issue ls ~/Media I can see the files but they're preceded with permission denied statement. Here's how it looks:

> ls: cannot access Media/bookmarks.html: Permission denied
ls: cannot access Media/karmic-desktop-i386.iso: Permission denied
bookmarks.html
karmic-desktop-i386.isoNote that those are not the only files in that partition, I just showed how it looks. Anyone help me pls..

---

### Post by Nhatz on 2009-08-18
Try mo bigyan ng execute permission yung directory/folder mo.

```
sudo chmod -R +x <directory/folder>
```

ASTIG!!! :guitar:

---

### Post by perbiu on 2009-08-19
This is my fstab line for storing files

**/dev/sda3	/media/Store	ext4	rw,relatime,errors=remount-ro	0	2**

---

### Post by frustphil on 2009-08-19
> **Nhatz said:**
> Try mo bigyan ng execute permission yung directory/folder mo.

```
sudo chmod -R +x <directory/folder>
```ASTIG!!! :guitar:
lol un lang pala. tried sudo chown -R useranme:username ~/Media pero hindi gumana eh.. hmmm kit kaya? even tried chmod -R 777 ~/Media pero ayaw parin... :)

---

### Post by .::welemski::. on 2009-08-19
maitanong ko lang bat mo naman sa account mo pinapamount ug drive?

ganyang klase ng mounting strategy ay hindi advisible at ung and drive mismo inisue nyu ng "chmod" comman ay hindi rin advisible...

---

### Post by frustphil on 2009-08-19
> **.::welemski::. said:**
> maitanong ko lang bat mo naman sa account mo pinapamount ug drive?

ganyang klase ng mounting strategy ay hindi advisible at ung and drive mismo inisue nyu ng "chmod" comman ay hindi rin advisible...

non ba? wla kc me alam about good security practice eh. hehe tsaka karmic testing lang namn to kc i failed to mount my /home partition to another partition. nyway salamat. care to tell y it's not advisable?

---

### Post by edyeeh on 2009-08-23
Nagkaproblema na rin ako ng ganyan.

try mo ilagay yung mount point sa **/mnt/(Folder)/**. Pagkakaalam ko doon lang pwede eh at sa **/media/**. Kung gusto mo easy access pwede mong gawan na lang ng symbolic link from **/mnt/(Folder)/** --> **/home/(username)/(etc)/**.

kung gusto mo ng mga ma detalyeng explansyon sa permissions tignan mo itong [forum na ito]("http://ubuntuforums.org/showthread.php?t=283131&highlight=setup+usb+fstab%22%20ADD_DATE=%221231697409%22%20LAST_MODIFIED=%221231697429%22%20ICON_URI=%22http://icon.foxmarks.com/fq1toae7-13%22%20ICON=%22data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABmJLR0QA/wD/AP+gvaeTAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAB3RJTUUH1gUYBy8UWHdfBwAAAcJJREFUOMuVk09IVFEUxn/nNb7pkbV7r4jQQHKTbQya2rSxJJmoRbYLEqZl0MJolataFkW4k0ebmDaVCD4EEQdsEW+aTRuxdKGDCDMuhJjxNWN5WnjHzHkqntW958/lu993PjhEhHjDId5iiHerkZO9mjXjtADdwGVgY+lLcqo0a3835ekU5R6ARNNg7uxRqmsOo/UscKORb79Se1SatceBa0A2FoEqwoQ7"). Nakatulong sa aking kaalaman tungkol sa fstabbing. :D

yung chmod nagiiba ng permissions manually. hindi advisable sa case na ito kasi yung fstab may predetermined na na mga users kung sino sino ang pwedeng mag mount at kung sino ang pwede mag access sa mga mount points kaya posibleng magkakagulo kung naiba mo yung permissions ng isang folder. pero ok lang tingin ko di naman ganun ka seryoso yung epekto nun.

---

### Post by frustphil on 2009-08-23
> **edyeeh said:**
> Nagkaproblema na rin ako ng ganyan.

try mo ilagay yung mount point sa **/mnt/(Folder)/**. Pagkakaalam ko doon lang pwede eh at sa **/media/**. Kung gusto mo easy access pwede mong gawan na lang ng symbolic link from **/mnt/(Folder)/** --> **/home/(username)/(etc)/**.

kung gusto mo ng mga ma detalyeng explansyon sa permissions tignan mo itong [forum na ito]("http://ubuntuforums.org/showthread.php?t=283131&highlight=setup+usb+fstab%22%20ADD_DATE=%221231697409%22%20LAST_MODIFIED=%221231697429%22%20ICON_URI=%22http://icon.foxmarks.com/fq1toae7-13%22%20ICON=%22data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABmJLR0QA/wD/AP+gvaeTAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAB3RJTUUH1gUYBy8UWHdfBwAAAcJJREFUOMuVk09IVFEUxn/nNb7pkbV7r4jQQHKTbQya2rSxJJmoRbYLEqZl0MJolataFkW4k0ebmDaVCD4EEQdsEW+aTRuxdKGDCDMuhJjxNWN5WnjHzHkqntW958/lu993PjhEhHjDId5iiHerkZO9mjXjtADdwGVgY+lLcqo0a3835ekU5R6ARNNg7uxRqmsOo/UscKORb79Se1SatceBa0A2FoEqwoQ7"). Nakatulong sa aking kaalaman tungkol sa fstabbing. :D

yung chmod nagiiba ng permissions manually. hindi advisable sa case na ito kasi yung fstab may predetermined na na mga users kung sino sino ang pwedeng mag mount at kung sino ang pwede mag access sa mga mount points kaya posibleng magkakagulo kung naiba mo yung permissions ng isang folder. pero ok lang tingin ko di naman ganun ka seryoso yung epekto nun.

thank you!

---

