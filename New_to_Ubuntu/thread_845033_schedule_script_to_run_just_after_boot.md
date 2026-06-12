---
title: "schedule script to run just after boot"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by benfindlay on 2008-06-30
I have a simple series of commands combined into 1 bash script so I can input several lines into the command prompt at once. How would I schedule this bash script to run automatically once my server has booted up?

Cheers

Ben

---

### Post by hyper_ch on 2008-06-30
add it to the according runlevels --> [http://www.debuntu.org/how-to-manage-services-with-update-rc.d](http://www.debuntu.org/how-to-manage-services-with-update-rc.d)

---

### Post by benfindlay on 2008-06-30
Will take a look at that, thanks!

---

### Post by benfindlay on 2008-07-01
Ok, so I copied the script to /etc/init.d/ and ran ```
update-rc.d myscript defaults
``` and when I reboot it doesn't run.

Any ideas?

---

### Post by hyper_ch on 2008-07-01
it might requier a structure of an init script... if that does not help, you can still attach the script to your autostart - or is it required to run as root?

---

### Post by benfindlay on 2008-07-01
This is the script:
```
#! /bin/bash
# script to mount drives and share
sudo mount /dev/sdb1 /media/disk
sudo mount /dev/sdc1 /media/disk-1
sudo mount /dev/sdd1 /media/disk-2
sudo mount /home/user/shared
sudo mount -a

```

I'm sick of remounting the USB hard drives everytime I reboot so I jsut chucked the commands into 1 file with the intnetion of running 1 command instead of 5 every reboot.

What do you think?

---

### Post by hyper_ch on 2008-07-01
why don't you mount them in the /etc/fstab?

---

### Post by benfindlay on 2008-07-01
That just gave me loads of problems and I couldn't get it to work. Also, the machine keeps switching the order of which one is sdb1, which is sdc1 and sdd1 etc, so mounting them manually is the only way I've been able to reliably mount them where I want them to be. Either running the script manually, or typing ```
sudo /etc/init.d/myscript start
``` gets the drives to mount up, but is there any way to do this automatically?

---

### Post by hyper_ch on 2008-07-01
if you have a script in the init.rd then you don't need a sudo, it will be run as root...

but I think you'll need to put it into an init like script...

---

### Post by benfindlay on 2008-07-01
Right, will take a look at that!

Cheers for your help!

---

### Post by hyper_ch on 2008-07-01
there's somewhere a skeleton file of it... or google it... that should return a few examples...

---

