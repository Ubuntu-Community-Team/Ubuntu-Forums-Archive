---
title: "How-to: Hibernate by closing the lid [NEWBIE-FRIENDLY]"
date: 2007-07-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Majorix on 2007-07-27
Closing the laptop lid didn't do anything by me before. I set the laptop to hibernate if the lid is closed, but like I said nothing would happen: I had to close the lid back up and close it again for hibernation to work. Now I invented a fix for it and wanted to share with you as I have never seen this kind of info anywhere. Hope it helps. If not don't kill me ok? :D

**1. Install the necessary tool.**

You will need uswsusp if its not installed. You can install it by typing this in a terminal:
```
sudo apt-get install uswsusp
```

**2. Backup the files to be edited.**

Its recommended that you backup the file before you edit it. If anything goes wrong, look at the end of this post on info how to replace it.
```
sudo cp /etc/acpi/hibernate.sh /etc/acpi/hibernate.sh.bkp
```

**3. Edit the file.**

Now is the time we actually change the necessary stuff.
```
sudo gedit /etc/acpi/hibernate.sh
```

Find the part that says this:
[PHP]if [ -x /sbin/s2disk ]; then
    DEVICE="/dev/disk/by-uuid/`awk -F= '{print $3}' </etc/initramfs-tools/conf.d/resume`"
    if [ -f /etc/usplash.conf ]; then
	. /etc/usplash.conf
	/sbin/s2disk -x "$xres" -y "$yres" $DEVICE
    else
	/sbin/s2disk $DEVICE
    fi
else
    echo -n "disk" >/sys/power/state
fi[/PHP]

Replace with:
[PHP]if [ -x /sbin/s2disk ]; then
    DEVICE="/dev/disk/by-uuid/`awk -F= '{print $3}' </etc/initramfs-tools/conf.d/resume`"
	/sbin/s2disk $DEVICE
else
    echo -n "disk" >/sys/power/state
fi[/PHP]

**4. Close the lid.**

You don't have to log out first or anything.

If the computer hibernates now without any problems, it means that you did it! Congrats!




**IF ANYTHING GOES WRONG:**

Replace the edited file with the original one using this command in a terminal:
```
sudo cp /etc/acpi/hibernate.sh.bkp /etc/acpi/hibernate.sh
```




HAVE FUN!

---

### Post by small_bigguy on 2007-08-04
Nice, Thanks although my system say's not enough swap space left to hibernate but il fix that soon :D

---

### Post by scholzilla on 2007-08-07
Works great for me on my Gateway MT-something running Feisty.

Thanks!!

---

### Post by arje on 2007-08-25
didn't work for me. s2disk is writing the image to disk when i choose hibernate from the shutdown panel and that's it, next time i start the machine i get a normal boot.

closing the lid doesn't do anything at all.

any help would be very welcome!!!

---

### Post by Majorix on 2007-09-01
I found a much easier way to fix it now: Wait for Gutsy or switch to alpha of it if you can't wait.

---

