---
title: "gnome-ppp doesn't detect modem"
date: 2012-11-22
forum: New to Ubuntu
---

### Post by Bearly Able on 2012-11-22
I need to configure a dial-up connection for my elderly friend's Xubuntu machine, but it's not detecting the on-board modem.  Running lshw produces ```
*-communication UNCLAIMED
                description: Communication controller
                product: V.92 56K WinModem
                vendor: LSI Corporation
                physical id: 5
                bus info: pci@0000:03:05.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=14 mingnt=252
                resources: memory:cfffec00-cfffecff ioport:e000(size=8) ioport:d800(size=256)
```Any help would be appreciated.

---

### Post by JKyleOKC on 2012-11-22
Here's the problem: 
> product: V.92 56K WinModemAlmost all "built-in" modems these days are WinModems, which depend upon Windows to make them work. It's possible to install drivers which might make them work in Linux, but such drivers do not always work properly.

Google for "hsfmodem" or "conexant" to find out more about such drivers. I've never gotten them to work, myself, but others apparently have had success.

The most reliable solution is to purchase an external modem that connects through USB and does NOT depend on Windows. Several such devices are available; look for advertised compatibility with Linux to be certain they are not themselves WinModems, however.

---

### Post by Bearly Able on 2012-11-22
Thanks, Jim.  I have a very old dial-up modem which is compatible, but it apparently pre-dates USB, and this machine doesn't have the correct type of connector (whatever that was :redface:).

The problem is that my friend's e-mail address was connected to her old dial-up account.  After she got broadband (with another company) it continued to work just fine, until her old machine died without warning.  Somebody gave her this one, but I can't set up the e-mail unless I connect via the dial-up account.  I was hoping I could do it just once, and that would be enough to get it up and running as before.  In the circumstances, it's not really worth buying a modem.  I'll ask around and see if I can borrow one, and in the meantime I'll set her up with a new e-mail address so we never have this problem again. :)

---

### Post by JKyleOKC on 2012-11-22
You might try googling the "hsfmodem" keyword first; it will lead you to a web site that has full instructions on trying to make things work, and it's at least worth an hour or two. The driver downloads are free for the initial installation although they have for-pay versions to support things like fax reception, and for the purpose you have in mind that should be adequate.

The socket for your older modem is probably the 9-pin that was standard for the original PCs back in 1981 and remained standard until USB took over some 15 years ago. There's an adapter available that will plug into a USB port and provide the socket, but it costs around $25 as I recall and you probably don't really need it for anything else...

---

