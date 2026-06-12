---
title: "[SOLVED] Mounting NTFS"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by smave on 2008-06-04
I am dual booting and have two 120 gig hdd's . i have XP (/dev/sda1) on one and Ubuntu on the other. I am having troubles mounting the windows drive so I can access my files. Here is what I have done so far.

sudo apt-get update
sudo apt-get install ntfs-3g

added the following to /etc/fstab:

/dev/sda1 /media/sda1 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda1 /media/windows ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1
 
I also made the /media/windows directory and rebooted. Can some help me or give me some advice. I still get the error. Cannot Mount volume, You are not privileged to mount this volume.

---

### Post by Joeb454 on 2008-06-04
See the link at the bottom of my sig - it's worked flawlessly for me every time I've tried it :)

---

### Post by smave on 2008-06-04
That seems a lot easier! After I did this I now get the error :
You are not privileged to mount this volume.

Help?

---

### Post by Joeb454 on 2008-06-04
Hmm, did you make sure you have the volume unmounted before you start?

---

### Post by smave on 2008-06-04
i cant mount it in the first place.

---

### Post by Joeb454 on 2008-06-04
Hmm odd. Try rebooting, see if it automounts it for you next time :)

---

### Post by smave on 2008-06-04
nope.

i have no desktop shortcut, nothing in the windows folder, and still cant mount my drive. How do i not have the priveledge... i installed the operating system....

how do i mount as root?

---

### Post by Joeb454 on 2008-06-04
```
sudo mount /dev/sda1
``` Though note that sda1 may different. sda1 is the 1st partition on the 1st hard drive :)

---

### Post by smave on 2008-06-04
smave@smavelaptop:~$ sudo mount /dev/sda1
[sudo] password for smave: 
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g force 0 0
smave@smavelaptop:~$ mount -t ntfs-3g /dev/sda1 /media/sda1 -o force
mount: only root can do that
smave@smavelaptop:~$ mount -t ntfs-3g /dev/sda1 /media/sda1 -o force


im about to give up >.< ](*,)

---

### Post by Joeb454 on 2008-06-04
OHH! That's why. Is it a Windows partition?

If so, try booting it up, and then shut it down cleanly

---

### Post by smave on 2008-06-04
solved. thanks for the help. Im so glad there is a place where people can help me out. <3's

---

### Post by Joeb454 on 2008-06-04
Oh good :) And it's no problem :)

---

