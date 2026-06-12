---
title: "messages about acpi commands at boot up"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by barbex on 2008-07-29
Hi there!

When I shut down my computer a can see a glimpse of the messages that are left in the terminal from boot time. I can also see these messages when I switch to the virtual terminal with "Ctrl+Alt+F1". (Does anybody know in what log these messages are stored? I could not find it) I don't know how long they have been showing up and apart from that the systems runs just fine.

The messages all have to do with acpi support, I don't know how to copy them from the Terminal so I wrote things down:
```

/etc/rc2.d/s99acpi-support: line 7 No such file or directory
*Checking battery state
/etc/acpi/power.sh: line 4 No such file or directory
/etc/acpi/power.sh: line 36 getState: command not found
/etc/acpi/power.sh: line 38 get... [unsure]
/etc/acpi/start.d/60-asus-wireless-led.sh: line 2: usr/share/acpi-support/state-funcs: No such file or directory
/etc/acpi/start.d/60-asus-wireless-led.sh: line 3 [...] No such file or directory
/etc/acpi/start.d/60-asus-wireless-led.sh: line 6 [...] No such file or directory

```


I can't make sense of it. This is a desktop computer, I never fiddled around with power management and acpi. 

Where do the scripts get called and can I safely remove them?

I'm running ubuntu 7.10 with xfce 4.4

---

### Post by eightmillion on 2008-07-29
Try this command:
> sudo apt-get install --reinstall acpi-support
and reboot.

---

### Post by barbex on 2008-07-29
I tried that and dpkg failed because something was not configured and this and that... I had enough of this and I removed acpi completly.

That removed the error messages but now I see

Enabling laptop-mode .... [OK]


Why that? This isn't a laptop, should I install the acpi-tools again or is there another way to convince the system of it's "non-laptop-iness"??

Thanks for the help!

---

### Post by eightmillion on 2008-07-29
I would advise you to reinstall whatever you removed, and if you paste the error message here I can help you fix it.

---

### Post by phidia on 2008-07-29
In your case you may want to try adding > noapic to menu.lst
Read the thread [here]("http://ge.ubuntuforums.com/showthread.php?t=843053") and see if that's something you want to try-you can always un-edit if it doesn't help.

---

