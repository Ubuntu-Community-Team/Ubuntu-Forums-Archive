---
title: "Laptop keyboard doesn't work"
date: 2012-08-12
forum: New to Ubuntu
---

### Post by magnusbrodin on 2012-08-12
Hi! I just traded my Win8 for Ubuntu12.04 LTS but I can't get my keyboard working. In the startup when I have to choose witch OS to use the built in keyboard works but when Ubuntu has started the keyboard doesn't work. I have to connect a USB keyboard to write. My touchpad works just fine. I'm really new to Linux so please write a really easy "get your keyboard startet for dummies" and I'll be happy :) The laptop is a LG S900.

---

### Post by Marric on 2012-08-13
Did you already try to reinstall Ubuntu 12.04. ?
I've read that it helped in those cases.

Good luck.

---

### Post by magnusbrodin on 2012-08-14
I have tried several different Linux versions with the same result, as soon as the OS is fully started the keyboard doesnt work. I have benn looking around for a good solution but so far havnt seen one.

---

### Post by Marric on 2012-08-14
Connect your USB keyboard, this solution for the LG S900 is from an old thread, but maybe it still works..

Paste the following in your Terminal
```
sudo gedit /etc/default/grub
```The editor will open a grub configuration file.
Be careful here, do not change anything except the below.

 Search for
```
GRUB_CMDLINE_LINUX_DEFAULT="*quiet splash*"
```and change it to
```
GRUB_CMDLINE_LINUX_DEFAULT="*quiet splash*** i8042.nopnp=1 i8042.dumbkbd=1**"
```there might be other text between the quotes, do not remove it.
Save and exit.

To make these changes work paste this command in your Terminal
```
sudo update-grub
```Ok then just reboot, cross your fingers and tell me how it went.

Source: [http://ubuntuforums.org/showthread.php?t=1301842](http://ubuntuforums.org/showthread.php?t=1301842) #13

---

### Post by magnusbrodin on 2012-08-14
Thank you Marric for trying to help, it's greatley apreciated. I entered the text you told me to an rebooted but unfortunately it didn't help. Anyone else that would like to have a go at the problem?

---

### Post by Marric on 2012-08-16
Add this to the grub as above
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi=off** i8042.nopnp=1 i8042.dumbkbd=1"
```Alternatively try```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off **i8042.nomux=1 i8042.reset**"
```and do not forget
```
sudo update-grub
```

---

