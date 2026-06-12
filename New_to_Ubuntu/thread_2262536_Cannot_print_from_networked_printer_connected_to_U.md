---
title: "Cannot print from networked printer connected to Ubuntu Server 12.04"
date: 2015-01-25
forum: New to Ubuntu
---

### Post by Jon_Messenger on 2015-01-25
New to linux, I have followed various guides and built a Ubuntu Media Server which serves video around the house. The server is headless and i can interact via VNC from a Windows 7 laptop.

I have now decided to add a Kodak ESP 3250 AIO Printer to allow anyone logged into my home network to print from one central location ie: the Ubuntu Media Server. I installed the 'c2esp' driver via Synaptic and this works perfectly when logged into VNC and printing direct from Ubuntu.

Via Webmin, I setup a SAMBA share and the printer is now visible within Windows as a networked printer. The printer is selected in Windows as default and the relevant driver installed. I can now send data to the printer from Windows but the printer only outputs what looks like the software commands used to generate the print. I also tried printing via Google Cloudprint but the output was the same. Again, printing direct from the server via VNC produces the correct print.

As i said before i am new to Linux and trying to learn as i go. I have changed many settings in Windows and on the server but nothing seems to make a difference. If anyone has any suggestions how to fix this problem i would be most grateful. Please remember i may not understand anything too complicated, so the simpler the explanation the better.

---

### Post by Jon_Messenger on 2015-01-25
Answered my own question by removing and then reconnecting on Windows laptop using the MS printer driver instead of Kodak. Another lesson learned.

---

