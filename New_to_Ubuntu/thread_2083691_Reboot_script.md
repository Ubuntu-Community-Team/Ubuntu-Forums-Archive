---
title: "Reboot script"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by Lupajz on 2012-11-13
Hello. I run dual-boot machine with 12.10 and W7. I wanted to make an script for machine reboot to an selected os. 

I modified line in /etc/defaults/grub
```
GRUB_DEFAULT="saved"

```

and made a simple executable file, containing my sudo pw : 
```
#!/bin/sh
echo "****" | sudo -S -i grub-reboot "Windows 7 (loader) (on /dev/sda1)"

sudo reboot
```


this works fine but, after that I realized that the grub option is always on Windows 7 entry. But I want it to always boot into ubuntu and get into windows after I run this executable. I also have one file for reboot into ubuntu, but I want to keep my machine to boot into ubuntu at the start not into last saved entry.

Also how could I implement those two executables into power menu ? I mean there where you can choose to shut down machine an so on ? 

Thanks for answears.

---

### Post by Impavidus on 2012-11-13
If I understand correctly, you have managed to write a script that sets grubs default to win7 and then reboots, but whenever you boot into Ubuntu you want the default reset to Ubuntu. So, I'd suggest you use a second script to set the default to Ubuntu and automatically call that script when booting into Ubuntu. Which leaves the question how to reset the default while running win7.

Concerning your second question (how to put it into the log-off menu), I'm not sure whether that menu is configurable. Off course you could make a button  that calls some home-brewed code displaying a nice menu with the options you want. I've never tried, but I think it should be possible to create gtk+ windows from a bash script. But then there's still the question of privileges. You have to be root to reboot. The standard reboot button allows every user physically present to reboot by using the setuserID bit, but if I'm correct this is disabled for scripts (for security reasons). You may need to program that in C or whatever you like, but I think it's possible.

Anyway, when you use your script as you have it now you already have to provide your password, which seems inconvenient to me and a possible security risk.

---

### Post by Cheesemill on 2012-11-13
You need to set the default grub boot value to whatever you want by doing:
```
sudo grub-set-default [num]
```
Where [num] will probably be 0 on your machine (the first grub entry).

You should only need to do this once (ie not put it in your script).

Also I would highly recommend taking your password out of the script and instead using visudo to add entries for reboot and grub-reboot to your sudoers file. This way you can use these commands with sudo without having to use a password. In this situation it isn't really a security issue as a user can reboot without their password anyway.

---

