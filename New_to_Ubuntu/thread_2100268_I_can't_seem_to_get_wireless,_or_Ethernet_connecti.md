---
title: "I can't seem to get wireless, or Ethernet connection on my desktop computer."
date: 2013-01-01
forum: New to Ubuntu
---

### Post by Aeru on 2013-01-01
I installed ubuntu from the windows installer yesterday. I tried for hours to get the wireless to work because the router was in another room and since the computer I'm trying ubuntu on is a desktop, I really didn't feel like moving it. I looked on forums, youtube, ask sites, and etc. I tried just about everything I came across. 
Finally I asked my dad for the Ethernet cable and moved my desktop to the router and tried it that way, but it did nothing. So I looked online for help about the Ethernet connection, tried everything I could that way for hours as well and still nothing. I eventually had to stop otherwise I was going to rip my hair out.
Please help.

---

### Post by Isamu715 on 2013-01-01
Use a LiveCD/USB and check if your connection is working from there. I think the issue is related to the Windows installer, Wubi is far from perfect. If the connection works in the live session, try installing Ubuntu directly and it should work.

---

### Post by gordintoronto on 2013-01-01
What version of Ubuntu? Can you open a rerminal and enter these two comands:
lspci
lsusb

and copy/paste the results into a message here? (The first command will probably display the identification of both wireless and wired devices, but the second one might be needed.)

---

### Post by ivicks on 2013-01-01
I would try the live CD first before anything (well live CD after making sure you can see active lights blinking on the NIC) it will be the least stressful route first. Personally I have never used the Windows Installer, I always boot from a live CD to test hardware first.

---

