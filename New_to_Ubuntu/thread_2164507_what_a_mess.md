---
title: "what a mess"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by dave6 on 2013-07-31
I am supose to log in here as DaveMcC, now it's dave6, not only that but the thing would not let me log in using my usual email address, so I had to use a different one which I now have to mark any thing coming from here as spam

I had asked before about how to edit grub, but for the life of me I can't find that post,  I have multi choice to boot up from, in the following order

Ubuntu                    **this part is OK**
Ubuntu test mem    ** this part is OK**
old / other version of linux or grub, (can't remember ) would like this line _**removed**_ please
win xp on dev/ ????** this part is OK**
win7 on dev/ ??? other drive in compter "_this line is missing_"

In short I had to do a full re-install of win7, I disconncected the hard drives to do so, when plugged back in, missing line in boot menu

Any one help me out of my mess

Dave

---

### Post by QIII on 2013-07-31
Hello!

Would you please start a thread in the Resolution Centre regarding your SSO issue.

The Admins are working very hard to get everyone's accounts straightened out.

Please let them know what your original account name was.

Thanks

---

### Post by dave6 on 2013-07-31
> **QIII said:**
> Hello!

Would you please start a thread in the Resolution Centre regarding your SSO issue.

The Admins are working very hard to get everyone's accounts straightened out.

Please let them know what your original account name was.

Thanks
  Resolution Centre ????? where is that hid at??
I know the admins are working hard to sot things out, but does it matter, I am now in here as dave6, password "cows eat grass" who cares, I don't

dave

---

### Post by CharlesA on 2013-07-31
It is that way: [http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

---

### Post by lisati on 2013-07-31
> **dave6 said:**
> Resolution Centre ????? where is that hid at??
I know the admins are working hard to sot things out, but does it matter, I am now in here as dave6, password "cows eat grass" who cares, I don't

dave

I hope you were joking about your password.... :D

The Resolution Centre can be found here: [http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)
There's also some useful information about what the admin team need to know in the stickies.

Please be patient, the admin team have been doing their best.

---

### Post by alfonsojon1997 on 2013-07-31
sudo apt-get autoremove
- This will remove old kernel versions (Old versions of linux)
sudo grub-update
- This will update your grub menu and hopefully bring back Windows 7 :)

---

### Post by dave6 on 2013-07-31
> **lisati said:**
> I hope you were joking about your password.... :D

The Resolution Centre can be found here: [http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)
There's also some useful information about what the admin team need to know in the stickies.

Please be patient, the admin team have been doing their best.

But every one knows "cows eat grass" just eat it, don't smoke it, I just smoke it, not eat it, I am getting confussed

You may noticed that the search opion is missing from above in the red bar, I am going cross-eyed looking for my post on editing grub

Never mind, I am sure that in the next week r so, the admins wil get ALL up and rnning again, lets give them our suport, go to the pub and have a small drink on their behalf

dave ooopppps

DaveMcC

> **alfonsojon1997 said:**
> sudo apt-get autoremove
- This will remove old kernel versions (Old versions of linux)
sudo grub-update
- This will update your grub menu and hopefully bring back Windows 7 :)

Cheers, thought that lokedas if it would work, sadly no

daboss@daboss-desktop:~$ sudo apt-get autoremove
[sudo] password for daboss: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
daboss@daboss-desktop:~$ sudo grub-update
sudo: grub-update: command not found
daboss@daboss-desktop:~$ 

I can get into win7 at post hit f11 and select the drive it is on, which ain't a bad thing doing that way

DaveMcC

---

### Post by angryfirelord on 2013-07-31
That one command is backwards, It's **sudo update-grub**, not grub-update.

apt-get autoremove only removes unusued dependencies. It doesn't remove old kernels. You can remove them, but you'll have to know the specific kernel number that you want to remove. You'll also have to keep in mind not to remove the currently running kernel you have installed.

---

### Post by ajgreeny on 2013-07-31
> **alfonsojon1997 said:**
> sudo apt-get autoremove
- This will remove old kernel versions (Old versions of linux)
sudo grub-update
- This will update your grub menu and hopefully bring back Windows 7 :)

No, sorry but you are wrong.  That will not remove any kernels, only packages that are not dependencies of any installed package, and are therefore not useful to you or the system.  It does not remove any packages that are at the top of the dependency tree such as kernels.

The best way to remove old kernels is firstly to install synaptic package manager.  Then, to see what you actually have installed run command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
``` and finally use synaptic to search for the old kernels by name only, using the version number as search term, eg 3.5.0-36.  That will probably show 3 packages installed for each version number which you can choose to remove completely, keeping only the two most recent.

---

### Post by dave6 on 2013-08-01
You are both wrong, not often I get a chance to say that here
Q1 to ajgreeny, what is the thing between cfg and cut on your code line, the sticky up thing ?
Q2 to angryfirelord, if I run sudo update-grub and it goes completly wrong.................... will you come to my house and fix it, "at your expense"

The line in question is as follows  **Previous Linux Versons**     I know I wrote it down wrong at the first post,, this is what I had written (old / other version of linux or grub, (can't remember ) would like this line _**removed**_ please)
So, that also leaves me wrong in my first Q, we are all wrong, y/n

Dave

err no

DaveMcC

I decided to be brave, got this

daboss@daboss-desktop:~$ sudo update-grub
[sudo] password for daboss: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found Microsoft Windows XP Professional on /dev/sda1
Found Windows 7 (loader) on /dev/sdc1
done
daboss@daboss-desktop:~$ 


must give it a reboot now and see what all **IS** there

---

### Post by ajgreeny on 2013-08-01
> **dave6 said:**
> Q1 to ajgreeny, what is the thing between cfg and cut on your code line, the sticky up thing ?

daboss@daboss-desktop:~$ sudo update-grub
[sudo] password for daboss: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found Microsoft Windows XP Professional on /dev/sda1
Found Windows 7 (loader) on /dev/sdc1
done
daboss@daboss-desktop:~$ 


must give it a reboot now and see what all **IS** there
The | in my command is the "pipe" character.  Pipe takes the output of a command in terminal and "pipes" it to another command; in my case to the **cut** command (see **man cut** for details of **cut**).

You have no need to remove any old kernels as you only have two versions at the moment so you can forget about that at the current time..

---

### Post by angryfirelord on 2013-08-04
> **dave6 said:**
> Q2 to angryfirelord, if I run sudo update-grub and it goes completly wrong.................... will you come to my house and fix it, "at your expense"
Why would it go completely wrong? All it does is generate boot entries. Even if your boot loader was messed up, you can reinstall it from a LiveCD.

In any case, it also looks like the Windows 7 entry was found. Let us know if you can boot into it.

---

