---
title: "operating system crashed , I hard rebooted and now lost desktop icons"
date: 2021-06-30
forum: New to Ubuntu
---

### Post by sixpiece on 2021-06-30
My system crashed I did a hard reset the computer didn't work anymore then I entered it in safe mode it recovered but when I got back working again as I am using it now... certain applications like software update Ubuntu and android studio no longer appear as icons. Android studio still works I have to go to its directory and load it via build.sh command... is there a way to get it back to normal?

---

### Post by ActionParsnip on 2021-06-30
If you look in /home/$USER/Desktop do you see the files OK?

---

### Post by tea for one on 2021-06-30
> **sixpiece said:**
> My system crashed I did a hard reset the computer didn't work anymore 

I assume by [COLOR="#0000FF"]hard reset[/COLOR], you powered off?

This is generally not a good idea because it can damage the file system. It would be more graceful to use R E I S U B.

Unfortunately, Ubuntu does not ship with REISUB fully enabled.

Here is a method to enable the process by editing a system configuration file:-
```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
```
Then change the number in line 26 from 176 to 244 i.e. kernel.sysrq = 244

I found the solution at this site [https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/](https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/) and the information was in section 3.

By the way, the last letter in the process **B** reboots your system, sometimes you may want to power off completely by substituting the **B** for an **O**

---

### Post by sixpiece on 2021-07-03
ActionParsnip: Thank you for the reply when I search /home/paul/Desktop it is empty... I cannot comment on the directory beforehand since I did not take note of this file directory until you mentioned it.

---

### Post by sixpiece on 2021-07-03
that was pretty neat I did the alt printscreen REISUB just now and the change you recommended... would have been useful to know before...

---

