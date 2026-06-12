---
title: "Laptop freezes at startup"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by cwrann on 2008-05-05
I have just upgraded my laptop to Heron in xubuntu now the computer hangs at:
```
running local boot scripts (/etc/rc.local)
```

I have tried upgrading in add/remove, I have tried the live cd and I have tried the alternate cd. I have no internet connection on this machine.

I should also note that the screen "blinks" black a couple of times when the "running local boot scripts first" comes up and then it simply hangs.

---

### Post by Trail on 2008-05-05
The screen blinking suggests to me it might be an X issue.

Can you login successfully through the recovery mode?

And, taking a wild guess here, is that there is some graphics driver issue. You could check Xorg's logs to see potential errors (located at /var/log/Xorg.0.log). If you think that might be the case, try ```

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
```
through the recovery console, then accept all defaults (make sure you select correct resolutions), then reboot.

---

### Post by cwrann on 2008-05-05
in rescue mode:

```
sudo dpkg-reconfigure xserver-xorg

unknown terminal: bterm
check the TERM environment variable.
Also make sure that the terminal is defined in the terminfo database.
Alternativley, set the TERMCAP environment variable to the desired termcap entry.
debconf: whiptail output to the above errors, giving up!
sh-3.1#
received signal. aborting xserver-xorg package config script
```

Any ideas on what this problem is and how to resolve it will be greatly appreciated.

---

### Post by cwrann on 2008-05-05
I'm sorry, you wanted mr to do recovery mode from the hdd not from the cd. 
When I try to do recovery mode the boot hangs at 

```
nm256: Mapping port 1 from 0x2709a0 - ox27ec00
```

---

