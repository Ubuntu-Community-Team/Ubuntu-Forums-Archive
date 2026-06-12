---
title: "Boot to text-only runlevel fails"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by Chiel92 on 2012-01-05
Hi all,

I'm experiencing troubles with booting to a text only runlevel.
I'm running ubuntu 10.04 and tried the following:

I changed in /etc/init/rc-sysinit.conf

```
env DEFAULT_RUNLEVEL=2
```into

```
env DEFAULT_RUNLEVEL=3
```.

I also changed in /etc/init/gdm.conf

```
stop on runlevel [016]
```into

```
stop on runlevel [0136]
```.

For some reason I do not know it doesn't work.
It just boots and starts a Gnome session, as if nothing changed.

```
runlevel

```returns

```
N 3
```Can anyone help?

Thanks in advance!

---

### Post by VCoolio on 2012-01-05
[http://ubuntuforums.org/showthread.php?p=10930539#post10930539](http://ubuntuforums.org/showthread.php?p=10930539#post10930539), second post, change that in /etc/default/grub, then sudo update-grub and reboot

---

### Post by JKyleOKC on 2012-01-05
+1 to changing the Grub default option.

In addition, Ubuntu and all Debian-based distros do **NOT** follow the RedHat standard runlevels where 3=CLI and 5=GUI. Instead, they default to runlevel 2, and 2 through 5 are all the same.

Since the introduction of upstart for controlling the boot sequence, runlevels actually are essentially meaningless to these distributions -- yet few, if any, guides to generic Linux ever mention that fact!

---

### Post by Chiel92 on 2012-01-06
Thanks for your replies!

> **VCoolio said:**
> [http://ubuntuforums.org/showthread.php?p=10930539#post10930539](http://ubuntuforums.org/showthread.php?p=10930539#post10930539), second post, change that in /etc/default/grub, then sudo update-grub and reboot
Does this method not cause my system to always boot into text-only?
I actually want to have a choice.
So I thought to create a text-only runlevel, using a non-used runlevel (I choose 3, because that is historically the text-only runlevel).
There I got already stuck, because it seems that gdm is still started, in spite of my modifications in /etc/init/gdm.conf.

(My next step would  be trying to mod a script somewhere such that I always boot into GUI - runlevel 2, unless I press a certain key (shift or something). In the latter case I want the script to boot into textonly - runlevel 3.)

But the problem is that I fail to even create a textonly runlevel.

> In addition, Ubuntu and all Debian-based distros do **NOT** follow  the RedHat standard runlevels where 3=CLI and 5=GUI. Instead, they  default to runlevel 2, and 2 through 5 are all the same.

Since the introduction of upstart for controlling the boot sequence,  runlevels actually are essentially meaningless to these distributions --  yet few, if any, guides to generic Linux ever mention that fact!


I know that Upstart is a different boot approach than most other distro's. But according to this [http://askubuntu.com/questions/22498/how-to-auto-boot-into-text-mode](http://askubuntu.com/questions/22498/how-to-auto-boot-into-text-mode) guide, modifying /etc/init/gdm.conf should be fine.

Do I overlook something? Or am I doing something completely wrong?

Thanks in advance for any help!

---

### Post by JKyleOKC on 2012-01-06
> **Chiel92 said:**
> I know that Upstart is a different boot approach than most other distro's. But according to this [http://askubuntu.com/questions/22498/how-to-auto-boot-into-text-mode](http://askubuntu.com/questions/22498/how-to-auto-boot-into-text-mode) guide, modifying /etc/init/gdm.conf should be fine.

Do I overlook something? Or am I doing something completely wrong?While I've not tested this idea, my not-fully-confident understanding of Upstart's actions suggests that you need to add another clause to the "start on" compound statement just in front of the "stop on" line of /etc/init/gdm.conf, to add "not 3" to the list of conditions. I'm not certain of the syntax for doing so though; you'll have to do some digging for the correct way of doing this.

An alternative would be to modify the grub default at boot time rather than in the file; at the grub menu, select the kernel you want but instead of hitting Enter, hit "e" to get into edit mode, then select the "linux" line, add " text" after "ro", and hit Ctrl-X to boot. I've done this when testing, and it works, but you may need to increase the grub delay time.

You could also add a new "menuentry" to the /boot/grub/grub.cfg file after the first one, and select from the grub menu, but you would have to do this after each kernel update because the file is automatically rewritten by update-grub. This approach would be the closest to what you're asking, but is also the riskiest because an error in grub.cfg can make the system unbootable.

Actually, if you change the grub defaults to always boot into CLI mode, you can then issue the "startx" command after logging in, which will give you the GUI. I operated in that manner for years before coming to Xubuntu! That's the simplest way of all...

EDIT: Try this syntax: change```
start on (filesystem
```to ```
start on (runlevel [!3] and filesystem
```Not tested but it may do the trick for you...

---

### Post by Chiel92 on 2012-01-06
Hey, thanks!
That worked!

---

