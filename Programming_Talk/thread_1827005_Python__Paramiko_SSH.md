---
title: "Python : Paramiko SSH"
date: 2011-08-17
forum: Programming Talk
---

### Post by Monu_93 on 2011-08-17
Hey everyone,

I use python module Paramiko in order to launch a program on a remote client.
This program aim to generate http or ftp traffic.
But the issue is that the traffic generated is **encapsulated** in the ssh channel.
So, unfortunately, i saw ssh traffic  with wireshark

So my question is : how can i solve this issue?

Thank you.
With regards, Monu_93

---

### Post by The Cog on 2011-08-18
All SSH communication is **supposed** to be encrypted, so there is no problem there. I'm not sure I understand what you are trying to do. Can you explain what this remote program is doing and what you are trying to capture in wireshark? E.g. is the program making HTTP connections to a web server on a third machine?

---

### Post by Monu_93 on 2011-08-22
The remote program aims to generate HTTP and FTP traffic.
The remote host generated HTTP and FTP traffic toward the SSH client.
I just want HTTP and FTP traffic will not encrypted in order to view with wireshark all the HTTP and FTP traffic.

---

### Post by r.darwish on 2011-08-22
Do you want to be able to see the traffic in Wireshark on a regular basis, or just temporary for debugging?
If, for some reason, you want the traffic to be always visible then why don't you run the program using an insecure method like telnet?

---

### Post by Monu_93 on 2011-08-22
First of all, thank you for replying
To answer to your question r.darwish, i want to see traffic as regular basis on wireshark.
According to you, i should use telnet. i'll try it.

Thank you.
With regards, Monu_93

---

