---
title: "Ubuntu 12.10 shows desktop screen and nothing else"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by cbierman on 2013-01-30
Hello! Everything was working fine until this afternoon. After I log in, all I get is my background image. No bar at the top, no launcher.

It's also worth noting it happened after I booted up Windows 7 again for the first time since installing ubuntu. It performed some kind of memory check before booting.

---

### Post by DuckHook on 2013-01-31
This could be caused by a number of items, but let's cover off the simple things first:

To bring up a terminal in the blank desktop, do:

```
<Alt>+<Ctrl>+<t>
```in the terminal, type:

```
ccsm
```If the system tells you that CCSM is not installed, do:

```
sudo apt-get install compizconfig-settings-manager
```after it successfully installs, then do:

```
ccsm
```This will bring up the CompizConfig Settings Manager. Find "Ubuntu Unity Plugin" under the "Desktop" collection and click on it.

Make sure that the checkbox for "Enable Ubuntu Unity Plugin" is checked. If it was already checked, then the problem of the missing desktop is elsewhere. If it was *not* checked (and you have now turned it on), then close CompizConfig Settings Manager and type into the terminal:

```
sudo shutdown -r now
```to reboot.

Let us know how it goes.

---

### Post by JawadHussain on 2013-01-31
i am also having the similar problem, followed the above mentioned steps and everything goes fine except that i am unable to get icons, launcher and all other things.... now it is also not showing anything when I make a right click with my mouse... I am using ubuntu 12.10 and it is installed on VMware 7.0.1...... please help me

---

### Post by scrumpypaul on 2013-01-31
I have also tried this but still no icons launcher or toolbar and no right mouse action.

---

### Post by bogan on 2013-01-31
Hi!,** all,**

Try: ```
sudo apt-get install linux-headers-generic
```If it says 'already the latest version' the problem has another cause: If installs it then run:```
apt-get remove --purge < your video driver package name> # and reinstall:
apt-get install < your video driver package name>
reboot
```You do not say what you are running, Please Post: ```
uname -r
lspci -nnk | grep -iA3 vga
```Chao!, **bogan**.

---

### Post by UbeuIbeMe on 2013-01-31
Hello, I've installed 12.10 on 2 machines and both times the desktop simply shows the background picture and nothing else.  No icons, no bar, nada - just the picture.  

I can get to ccsm and the suggestion is to turn on Ubuntu Unity Plugin on the desktop menu - when I click on it, it is enabled, however, there's no check mark like the other icons.

I'm a complete noob to this and would like to try Ubuntu.

---

### Post by DuckHook on 2013-01-31
Unity Plugin is usually enabled by default after installation. However, when a glitch occurs, and it becomes disabled, its mere presence in the CompizConfig Settings Manager does not mean that it is thereby enabled. You must click on the "Ubuntu Unity Plugin" icon. This opens up a further dialogue box. On the left panel of the dialogue box, close to the bottom, there is a label in orange lettering: "Use This Plugin". Under these letters is a checkbox: "Enable Ubuntu Unity Plugin". It is *this* checkbox that must have a checkmark in it. Repeat: you will *not* see this checkbox in the top-level CompizConfig Settings Manager window. You must drill down further.

---

### Post by scrumpypaul on 2013-02-01
I eventually decided to try 12.04, but it was very slow. Instead I've put Lubuntu on a couple of old machines and that is working fine.

---

