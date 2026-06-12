---
title: "Ubuntu does not shutdown or reboot"
date: 2015-06-27
forum: New to Ubuntu
---

### Post by balthazar.flechell on 2015-06-27
Hi all,
I post this here because I have no idea where I should post it…
I have recently installed Ubuntu 15.04 32 bits on a recently bought computer : an Aspire E5 411 C5RZ. I am having no problems with the install, except for the restart / shutdown.
On shutdown, the splash just hangs on, the screen is still on, as well as the fans, but I can't access the ttys, look to the shutdown logs (pressing escape), etc.
When restarting, it is the same, but this time, the screen is turned off at the end of the process.
In both cases, using "sudo shutdown -P now", "sudo reboot", or "sudo poweroff" ends up the same (as well as all the variants I've tried).

I have seen numerous solutions proposed on the web, but it looks like it can be caused by a lot of possibilities (processes not killed, bad grub configuration, etc.), and among everything I've tried, nothing has worked for the moment.
I have tried :
[LIST]
[*]disable quiet splash in the kernel options in order to see whether there was problems during the shutdown (or press ESC during the splash screen). I don't see anything suspect, and it ends up with "Reached target shutdown" after several items.
[*]adding options to the kernel with /etc/default/grub (I have tried adding "acpi=force apm=power_off", "reboot=bios" or "reboot=dell" (there is currently the option acpi=off in order to boot well (I can't usually boot any live CD without this, and the installed ubuntu does boot sometimes, but not everytime if it is not there), so I tried each of the different options with and without "acpi=off"). There was also something about the modules apm and power_off=1 in /etc/modules, but there is no module specified here, and when I add these lines, there is errors during the boot (Error : kernel failed to load modules or something like that).
[/LIST]
So far, I don't know what is really the problem, and thus don't know how to fix it…
Thank you very much,

Balthazar Fléchelles

P.S. : I have also tried a Boot-repair, and generated a BootInfo report you can see at : [http://paste.ubuntu.com/11782324/](http://paste.ubuntu.com/11782324/).

---

### Post by dino99 on 2015-06-27
with one of my system i had such a issue, and i finally found that the bios was using 'auto' to set the ram voltage. In fact the voltage set was too low, so i switch to 'manual' cpu frequency, that unlock the ram voltage which i set to 'manual' with the required voltage. Then the problem was gone.
your system is recent, so it might better work with the latest kernel (4.1) and you need to know about all the message during 'shutdown' process (it might wait for something that never happen); so here is what i propose:
 > sudo update-pciids
 sudo update-usbids
 sudo mkdir /var/log/journal
this will create the 'journal' folder where every message will be added and be viewable with the command 'journalctl' (so you need to empty it when you want to remove the oldest messages; or remove that folder to switch back to the default 'journalctl' inside ram)

---

### Post by llamabr on 2015-06-27
```
"sudo shutdown -P now"
```
-P halts action.  Try:
```
sudo shutdown -h now
```
and then report back what happens.

---

### Post by balthazar.flechell on 2015-06-30
Thank you very much for your answers, but I will not be able to do what you advised me to do for 2 reasons : I don't have a stable internet connection for the moment (can't install linux kernel 4.1, or anything else, and can barely answer you today !), and when I'll have one, I won't have access to the computer in trouble anymore&#8230; I think it is enough to give up there&#8230;
May I ask you how to close a thread ?
Thank you,

Balthazar Fléchelles

---

### Post by dino99 on 2015-06-30
> **balthazar.flechell said:**
> 
May I ask you how to close a thread ?
Thank you,

Balthazar Fléchelles

from your first post, click on 'thread tools' on the top right corner, and select 'SOLVED'

---

### Post by cariboo on 2015-07-01
I would not recommend marking the thread as solved, as obviously it isn't, instead click the Report Post, and request the thread be closed.

---

### Post by eggzenbeanz on 2015-09-15
Hi - I have the same problem of server 15.04 getting stuck at "shutdown target reached" - the same happens if I use "reboot" "shutdown -h now" "shutdown -P now" - I cannot then interact with the terminal or send any further commands, I need to physically power off at the device.

Any ideas?

---

