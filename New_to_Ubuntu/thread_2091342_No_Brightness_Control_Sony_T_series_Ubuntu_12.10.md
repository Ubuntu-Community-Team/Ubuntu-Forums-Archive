---
title: "No Brightness Control Sony T series Ubuntu 12.10"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by Dendo on 2012-12-04
Sorry I read this thread: [http://ubuntuforums.org/showthread.php?t=2088190](http://ubuntuforums.org/showthread.php?t=2088190) and it is very similar and I wasnt sure if i should reply or start new thread. I have a JP Sony vaio 13' T-series dual boot windows8 oem with 12.10.    

But like the poster I was able to change brightness up and down with the terminal command:

echo 2441 | sudo tee /sys/class/backlight/intel_backlight/brightness

and

echo 4882 | sudo tee /sys/class/backlight/intel_backlight/brightness

here is my acpi_listen:

zombie@zombie:~$ acpi_listen
video DD02 00000087 00000000
video DD02 00000086 00000000

im stuck here as the other poster has a different output.  Any help would greatly be appreciated.

---

### Post by Toz on 2012-12-04
> zombie@zombie:~$ acpi_listen
video DD02 00000087 00000000
video DD02 00000086 00000000
Are these the codes that are generated when you press the Fn+F5 (brightness down) and Fn+F6 (brightness up) keys? They don't look right.

---

### Post by Dendo on 2012-12-05
Yes the first is FN+F5 (brightness up) FN+F6 (down)

---

### Post by honeybear on 2012-12-05
> **Dendo said:**
> Sorry I read this thread: [http://ubuntuforums.org/showthread.php?t=2088190](http://ubuntuforums.org/showthread.php?t=2088190) and it is very similar and I wasnt sure if i should reply or start new thread. I have a JP Sony vaio 13' T-series dual boot windows8 oem with 12.10.    

But like the poster I was able to change brightness up and down with the terminal command:

echo 2441 | sudo tee /sys/class/backlight/intel_backlight/brightness

and

echo 4882 | sudo tee /sys/class/backlight/intel_backlight/brightness

here is my acpi_listen:

zombie@zombie:~$ acpi_listen
video DD02 00000087 00000000
video DD02 00000086 00000000

im stuck here as the other poster has a different output.  Any help would greatly be appreciated.


the brightness is controlled by the kernel
type us:

lsmod

---

### Post by Toz on 2012-12-05
> **Dendo said:**
> Yes the first is FN+F5 (brightness up) FN+F6 (down)

Follow the same steps in that previous thread, but use the following files instead:

**/etc/acpi/events/sony-brightness-up**
```

event=video DD02 00000087 00000000
action=/etc/acpi/brightup.sh
```

**/etc/acpi/events/sony-brightness-down**
```

event=video DD02 00000086 00000000
action=/etc/acpi/brightdown.sh
```

---

### Post by Dendo on 2012-12-06
Thank you so much it worked. I will mark as SOLVED.

---

### Post by ratnadeep gaikwad on 2012-12-09
I have a sony Vaio VPCEG3AEN and the following worked for me:

I opened the file /etc/X11/xorg.conf and changed the below section

sudo gedit /etc/X11/xorg.conf

Initially the setion was:

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection


Changed it to:

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option  "NoLogo"        "True"
    Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection


Note: Some forums suggest a change in the /etc/default/grub file
You need to revert back those changes for this to work

---

