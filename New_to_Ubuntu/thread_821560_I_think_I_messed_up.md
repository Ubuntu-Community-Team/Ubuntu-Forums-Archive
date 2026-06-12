---
title: "I think I messed up"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Mossback on 2008-06-07
I installed Ubuntu 8.04 from the CD on my hard drive and everything went well. It worked fine until I was exploring the desktop options and somehow got the reverse cube and accidentally made the menus 90%+ opaque. Now I can't see them well enough to return the desktop to normal. I tried to reinstall Ubuntu but it wanted to repartition the disk.

Is there a way to start Ubuntu in a safe mode like using F8 when starting windows? Or does anyone have a suggestion on how to reset the desktop without seeing any menus.

I think I am going to enjoy using Ubuntu, I just need to get past the early hurdles.

Thanks in advance for your help.

---

### Post by quelx on 2008-06-07
Open a terminal **ALT-F2** > **gnome-terminal** <enter>

[COLOR="Red"]type[/COLOR]

```
mv ~/.config/compiz ~/Desktop/compiz.bak
```

Close any applications and **CTRL-ALT-Backspace**

---

### Post by Mossback on 2008-06-07
Okay - I guess I spent too much time in Microsoft land, I brought up Ubuntu and tried both hitting the Alt-F2 keys and typing Alt-F2>gnome-terminal and nothing happened in either case.

When you indicated "bring up a terminal" is there something I need to do during the boot process? 

Thanks for the help.

---

### Post by dnns123 on 2008-06-07
when you boot up GRUB, you see Ubuntu and Ubuntu (recovery mode, i think this is the name) right? use the recovery mode and fix the settings

---

### Post by RSingh on 2008-06-07
press alt+f2

type:
```

"metacity --replace"
```

and press enter. That should disable compiz and you should then be able to fix the problem.

---

### Post by quelx on 2008-06-07
after hitting **ALT-F2** type **gnome-terminal** <enter> you should get something that looks like a command prompt.

If nothing shows up, hit **CTRL-ALT-F1** and you should be at a text login screen.  login using your system account and use the same **mv**, which I just noticed I had wrong, sorry.

```
mv ~/.config/compiz ~/Desktop/compiz.bak
```

---

### Post by Mossback on 2008-06-07
You guys ROCK!!!:)

It worked and I'm back in business.

Another quick question - I have used Open Office in Windows and like it. I downloaded Open Office for Ubuntu to the desktop but can't get it to install by double clicking on it like I would in Windows.

Is there another way to get the program to install?

Thanks

---

### Post by avtolle on 2008-06-07
AFAIK, OpenOffice is installed by default in Ubuntu, and you should not need to install it from the site (unless you're trying to install the Beta for OO3). Check to see if it's installed by going to Applications at the top left of the bar, click on it, then select Office, and it should show Open Office Writer and Spreadsheet installed. If it isn't, use Add/Remove Applications (under the same menu) or Synaptic to install.

---

### Post by baddnady23 on 2008-06-07
Correct.  OpenOffice is installed by default.  open up the applications menu  and it is listed in there

---

### Post by Mossback on 2008-06-07
Correct on both counts - Open Office 2.x installed with Ubuntu, however, I found the 3.0 Beta version and have been using it in Windows and would like the same program in Ubuntu.

If it won't work I am good with the 2.x version, but I would really like to use the new version.

Thanks

---

