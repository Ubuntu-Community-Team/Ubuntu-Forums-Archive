---
title: "I can't get beyond the greeter login"
date: 2017-05-01
forum: New to Ubuntu
---

### Post by russed2 on 2017-05-01
Hi.
1- I wanted a live cd to testing stuff, and Lubuntu 16.04 LTSis great for that, but it kept messing with the real clock, despite of the utc=no kernel boot parameter (it just ignore it). It was very annoying to put the hardware clock back to local time everytime after I booted Lubuntu.
So, I decided to make a customized live cd, just for my personal use. I changed the monitor resolution, added restricted extras, another web browser, installed a printer, and few things more.
My customized live cd boots, but I can't get beyond the greeter login.
I put my username and password, the greeters accepts it (there is no a red line saying wrong password), but instead of access to my destops it returns to the greeter and keeps asking for my username and password again and again for ever.
I miss the Kubuntu style greeter, where the username field is allready filled with my username and I just have to put the password.
I will be the only user of this customized live cd, but I want to keep the option to close session and switch user, in order to clear memory and update the user inteface, but **is there a way to get rid of the greeter login **and access directly to the desktop?

2-Another question:
I can succesfully install a printer in live Lubuntu 16.04 LTS, and it works fine. But few minutes after printing, **Lubuntu forgets that it has a printer installed**, and I must turn the printer off and on again in order to make it appear. it is very annoying.

Any ideas?
Best regards.

---

### Post by Bucky Ball on 2017-05-01
Welcome. Just a tip. Get rid of the printer question and post it in Hardware. Modus operandi is one question per thread here. Lot less confusing. :)

How exactly did you make this customised CD? That would help and I'm certainly curious ...

---

### Post by russed2 on 2017-05-01
Ok, thank you.
I used CUBIC, (Custom Ubuntu Iso Creator), to make my customized live cd. It is a simple python script, very well done, easy to use.

---

### Post by russed2 on 2017-05-01
Okay.
To be more specific, I think that, in order to reproduce the error, you must follow these steps:

1- Boot Lubuntu 16.04 live cd.
2- Install Cubic.
3- Close session and or switch user to yourself.
4- Run Cubic.
5- When Cubic pauses to allow you make your modifications and customization, you copy your root filesystem into cubic's squashfs-root.
6- Allow Cubic continue. You beter spare enough disk space, at least 5 Gb, for cubic's working folder, prefearibly on a linux partition, or else, if it's mksquashfs command runs out of disk space, it will continue forever, without giving you not even an error message or hint.
7- Once cubic finishes your customized live cd, boot it.

I think the key is in step 3.
I wanted numlock on at boot, and a customized background image in the greeter login screen, so I followed the instrucctions in [http://manpages.ubuntu.com/manpages/precise/en/man1/lxdm.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/lxdm.1.html). I created my customized bacground image in the same folder than the original, with the same file extension and resolution, and similar size. Then I modified the right lines in the file /etc/xdg/lubuntu/lxdm/lxdm.conf, and then I closed session and or switched user to myself several times to see if it worked. It never did, no matter how much I tried.
I still don't figure out how to do this, I mean, get numkey on at boot and a a customized background image in the greeter login screen. I will also need your help for that.

---

### Post by russed2 on 2017-05-01
By the way, I didn't copied the entire root filesystem into cubic's squashfs-root in step 5. I excluded some folders with this command:

sudo rsync -av --one-file-system --exclude=/proc/* --exclude=/dev/* \
--exclude=/sys/* --exclude=/tmp/* --exclude=/home/* --exclude=/lost+found \
--exclude=/var/tmp/*  --exclude=/isodevice/*  --exclude=/media/lubuntu/* --exclude=/boot/grub/* --exclude=/root/* \
--exclude=/var/mail/* --exclude=/var/spool/* --exclude=/media/* \
--exclude=/etc/fstab --exclude=/etc/mtab --exclude=/etc/hosts \
--exclude=/etc/timezone --exclude=/etc/shadow* --exclude=/etc/gshadow* \
--exclude=/etc/X11/xorg.conf* --exclude=/etc/gdm/custom.conf \
--exclude=/etc/lightdm/lightdm.conf /cubic/squashfs-root

I think I shouldn't have to exclude the /tmp folder, because I think it is in some way related to the greeter login in the live cd, because I remember that, in previous unsuccesful tries, when I deleted /tmp/* (after sudo apt-get clean, after installing some packages), after I closed session and or switched user to myself, I was unable to sudo, because Lubuntu asked something like «who are you», user 999.

---

### Post by yetimon_64 on 2017-05-01
> **russed2 said:**
> Hi.
1- I wanted a live cd to testing stuff, and Lubuntu 16.04 LTSis great for that, but it kept messing with the real clock, despite of the utc=no kernel boot parameter (it just ignore it)....

Edit as root the file "/etc/default/rcS" and change "UTC=yes" to "UTC=no" and reboot. _*No need to set any boot parameters for that change normally*_, just editing the "default" file for rcS will do the change you want. To edit the file you can use the next command ...
```
sudo -H leafpad /etc/default/rcS
``` and change the value for UTC to "no", save and reboot.
**Edit: **I am not sure of the correct editor in use in lubuntu, I use ubuntu and gedit; check which editor is standard on lubuntu before using the command above.

> ...kernel boot parameter (it just ignore it)...
Just a side note, if you set a boot parameter in /etc/default/grub you need to run "sudo update-grub' before any changes take place, even if the file is saved and a reboot occurs no change will happen until you run the update-grub command.

---

### Post by russed2 on 2017-05-02
> **yetimon_64 said:**
> Edit as root the file "/etc/default/rcS" and change "UTC=yes" to "UTC=no" and reboot. 
Thank you, Yetimon, but Lubuntu is not installed. I'm using the live cd version in order to not mess my installation with my tests. So, if I reboot I'm again in the same place. I modify the file rcS, with leafpad, Lubuntu's default text editor, but it hasn't any effect. The only way to make it work is to customize the live cd and boot it.

> Just a side note, if you set a boot parameter in /etc/default/grub you need to run "sudo update-grub' before any changes take place, even if the file is saved and a reboot occurs no change will happen until you run the update-grub command.
Same case. When I reboot I'm again in the same place, unless I boot a customized live cd.

---

### Post by Bucky Ball on 2017-05-02
If you're running a live session, any changes you make during a live session will be lost on reboot. The 'Try Ubuntu' live session is intended for trying Ubuntu, not for modifying or tweaking it. Sure, experiment, but when you reboot, the experiment is over.

---

