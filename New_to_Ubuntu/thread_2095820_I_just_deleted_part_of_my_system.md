---
title: "I just deleted part of my system"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by Thrashrokz33 on 2012-12-18
I'm running Kubuntu Desktop 12.04.

I wanted to install LAMP server on my system, and used the program "tasksel" for the job, as I saw in an online article. When I went to the installer, kubuntu-desktop, ubuntu-desktop were checked. I unchecked them, and marked LAMP for installation (I realize now why this was stupid).

After I progressed to the next screen, the installer started removing various KDE packages, and I immediately realized what I had done. I quickly closed the installer so it wouldn't remove anything else. I now cannot launch Konsole, and various other programs. I've not yet logged out of this session in fear of not being able to get back into it.

I'm going to assume I have to completely reinstall kubuntu-desktop packages by "apt-get install kubuntu-desktop", but I'm hoping that's all that got removed, and nothing more critical to the system. 

What is the best course of action at this point?

---

### Post by Thrashrokz33 on 2012-12-18
I just found this thread:

[http://ubuntuforums.org/showthread.php?t=1369551](http://ubuntuforums.org/showthread.php?t=1369551)

User Mofef offers this command that I feel may work. Good idea?

```
sudo apt-get install $(for i in $(cat /var/log/dpkg.log |grep -oP "(?<=`date +%Y-%m-%d`\s\d\d\:\d\d:\d\d\sremove)\s\S*\s"); do echo -n "$i "; done;)
```

---

### Post by Thrashrokz33 on 2012-12-18
Well I ran that script, and it just tells me that one of my packages can't be found:

"E: Unable to locate package redshiftgui"

I'm at a loss here. If I shut my computer down, I'm most likely just going to have to reinstall Ubuntu altogether, and it's 2am here so I may just have to do that if I get no replies in the next half hour or so.

---

### Post by Sealbhach on 2012-12-18
In earlier versions of Ubuntu you could do Ctrl+Alt+F1 or F2 or whatever, to bring up a normal xserver screen. Can you do that and reinstall kubuntu that way?

If not, you can always reinstall it using a LiveCD.

.

---

### Post by Thrashrokz33 on 2012-12-18
Yes, I'm going to try that now. Thanks.

---

### Post by Thrashrokz33 on 2012-12-18
How do I install kubuntu-desktop while on the Live-CD?

---

### Post by Thrashrokz33 on 2012-12-18
Do I just mount the Ubuntu partition into /mnt, cd into it, and "sudo apt-get install kubuntu-desktop"?

edit: Do I use chroot?

---

### Post by Sealbhach on 2012-12-18
See [here]("https://help.ubuntu.com/community/LiveCdRecovery") under Update Failure.  You need to replace hda1 with sda1 or sda2 or whatever is appropriate for your system. Instead of just updating you can install or remove packages too.

.

---

### Post by Thrashrokz33 on 2012-12-18
Well, after fixing Grub, it looks like crisis semi-averted. I've lost all of my installed applications, and it looks like I'll have to tweak my Desktop again, but it's better than starting from fresh I guess. Thanks for your help.

---

### Post by Sealbhach on 2012-12-18
Good! It's an opportunity to try out a new theme! :)

.

---

