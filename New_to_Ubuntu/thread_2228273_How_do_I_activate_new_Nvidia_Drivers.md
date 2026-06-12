---
title: "How do I activate new Nvidia Drivers?"
date: 2014-06-06
forum: New to Ubuntu
---

### Post by nigel-huang312 on 2014-06-06
I just installed NVIDIA Driver 331.79 x64 using the download from Nvidia website . I used the terminal and then everything as I would do in Ubuntu 12.04. and then I restarted. The driver in the software and updates are still on the old one. The new option is not even there!

---

### Post by deadflowr on 2014-06-06
I wouldn't think it would be there.
That program lists the driver available through Ubuntu's repos.
Did you run 
```
sudo nvidia-xconfig
```
If you did, then the driver should be activated.
```
 lspci -nnk | grep -iA3 vga
```
will list the driver in use.
If it says nvidia, then the driver is running.

---

### Post by papibe on 2014-06-06
Hi nigel-huang312. Welcome to the forum ):P

The drivers on the tab 'Additional drivers' from the 'Software & updates' are the one from the Ubuntu repositories, and their purpose is the both install them and check if they are running.

The driver from the Nvidia site does not fall in that category, so that tab won't do you any good.

If you want to know if the Nvidia driver is running, please run the this command:
```
lspci -nnk | grep -iA2 vga
```
There should be a line that says: 'driver in use: nvidia'

If you want to check which is the version of the driver you are running, there several options.

The simplest is to open 'Nvidia X Server settings' and check the version there.

Another option is to check the corresponding version of nvdia-settings:
```
nvidia-settings --version
```
Alternatively, you could check the version of the driver using module commands:
```
modinfo nvidia
```
or if that don't work:
```
modprobe --resolve-alias nvidia
```
Hope it helps. Let us know if you have more questions.

Come here often and have fun.
Regards.

P.S.: most of us prefer to use the version provided from Ubuntu (the one on 'Software & updates'), because has been through a fairly strict testing process thus making it more stable.

---

### Post by nigel-huang312 on 2014-06-06
Thank you both it worked

---

