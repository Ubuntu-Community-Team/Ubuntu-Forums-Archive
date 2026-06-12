---
title: "I will pay (paypal) if you solve my 2 problems!"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Simbuntu on 2008-06-01
Ok. I want to use Ubuntu 7.10 gutsy and I want to sleep in the night :(
So....if you help me to solve my problem with printing (epson stylus color 400 LPT1 or lexmark X7170 USB) and capturing (samsung DV cam and KINO) I will pay 100 $ (if you solve only 1 problem 50 $).
Trust me , I'm not a kid, I'm a father (so, no time to solve Linux problem).
Please help me!

Simone.

---

### Post by kansasnoob on 2008-06-01
No one here would accept payment of any kind!

How about starting a new thread for each problem?

Or you could contact the real Ubuntu paid support team:

[http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

Believe me, you want to work thru one problem at a time right here.

---

### Post by bobnutfield on 2008-06-01
The Lexmark printer is going to be nearly impossible to get going in Linux.  Most Lexmark printers are not supported in Linux.  [www.linuxprinting.org](www.linuxprinting.org) has further details.

Most DV camera capturing problems with Kino have to do with the raw1394 module not being loaded, or having the wrong permissions.  Make sure you have the device:

/dev/raw1394

and that it is owned by users.  I am assuming your DV camera is connected by 1394 and not USB, as Kino will NOT capture from USB.

Bob

---

### Post by wolfen69 on 2008-06-01
it says [HERE]("http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Color_400") that your epson stylus should work perfect. i wont even look up the lexmark. most lexmarks will not work in linux.

did you go to system>admin>printing and add printer?

---

### Post by Sef on 2008-06-01
A) How are the printers connected: Directly or through a print server?

(According to Openprinting.org:)

1) [Epson Stylus 400]("http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Color_400") should work perfectly.

a) If hooked directly up, go to System > Administration > Printing, 

b) Hint: don't click install driver, click foward or next instead.

2)[Lexmark 7170]("http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-x7170") is a paperweight under GNU/Linux.

a)They only way to get this to work under GNU/Linux is to have a windows print server.  

b) If you don't have one an old P3 will work fine.

B) What are your problems exactly?

C) What have you done to resolve them?

---

### Post by Simbuntu on 2008-06-02
Thank you everybody.
Tonight i will use some of your advices, but I think I will need further assistance later.
Bye.
Simo.

---

### Post by Joeb454 on 2008-06-02
> **Simbuntu said:**
> Thank you everybody.
Tonight i will use some of your advices, but I think I will need further assistance later.
Bye.
Simo.

Don't hesitate to ask, it's how we learn & why we're here :)

---

### Post by hyper_ch on 2008-06-02
what can the lexmark do that the epson can't? You could also take those $ 100.- and then buy a printer that works on linux and can do exactely those things that the epson one can't :)

And if the epson can do everything that the lexmark can, take those $ 100.- and invite your wife/husband/gf/bf/some other good friends for a dinner or some place else to have some fun ;)

---

### Post by eldragon on 2008-06-02
to get your dv camera working under kino, you have to set rw privileges to /dev/raw1394 like someone here said.

to do that, do 
```

sudo chmod a+rw /dev/raw1394

```

make sure to plug your dv camera and turn it on before doing that, otherwise /dev/raw1394 wont be created.

if you still have problems you could do
```

lsmod |grep 1394

```

and post back results here.

if i fixed your problem, just buy 50$ worth of clothes / food and donate them. or pick your favorite open source project and just paypal them. :D

---

### Post by stchman on 2008-06-02
> **Simbuntu said:**
> Ok. I want to use Ubuntu 7.10 gutsy and I want to sleep in the night :(
So....if you help me to solve my problem with printing (epson stylus color 400 LPT1 or lexmark X7170 USB) and capturing (samsung DV cam and KINO) I will pay 100 $ (if you solve only 1 problem 50 $).
Trust me , I'm not a kid, I'm a father (so, no time to solve Linux problem).
Please help me!

Simone.

The Epson is not yet entered into the database.

[http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_400](http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_400)

The Lexmark printer is called a "paperweight"

[http://openprinting.org/show_printer.cgi?recnum=Lexmark-x7170](http://openprinting.org/show_printer.cgi?recnum=Lexmark-x7170)

Lexmark printers are very incompatible with Linux as Lexmark will not author drivers for them.

As far as Kino and DV capture I cannot help you.

Buy a decent HP color laser.  You can get the HP Color Laser 2605dn now at Office Depot at close out prices for under $300 and it works excellent with Linux.

---

