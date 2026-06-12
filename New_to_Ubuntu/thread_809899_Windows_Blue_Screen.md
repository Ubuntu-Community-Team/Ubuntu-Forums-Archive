---
title: "Windows Blue Screen"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by SIXAXIS on 2008-05-27
Hi guys,

It seems that my friend is having a problem with his dual-boot computer. I tried all that I can to help him, but nothing. Basically, he updated Ubuntu 8.04 using the default updater. It changed the kernel version and added some things in the menu.lst file. It also removed Windows XP from there. I helped him and we added Windows back and the newer Linux kernels. Whenever he tries to boot up Windows, it loads, gets to his desktop and then flashes a blue screen. We can't pause it or get a look at it so we don't know what it is. We used the Windows XP install CD and used the recovery console. We used the commands:
```
fixboot
```
and
```
fixmbr
```
Now he doesn't have GRUB bootloader or Windows. We suspect that a vital file is missing from Windows. Wow, I hate Windows.

---

### Post by EXCiD3 on 2008-05-27
Here is a quick little tutorial on how to reinstall grub from the Live CD so that you can at least use the computer: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Have you tried booting into Windows in safe mode by hitting F8 before the loading screen?

---

### Post by SIXAXIS on 2008-05-28
Yes, safe mode works. But we don't know what's wrong so we don't really know what files to edit or change.

**EDIT:** Yeah, I reinstalled GRUB for him.

---

### Post by EXCiD3 on 2008-05-28
> **SIXAXIS said:**
> Yes, safe mode works. But we don't know what's wrong so we don't really know what files to edit or change.

**EDIT:** Yeah, I reinstalled GRUB for him.

Well if you have no trouble getting into safe mode then it sounds like one of your applications autoruns on startup is bluescreening your computer. Try uninstalling the applications that autorun because they dont run automatically on safemode.

---

### Post by diablo75 on 2008-05-28
If you can get into safe mode, run "msconfig" (Windows-Key+R, or Start>Run>msconfig) and then look at the startup tab.  Find programs listed in there that you know shouldn't be running right off the bat, or serve you no good and disable them from loading at startup by unchecking them.

---

### Post by eriqjaffe on 2008-05-28
It's pretty simple to disable the auto-BSOD-reboot:

[http://www.tunexp.com/tips/maintain_your_computer/disabling_blue_screen_of_death_auto-reboot/](http://www.tunexp.com/tips/maintain_your_computer/disabling_blue_screen_of_death_auto-reboot/)

If you can get into safe mode, you should be able to do that.  Then you'll be able to see what the BSOD's all about.  Or, at least, be able to see the cryptic message.

---

### Post by diablo75 on 2008-05-28
> **eriqjaffe said:**
> It's pretty simple to disable the auto-BSOD-reboot:

[http://www.tunexp.com/tips/maintain_your_computer/disabling_blue_screen_of_death_auto-reboot/](http://www.tunexp.com/tips/maintain_your_computer/disabling_blue_screen_of_death_auto-reboot/)

If you can get into safe mode, you should be able to do that.  Then you'll be able to see what the BSOD's all about.  Or, at least, be able to see the cryptic message.

Another way to do this is to hit F8 to get to the hidden boot menu, and boot normally but with DEBUGGING MODE enabled.  This will freeze the screen upon a crash and allow you to view the error and see what its being caused by.

---

### Post by SIXAXIS on 2008-05-28
Cool. Thanks guys.

---

