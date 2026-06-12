---
title: "Mutliple problems/questions."
date: 2008-07-24
forum: New to Ubuntu
---

### Post by lopolop on 2008-07-24
Well I installed Ubuntu yesterday after reformatting my Windows computer. It seems to be going alright, I have a few problems but nothing I can't live with(At least for the time being :D.)

     Anyways my first problem is I can't shutdown my computer, I goto system > Quit... Then log out. I get to like shutting down network stuff and then hault! So I end up holding my power button for a few seconds.

     I had a lot of music that I transferred from my laptop(What I have Ubuntu on.) too my computer via my network. But now I can't access it on Ubuntu I goto Places > Network and I see Windows Networks, inside that is Work group and MS Home but both of them are empty.

     I want to change my theme, I downloaded a GTK theme but I don't have an option to choose from through System > Preferences > Theme. Theme isn't there.

     I have one other question, I saw a post on using two monitors but I didn't understand, but I would like use dual monitors like I had in Windows.

Okay well that is less question then I though XD. But any help would be great thanks!

---

### Post by Potatoj316 on 2008-07-24
Try System -> Prefrences -> Apearance

---

### Post by iDaniel on 2008-07-24
> **Potatoj316 said:**
> Try System -> Prefrences -> Apearance

And if you downloaded the theme you're going to have to install it (lower right-hand button) before you'll see it in the menu.

---

### Post by lopolop on 2008-07-24
Okay thanks it worked!

---

### Post by unutbu on 2008-07-24
lopolop, regarding the shutdown problem: do you use any special kernel options to get your machine to boot?

If you are unsure, please post

```
cat /proc/cmdline 
```

---

### Post by lopolop on 2008-07-24
Well for some reason, I guess that was another problem... I don't get a boot screen anymore because the first time I loged into Ubuntu I was doing something I don't remember anything major but it froze, but I log in and do Startx.
But I did that and got.
```

john@john-laptop:~$ cat /proc/cmdline
root=UUID=f367e654-d213-47c2-8d78-f015eafbf457 ro quiet splash

```

---

### Post by unutbu on 2008-07-24
Well, no promises (more likely than not I won't be able to find what's wrong), but if you run
```

bzip2 -c /var/log/messages > messages.bz2
bzip2 -c /var/log/syslog > syslog.bz2
dmesg | bzip2 -c > dmesg.bz2
```

and post messages.bz2, syslog.bz2 and dmesg.bz2 as attachments I'll take a look.

---

### Post by lopolop on 2008-07-24
Okay thanks a lot for the help. I'm going away for the weekend, leaving tonight but here are the files.

---

### Post by unutbu on 2008-07-24
First order of business: Try not to power off your machine by holding in the power button unless you have to. Especially try not to power off if you hear disk activity. It can lead to a corrupted filesystem. Next time you need to power off, try this:
```

Alt-SysRq-R  turns off keyboard raw mode and sets it to XLATE
Alt-SysRq-E  send a SIGTERM to all processes, except for init.
Alt-SysRq-I  send a SIGKILL to all processes, except for init.
Alt-SysRq-S  attempt to sync all mounted filesystems.
Alt-SysRq-U  attempt to remount all mounted filesystems read-only.
Alt-SysRq-O  poweroff
or
Alt-SysRq-B  immediately reboot the system without syncing or unmounting
```

Wait a few seconds between each command, to allow the linux kernel to perform the operation.

----------------------------------------------------------------------
Secondly, note that messages.bz2 contained this:
> 
Jul 24 20:19:14 john-laptop kernel: [  123.700761] Clocksource tsc unstable (delta = -219370503 ns)

Run the following command:
```
sudo cat /sys/devices/system/clocksource/clocksource0/available_clocksource

```
You should see something like
```

tsc hpet acpi_pm jiffies 
```

Try booting kernel with "clocksource=hpet", or "clocksource=jiffies" or "clocksource=acpi_pm" -- anything but tsc.

To try temporarily booting with a kernel boot:
(1) Power on
(2) Press ESC to get to the GRUB menu
(3) Press 'e' to edit
(4) Use the down arrow to select the line that says "kernel"
(5) Press 'e' to edit
(6) Press End to go to the end of the kernel line. It should say something like
```

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro quiet splash

```
(7) Type in the kernel option so the line becomes

```
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro quiet splash clocksource=hpet

```
(8) Press return to finish editing the line
(9) Press 'b' to boot

GRUB will proceed with the booting processes, with your kernel option inserted. The effect will last only for the current session. Next time you reboot you'll have your regular kernel boot settings back, so if "clocksource=hpet" does not work for you, just reboot. If hpet doesn't work, try jiffies, then acpi_pm, and so on.

I don't know if this will help with the shutdown problem or not. It seems to have helped some others, however, so perhaps give it a try.

If by a stroke of amazing luck one of these kernel options does fix the shutdown problem, remember the option that works and I'll post instructions on how to make it permanent (by editing /boot/grub/menu.lst).

---

### Post by lopolop on 2008-07-31
Sorry about not replying, I messed something else up big time which led me to reinstalling Ubuntu which wasn't a big deal, but thanks a lot. But now I seem to have a different problem of random freezing, like I minimize Firefox and all I can do is open a shell through a Hotkey thing I setup and I can't click the desktop move the window or scroll up and down only type...

---

### Post by unutbu on 2008-07-31
Perhaps try booting, press ESC to get to the GRUB menu, and then select "memtest" (to do a memory test). 

When you install Ubuntu twice on the same machine from the same CD and get two different results, it suggests some piece of hardware (like possibly a memory chip) might be failing.

---

