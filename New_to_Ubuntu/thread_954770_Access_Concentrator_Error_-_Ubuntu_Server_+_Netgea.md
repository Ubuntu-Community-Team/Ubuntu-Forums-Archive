---
title: "Access Concentrator Error - Ubuntu Server + Netgear"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by expza on 2008-10-21
Hi everyone, COMPLETE novice to Ubuntu / Linux here.

I'm trying to set my spare pc up as an internet gateway and one of the steps involves me going to pppoeconf and setting up a few things there. Running into some problems as I get the following error message after scanning:

[IMG]http://i74.photobucket.com/albums/i266/mikemullany/DSC00225.jpg[/IMG]

Here's the deal:
Ubuntu Server 8.04
Netgear DG 834 GT (IP 192.168.0.1)

I have set it to Modem mode using that special hidden menu.

I tried editing my network interfaces to give my spare pc a static ip and despite it working, still same error.
I can ping the router fine.

[IMG]http://i74.photobucket.com/albums/i266/mikemullany/DSC00227.jpg[/IMG]

Last but not least, if I type in IPConfig it says the command doesnt exist.

Step by step of what im doing:
Turning on PC
Logging in with username mike and password ****
type su
log in using password (already set it up) - then reports "Root@MikeuBuntu ect ect"
Type pppoeconf
Choose Yes, gives me that error message.

Is it odd that ipconfig isn't working?

Thanks in advance.
Mike

---

### Post by expza on 2008-10-21
Could it be that my router doesn't support this type of connection?

...

Which doesn't make any sense at all.
I'm thinking that since I configured my Ubuntu while it was in "Router mode" and now it's in "Modem Mode", it doesn't like something.

Please help :)
Thanks.

---

### Post by eks on 2008-10-21
There's no ipconfig on linux, it's actually called ifconfig, with an F instead of a P.

Yes, I also find it weird. :)

Besides that, try searching for "internet connection sharing ubuntu" on google. It was on my last home I had something like that, so it's a bit forgotten already. But no idea about the problem you are having... :?

---

### Post by expza on 2008-10-22
Haha, IFConfig works ;)

Tried searching like crazy but with no luck.
Ugh.

---

### Post by expza on 2008-10-22
Tried switching my network card and reinstalling. Let's see...

---

