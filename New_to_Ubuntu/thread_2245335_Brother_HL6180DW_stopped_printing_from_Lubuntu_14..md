---
title: "Brother HL6180DW stopped printing from Lubuntu 14.04"
date: 2014-09-22
forum: New to Ubuntu
---

### Post by david289 on 2014-09-22
I have a Brother HL6180DW set up as a wireless printer (connected to my WiFi network using SSID and password). I am printing to it from win VISTA, Android, and Ipad2. I recently switched from win XP on my netbook to Lubuntu 14.04 and after some use installed printer driver using Brother's software tool. It worked fine for a while and then it stopped. I uninstalled the driver using Brother uninstall tool and reinstalled driver. In process of poking and clicking around I generated troubleshoot.txt file. Don't know what it means. I have used DOS since 2.1 and used UNIX back in 80's, but am not expert at solving issues. Can do basic command line stuff. Help I don't have a clue as what to do next and I really need to abe able to print. Am generating this on my Lubuntu machine (Eee PC 1805HA)

Thank you.

David

File troubleshoot.txt too big to attach

---

### Post by JeQhdMD on 2014-09-23
If you have the IP address for the printer handy, you can set it up for Cloud Print.   Just check at Google for detailed instructions.  I have several devices enabled, and each took less than a couple minutes to do.

---

### Post by david289 on 2014-09-23
Hi! Thanks for taking time to suggest a solution. I am determined to make my printing work with my network. If I hit a wall, I'll give this a shot. I have this thing about the cloud. db

---

### Post by david289 on 2014-09-23
I am not sure where to mark this thread as SOLVED. When this first occurred, I panicked and I searched for a solution - not knowing where to search Lubuntu, Brother, Ubuntu, ASUS, etc. I finally found this forum and posted the thread. Then, while sitting back and waiting for replies, I started googling about brother printer and cups. The main error message that I was receiving when I tried to print was "printer not found". But CUPS found the printer at BRW008092796FE6 and was using that (which the printer identified as the node name). I modified this to the ip address of the printer and it started printing. I don't know why it initially worked and stopped but now I know what to do if it happens again. db

---

