---
title: "HOWTO: Make KDE only automount NOT autoexecute"
date: 2005-11-15
forum: Outdated Tutorials &amp; Tips
---

### Post by GoldBuggie on 2005-11-15
If you are troubled by the autoexecution of konqueror or kaffeine whenever you insert a CD or USB-memorystick etc and you would like things to automount but not execute a software then this is the thing for you.

The software that handles automount and all these execution is ivman. A nice litte utility but not configured to my likings. Here is how to make it _ONLY_ automount.

```
 sudo kate /etc/ivman/IvmConfigActions.xml
```

the only thing that should be in that file is this:
```

** <?xml** version="1.0" encoding="UTF-8"?**>**
** <ivm:ActionsConfig** version="0.2" xmlns:ivm="http://www.eikke.com/ivm"**>**
      [COLOR=Silver]<!-- try to mount any mountable volume at all -->[/COLOR]
      **<ivm:Match** [COLOR=Lime]name=[/COLOR][COLOR=Red]"ivm.mountable"[/COLOR] [COLOR=Lime]value=[/COLOR][COLOR=Red]"true"[/COLOR]**>**
          **<ivm:Option** [COLOR=Lime]name=[/COLOR][COLOR=Red]"mount"[/COLOR] [COLOR=Lime]value=[/COLOR][COLOR=Red]"true"[/COLOR] **/>**
      **</ivm:Match>**

** </ivm:ActionsConfig>**
```

Everything else in that file are either for execution or popup signals when a printer is detected. If you do not want to remove everything is that file just comment everything except the above section.

To comment out things in a .xml file just wrap it with
```
[COLOR=Silver]<!-- [COLOR=DimGray]...CODE...[/COLOR] -->[/COLOR]
```

---

### Post by Divan Santana on 2006-01-18
Perhaps just apt-get remove ivman 

This removes the program that automounts stuff as kde3.5 has a built in handler that does a nicer job of it...

---

### Post by GoldBuggie on 2006-01-18
That is another choice but I do find ivman to be a nice tool which you can configure some individual behaviour and since kubuntu us configured for ivman I don't think removing it is the ideal behaviour. But to each his own.

---

### Post by DrinkYourOvaltine on 2006-01-18
Thanks for this! - I have been getting more and more frustrated with both konqueror and kscd opening when I put a cd in. 

[SIZE="1"](That kscd check-box to disable autoplay is a filthy lie!)[/SIZE]

---

### Post by gingermark on 2006-04-22
```
 sudo kate /etc/ivman/IvmConfigActions.xml
``` really should be ```
kdesu kate /etc/ivman/IvmConfigActions.xml
```

From [https://wiki.kubuntu.org/RootSudo](https://wiki.kubuntu.org/RootSudo):
> **NEVER** use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail.

---

### Post by tsb on 2006-05-13
[QUOTE=gingermark]```
 sudo kate /etc/ivman/IvmConfigActions.xml
``` really should be ```
kdesu kate /etc/ivman/IvmConfigActions.xml
```

From [https://wiki.kubuntu.org/RootSudo](https://wiki.kubuntu.org/RootSudo):[/QUOTE]

Thanks.  I always wondered why kate always crashed when I tried sudo.  On reboot the password prompt would come up but open a blank page.  Now it works perfectly.

Thanks to the OP for help with that launching crap.

---

### Post by Jucato on 2006-07-12
Question: Doesn't System Settings > Hardware > Storage Media have settings for what to do when a certain media is inserted? Maybe it could be set to "Do Nothing"?

---

