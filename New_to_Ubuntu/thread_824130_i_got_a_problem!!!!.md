---
title: "i got a problem!!!!"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Masricano on 2008-06-09
i got a problem when i rename my drive 45.6 GB Volume: hda1

you can see in attachments and i try to install mtools from the terminal but 

i got Permission denied how can i fix this :confused:

---

### Post by JoshuaRL on 2008-06-09
If you're going to install anything from the terminal, you'll need to use "sudo".  For instance,
```

sudo apt-get install the-package-of-awesome

```
Sudo means "super-user do" and allows you administrative (or in Linux, root) privilidges necessary to install.  This is a security feature long implemented in UNIX, Linux OSs.

---

### Post by azurepancake on 2008-06-09
EDIT: JoashuaRL beat me to it! ;P

To install mtools, open up a terminal session and type:

```
sudo apt-get install mtools
```

The reason why you got permission errors is because you need to be "super-user" to use apt-get.

---

### Post by Het Irv on 2008-06-09
Did you use sudo when you typed your commands in the terminal?

---

### Post by ibuclaw on 2008-06-09
Have you tried to use **sudo** with the command?

Also, the device must be **unmounted** before you can rename the label of it.

Can you post the output of the command
```
df
```
Thanks

Regards
Iain

---

### Post by Masricano on 2008-06-09
i used sudo apt-get install mtools

i think it's installed but how can i use mtools and i tried to unmount volume but i got this pic

---

### Post by JoshuaRL on 2008-06-09
What do the details say?  Is mtools a command line only application, or does it have a GUI?

---

### Post by Masricano on 2008-06-09
it says unmount: /media/hda1 mount disagrees with the fstab :(

---

### Post by Masricano on 2008-06-09
i want also to know how ca i have all permissons

---

### Post by JoshuaRL on 2008-06-09
You do, you just need to sudo to use them.  You seriously don't want to enable login in as root, and no one here will help you to do it.  It's against forum policy.  The reason is that it is really dangerous.  Sudo is a security layer that has long been implemented in UNIX/Linux OSs.

---

### Post by Masricano on 2008-06-09
sorry for that
but how can i rename this drive :mad:

am sorry but am new for ubuntu

---

### Post by gr4nf on 2008-06-09
Just to reiterate that, i once erased my entire HD with the command:
```
ls -R / | grep .exe | rm -rf
```
just because of a misuse of |. Logging in as root is dangerous. With sudo you give yourself everything that root could give you.

---

### Post by Masricano on 2008-06-09
can i rename this drive by sudo or no?

---

### Post by JoshuaRL on 2008-06-09
Let's be clear.

**DON'T USE rm -rf AS ROOT UNLESS YOU KNOW EVERYTHING IS RIGHT.  PLEASE BE CAREFUL.**

---

### Post by Masricano on 2008-06-09
thanks JoshuaRL

but is something wrong in my ubuntu when i installed it or every thing oky? 

i did a drive when i installed ubuntu in format fat32

/media/hda1

it's just for save my own files or mp3

or i hav to install it again?!!!!!1

---

### Post by azurepancake on 2008-06-09
> **tinivole said:**
> Have you tried to use **sudo** with the command?

Also, the device must be **unmounted** before you can rename the label of it.

Can you post the output of the command
```
df
```
Thanks

Regards
Iain

Like stated above, you'll have to "unmount" your device to rename it. If you run the "df" command and paste the output, we should be able to help you further.

---

### Post by Masricano on 2008-06-09
here it is

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             28834716   2169748  25200244   8% /
varrun                  253932       100    253832   1% /var/run
varlock                 253932         0    253932   0% /var/lock
procbususb              253932       104    253828   1% /proc/bus/usb
udev                    253932       104    253828   1% /dev
devshm                  253932         0    253932   0% /dev/shm
lrm                     253932     33788    220144  14% /lib/modules/2.6.20-15-generic/volatile
/dev/sda5             47837856        32  47837824   1% /media/hda1

---

### Post by ibuclaw on 2008-06-09
```
sudo umount /dev/sda5
```
Should unmount the volume.

If that doesn't work. Close all currently open apps. As a program is probably still using the drive. If that still doesn't sort it, reboot. Then run the above command again.

Next, run this command to setup mtools to ignore some strict checks:
```
echo mtools_skip_check=1 >> ~/.mtoolsrc
```
Then to change the name of the label, use:
```
sudo mlabel -i /dev/sda5 ::**mynewlabel**
```
Where you replace "mynewlabel" with the name you wish to give it.

Finally. Reboot to see your changes in Gnome.

Regards
Iain

---

