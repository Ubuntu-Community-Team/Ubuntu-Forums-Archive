---
title: "White Terminal At Boot Screen No Gui!"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by SEECo on 2013-05-31
Hi Ubuntu users, I have dual boot on my PC with Windows Xp and Ubuntu 10.04. Some days before i messed up with my SAM file trying to break password but it changed my password then I repaired my Xp using an XP cd. But after repairing my ubuntu started behaving irregular like no title bars, no right click on desktop o desktop icons. I tried to repair it but it turned out even worse when I boot into Ubuntu it shows the boot screen(picture Given) with a white terminal at top left corner(separate picture). I have no gui no nothing. Plzzz help Me. :'(

---

### Post by gordintoronto on 2013-05-31
Ubuntu 10.04 Desktop is not supported any more.

It might be useful if you described your computer, especially the video card and whether you installed an Additional Driver.

---

### Post by SEECo on 2013-06-01
> **gordintoronto said:**
> Ubuntu 10.04 Desktop is not supported any more.

It might be useful if you described your computer, especially the video card and whether you installed an Additional Driver.

I have a desktop Dell DC7800 Mini Tower, 4GB ram, built-in graphics card no additional drivers, 2.93 Ghz Core to duo. Is that enough!

---

### Post by squakie on 2013-06-01
[B]
In that terminal window type lspci and post the output back here.

Also try startx into that same window and post back any messages.[/B]

---

### Post by SEECo on 2013-06-03
> **squakie said:**
> [B]
In that terminal window type lspci and post the output back here.

Also try startx into that same window and post back any messages.[/B]

With Startx it says'

fahad@Fahad-Terminal:$ startx

X: user not authorized to run the X server, aborting

When i run "lspci" it gives something about my chipset and graphics card but i am unable to copy it and paste it as it is in another OS.

---

### Post by SEECo on 2013-06-05
What should I do now, I am in an urgent condition Ubuntu have a lot of programs installed and many doata. What Should I Do????????????

---

### Post by SEECo on 2013-06-12
> **squakie said:**
> [B]
In that terminal window type lspci and post the output back here.

Also try startx into that same window and post back any messages.[/B]

Well, Somehow I managed to copy the messages. Here they are 

```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q35 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
00:03.2 IDE interface: Intel Corporation 82Q35 Express PT IDER Controller (rev 02)
00:03.3 Serial controller: Intel Corporation 82Q35 Express Serial KT Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
ubuntu@ubuntu:~$ 


```

Now, that you got what you asked for now please help me.:

---

### Post by QIII on 2013-06-12
Hello!

What exactly did you do when you tried to repair your Ubuntu installation?

Thanks!

---

### Post by SEECo on 2013-06-12
> **QIII said:**
> Hello!

What exactly did you do when you tried to repair your Ubuntu installation?

Thanks!

i didn't do anything to Ubuntu actually my Windows XP was who I repaired. But Ubuntu was the one who started to act strange like no clicks on desktop, desktop icons gone, then I ran some commands on terminal for nautilus to work properly and then after a reboot the last thing I saw was a boot screen with a terminal at top left corner.

---

### Post by mastablasta on 2013-06-12
> then I ran ***some commands*** on terminal for nautilus to work properly

what commands?

is this a wubi install? there is no way windows repair or messign arround in windows can influence ubuntu if this is side by side install (well appart from boot loader but that is not the OS).

also startx - as you can see you do not have the necessary privilege (as user) to run it. so you need to run it with sudo.

---

### Post by SEECo on 2013-06-13
> **mastablasta said:**
> what commands?

is this a wubi install? there is no way windows repair or messign arround in windows can influence ubuntu if this is side by side install (well appart from boot loader but that is not the OS).

also startx - as you can see you do not have the necessary privilege (as user) to run it. so you need to run it with sudo.

Well I do not remember the commands now. Well when I run the sud startx it says as follows:
```
ubuntu@ubuntu:~$ sudo startx


Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log
ubuntu@ubuntu:~$ 





```

---

