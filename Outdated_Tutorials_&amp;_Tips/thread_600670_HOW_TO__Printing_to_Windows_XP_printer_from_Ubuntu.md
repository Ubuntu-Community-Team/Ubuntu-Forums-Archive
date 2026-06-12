---
title: "HOW TO : Printing to Windows XP printer from Ubuntu Gutsy"
date: 2007-11-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Claus7 on 2007-11-02
Hello,

while trying to find a solution to this problem I have to say that I didn't come across a definite how to. These are the steps I followed on how to configure my ubuntu gutsy pc in order to print to a windows xp machine. Both of these computers share the same network. 

Before you do anything go to synaptic and install samba.

1) Go to System -> Administration -> Printing

There choose the New Printer icon.

2) Select Network Printer and Windows Printer via Samba

There you will see a small window on your right. There there is a smb// option in which you should type very carefuly three different things :
the_name_of_the_WORKGROUP/the_ip_address_of_the_windows_machine/the_name_of_the_printer

for example ubuntu/123.456.78.90/HPdeskjet

Click the next box, put your username and password (of your ubuntu machine) click forward and you are ok. In order to verify your success print a test page (the windows machine should be open, also it should allow other computers to connect to it-for the latter the solution might be here [https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)).

In order to find the name of the workgroup (from [http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+printer](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+printer)) :
To find out the Workgroup name in Windows follow these steps:

- Click "START"
- Click "Control Panel"
- Click "System"
- Click the 2nd Tab entitled "Computername" and find the name of the Workgroup there.

I hope this is helpful,
Regards!

---

### Post by H3retic on 2007-12-08
Thanks for posting this.  I've been wrestling with gutsy's "upgraded" print dialog ever since I upgraded from 7.04.  This really cleared it up for me!

---

### Post by TUOggy on 2008-04-11
is there anyway to do this for networks that use dynamic ip or are we going to have to just keep changing the ip address?

EDIT: I answered my own question.  If you put the name of the computer in place of its IP, then it should do the same thing.  This way you don't have to worry about the IP address constantly being a pain.

---

