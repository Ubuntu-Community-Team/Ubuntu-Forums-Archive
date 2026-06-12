---
title: "Where is software center in 4.18.0-15?"
date: 2019-02-12
forum: New to Ubuntu
---

### Post by eddyq on 2019-02-12
Some web pages say to open Software Center. So I searched for Software Center but they only mention up to Ubuntu 11.10. Some say it is in the Launcher so I searched for Launcher and found this: "T[COLOR=#101010][FONT=&quot]he launcher sits on the left-hand side of the screen" but there is nothing on the left side that hints at the Launcher.

[/FONT][/COLOR]So (1) where is the Launcher, (2) better yet, where is the Software Center?

---

### Post by Dennis N on 2019-02-12
If your using Ubuntu 18.04 or 18.10 type "software" in the search box on the overview screen. "Ubuntu Software" appears among the results. That's equivalent to Software Center.

See attached image.

---

### Post by eddyq on 2019-02-13
I had already looked at Ubuntu Software but it does not seem to be the one that web pages reference as Software Center. For example I install a program but don't know where it is so I go to Ubuntu Software but it is not listed there. Also where is Launcher?

---

### Post by coffeecat on 2019-02-13
What do you mean by 4.18.0-15? That is not a version number for Ubuntu that I recognise. What release of Ubuntu are you using?

**Edit:** not enough coffee yet - I now see that's the kernel version for 18.10.

@eddyq, please in future quote the release of Ubuntu you are using, not the kernel version. As a courtesy to forum members trying to help you, you see.

The web pages you were reading were probably referring to the now discontinued Unity desktop. Ubuntu now uses the gnome desktop - since Ubuntu 17.10. Web pages telling you how to use the now discontinued Software Centre will eventually be out of date. Make sure you find web howtos that correspond with the release you are using. There's a distressing amount of out-of-date and plain wrong information out there on the big wide internet.

---

### Post by Impavidus on 2019-02-13
4.18.0-15 is a kernel version, which does not have a 1:1 relation to an Ubuntu version. 4.18 is available for Ubuntu 18.10 and 18.04, but 18.04 also supports 4.15. The Ubuntu version is the more relevant thing for your question.

The software centre has gone through some name changes over the years, which does not facilitate interpretation of old documentation. There have been significant changes to the GUI as well and there are many different GUIs available anyway. But newly installed applications should be available for use in the same way as those installed by default. They may not automatically appear in the launcher/panel, but should be available from menus/search function (except command line applications).

---

### Post by eddyq on 2019-02-13
> **coffeecat said:**
> What do you mean by 4.18.0-15? That is not a version number for Ubuntu that I recognize. What release of Ubuntu are you using?

@eddyq, please in future quote the release of Ubuntu you are using, not the kernel version. As a courtesy to forum members trying to help you, you see.



That is from the output from "uname -a". 

Here is the full output: eddyq@eddys-ubuntu:/mnt$ uname -aLinux eddys-ubuntu 4.18.0-15-generic #16-Ubuntu SMP Thu Feb 7 10:56:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


I didn't know that was just for the kernel. I see now that  I should have used "[FONT=Roboto]lsb_release -a"

So how do I find "[/FONT][COLOR=#000000]launcher/panel"?[/COLOR]

---

### Post by howefield on 2019-02-13
> **eddyq said:**
> ..... How else would I get the Ubuntu version?

Use..

```
cat /etc/*-release
```

What is the output from that command ?

---

### Post by oldrocker99 on 2019-02-13
EDIT; Oops. No coffee yet myself.

Nothing to see here...

---

### Post by deadflowr on 2019-02-13
Post back the results from
```
echo $XDG_CURRENT_DESKTOP
```

The launcher on Ubuntu runs across the leftside of the default screen (if mutli-monitor that normally defaults to the left monitor)
If you're not seeing it then either the setup is mucked up or you might be running a different desktop than Ubuntu's, which is fine.

---

### Post by eddyq on 2019-02-13
I thought the left side was called the doc. I have seen it called another name but never saw it called the Launcher. I have searched the web for "Launcher on Ubuntu" but no meaningful results.

Anyway, now I know what they are talking about when they use the term "Launcher".

The output from the "echo $XDG_CURRENT_DESKTOP" command is "ubuntu:GNOME"

---

### Post by eddyq on 2019-02-13
So now I know to get Software Center I should click on the square of dots at the lower left and type "software". But how do I get the display shown in [https://help.ubuntu.com/community/UbuntuSoftwareCenter#Launching_Ubuntu_Software_Center?](https://help.ubuntu.com/community/UbuntuSoftwareCenter#Launching_Ubuntu_Software_Center?)

---

### Post by Holger_Gehrke on 2019-02-13
> **eddyq said:**
> ... But how do I get the display shown in [https://help.ubuntu.com/community/UbuntuSoftwareCenter#Launching_Ubuntu_Software_Center?](https://help.ubuntu.com/community/UbuntuSoftwareCenter#Launching_Ubuntu_Software_Center?)

You won't. Don't just look at the pictures, read the text, too. That page describes the Software Center on Ubuntu 9.10 to 11.04. It's for versions of Ubuntu that were released in 2009 to 2011. A new release is made every six month, Ubuntu "Version Numbers" are actually release dates in the form "year.month". I'd be very surprised if Ubuntu Software still looked like the Software Center from 8 years ago.

Holger

---

### Post by oldrocker99 on 2019-02-13
Back in Ye Olden Days, the only package manager available was synaptic, and it's a must for anyone who wants to do some serious repository searching. It's where I go first. Gnome-software-manager is fine for discovering a few new apps I might not have known about, but I either use synaptic or the terminal for all my software installation.

---

