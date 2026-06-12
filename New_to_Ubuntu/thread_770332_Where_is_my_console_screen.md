---
title: "Where is my console screen?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by ddzghr on 2008-04-27
Well, I'am new with linux, but exploring it. So I installed Ubuntu 8.04 server and found myself in trouble. After having problems with   error "GRUB error 18" (found solution), install passed well, but after reboot my screen was empty (no console), so I've tried to connect from other computer with putt and it was success. So my question is: WHERE IS MY CONSOLE? (already tried shift+F1 and alt+shift+F1) Please Help?

---

### Post by unbuntued on 2008-04-27
> **ddzghr said:**
> Well, I'am new with linux, but exploring it. So I installed Ubuntu 8.04 server and found myself in trouble. After having problems with   error "GRUB error 18" (found solution), install passed well, but after reboot my screen was empty (no console), so I've tried to connect from other computer with putt and it was success. So my question is: WHERE IS MY CONSOLE? (already tried shift+F1 and alt+shift+F1) Please Help?
I'm not quite sure I follow up.
Where you able to get to the login screen?
If yes, you can click on 'Sessions' and select 'Failsafe terminal' then login. This will get you the console screen.

If you're already logged in to the desktop environment (which I don't think you are through your description, but just in case):
ALT+F2 then type 'gnome-terminal' if you're using GNOME, or 'konsole' for KDE

---

### Post by Joeb454 on 2008-04-27
The OP is running Ubuntu server. After all the text it should provide you with a prompt asking you to login.

It will just be white text on a black background. If you are at the actual machine you installed on that is (not remotely using it)

---

### Post by ddzghr on 2008-04-27
> **Joeb454 said:**
> The OP is running Ubuntu server. After all the text it should provide you with a prompt asking you to login.

It will just be white text on a black background. If you are at the actual machine you installed on that is (not remotely using it)

Server is UP and running, but monitor connected on server is black, no text mode login screen! :confused:

---

### Post by Joeb454 on 2008-04-27
Have you checked all the connections? And do you have a graphics card in the server? You don't really need one, but I thought I should ask :D

---

### Post by ddzghr on 2008-04-27
> **Joeb454 said:**
> Have you checked all the connections? And do you have a graphics card in the server? You don't really need one, but I thought I should ask :D

:) I'am playing with computers for a 25 years, so there is a graphic card, and when booting it asks me where from to boot from, so for graphic card and monitor, they work fine. :)

---

### Post by louieb on 2008-04-27
Just wondering if your seeing any messages when it boot?
Server boot will usually display several pages of messages ending with
... rc.local ..
at this point if you press enter it will give you the login prompt on tty1. 

might try adding the **vga=** option just do a search for **vga=** on this page for the list 
[BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")

---

### Post by Joeb454 on 2008-04-27
I know the graphics card may work fine - but Ubuntu may not be able to load the drivers for it, so if you use an onboard graphics chip - you may be able to install the graphics drivers.

---

### Post by ddzghr on 2008-04-27
> **Joeb454 said:**
> I know the graphics card may work fine - but Ubuntu may not be able to load the drivers for it, so if you use an onboard graphics chip - you may be able to install the graphics drivers.

No it's not onboard card, it's pci NVIDIA"something". Is there any way I can find out what is happening? I also tried many vga=xxx, stil does not work. When it starts grub it just turns black. That's all.:confused:

---

### Post by Joeb454 on 2008-04-27
Is there an onboard card in the PC? if so try removing the PCI Nvidia card, and using the onboard card temporarily to see if that works :)

---

### Post by ddzghr on 2008-04-27
No there's no obboard card. :(

---

### Post by ddzghr on 2008-04-27
No, there is no onboard card. :(

---

### Post by Joeb454 on 2008-04-27
Hmm...I'm not sure then, it sounds like you need a restricted driver for your graphics card.

Other than that I'm not really sure what else to do :( sorry

---

### Post by ddzghr on 2008-04-27
> **Joeb454 said:**
> Hmm...I'm not sure then, it sounds like you need a restricted driver for your graphics card.

Other than that I'm not really sure what else to do :( sorry

I've found some old ATI RADEON 9200, and put it instead of NVIDA card, and it started to work. It is some problem with NVIDIA card/drivers, I'am not sure and I don't have enough knowledge/time to find out. Thanks all.

---

