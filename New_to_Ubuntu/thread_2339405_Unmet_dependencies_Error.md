---
title: "Unmet dependencies Error"
date: 2016-10-08
forum: New to Ubuntu
---

### Post by kaleidopunk on 2016-10-08
Hello, 
Running Ubuntu 16.04 LTS 32-bit getting an error that says 

'Error: Opening the cache (E:Couldn't create temporary file to work with /var/lib/apt/lists/gb.archive.ubuntu.com .... etc ending with The package lists or status file could not be parsed or opened.) This usually means that your installed packages have unmet dependencies'

Laptop is being generally slow. I was looking through the forum here and tried 

sudo apt-get update
sudo apt-get upgrade

[FONT=arial]then it says

[/FONT] sudo apt-get upgrade
Reading package lists... Error!
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Couldn't create temporary file to work with /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_xenial_InRelease - mkstemp (30: Read-only file system)
E: The package lists or status file could not be parsed or opened.


[FONT=arial][/FONT][FONT=arial]Any help appreciated. Please give slow step-by-step instructions as I am an Ubuntu beginner!

Cheers
[/FONT]

---

### Post by ajgreeny on 2016-10-08
Try command ```
sudo rm /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_xenial_InRelease
```which I think will give you an error of "file not found" as it looks as if that file is misnamed for some reason, so try again but omit the final "e" of the command, hit Tab to autocomplete the file name and see if that works for you.

If it does, run the ```
sudo apt-get update
sudo apt-get upgrade
``` again to refresh all the lists and hopefully upgrade all packages for you.

---

### Post by kaleidopunk on 2016-10-08
Hi, thanks for that.
It's saying 

rm: cannot remove '/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_xenial_InRelease': Read-only file system

Then I tried the tab thing and it said

cannot create temp file for here-document: Read-only file system

---

### Post by ajgreeny on 2016-10-08
Hmmm? Not sure about that.

Using sudo to raise your permissions to that of root should make all the files in /var/lib/apt/lists/ read/write not read only, and the filesystem should not be read only or almost nothing will work as it should.

Can I check that you are not running from a live USB/DVD system; is this a fully installed Ubuntu 16.04 system, and have you been able to update in the past or is this a new installation?

---

### Post by #&amp;thj^% on 2016-10-08
Sorry for stumbling in here.
To get read write back I have used this with great success.
```
sudo mount -o remount,rw /
```
**But wait for ajgreeny to confrim**...as he might have a different method or route he wants to pursue.

---

### Post by kaleidopunk on 2016-10-08
It's a new installation, only about a week old. Maybe it didn't install properly? Haven't had any problems running anything until now.
Just noticed a couple of programs I installed aren't working now

---

### Post by ajgreeny on 2016-10-09
OK, yes try out the command shown by 1fallen at post #5 to remount everything read/write.

The big query is why has the filesystem been mounted read only; was this the first and only time it has happened or is it always the same when you boot the computer?

It certainly should not happen unless something has gone very wrong so we need to try to figure out what and why and how to put it right.

---

### Post by ian-weisser on 2016-10-09
Doe the 'read-only' issue persist after a poweroff/reboot?
Have you ever had hard disk problems before?
How old is the hard drive?
You can use SMART tools to identify many problems: [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

