---
title: "GRUB does not show on start up but is working [and more]"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by klqd on 2012-07-21
Hi,
I know grub is working - when I press down seven times followed by the enter key I start in windows, if I just press enter then ubuntu. But it doesn't show in the screen.


Two other questions:
1. Is there a finite number of key presses that might get me into BIOS so I can install xubuntu on my other PC? What are they - I have tried a couple.
2. On this second PC I have a down key that gets stuck and I have to press up firmly a few times and then it works OK. I prized off the key but actually I can't reattach it. How easy is this problem with "down" to fix?

Thanks :popcorn:

---

### Post by drs305 on 2012-07-21
It sounds like you badly need a new keyboard!

Regarding GRUB, since you can (blindly) select the OS to boot, you may be able to get the display to work by changing one of the settings in the GRUB configuration file. 

Open this file as root:
```
gksu gedit /etc/default/grub
```

Uncomment (remove the # symbol) from this line:
> **[COLOR="Red"]#[/COLOR]**GRUB_GFXMODE=640x480
GRUB defaults to automatically selecting what it thinks is the best resolution for your computer's screen. Rarely this doesn't work. Removing the # symbol will force the computer to use the basic resolution of 640x480, which almost all computers should be able to use.

Save the file, then update the GRUB settings:
```
sudo update-grub
```

Reboot and see if the menu appears. If it doesn't, you can remove graphics entirely from the equation by editing the same file and uncommenting this line. Then follow the same procedure as before:
> **[COLOR="Red"]#[/COLOR]**GRUB_TERMINAL=console

---

### Post by klqd on 2012-07-21
that worked great, thanks :guitar:

---

### Post by drs305 on 2012-07-21
Glad it worked for you. If you don't have any other questions about this issue would you please mark the thread SOLVED via the 'Thread Tools' link near the top right of the first post.

Now, about replacing that keyboard ....   ;-)

Happy Ubuntu-ing !

---

### Post by klqd on 2012-07-21
ok... no help with bios though? the hard failed and was replaced and i've been unable to reinstall :)

---

### Post by drs305 on 2012-07-21
Entering the BIOS is normally accomplished by pressing one key (only) during the initial boot up (often just after the beep). The specific key depends on the manufacturer - it is often the DEL key or one of the function keys (F1-F12). Internet searches generally can help you find the key you need to press if you don't already know it.

If you still need help on the BIOS problem, it would be best to start a new thread since some helpers will know about BIOS issues but might not read a thread with 'GRUB' in the title. I'll monitor any new thread you start and post if I can help.

---

