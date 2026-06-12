---
title: "Printer Spooler service"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by ranger5664 on 2008-08-18
I have a Cannon Pixma IP1700 Photo printer, and when i try to install the software, I get an error message that tells me that the Printer Spooler service has been stoped. It also says to restart the computer to restart the service. I restarted and tried to install the software again and nothing happened. I really could use some help.

---

### Post by ranger5664 on 2008-08-18
Oh and i am using wine version 1.xto install the software

---

### Post by Oliverkat on 2009-02-07
Have you made any progress on this? I have exactly the same problem with a MP600

---

### Post by cariboo on 2009-02-07
You are never going to get that printer working using the windows driver. Have a look at the [OpenPrinting Database]("http://openprinting.org/show_printer.cgi?recnum=Canon-ip1700") for the correct linux driver for your printer.

Jim

---

### Post by halitech on 2009-02-07
> **Oliverkat said:**
> Have you made any progress on this? I have exactly the same problem with a MP600

the MP600 should work with this driver but only tested in FC5

[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600_R](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600_R)

---

### Post by Oliverkat on 2009-02-08
Thanks for that, halitech. I have the printer working pretty well using a MP500 driver, but the problem is that I wanted to use Easy Photo Print with Wine, but when I try to use it I get the "spooler is stopped..." message, which was similar to ranger5664's problem, so I'm afraid I rather hijacked his thread

---

### Post by halitech on 2009-02-08
> **Oliverkat said:**
> Thanks for that, halitech. I have the printer working pretty well using a MP500 driver, but the problem is that I wanted to use Easy Photo Print with Wine, but when I try to use it I get the "spooler is stopped..." message, which was similar to ranger5664's problem, so I'm afraid I rather hijacked his thread

so worries but I don't think WINE gives direct access to the hardware for printing but you may have luck with something like virtual box and installing windows xp in a virtual machine.

---

### Post by Oliverkat on 2009-02-08
Thanks halitech. One of the reasons I'm using Ubuntu is because I decided to re-install XP to try and solve a problem, but it wouldn't play. I tried an emulator a little while ago and once again XP wouldn't install, so there's obviously something in my computer that it doesn't like! Not to worry...:)

---

