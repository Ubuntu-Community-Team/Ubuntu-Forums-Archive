---
title: "Visual Basic 2010 - Test RDP port"
date: 2011-12-13
forum: Programming Talk
---

### Post by Raventat on 2011-12-13
Hi all,
 
I am attempting to add functionality into server monitoring software I have developed, however I cant seem to figure out in VB 2010 what the specific coding is to check port [SIZE=2]3389 (remote desktop).[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Any advice is greatly appreicated,[/SIZE]
[SIZE=2]
Thank you![/SIZE]

---

### Post by Zugzwang on 2011-12-14
> **Raventat said:**
>  
I am attempting to add functionality into server monitoring software I have developed, however I cant seem to figure out in VB 2010 what the specific coding is to check port 3389 (remote desktop).


You might want to add what you mean by "check" - whether some application is listening, whether you can connect to it, whether some application listening to it actually follows the RDP protocol, etc...

---

### Post by Raventat on 2011-12-16
Hi Zugzwang,
 
By "check" I mean I want the program to check if the port is open and accepting new connections.
 
I realize this could be done through telnet, however my goal is to have all of the functions "behind the scenes" so to speak.
 
Thank you!

---

### Post by Zugzwang on 2011-12-18
> **Raventat said:**
> Hi Zugzwang,
 
By "check" I mean I want the program to check if the port is open and accepting new connections.
 
I realize this could be done through telnet, however my goal is to have all of the functions "behind the scenes" so to speak.
 
Thank you!

As far as I know, You should find the required information in the MSDN programmer's documentation. The keyword to search for is "socket" or "Winsock" programming. There should be a simple TCP or UDP client example somewhere, which should be easy to adapt to your problem.

---

