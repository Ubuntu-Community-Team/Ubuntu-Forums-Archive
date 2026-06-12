---
title: "madwifi install problems"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by -=m1cha3l=- on 2008-09-14
i have tried to follow the guide provided [here](http://ubuntuforums.org/showthread.php?t=792158&highlight=atheros)

when i use the command 
```

make

```

i get this error
```

cd: 1: can't cd to /lib/modules/2.6.21.5/build
Makefile.inc:66: *** /lib/modules/2.6.21.5/build is missing, please set KERNELPATH. Stop.

```

my kernel is in /lib/modules/2.6.24-16-generic 

how would i change this?

i have tried
```

KERNELPATH=/lib/modules/2.6.24-16-generic/

```

i check the variable has been set with 
```

echo $KERNELPATH

```

but this still does not work.

so i then tried creating a folder called 2.6.21.5 in the modules dir and linking it to 2.6.24-16-generic

this allowed me to make and make install but when it came to 

```

modprobe ath_pci

```

i get this error message

```

WARNING: Error inserting ath_hal (/lib/modules/2.6.24-16-generic/net/ath_hal.ko): Invalid module format
WARNING: Error inserting wlan (/lib/modules/2.6.24-16-generic/net/wlan.ko): Invalid module format
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-16-generic/net/ath_pci.ko): Invalid module format

```

any help would be greatly appriciated

---

### Post by pytheas22 on 2008-09-14
There's a script [here]("http://ubuntuforums.org/showthread.php?t=798485&highlight=madwifi+script") for compiling the latest madwifi from source that you may want to try.  If that doesn't work, we can try to troubleshoot your strange make errors, but hopefully the script will just take care of it all for you.  I'm not sure what's going on above, unless it's a bug with the particular subversion code that you checked out.

---

### Post by -=m1cha3l=- on 2008-09-14
thank you for your help. I tried the script you suggested and still no joy :(

i think i have found the cause though just not sure of the fix!

i am triple booting with ubuntu/XP/Backtrack the back track kernel is 2.6.21.5

and this is what shows up when you run the command
```

uname -r

```
2.6.21.5

yet ubuntu kernel is 2.6.24-16

any idea why is it reading backtracks version when in ubuntu?

and is there a way to change this value?

---

### Post by pytheas22 on 2008-09-14
That's pretty strange.  Perhaps something is amiss with your grub menu.  You can take a look at the grub configuration by typing:
```

sudo gedit /boot/grub/menu.lst
```

You should see at least one section that looks like:

```
title		**Ubuntu** 8.04.1, kernel 2.6.24-19-generic
root		**(hd0,1)**
kernel		**/boot/vmlinuz-2.6.24-19-generic** root=UUID=b5725877-5158-4c5f-b858-e0f6eededc1e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

Check to make sure that the kernel image that it boots to is the right one, and that it's on your Ubuntu partition (in the above example, that is hd0,1, which means the second partition of the first hard drive).  If nothing looks wrong with your grub file in Ubuntu, check the one in Slackware.

It might also help in Ubuntu to download system updates, if you're online in some way:
```

sudo apt-get update
sudo apt-get upgrade
```

---

### Post by -=m1cha3l=- on 2008-09-14
I boot with lilo

here is the contents of lilo.conf

```

boot = /dev/hda
message = /boot/boot_message.txt
prompt
timeout = 1200
change-rules
reset
vga = normal
other = /dev/hda1
label = Windows
table = /dev/hda
image = /boot/vmlinuz
root = /dev/hda5
label = Linux
read-only
image = /boot/vmlinuz
root = /dev/hda4
label = ubuntu
read-only

```

do you whink i should use grub?

---

### Post by pytheas22 on 2008-09-14
I didn't think anyone used lilo anymore :)

I never used it to speak of and am not sure how to read the configuration file, unfortunately, so I can't tell you if something is wrong or not.  If I were you, I'd probably just install grub.

Otherwise, there's no reason why madwifi shouldn't compile on the older Slackware kernel, as far as I know.  Did you take a look at [this page]("http://madwifi.org/wiki/UserDocs/Distro/Slackware")?

---

### Post by -=m1cha3l=- on 2008-09-14
i have just re-installed and am now using grub.

for some reason i now dont need the madwifi installing as it works out the box.

i give in asking questions! lol

thank you for your help

---

