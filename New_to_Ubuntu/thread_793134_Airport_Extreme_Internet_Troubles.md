---
title: "Airport Extreme Internet Troubles"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by shrummin_newman on 2008-05-13
Hello, I have been using linux now for about 6 months and I have noticed something odd with regards to my internet connection.  When connected to a generic router for wireless internet, linux connects to the internet fine.  However, whenever I try to connect to a wireless network set-up using an apple airport, it never connects and never really tells me I can't connect.  It just continually tries to connect without doing so.  Any help with the subject is appreciated however, you are going to have to bear with me, I am using a dual boot so any posts will take a little time to respond to.

Thank You Kindly

---

### Post by mlentink on 2008-05-13
Is your Airport perhaps configured to use Bonjour only? Bonjour is Apple's iteration of a zero-configuration protocol, which seems to work mainly on Apple products.
I might be mistaken, I really don't know Apple products that well...

---

### Post by cyberbill on 2008-05-13
How are the two routers setup?

Plug one into the other [modem]-[router1]-[router2] so both have internet access.
Start off with different SSIDs and running on different channels to minimize interference.
Use the same encryption type on both (WEP/WPA/WPA2) but use different keys.

Post any non-private info you can give. I would imagine it is related to a router setting and not ubuntu.

-cb

---

### Post by shrummin_newman on 2008-05-13
cyberbill, you misunderstood me.  The two airports are in different locations but I have trouble connecting to both of them which led me to believe that the problem was no specific to the one but a general problem with connecting to airports

---

### Post by shrummin_newman on 2008-05-13
what kind of info do you need
im relatively new at linux and
dont really now what can be useful.

---

### Post by cyberbill on 2008-05-13
My misunderstanding.
I am still curious about the encryption.
Found this, might want to give it a try, hope it will help.

[http://ubuntuforums.org/showthread.php?t=209929](http://ubuntuforums.org/showthread.php?t=209929)

-cb

---

### Post by shrummin_newman on 2008-05-13
Its a WEP-128 encryption 
ill try tthe other post but i think i
may have already done that

---

### Post by shrummin_newman on 2008-05-13
I tried using the WEP 64/128 Bit Hexadecimal
security but when I entered the password (which is 13
characters) the hexadecimal option only allowed 10.
I also tried using the ASCII option which did allow for
13 characters but when I clicked login it just 
searched for the network without connecting for several
minutes.

---

### Post by cyberbill on 2008-05-13
Try this,

Goto this site:
[http://www.powerdog.com/wepkey.cgi](http://www.powerdog.com/wepkey.cgi)

Enter in the passphrase, it will convert it to the HEX string which you can then enter into the dialog. It will actually give you four different 64bit keys. If one doesn't work, try the others.

-cb

---

### Post by OldTimeTech on 2008-05-13
In the router setup have you given the ip of your machine?

---

### Post by sunstriker on 2008-05-13
Did you installed the kernel modules for the airport. I had some problems too with my mbp but I found a tutorial here somewhere and it fixed everything from suspend to connection probs...

---

### Post by Elcoco on 2008-11-14
I have this same problem, i installed the ath9k drivers and got the airport on my mac book pro working but i cant connect to the airport extreme thats doing the routing, the icon just spins forever. i have ubuntu 8.04
-laptop 2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64 GNU/Linux and an intel mbp

---

