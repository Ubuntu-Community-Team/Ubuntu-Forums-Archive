---
title: "Can't log into Xubuntu after failed installation."
date: 2011-10-10
forum: New to Ubuntu
---

### Post by primvirlaux on 2011-10-10
In short: I installed something, my root partition is full, I cannot log in/start Xubuntu anymore, so I can't change or delete anything either.

Longer version: I'm running xubuntu 11.04 on an Asus X101 netbook. Just tried to install 'Battle for Wesnoth' (yeah, and immediately got punished for installing a game on my work machine) via the Software Center. From what I can tell, the installation size was too big, and now my root partition is 100% full. I tried to uninstall, but the system acted weird, so I rebooted and couldn't log in anymore. I assume (correct me if I'm wrong) that this is related to lack of space on /.

My questions:

1) How do I get into my system again? Any workaround to the fact that, when I try to log in, the log-in screen just accepts my input and then re-appears, without any error message.

2) (probably related to question 1) How do I completely remove all the files of 'Wesnoth' that the Software Center downloaded and installed. Simply pressing 'remove' doesn't work, so how can I find out what exactly is left of the failed installation?

(the following two questions are less urgent. They only matter once I get my computer running again)

3) Can I install, via the Software Center, to a different partition, e.g. install software to my /home partition instead of root (sorry, I'm a newbie, maybe that's impossible...)

4) Is it on purpose that the software center doesn't make a simple check for available disk space before installing, or did I encounter a bug?


Thanks a lot for reading this far! Hope anyone can help.

---

### Post by Lisiano on 2011-10-10
Could you tell us what filesystem does the / partition use?
If it's ext, you can use the following command to free up some space by removing reserved blocks for privileged processes, AKA, Root stuff. Note you should only do this on big disks as it's there for a reason.
```
sudo tune2fs -m 1 /dev/sda1
```
/dev/sda1 is your / partition, replace accordingly.
-m 1 is the percent to set the reserved blocks, in this case 1%, the default is 5%.
You can also remove wesnoth by going into a TTY and using this
```
sudo apt-get purge wesnoth*
```
To get into a TTY, press Ctrl+Alt+F1-F6 or reboot into recovery mode and select "Root with networking". If you go the Recovery console way, you can omit sudo.
Now if removing wesnoth didn't help, you can try asking apt-get to fix everything.
```
sudo apt-get update
sudo apt-get -f install
```

Now for your optional questions:
3) Short: No.
Long: To install somewhere beside the / partition (To be more precise, /bin, /sbin, /usr/bin, /usr/sbin, /opt, /var/opt, etc) you need to download the source code manually, compile it and install anywhere or run it from the directory you placed the code at. This is not supported by neither synaptic, USC, kpackagekit, I don't know about whatever LXDE uses, it's partially supported in apt-get though since you can tell it to download source code and compile it.
4) I don't know, but usually Ubuntu warns you if you are running low on any partition.

Offtopic: Why were you installing a game on a work machine? And how did you get the sudoer rights to install it (Administrative privileges)?

EDIT: You can also try telling apt-get to clean it's cache file.
```
sudo apt-get clean
```
If you use "clean" you delete every cached file. You can replace it with "autoclean" and so it will only delete stuff that you can't download (AKA Outdated stuff)

---

### Post by ezramorris on 2011-10-10
Hi,
> **primvirlaux said:**
> My questions:

1) How do I get into my system again? Any workaround to the fact that, when I try to log in, the log-in screen just accepts my input and then re-appears, without any error message.

Are you able to boot into recovery mode?

[LIST=1]
[*]Start your computer, and hold the shift key. This will cause the GRUB boot menu to be displayed.
[*]Use the arrow keys to go down to the "Ubuntu, with Linux....(recovery mode) option" and press return.
[*]Once booted, a recovery menu will appear. Go down to the "root" option and hit return.
[/LIST]

This should get you to a root shell prompt, where you can uninstall/fix stuff.

> **primvirlaux said:**
> 2) (probably related to question 1) How do I completely remove all the files of 'Wesnoth' that the Software Center downloaded and installed. Simply pressing 'remove' doesn't work, so how can I find out what exactly is left of the failed installation?

To remove the Wesnoth package itself, run:
```
apt-get remove wesnoth
```

You'll also want to remove other packages that were installed which aren't needed any more:
```
apt-get autoremove
```

Finally, as you're low on disk space, I would recommend clearing out the local cache of retrieved package files:
```
apt-get clean
```

Then you can reboot, and hopefully you'll be good to go:
```
reboot
```

> **primvirlaux said:**
> 3) Can I install, via the Software Center, to a different partition, e.g. install software to my /home partition instead of root (sorry, I'm a newbie, maybe that's impossible...)

Not as far as I'm aware. Primarily because, when you install a package, it puts lots of files in different places, so that the system can find each type of file.

> **primvirlaux said:**
> 4) Is it on purpose that the software center doesn't make a simple check for available disk space before installing, or did I encounter a bug?

I'm not sure on this one, but it's possible that it's just too difficult to predict how much space will be taken up once the packages have been downloaded, unpacked, and post-install scripts run.

---

### Post by primvirlaux on 2011-10-11
My system is running again and I can log in via the graphical interface. Thanks a lot, Lisiano and ezramorris.

First, I didn't know I can get into the terminal directly with Ctrl+Alt+F1 even before logging in with the graphical logon screen (stupid, I know, it's kind of obvious).
Second, 'sudo apt-get purge wesnoth*' freed a lot of space already, and 'autoremove' and 'clean' even more. Afterwards I could log in again normally.

The disk space of this netbook is pretty low (8GB in total), and I probably made the root partition too small (about 3.5 GB, of which < 1 GB is free now).
Since space is running low on my root partition, I guess I need to learn how to compile source code of programs I want myself and run it from another partition. Or is there a way to change the size of my partitions in an existing installation? Then I would make my /home smaller and / bigger.

> **Lisiano said:**
> Offtopic: Why were you installing a game on a work machine? And how did you get the sudoer rights to install it (Administrative privileges)?
Nah, not work computer , more like "work" computer. It's my own computer and I could in theory do whatever I want with it, but it's the one I take to the library to work on, read articles and use Latex, as opposed to my home computer on which I tend to waste a lot of time playing games. The lesson is learned though.

---

### Post by ezramorris on 2011-10-11
> **primvirlaux said:**
> Or is there a way to change the size of my partitions in an existing installation? Then I would make my /home smaller and / bigger.

You can't do this while the partitions are in use, but if you boot from the live cd, then you can launch the gparted partition editor and resize them.

Would strongly recommend backing up first though!

---

### Post by Lisiano on 2011-10-11
If you have the patience, time and a big memory card (And a memory card reader in your netbook) you can move the files in your home folder to it and use it as a home folder. This is easily doable and will both give you a lot more space on the HDD and you can take files with you if you decide to move some files without turning the netbook on.

---

### Post by primvirlaux on 2011-10-11
Just created a live-USB with GParted (great program) and resized my partitions (made swap smaller, but mainly reduced my home parition). System is running stable afterwards. It appears that the xubuntu startup time went up by a few seconds, which I can't explain (SSDs don't suffer from fragmentation), but that's probably a question for another thread, if at all. Thanks for your continued help!

---

