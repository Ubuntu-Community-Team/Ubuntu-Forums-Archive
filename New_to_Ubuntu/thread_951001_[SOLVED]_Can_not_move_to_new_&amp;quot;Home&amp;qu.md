---
title: "[SOLVED] Can not move to new &amp;quot;Home&amp;quot; ?"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by germanix on 2008-10-17
I am at a complete loss! I wanted to make a new partition for my "Home" using GParted. I followed the tutorial on psychocats to the letter. The partition worked fine, but moving the old home to the new home did not work. I could not boot. I went into recovery mode and again followed the instuctions in the tutorial,this did not help. I then followed the instructions to undo everything and this does not work. 
I do not know what to do next?

---

### Post by Harisz750 on 2008-10-17
format????

---

### Post by detroit/zero on 2008-10-17
Back up all your important data and reinstall.

Make sure you choose to set home on its' own partition while you're installing, too :lolflag:

Seriously, though, what kind of errors are you getting?

---

### Post by germanix on 2008-10-17
It tells me it cannot find my home file, that it does not exist. I am now booting with the live CD.

---

### Post by handydan918 on 2008-10-17
If you are running from the live cd, I suspect you need to mount the /home directory first.

---

### Post by alex1996arm on 2008-10-17
uhhh wierd...
could you specify more?

---

### Post by alex1996arm on 2008-10-17
what does the error say exactly?

---

### Post by detroit/zero on 2008-10-17
> **germanix said:**
> It tells me it cannot find my home file, that it does not exist. I am now booting with the live CD.
Oh, I see.. You'll probably have to edit fstab to reflect the new partition being used. 

I don't know much about doing that.. maybe someone else can help.

If it were me, and I didn't get a response in whatever I deemed a reasonable amount of time (depending on the severity of the problem, which I would think not having access to a home directory is pretty severe...), I would go ahead and do a backup/reinstall.

But that's just me.

Can you give us a link to this tutorial and tell us where you ran into problems? Does the tutorial include a section on editing */etc/fstab*?

---

### Post by germanix on 2008-10-17
I cannot boot normally, only with the live CD. How do I mount the home directory from the live CD?

---

### Post by alex1996arm on 2008-10-17
from the partition on hdd?

---

### Post by germanix on 2008-10-17
The error says: Your home directory is listed as /home/jac but does nor appear to exist. Do you want to log in with the root directory. It is unlikely anything will work unless you use a failsafe session.

---

### Post by germanix on 2008-10-17
from the partition on hdd?
yes. Old home was sda1, should now be on sda3

---

### Post by detroit/zero on 2008-10-17
> **germanix said:**
> I cannot boot normally, only with the live CD. How do I mount the home directory from the live CD?
Do us a favor.

Take a screenshot of your hard disk from inside gparted, and provide a copy of the  /etc/fstab file from the drive.

It should look something like this, with some differences in the numbers:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=97882d01-2555-456e-92c2-39a02d2eb9df /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=ec6d9351-2178-4474-b123-a4126dfbdc8c /home           ext3    relatime        0       2
# /dev/sda6
UUID=8887efa3-3b11-44e1-b24f-2f982a06bb72 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

---

### Post by alex1996arm on 2008-10-17
thanks,
this may help [http://ubuntuforums.org/showthread.php?t=644400](http://ubuntuforums.org/showthread.php?t=644400)

---

### Post by germanix on 2008-10-17
Have tried this in recovery mode:
chown -R username:username /home/username
chmod 644 /home/username/.dmrc
chmod 644 /home/username/.ICEauthority
exit
Says no such file or directory?

---

### Post by alex1996arm on 2008-10-17
maybe this then(its launchpad)
[https://answers.launchpad.net/ubuntu/+question/14843](https://answers.launchpad.net/ubuntu/+question/14843)

---

### Post by alex1996arm on 2008-10-17
sorry for bombarding you with links
its just that they are soooooo pratical:)

---

### Post by germanix on 2008-10-17
At the moment I cannot boot, not even with the live CD.

---

### Post by alex1996arm on 2008-10-17
so what you are trying to say is that you cant boot your computer at all????

---

### Post by germanix on 2008-10-17
When trying to boot normally I get the error: $HOME/.dmrc file is being ignored. File should be owned by owner and have 644 permission etc

---

### Post by germanix on 2008-10-17
I am now booting with the live CD

---

### Post by alex1996arm on 2008-10-17
good now i will look for solution

good tip for next time,
try googling for common error
like instead of 
:Your home directory is listed as /home/jac but does nor appear to exist. Do you want to log in with the root directory. It is unlikely anything will work unless you use a failsafe session.

this should be your search:Your home directory is listed as /home but does nor appear to exist

---

### Post by mister_pink on 2008-10-17
When you get to the login screen, try changing the session to failsafe terminal. Log in (ignore the errors). Try doing "sudo mount /home" then "exit" and log in again. 

This should temporarily let you log in normally until you get things fixed.

If this doesn't work, post any error messages exactly as you get them (if they're any different to before). In particular I'd be interested to see if it tells you its already mounted or not.

Edit: I should add, if the failsafe terminal doesn't work, you can press ctrl+alt+F1 to get a terminal and try the same commands. Do alt+F7 to get back to the log in screen.

---

### Post by alex1996arm on 2008-10-17
do what mister_[COLOR="Magenta"]pink[/COLOR] says and put > sudo chown jack:jack /home/jack/.dmrc

---

### Post by germanix on 2008-10-17
The only failsafe session I can get into is the terminal. I am in now, what do I do?

---

### Post by alex1996arm on 2008-10-17
do what mister_pink wants then put > sudo chown jack:jack /home/jack/.dmrc

---

### Post by germanix on 2008-10-17
sudo chown jack:jack /home/jack/.dmrc 
command not found!

now get:chown: missing operand after jac:jac/home/jac/.dmrc
try chown --help
???

---

### Post by alex1996arm on 2008-10-17
uh ohhhhhhhhhh
i only now how to use chown

---

### Post by alex1996arm on 2008-10-17
i can only leave you with this... [http://www.google.ca/search?hl=en&client=firefox-a&rls=com.google.ggic:en-US:official&hs=4Ny&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=Your+home+directory+is+listed+as+/home+but+does+not+appear+to+exist&spell=1](http://www.google.ca/search?hl=en&client=firefox-a&rls=com.google.ggic:en-US:official&hs=4Ny&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=Your+home+directory+is+listed+as+/home+but+does+not+appear+to+exist&spell=1)
i will check back for news...
good luck!

---

### Post by germanix on 2008-10-17
Well it is after 1:00 am here in germany so i will call it a night and try again tomorrow. thank you all for the help so far.

---

### Post by alex1996arm on 2008-10-17
over and out with germanix

---

### Post by Kellemora on 2008-10-17
Hi Germanix

Being a Noob, I might not be much help here, but I did look at my two computers that have /home/user other than in the OS's partition.

It seems like when I was first setting up the first computer, after partitioning I had to  mkdir /home then inside /home mkdir /user

But I'm sure you already passed that point.

The reason I chimed in was to say I looked at the fstab file on both computers.

On the computer with one hard drive the line reads
/dev/hda4 /home ext3 nodev,nosuid 0 2

On the computer with two hard drives, home on the slave hard drive it reads
/dev/hdb3 /home auto nodev,nosuid 0 2

in both cases, these are the last lines in fstab under the fd0 line.

I also looked in Grub menu.lst and did not see anything there pointing to anything other the boot up kernel.

I was looking for something that would have mounted the partition /home is in or some way it knew I had two separate hard drives on the other computer.  I did this way back when I first set up, so just don't remember anymore now if there were questions asked and answered during setup or not.

Good Luck

TTUL
Gary

---

### Post by mister_pink on 2008-10-18
> **germanix said:**
> Well it is after 1:00 am here in germany so i will call it a night and try again tomorrow. thank you all for the help so far.
Did you try the mount command? If so did it give any errors?

---

### Post by dave.com on 2008-10-23
1) Terminal command-line, check mounted partitions with the mount command: $sudo mount.
2) Check / has been mounted somewhere, for this example mount /root at /mnt. Make a directory /mnt/root first if the /mnt/root command doesn't work straight away: $sudo mkdir /mnt/root. 

3)Mount /home partition, thus:
```

~$ sudo su
~# cd /
/# mount -t ext3 /dev/sdxx /mnt/root/home 
/# mount -t proc none /mnt/root/proc
/# mount -o bind /dev /mnt/root/dev
/# sudo chroot /mnt/root /bin/bash
/# sudo nano -w /etc/fstab
``` 
(use ctl+o to write changes to file, use <CR> to save them, use ctl+x to exit nano, navigate cursor location for entry location of text not the mouse pointer)
*Add your /home partition to the fstab. Presumably you know how to:
```
# /dev/sdxx /home ext3 defaults 0 0
# sudo ntfs-config
# sudo update-grub 
```

You should now be able to start with the /home partition mounted, a detail may be you need to export your Xauthority permissions to /home. Somebody may know how this is accomplished, I don't.

---

### Post by germanix on 2008-10-23
You have all been very helpfull and I thank you for this. I tried all your suggestions but nothing seemed to work for me. Its realy my own fault. I have tried the same process twice before using the psychocats tutorial and both times it failed bad. I had to go and try it a third time. Well if I learned something it is not to follow that specific tutorial again. I have mada a new install, but this time I made the "home" partition before the installation, and then mounted it, instead of trying to move it after the installation as before. I am now the proud owner of a seperate home partition and I am a happy man. Once more thank you for all your help.

---

