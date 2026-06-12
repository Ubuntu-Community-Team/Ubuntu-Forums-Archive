---
title: "Installed Virtual Box - Now Ubuntu won't load properly"
date: 2014-05-30
forum: New to Ubuntu
---

### Post by Drowz0r on 2014-05-30
Hello all

I created this thread: [http://ubuntuforums.org/showthread.php?t=2209277](http://ubuntuforums.org/showthread.php?t=2209277)

I installed virtual box and now when I log in, the bar to the top and the unity launcher will not show. Also the tops to all my windows are missing. It would appear some plugins are not working too, like "open folder in terminal" etc. The only reason I can get firefox open is because an error comes up saying if I want to report a problem. If I check details there is a web link and from there I can use the address bar to come here.

P.S. the error is about virtualbox. It seems to be running on start up and disrupting my normal start up process. If I stop it or uninstall it some how that might fix it.

There is a kind of command line option there where I tried "sudo apt-get remove virtualbox" but it just keeps throwing errors something along the line of there being no such thing as a remove command.

It was a standard .deb install from a legit source too.

I have tried to run Ubuntu from the CD, and access the HDD. I was able to change permissions to allow me to delete stuff. I deleted the VM folder in my Home folder and ran sudo apt-get purge virtualbox and some files were removed.

Boot back into my HDD and there is absolutely no change.

How can I fix this? I cannot get to the terminal or software centre or  anything. I tried to find some kind of safe mode but recovery mode  doesn't really get me anywhere. Just gives me a menu - tried repairing  stuff but no change. Tried loading into safe graphics mode and it just  hangs on a black screen.

Thanks

---

### Post by tripp98 on 2014-05-30
here is another thread on missing menu at the top.

[http://ubuntuforums.org/showthread.php?t=2170726](http://ubuntuforums.org/showthread.php?t=2170726)

---

### Post by jdeca57 on 2014-05-31
> **Drowz0r said:**
> 
P.S. the error is about virtualbox. It seems to be running on start up and disrupting my normal start up process. If I stop it or uninstall it some how that might fix it.

There is a kind of command line option there where I tried "sudo apt-get remove virtualbox" but it just keeps throwing errors something along the line of there being no such thing as a remove command.

It was a standard .deb install from a legit source too.


Virtualbox is in the standard Ubuntu repositories (v 4.3.10) and if you have no pressing reason to install the latest (4.3.12) that installation is the safest - and I know 'it works for me is not a good answer, there are no certainties.
Depending on the work you do with your computer (but if the problem is as bad as you describe it can't be much) a reinstall might be de best way to go.

---

### Post by Drowz0r on 2014-06-01
Good lord, virtual box uninstalled ubuntu software centre, the terminal and unity.

I managed to make a new folder on my desktop, navigate to my home folder, open a random .deb install I left there, which prompted a "search online for software to open this". Re-installed the missing apps, rebooted.

Fixed.

Crazy... but fixed.

---

### Post by Jaco.csm on 2014-07-11
On newly installed Ubuntu 14.04:

Installing VirtualBox 4.3.12 from the official VirtualBox site removed unity, Ubuntu Software Centre and gnome-terminal. After rebooting and logging in you are left with only a ubuntu background image. No unity bar, no menu bar nothing. Not even ctrl+alt+T works. 

Solution to get it fixed:
Step one: Install unity. Press ctrl+alt+F1. Log in. Type ```
sudo apt-get install unity
``` This removed VirtualBox.
Step two: Reboot. Type ```
sudo reboot
``` After reboot unity bar and menu bar should be back.:):cool:
Step three: Press ctrl+alt+F1 and log in. Type ```
sudo apt-get install gnome-terminal
sudo apt-get install software-center
```

and that's it. If you still want to install VirtualBox install it from the software center. It will only be Virtualbox 4.3.10 but it will be a VirtualBox 4.3.10 on a working system.

---

### Post by Drowz0r on 2014-07-14
ctrl+alt+F1 did nothing. It would appear on removing a load of stuff that the hotkeys also stopped working.

It's fixed now anyway. Thread was solved :)

---

