---
title: "how can i set up five computers in a private network ,different distros."
date: 2008-08-15
forum: New to Ubuntu
---

### Post by cmay on 2008-08-15
hi.
i was just wondering if any one could help me whit this .
i have five old computers i got second hand. i want to beta test different distros but i want one computer that can store all my personal files so that i can acces it from the other computers. i dont have a clue about how this works but i have a router whit four inserts. the distros i currently use is ubuntu /debian testing /freebsd / open-solaris. and i have minix3 and freedos but these i dont need to consider regarding to this question.:)

the point is to have so many testing distributions running as possible
and i will maybe get rid of the solaris and bsd in favor of the ubuntu testing version. 
but as far as to transport all my files from pc to pc whit usb stick i have a usb-stick problem that rules this out as of the moment. 
any help would be of great value. 
thanks

---

### Post by TJCIB on 2008-08-15
Seems like NFS would be good.  

Here is a basic how to [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

It has good resources.  NFS can be as secure/unsecure or confusing/simple as you want.

You would have one computer act as a "server" and share the directories that you want to access from all your other clients.  It even works sharing to Windows with the help of some small (free) software that Microsoft put out.
I do this at my small private school with 15 computer, 10 being various Linux distros and the others being XP.

**edit**
I forgot to mention that you would not be "transporting" files then, you would simply be accessing them from a client.  Changes and everything will be made to the server box, and you can easily mount and unmount the directories as you see fit.  There really is no "transportation" involved.

---

### Post by cmay on 2008-08-15
thanks . i will try reading this.

---

