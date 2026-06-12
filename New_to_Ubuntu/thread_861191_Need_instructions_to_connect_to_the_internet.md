---
title: "Need instructions to connect to the internet"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Struggling1 on 2008-07-16
Hi,
I recently purchased a new hard drive and have had Ubuntu installed.  I am not able to access the internet using my modem - broadband, ADSL (The ISP is Alice in Germany.  It worked perfectly fine when I had Windows.
I have tried going to the help menu and all that sudo pppoe conf business doesn't help.  When I click on "ping" it shows that 0% of the "packets" were received or something.
I'm not a computer geek, and would really appreciate it if someone could just give me clear instructions on how to make ubuntu work with my modem.  I am at my wits' end!
PS - the person who installed it for me has since left the country and I don't know anyone else who knows anything about Ubuntu here in Germany.
Please help!  I'm paying my ISP for internet access at home and yet I am not using it!!

---

### Post by dracayr on 2008-07-16
Do you know your modem's IP? If not, it will probably be 192.168.1.1 or 192.168.2.1 (I found that 192.168.2.1 is more popular in germany)
I have no Idea If there's sth. different with modems, but this is what I would do If it was a router:
Replace XXX.XXX.XXX.XXX with the Ip of the router
Replace YYY.YYY.YYY.YYY with the IP you want to have (the first 3 sections have to be the same ones of the modem)
Open a terminal (Anwendungen->Zubehör->Terminal) and execute

[CODE]ifconfig eth0 YYY.YYY.YYY.YYY
route add default gateway XXX.XXX.XXX.XXX[CODE]

dracayr

---

### Post by halitech on 2008-07-16
can you open a terminal and post the output of 

```
ifconfig
```

this will tell us if your network card is being seen or not

---

### Post by steveneddy on 2008-07-16
> **Struggling1 said:**
>  I don't know anyone else who knows anything about Ubuntu here in Germany.


I thought that Ubuntu and Linux were very popular in Germany.

---

### Post by halitech on 2008-07-16
it is supposed to be but he may be in an area with few users. I live in an area with a very active LUG but not one of my friends uses it and other then the ones I talk to about computers they dont know what it is

---

### Post by Struggling1 on 2008-07-18
> **dracayr said:**
> Do you know your modem's IP? If not, it will probably be 192.168.1.1 or 192.168.2.1 (I found that 192.168.2.1 is more popular in germany)
I have no Idea If there's sth. different with modems, but this is what I would do If it was a router:
Replace XXX.XXX.XXX.XXX with the Ip of the router
Replace YYY.YYY.YYY.YYY with the IP you want to have (the first 3 sections have to be the same ones of the modem)
Open a terminal (Anwendungen->Zubehör->Terminal) and execute

[CODE]ifconfig eth0 YYY.YYY.YYY.YYY
route add default gateway XXX.XXX.XXX.XXX[CODE]

dracayr

YOU ARE A GENIUS!  IT WORKED!  I AM WRITING TO YOU FROM HOME.  HURRAY!:popcorn: Have a great weekend. :-)

---

