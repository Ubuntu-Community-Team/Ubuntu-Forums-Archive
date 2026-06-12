---
title: "[SOLVED] Connecting to Internet via Dial-up"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by lhb1142 on 2008-06-17
I am completely new to Ubuntu Linux having recently installed the "Hardy Heron" version. I am very satisfied with the results so far with two, one relatively minor, one major {for me) exceptions. (Please note that I own two Ubuntu books - UBUNTU LINUX by William von Hagen [2007] and THE OFFICIAL UBUNTU BOOK Second Edition by Benjamin Mako Hill et. al. [2007].)

The first problem that I am having is the lesser in importance of the two; it concerns playing "protected" DVDs. No matter what I have tried (and this includes reading the instructions from the books as well as trying to find directions I can understand online), I have been unable to play one. I wish that in future releases, the process of adding this capability could be made easier for people like me.

The second problem is of more importance to me. I found it very easy to connect to the internet via my wireless router but I cannot connect via my dial-up service (EarthLink) via a telephone cable.

The reason I really need this capability is because, when I go on vacation, I must engage in online banking and other financial transactions and I certainly will not do this via a hotel's Wi-Fi (even if it's "encrypted;" after all, every other guest in the hotel will have the key also!). Even a wired LAN is not safe for this activity, in my opinion. I would like to have the capability of easily setting up my dial-up service and connecting to the internet via a telephone line for these financial purposes.

Is there any chance that this process will be made easier with the next release? I do not know to whom to write concerning this so I am posting this here. I apologize if this has been answered "a million times" before. I found no information at all concerning dial-up connections in either of my two books.

Thank you for any help and answers you can give me.

---

### Post by Duck2006 on 2008-06-17
This may help.

[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html)

[http://ubuntuforums.org/showthread.php?t=126810](http://ubuntuforums.org/showthread.php?t=126810)

---

### Post by phidia on 2008-06-17
Dial up is something of a "old" technology and with the spread of broadband things are not getting better. A laptop's internal modem is very likely to be a winmodem (basically a modem that uses windows to function) Many of those can be made to work but you need to discover what chipset your internal modem uses. 
If you go [here]("http://www.linmodems.org/") and follow the guides there you may be able to get it working. There are also guides specific to ubuntu-check the community docs (see my sig).

---

### Post by fatality_uk on 2008-06-17
> **lhb1142 said:**
> I am completely new to Ubuntu Linux having recently installed the "Hardy Heron" version. I am very satisfied with the results so far with two, one relatively minor, one major {for me) exceptions. (Please note that I own two Ubuntu books - UBUNTU LINUX by William von Hagen [2007] and THE OFFICIAL UBUNTU BOOK Second Edition by Benjamin Mako Hill et. al. [2007].)

The first problem that I am having is the lesser in importance of the two; it concerns playing "protected" DVDs. No matter what I have tried (and this includes reading the instructions from the books as well as trying to find directions I can understand online), I have been unable to play one. I wish that in future releases, the process of adding this capability could be made easier for people like me.

The second problem is of more importance to me. I found it very easy to connect to the internet via my wireless router but I cannot connect via my dial-up service (EarthLink) via a telephone cable.

The reason I really need this capability is because, when I go on vacation, I must engage in online banking and other financial transactions and I certainly will not do this via a hotel's Wi-Fi (even if it's "encrypted;" after all, every other guest in the hotel will have the key also!). Even a wired LAN is not safe for this activity, in my opinion. I would like to have the capability of easily setting up my dial-up service and connecting to the internet via a telephone line for these financial purposes.

Is there any chance that this process will be made easier with the next release? I do not know to whom to write concerning this so I am posting this here. I apologize if this has been answered "a million times" before. I found no information at all concerning dial-up connections in either of my two books.

Thank you for any help and answers you can give me.

First issue. Ubuntu does not, in the default setup, install the codecs required to decompile DVDs and as such enable playback. These are available but there are conditions of use. Please bear that in mind.

You need to enable something called **libdvdcss2**

This is easy to do. Just open up the terminal and type the following:
```
sudo aptitude install libdvdcss2
```

This should enable DVD playback.


As for your second question. The best way to get dial-up in Ubuntu is to use one of the following two applicarions, both of which are available from add/remove programs

> KPPP/ Gnome PPP

Once you have installed these applications, you can then copy the phone numbers, and other information given to you by your service provider.

Hope this helps

---

### Post by phidia on 2008-06-17
The Gnome PPP or KPPP programs will only work if the modem is supported and with a laptop (I'm assuming a laptop since people usually are not lugging desktops around) the possiblity is close to 100% that the modem is a winmodem.

---

### Post by lhb1142 on 2008-06-17
Thanks to all for your help. I'll try the various suggestions and I hope they work. If not, I'll be back here ...

---

### Post by fatality_uk on 2008-06-17
> **phidia said:**
> The Gnome PPP or KPPP programs will only work if the modem is supported and with a laptop (I'm assuming a laptop since people usually are not lugging desktops around) the possiblity is close to 100% that the modem is a winmodem.

You assume correctly. I don't think he is lugging a midi tower under his arm! And again correct on a win-modem. Ill make sure to consult you next time before I post anything!!

---

