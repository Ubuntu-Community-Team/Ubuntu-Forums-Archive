---
title: "constant flash drive problem...read only"
date: 2015-07-01
forum: New to Ubuntu
---

### Post by HippieDave on 2015-07-01
Every time I load files onto a new flash drive it appears to become reset as a "read only" drive.  None of these drives have every been on an OS other than Ubuntu.  I am currently using 14.04 and created a flash drive to boot up and install 14.04 on my laptop.  This was successfully done.  When I went back to load some data files onto the drive for transferring to the laptop, I get the error message "destination is read only"./  I get the same message when trying to use four other drives, two of which hold nothing but data files.  What gives?

I have searched and found that this or similar problems are widespread, but I cannot find any solution that works.

---

### Post by Bucky Ball on 2015-07-02
Did you try wiping the drive first and reformatting it?

---

### Post by HippieDave on 2015-07-02
yes --on two of the four drives I deleted files and then used Disks to attempt to format.  I don't think it did it, probably for the same reason. The drives appear locked.  In any event, wiping out files...especially a boot drive that took a while to create...is not a long term answer to what seems to be a common Ubuntu problem.  There are many, many posts about the problem, but no posted solutions that appear to work.  Usually people assume something is wrong with the drive, or that moving it between Windows and Ubuntu creates a problem...I've got four new drives, never been tainted with anything other than Ubuntu, and they are all locked down as 'read only'.

---

### Post by yetimon_64 on 2015-07-02
I think you'll find the root of any removable drive is owned by "root" and when created with standard permissions of 755 (system umask of 0022 causes that) that leaves it read only for the user. How I work around this is to always add myself (ie. my user name) to the group called "root" after a new installation. Then set the folder for any removable drive in /media/$USER/<drive-name> to permissions of 775 this allows the group 'root" (you only, if you are the only other user of the system) to write to the first tier of that drive.

The commands: (see second option below before doing this -- it may be quicker/easier and safer by altering the basic mount options in the disk utility)

[B]Option 1.
[/B]To add yourself to the group "root":
```
sudo usermod -a -G root <user>
``` replacing <user> with your actual user name. This is done only once, a log out and log back in is necessary to set it in use though for the first time. After which you remain as part of the group "root" permanently whenevery you log in.

Then for any removable drive you need to write to, change its "/media/$USER/<drive-label>" permissions to "0775"

```
sudo chmod 0775 /media/$USER/<drive-label>
``` Change <drive-label> to match the mount folder name in /media/$USER, the $USER is ok to leave, it will automatically pick up your username (it is a system variable).
This can be done with the folder mounted, but if you have the folder open in nautilus refresh the window to get write access in the folder, nautilus will continue to use the old permissions till the window is either shut and reopened or the view is refreshed.
For any drive that is added this also is only needed to be done ONCE and the new permissions are permanent for that folder.
This seems to be the minimum permissions change to allow a user to write to the root of a removable drive.
[B]
Option 2.[/B]
It may be also possible to alter mount options for the drive in the "disks utility" in Ubuntu if you don't want to mess with permissions and groups. The "user" option added to the mount options may possibly make it writable to the user mounting it, I got myself into the habit of joining the group "root" and changing base permissions for access. I have heard of this method but have not tested it out for myself.

Hope either of these ideas work for you, cheers, yeti.

---

### Post by mastablasta on 2015-07-03
I am not sure which utility does this in Linux, but in windows there are some good options to run a test on the drive. had a same issue, formatting didn't help, the partition manager said the drive state is good, ran a windows app on it (read test) and found out some sectors are damaged which is why the drive switched to read only mode. I've used the following app to test the USB: [http://www.vconsole.com/client/?page=page&id=13](http://www.vconsole.com/client/?page=page&id=13)

exchanging the USB with newer one solved the problem.

---

### Post by Mike_Walsh on 2015-07-04
It's not a SanDisk, by any chance?

The Cruzer 'Blades', in particular, seem to have an ongoing problem with this behaviour.

[http://forums.sandisk.com/t5/All-SanDisk-USB-Flash-Drives/Sandisk-cruzer-16GB-became-read-only/td-p/255218/page/2](http://forums.sandisk.com/t5/All-SanDisk-USB-Flash-Drives/Sandisk-cruzer-16GB-became-read-only/td-p/255218/page/2)

If you have a poke around the SanDisk forums, you'll find there are many, **many** threads/posts about this specific issue.....and SanDisk themselves admit that there is **no** known solution. Apart from sending it back to SanDisk, who will send you a replacement.....which is just as likely to suffer from the same problem.

Ain't technology great?


Regards,

Mike. :)

---

