---
title: "Dial Up Networking with Oneiric SERVER"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by RoundTuit on 2012-06-26
I installed ubuntu server (no GUI) and I am now trying to attach my cell phone via USB (for which I have found splendid instructions) BUT I need to install wvdial which appears to no longer be distributed with this version [oneiric](??). I have figured out how to mount the install cd, but when I run apt-get update and then apt-get install wvdial it tells me the package is not found. Is there a replacement for it? Is there another way to install it?

Although I have 35 years of computer experience (mainframes, DOS, Winblows) I am new to linux so please speak Slowly and precisely ;) and leave nothing as "assumed". I have access to the Internet via my phone on my Winblows machine so I can download things and burn them to a cd.

---

### Post by roger_1960 on 2012-06-26
Hi

To clarify, are you trying to use the mobile phones data service 3G, edge etc. on your server or are you trying to use the mobile phone to connect to an old fashioned dial up connection?    Also, what is your server going to serve via a dial up connection?

---

### Post by RoundTuit on 2012-06-26
Thank for replying. I'm going to use the phone's PPP connection. Under Winbloze, it's set up as a dial up connection. It works well and is stable that way, so I would prefer to keep that arrangement. I have complete directions for setting it up to work that way, but I just can't seem to find how to set up wvdial in ubuntu server (oneiric). For now it would be just for the ubuntu server to communicate with the web, but in the future (not too distant) I may want to add the Winbloze machine sharing the connection.

Oh, and by going through as a dial-up connection, I bypass my carrier's proxy server and get my own external IP.

---

### Post by roger_1960 on 2012-06-26
Have you looked at the manual page for wvdial, code in terminal:

> man wvdial

and the links to other "man" pages at the end of that page?

---

### Post by RoundTuit on 2012-06-26
It says "No manual entry for wvdial" :(

---

### Post by RoundTuit on 2012-07-05
After much head banging I was able to manage to install wvdial after :

    1) networking the ubuntu box to my winbloze machine.
    2) setting up a small proxy server (3proxy) on my winbloze machine.
    3) Configuring apt-get to run through the proxy.
    4) doing apt-get update and apt-get upgrade through the proxy.
    5) running apt-get install wvdial. (It works after the above)
    6) undoing 1-4 above.
    7) following this wonderful mini-tutorial to set up my phone:

[http://ubuntuforums.org/showthread.php?t=780339](http://ubuntuforums.org/showthread.php?t=780339)

My server is now happily talking to the world.

---

