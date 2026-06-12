---
title: "Cannot see folders and shared files."
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Settler on 2008-10-05
Hello,

I have successfully installed ubuntu linux and first days first question.

1. I have removed transmission and added azureus torrent client. The sad is i cannot see the /home/home/.azureus/torrent folder anywhere. I can find the file by search but i think this is not the right way.

2. What are the folders with a point in fron of them like /home/home/.screenlets

3. How can I "see" the shared files of a Windows PC in my LAN. I'm asking this beacause when I was running the live cd to see if I like ubuntu or not by just clicking places -> network I saw the shared.

4. How do I put a static LAN IP address to my linux pc? I need firewall to be fixed that's why.


Thanks to all in advance!

---

### Post by cjv8888 on 2008-10-05
The files with a dot in front are hidden files.

Go to View/show hidden files and press Ctrl+H

To see the shared windows files, 

go to Places - Network

then put smb://
followed by the IP address of the Windows computer eg 192.168.1.100
depending on your home network

---

### Post by Settler on 2008-10-05
thanks a lot! 1,2,3 questions are solved. Only 4 is up.

---

### Post by cjv8888 on 2008-10-05
Do you mean the ip address assigned to your computer by the router?

That will depend on the router.

Generally if you do not turn off the router and the modem at the power switch, then the ip address should remain the same.

Does that answer your question?

---

### Post by Settler on 2008-10-05
Not exactly. I want my pc IP address to be 192.168.1.2 and gateway 192.168.1.1.

Where do i assign my pc address to be 192.168.1.2?

that is the exact question

---

### Post by Settler on 2008-10-05
anyone can help?

How do I give my pc a static ip i want?

---

### Post by Levo on 2008-10-05
System->System Administration->Network
Press the Unlock button and enter your password. Then select your Network Adapter and press Properties.

---

### Post by Settler on 2008-10-05
thanks!

---

