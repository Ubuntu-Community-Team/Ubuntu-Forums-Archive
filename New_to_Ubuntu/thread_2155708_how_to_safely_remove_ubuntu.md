---
title: "how to safely remove ubuntu"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by reptile1 on 2013-06-19
Hey guys, running dual boot XP and Ubuntu. Have run out of disk space as partition 127GB XP and 337GB Ubuntu. Want to totally uninstall Ubuntu and only have 1 partition for XP. How do I do this safely and not lose data or corrupt files/programs etc.
Will I have issues of rebooting after removal of Ubuntu? How do I manage this?
Xp consists of Xp(original disk),XPsp1,Xpsp2.Xpsp3, all on separate disks.

Thanks
Rep

---

### Post by HiImTye on 2013-06-19
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by reptile1 on 2013-06-19
> **HiImTye said:**
> [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

Hey Hilm Tye, thanks
What about backing up best methods before using uninstaller etc
Rep

---

### Post by reptile1 on 2013-06-19
Hey Just checking is this the best way to remove ubuntu without problems or are there other ways that are better or any warnings before I go ahead?

Thanks
Rep

---

### Post by reptile1 on 2013-06-19
If I decide not to uninstall ubuntu how can I safely reduce the unused partition considerably (which is also where ubuntu is located) and expand the xp partition instead?

Thanks
Rep

---

### Post by Jonathan Precise on 2013-06-19
> **reptile1 said:**
> If I decide not to uninstall ubuntu how can I safely reduce the unused partition considerably (which is also where ubuntu is located) and expand the xp partition instead?

Thanks
Rep

Note: Before you do the instructions posted below, BACK-UP YOUR DATA!! (If you don't do this, there is a chance of losing your files) To back-up your data in Ubuntu, use the Deja-dup Backup tool (available in the software center, or at the [Ubuntu Apps Directory]("https://apps.ubuntu.com/cat/applications/deja-dup/"). Remember that if you clicked the link, you must choose your appropriate Ubuntu version in the side menu). Follow the instructions, and choose what you want to back-up. Then choose where you want to store your backup. Click "Back Up Now". The backup will begin. (If you want to use another back-up tool, then follow the instructions they have. GParted also recommends backing-up with [Clonezilla]("http://sourceforge.net/projects/clonezilla/files/clonezilla_live_stable/2.1.1-25/clonezilla-live-2.1.1-25-i486.iso/download"))

Now we can re-size the partition. I think it is easier to use the [GParted Live CD]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.16.1-1/gparted-live-0.16.1-1-i486.iso/download"). If you plan to use it, then burn the ISO to a CD (How to do this is shown later). Reboot the computer with the CD inside. You should see a menu. Wait a few seconds. Then it will ask you some questions. Choose the answer that applies to you. After all the questions, the GParted window should pop-up. Then you can re-size the partition accordingly. Apply the changes, then reboot. That's it!
Note: After applying the changes, the action can't be undone.

How to burn an ISO to a CD:

If you are not running Ubuntu, then reboot and choose Ubuntu from the grub menu. Insert a blank CD. If a dialog box pops up, then close it. Right-click the downloaded file, and select write to disk. Choose your CD/DVD drive. Then click Burn.
Note: Instructions may slightly vary, depending on your Ubuntu version.

---

