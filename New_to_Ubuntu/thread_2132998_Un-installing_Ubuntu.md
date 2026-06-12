---
title: "Un-installing Ubuntu"
date: 2013-04-06
forum: New to Ubuntu
---

### Post by Melita on 2013-04-06
Could you please direct me to the Ubuntu document page where I can find un-installing instructions for Ubuntu 12.04

Thank you.

---

### Post by oldfred on 2013-04-06
An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

You then need to delete any partitions that you created for Ubuntu.

If you have Ubuntu installed inside Windows as wubi, then you just uninstall from inside Windows as any other application.

---

### Post by Melita on 2013-04-06
> **oldfred said:**
> An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

You then need to delete any partitions that you created for Ubuntu.

If you have Ubuntu installed inside Windows as wubi, then you just uninstall from inside Windows as any other application.

I don't have Windows. I installed Ubuntu only on a new hard disk on my desk top, with an Asus P5LD2 Main Board.

(1) Linux Secure Remix is only available with Ubuntu 12.10. Please see the attachment. Mine is 12.04. Will this be suitable to un-install 12.04?

(2) I don't remember whether I created a partition when I installed Ubuntu or whether I just installed it. How can I check this?

(3) Even though I un-install the system, do I still lose that disk space?

Thank you.

---

### Post by pfeiffep on 2013-04-06
> [COLOR=#000000]I don't have Windows. I installed Ubuntu only on a new hard disk on my desk top, with an Asus P5LD2 Main Board.[/COLOR]

[COLOR=#000000](1) Linux Secure Remix is only available with Ubuntu 12.10. Please see the attachment. Mine is 12.04. Will this be suitable to un-install 12.04?[/COLOR]

What OS are you currently running?
> [COLOR=#000000](2) I don't remember whether I created a partition when I installed Ubuntu or whether I just installed it. How can I check this?[/COLOR]
If you installed Ubuntu and now want to delete it ... see above question.  If you have a viable Ubuntu installation you can install gparted which is a gui interface to help you understand the partition info
> [COLOR=#000000](3) Even though I un-install the system, do I still lose that disk space?[/COLOR]
You will not loose any disk space IF you use partioning information correctly. You should be able to use the live dvd and completely remove all partitions on your new HD ... gparted usually is present on live dvd

---

### Post by Melita on 2013-04-07
*"What OS are you currently running?"*

I have **only** Ubuntu 12.04 installed on this computer and nothing else. I want to uninstall it to clear my hard disk completely. There is nothing I need to save from this installation.(I have Ubuntu on another computer which I am going to keep).

Is the Linux Secure Remix is only available with Ubuntu 12.10

[http://sourceforge.net/projects/linux-secure/files/](http://sourceforge.net/projects/linux-secure/files/)

Is this suitable to uninstall 12.04

---

### Post by pfeiffep on 2013-04-07
You can boot a live dvd, use gparted and delete all partitions. Without more research I suspect that the live dvd will have gparted

```
**Linux Secure Remix**[COLOR=#333333][FONT=Ubuntu] (ex- [/FONT][/COLOR]**Ubuntu Secure Remix**[COLOR=#333333][FONT=Ubuntu]) is a slightly improved Ubuntu disk designed especially to install Ubuntu in dual-boot with Windows (or MacOS). It is a non-official Ubuntu derivative.[/FONT][/COLOR]
```

---

### Post by Melita on 2013-04-07
> **pfeiffep said:**
> You can boot a live dvd, use gparted and delete all partitions. Without more research I suspect that the live dvd will have gparted

```
**Linux Secure Remix**[COLOR=#333333][FONT=Ubuntu] (ex- [/FONT][/COLOR]**Ubuntu Secure Remix**[COLOR=#333333][FONT=Ubuntu]) is a slightly improved Ubuntu disk designed especially to install Ubuntu in dual-boot with Windows (or MacOS). It is a non-official Ubuntu derivative.[/FONT][/COLOR]
```

What is 'gparted' please?

---

### Post by pfeiffep on 2013-04-07
it's a gui application for partitioning disk drives ... even though your version of choice is 'not official' I respectfully suggest reading [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)

---

### Post by oldfred on 2013-04-07
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by user333 on 2013-04-07
To totally wipe a hard-drive use [dban]("http://www.dban.org/"). It is open source, and will completely remove all data, which deleting files won't. I wouldn't use Gparted for this, but I suppose that would be OK too.

---

### Post by Melita on 2013-04-07
Thank you very much for all the help.

Kind regards.

---

