---
title: "[SOLVED] Load Screens Gone?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by melrom on 2008-05-29
Hi- I used this tutorial:

[http://www.myscienceisbetter.info/2008/04/configure-broadcom-wireless-using-compat-wireless.html](http://www.myscienceisbetter.info/2008/04/configure-broadcom-wireless-using-compat-wireless.html)

to try to configure the Wireless in my computer. It said to reboot afterward but for some reason, restart doesn't work [it needs to be manually shut off now] and there is no load screen when I'm waiting for the login screen [i.e. when it usually says Ubuntu and has the orange bar thing].

Please help!

---

### Post by shifty_powers on 2008-05-29
is it that restart doesn't work, or your actual gnome start button is unresponsive, (i.e. the one in the right corner... well of my screen at any rate :D)

---

### Post by ibuclaw on 2008-05-30
When you go to power off, press "**Ctrl+Alt+F1**" to show the shutdown messages. If it hangs at a certain point, you'll be able to find out exactly what it is doing when it hangs.

If you write down the last few lines and post it on the forum, that would prove helpful for us helpers to try and debug your system.





> **shifty_powers said:**
> is it that restart doesn't work, or your actual gnome start button is unresponsive, (i.e. the one in the right corner... well of my screen at any rate)
Nope, I'm sure that she means the bootsplash... (The Words "Ubuntu" and "Big Orange Bar" kind of give it away).

This I can't really explain as such.
What is your kernel version?
If you've recently upgraded to the 2.6.24-17 kernel, perhaps you should try to downgrade it back to the 2.6.24-16 one...

But anyway, two checks that you can make though, are:
1) Open up a terminal and type in:
```
cat /boot/grub/menu.lst | grep "vmlinuz-$(uname -r)"
```
You should get two lines printed.
The first should end with "**ro quiet splash**" and the other with "**ro single**"

2) Check that the usplash.conf file exists and has a size greater than zero.
```
test -s /etc/usplash.conf && echo YES || echo NO
```
You should get **YES** as an answer.
Though, just for paranoia's sake. You should also cat the file, just incase...
```
cat /etc/usplash.conf
```
And you should get an output like this:
> 
# Usplash configuration file
xres=640
yres=480

If they both check out, then there is no obvious reason for there to be no bootsplash at startup...





And lastly, you should never really have to hard-poweroff the computer yourself.

For the moment, you should use the [Magic SysRq Functions]("http://ubuntuforums.org/showthread.php?t=617349"), as that will provide a safer way to bootdown.

In sequence, press
```

Alt+PrintScreen+R
Alt+PrintScreen+S
Alt+PrintScreen+E
Alt+PrintScreen+I
Alt+PrintScreen+U
Alt+PrintScreen+O

```
Or at the very least, the sequence **R I U O**.

Regards
Iain

---

### Post by melrom on 2008-05-30
thanks so much. that was exceptionally helpful. :)

---

