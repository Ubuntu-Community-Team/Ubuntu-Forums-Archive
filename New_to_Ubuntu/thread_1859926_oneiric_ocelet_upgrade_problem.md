---
title: "oneiric ocelet upgrade problem"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by krishnan t s k on 2011-10-14
hi :)
today i upgraded to the latest version of lubuntu and upgrade went fine upto restart
upon restart, my age old laptop started blinking the lubuntu screen for 25 seconds approx then it went blank..... i waited for 5 minutes to see if it would ever show anything but nothing happened.... i manually rebooted thrice and met with the same problem..... then on my fourth manual reboot, the grub bootloader came up and i chose ubuntu linux 3.00.12(or something to that effect if i remember correctly) recovery mode and voila it booted properly though the login dm was light dm.....during upgrade, i had chosen the default dm as lxde but it now its booting to light dm..... and i found that lubuntu loads only under recovery mode and not under normal boot..... is it a bug or a bigger problem??
i also use xubuntu and that too works under the recovery mode
i use an old toshiba laptop which my sister was previously using....its p3 512 gb ram if it helps :) :)
thanks in advance :) :)

---

### Post by drs305 on 2011-10-14
I was experimenting with Lubuntu on a very old laptop last week and found that I solved the totally blank screen by removing "quiet splash" and adding "nomodeset" to the kernel options. Previously I'd only needed to use this option with uninstalled video cards.

If you want to try this, at the Grub menu press 'e' to edit the menuentry, then cursor to the 'linux' line, remove 'quiet splash', add 'nomodeset' and press CTRL-x to see if it works. This is a test - the change is not persistent.

---

### Post by krishnan t s k on 2011-10-17
thank you very much for this..... it worked for me but as you said, the change is not persistent...on my next reboot, it goes back to quiet splash which is quiet annoying as i have to bring grub up again....lubuntu has of course brought my sisters old toshiba laptop back to life where windows xp couldn't in the first place
cheers!!! :) :)

---

### Post by drs305 on 2011-10-17
> **krishnan t s k said:**
> thank you very much for this..... it worked for me but as you said, the change is not persistent...on my next reboot, it goes back to quiet splash which is quiet annoying as i have to bring grub up again....lubuntu has of course brought my sisters old toshiba laptop back to life where windows xp couldn't in the first place
cheers!!! :) :)

We can make the menu change permanent since we now know it works, but there is a better option.

Using the 'nomodeset' option prevents certain modules from loading. The next step is to see if there is a video driver which will resolve the issue. Once booted (using the manual 'nomodeset' edit if necessary), click the Home/Dash icon (upper left) and start typing 'Additional Drivers'. Click on the 'Additional Drivers' icon. Hopefully it will find a video driver for your system. If it does and successfully installs you will probably be able to boot without editing the menu.

If the system doesn't find any driver, we can make a permanent menuentry with the 'nomodeset' option so you don't have to manually type it in each time. If this becomes necessary, please post the contents of the menuentry you are using in your /boot/grub/grub.cfg file. If it is the first (top) entry, you can get it by running this command:
```
grep -A12 --max-count=1 'menuentry' /boot/grub/grub.cfg
```

---

