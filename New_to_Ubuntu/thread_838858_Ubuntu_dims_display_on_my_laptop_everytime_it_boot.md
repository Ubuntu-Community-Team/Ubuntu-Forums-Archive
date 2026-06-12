---
title: "Ubuntu dims display on my laptop everytime it boots"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by 133794m3r on 2008-06-23
yeah everytime that I boot ubuntu it dims my display to almost nothing... it angers me... b/c I have to increase it back again... even when I'm on AC power. I'm running it on my laptop... and i know that it's ubuntu doing it... so is there anyway to stop it?

---

### Post by |{urse on 2008-06-23
probably an acpi incompatibility 
try booting with 

acpi=off

---

### Post by RiceMonster on 2008-06-23
Check the brightness settings in your bios.

---

### Post by |{urse on 2008-06-23
btw you just edit the menu.lst and add acpi=off to the end of the "kernel" line. then run 

update-grub

---

### Post by 133794m3r on 2008-06-23
the what? where?

---

### Post by |{urse on 2008-06-23
k. open ye olde terminal. menu > accessories > terminal

```
sudo gedit /boot/grub/menu.lst
```

add acpi=off to the end of the the "kernel" line (it'll say "kernel" at the beginning of the line)
be sure to save it.

then run 

```
update-grub
```

\\:D/

---

### Post by 133794m3r on 2008-06-23
I get this when I do that...
```
macarthur@macarthur-laptop:~$ sudo gedit /boot/grub/menu.lst
macarthur@macarthur-laptop:~$ update-grub
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=86cf69bd-4f08-437c-9b2d-e9c8cb9daf71'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
cp: cannot remove `/boot/grub/menu.lst~': Permission denied 
```

---

### Post by RiceMonster on 2008-06-23
you need to run that command as root:

```
sudo update-grub
```

---

### Post by |{urse on 2008-06-23
ah yes ty for the catch (multi-tasking) ^^

---

### Post by 133794m3r on 2008-06-24
Ok.... still not working... I added the thing here
```
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro acpi=off

#
```
so yeah... help me......

---

### Post by |{urse on 2008-06-24
> **133794m3r said:**
> yeah everytime that I boot ubuntu it dims my display to almost nothing... it angers me... b/c I have to increase it back again... even when I'm on AC power. I'm running it on my laptop... and i know that it's ubuntu doing it... so is there anyway to stop it?

when you increase it back again, how exactly are you doing it? with fn keys?

---

### Post by rainwalker on 2008-06-24
Have you messed with the settings in System > Preferences > Power management?

---

### Post by 133794m3r on 2008-06-24
> **|{urse said:**
> when you increase it back again, how exactly are you doing it? with fn keys?

yes and to the second person no

---

### Post by rainwalker on 2008-06-24
Make sure the "Dim Display" box in System > Preferences > Power Management isn't checked (see attachment)

---

### Post by 133794m3r on 2008-06-24
> **rainwalker said:**
> Make sure the "Dim Display" box in System > Preferences > Power Management isn't checked (see attachment)

yeah... I guess i've already done that..... and it's not checked.... so yeah.... if was used to be... then... I've changed that... if not then I haven't.

---

### Post by balagosa on 2008-06-24
I also have this problem, many other also did too. I found one solution for this, but I lost the bookmark for it. There was this one guy that made his own solution. He made a code that every time Ubuntu boots up, he would increase the brightness.

I will try to find the code.

---

### Post by balagosa on 2008-06-24
here is the [thread]('http://ubuntuforums.org/showthread.php?t=763809&highlight=dim+boot&page=3'). Look for **g_damian**'s post. He also posted a link for his code.

This thread was started by treb0r that had the same problem as you. Tell me how it works out.

---

### Post by 133794m3r on 2008-06-24
ok... yeah what am I supposed to save it to?

---

### Post by balagosa on 2008-06-24
g_damian said where to save it.

```
sudo gedit /etc/rc.local
```

Note: Save it before "exit 0"

---

### Post by 133794m3r on 2008-06-24
nvm.... I forgot a space between gedit and /

---

### Post by bertilow on 2008-06-25
Have a look here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/12637](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/12637)

A possible work-around is mentioned at the end.

---

### Post by |{urse on 2008-06-25
did you try the aforementioned fix in that link?

> echo blacklist video | sudo tee -a /etc/modprobe.d/local

??

---

### Post by 133794m3r on 2008-06-25
> **|{urse said:**
> did you try the aforementioned fix in that link?



??

the what? and how? just type that in directly?

---

### Post by |{urse on 2008-06-26
yes in the terminal. Be sure to read the whole post though. (its near the bottom)

---

### Post by 133794m3r on 2008-06-27
> **|{urse said:**
> yes in the terminal. Be sure to read the whole post though. (its near the bottom)

well yeah it's working now thanks.....

---

### Post by |{urse on 2008-06-28
hey no problem, if you click the blue ribbon in the lower right hand corner of the guy above me who found that fix then you're welcome. :lolflag:

---

