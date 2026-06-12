---
title: "How to capture errors that appear on my screen while booting"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by bcstrawn on 2012-12-08
I recently installed Ubuntu to be dual-booted on a fresh drive. After finally getting an Nvidia driver working instead of nouveau, when booting, the Ubuntu booting logo looks a bit different, and at the point where it'd usually go to a login screen, it shows a lot of errors, all overlapping for a few seconds, and then the login screen appears. 

I edited /etc/default/bootlogd to turn on logging, and /var/log/boot.log has logged some info, but not the errors I saw. My boot.log file is here: [http://pastebin.com/MWbgfrrr.]("http://pastebin.com/MWbgfrrr")

---

### Post by Bucky Ball on 2012-12-08
Welcome to the forums. You might try looking at dmesg immediately after boot. Just put that in a terminal and check the output:

                ```
dmesg
```

---

### Post by bcstrawn on 2012-12-08
Thanks Bucky. I sent the output of dmesg to a file, and it's way bigger than the errors I saw on screen when booting. I'm not sure where to start when diagnosing what's causing them. The file is here: [http://pastebin.com/vXrhi3U7](http://pastebin.com/vXrhi3U7).

Also, after booting just now, Ubuntu said it encountered an error and if I wanted to report it, which I did. This is something I haven't seen before. I'm not sure if the Nvidia driver is causing errors, of if it just changed my being able to see them.

---

### Post by Bashing-om on 2012-12-08
bcstrawn; Hi !

Here is what I have done to see my boot messages.
1. Edit /etc/defaulr/grub -> remove the terms "quiet splash" and in the line
#GRUB_GFXMODE=640x480
change it to:
GRUB_GFXMODE=text
Don't forget to update grub
```
sudo update-grub
```
2.  change in /etc/init/tty1.conf. By default the virtual console logins clear the screen when they start; on tty1, this has the effect of erasing the last screen's worth of boot-time messages. To tell getty not to do this, we add --noclear to the exec line:
```
    exec /sbin/getty --noclear -8 38400 tty1
```2a. grub kernel to boot-> "e" to edit -> kernel boot line add "text' without the quotes;
ctl-x to boot to command line; log in then:```
sudo start lightdm
``` -> ctl-alt-f7 to go to the GUI ; ctl-alt-f1 return to console: ```
sudo stop lightdm
``` -> ctl-alt-f7 and on this screen is all the boot messages !
3.```
sudo service lightdm restart 2> ~/Desktop/errors.txt
``` will give you a text file of the lightdm startup messages.

finally if you think it is a graphics driver issue look also into the following files.
/var/log/Xorg.0.log and in your home directory, enable hidden files (ctl-h), and look at .xsession-errors.[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by ibjsb4 on 2012-12-08
Maybe this

[http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925)

---

