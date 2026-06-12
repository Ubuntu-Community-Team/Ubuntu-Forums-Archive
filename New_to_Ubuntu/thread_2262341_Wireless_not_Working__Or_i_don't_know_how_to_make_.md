---
title: "Wireless not Working / Or i don't know how to make them work?"
date: 2015-01-24
forum: New to Ubuntu
---

### Post by chris341 on 2015-01-24
Hello. I am an advanced Windows user. I have just installed ubuntu.

But i can't connect to my wifi. When i click the icon, there are not available networks. I can just use ethernet.
I need help. Can someone help me please to connect to my network?

Also, i am a new user to Ubuntu.

---

### Post by arochester on 2015-01-24
Open a Terminal.

Issue the command: lspci |grep Network

What is the result? Can you copy and paste here?

---

### Post by chris341 on 2015-01-24
3:00.0 Network controller: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter

Also, I am using version 14.04.1 lts

Please help, i am a laptop user and i can't use always ethernet :/

---

### Post by ptn107 on 2015-01-24
Maybe [_this_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146/comments/214") will work for you.  It looks like there is mixed success.  Follow directions carefully.

---

### Post by chris341 on 2015-01-24
> **ptn107 said:**
> Maybe [_this_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146/comments/214") will work for you.  It looks like there is mixed success.  Follow directions carefully.

How can i install this?
I am preatty new to Ubuntu

---

### Post by ajgreeny on 2015-01-24
Here is one solution from a week ago which is worth trying.
[http://ubuntuforums.org/showthread.php?t=2260590](http://ubuntuforums.org/showthread.php?t=2260590)

---

