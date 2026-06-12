---
title: "screen brightness level"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by syednasirraza on 2012-11-18
everytime i swtich on my laptop, its brightness is at lowest level...i change it as i m attaching clip to show in system settings,, but every other time after restart, i find brightness at lowest level... why my changes are not perstistent???how to do it???

---

### Post by Toz on 2012-11-18
What is the make and model of your laptop?

What video card and driver do you have? Open a terminal window, type in the following command, and post back the results:
```
sudo lspci -vnn | grep -A10 VGA
```

Perhaps this thread might help: [http://ubuntuforums.org/showthread.php?t=1972303&highlight=screen+Brightness+ste+0%25]("http://ubuntuforums.org/showthread.php?t=1972303&highlight=screen+Brightness+ste+0%25").

---

### Post by Calinou on 2012-11-18
In a terminal:

```
gksudo gedit /etc/rc.local
```

Put this line before the "exit 0" line:
```
echo 10 > /sys/class/backlight/acpi_video0/brightness
```

Save, reboot and see. Note that 10 means full brightness.

---

### Post by syednasirraza on 2012-11-19
> **calinou said:**
> 

```
gksudo gedit /etc/rc.local
```put this line before the "exit 0" line:
```
echo 10 > /sys/class/backlight/acpi_video0/brightness
``` .

it worked...thanks dear

---

### Post by sperovic on 2013-02-01
I'd just like to point out that people trying to fix this should check the path provided because on some other forum/topic they said intel_backlight, but on my system it says acpi_video0. Just a heads up for people less skilled, who are looking for quick fix. And it works, yes. Sorted out mine at least :)

---

