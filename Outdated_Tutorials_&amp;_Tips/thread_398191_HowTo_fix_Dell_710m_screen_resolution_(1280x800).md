---
title: "HowTo: fix Dell 710m screen resolution (1280x800)"
date: 2007-03-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Thisbetom on 2007-03-31
Hey,

I spent many an hour browsing through the forums and finding several dead end posts that got me halfway through changing the screen resolution on my Dell 710m (Intel graphics card I believe).  I thought it would be helpful to have a quick post for what worked for me as it seems I'm not the only one having trouble fixing it.

(Note to mods.  New to the forum & Ubuntu.  If this is not within guidelines, please email me and I will modify it. - Thanks, Tom)

1. Make sure your system is up to date (System > Administration > Update Manager)

2. Open the terminal (Applications > Accessories > Terminal) and enter the following command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

3. Select the i810 driver from the list by clicking the space bar while it is highlighted.

4. Select the 1280x800 option on the next menu by clicking the spacebar on it.

5.  Open Synaptic Package Manager. (System > Administration > Synaptic Package Manager)

6.  Search for "915resolution".  Install it.

7. Open the terminal (Applications > Accessories > Terminal)

8. Enter the following code:
```
cd /etc/init.d/
```
```
sudo 915resolution -l
```

9. The code should produce the following output:
Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x768, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x768, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x768, 32 bits/pixel

10. Overwrite a mode you do not by using the following code syntax:
915resolution {mode number} {width} {height} {Optional: bits/pixel}
For example: I overwrote Mode 38 (1280x1024) by typing the following into the terminal
```
sudo 915resolution 38 1280 800
```

11. Make sure the changes went through
```
sudo 915resolution -l
```
output should now be:
Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x800, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x800, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x800, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
Mode 7c : 1280x800, 8 bits/pixel
Mode 7d : 1280x800, 16 bits/pixel
Mode 7e : 1280x800, 32 bits/pixel

12. You have to now modify your code to run everytime you boot.  To do this type: ```
cp bootmisc.sh bootmisc.sh_BACKUP
```
```
gksudo gedit bootmisc.sh
```

13. Insert the following line: "/etc/init.d/915resolution 38 1280 800" between the comments and PATH statement so your top ~15 lines look like this:
```
#!/bin/sh
### BEGIN INIT INFO
# Provides:          bootmisc
# Required-Start:    $local_fs hostname $remote_fs
# Required-Stop:     $local_fs
# Default-Start:     S
# Default-Stop:
# Short-Description: Miscellaneous things to be done during bootup.
# Description:
### END INIT INFO

/etc/init.d/915resolution 38 1280 800

PATH=/usr/sbin:/usr/bin:/sbin:/bin
[ "$DELAYLOGIN" ] || DELAYLOGIN=yes
. /lib/init/vars.sh
```

14. That should take care of it.  Click the shutdown button up top and restart your computer.  Once restarted, goto System > Preferences > Screen Resolution and 1280x800 should appear in the dropdown menu.  Check the "make this my default" and you should be good.

(Big credit to the writer of the 915resolution package along and the ReadMe.txt found on his site ([http://www.geocities.com/stomljen/)](http://www.geocities.com/stomljen/))... Also to the community... And I couldn't find it on my second attempt to fix the screen resolution, but the first time I tried to fix it, I used this FAQ ([http://users.skynet.be/thomasvst/linux-on-laptop/#wide)](http://users.skynet.be/thomasvst/linux-on-laptop/#wide)))

Thanks again,
-Tom

---

### Post by aysiu on 2007-03-31
Thanks for that HowTo. I've moved it to Tutorials & Tips to help future 700m users.

There is also another tutorial on the Wiki that advises using the 855resolution package. More info here:
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell)

---

### Post by jweila01 on 2007-03-31
Interesting but all I had to do was install the 915 resolution driver, restart X, and my machine restarted in 1280x800 mode. Guess I was lucky.

---

### Post by bekirserifoglu on 2007-04-05
i had this problem. but your solution didnt work for me. when i reboot it returns to its old resolution again.????

---

