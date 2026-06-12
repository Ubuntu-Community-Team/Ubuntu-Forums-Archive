---
title: "my new Ubuntu and my HP printer"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Ken Gibson on 2008-07-03
I am brand new to Ubuntu and need next to find out how to connect wirelessly to my hp printer (hp photosmart C6180).  Can some one help me?

---

### Post by Daveth on 2008-07-03
might be worth trying this

[http://forums.linux-foundation.org/read.php?20,3995,4462,quote=1](http://forums.linux-foundation.org/read.php?20,3995,4462,quote=1)

or, dispair, and read this

[http://ubuntuforums.org/showthread.php?t=659837](http://ubuntuforums.org/showthread.php?t=659837)

---

### Post by ramjet_1953 on 2008-07-04
Firstly, here is a link about installing your printer under Linux:

[http://openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C6180](http://openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C6180)

However, before doing this I would suggest that you install the [COLOR="Blue"]python-qt3[/COLOR] package. This can be done using the Synaptic Package Manager, or by cutting and pasting this command into a terminal:

[COLOR="Red"]sudo apt-get install python-qt3[/COLOR]

This package is needed to use the HP utilities [COLOR="Blue"]hp-setup[/COLOR] and [COLOR="Blue"]hp-toolbox.[/COLOR]

Also, use the Synaptic package manager to check if these packages are installed:

[COLOR="Blue"]hpijs
hplip
hplip-data[/COLOR]

Now, I am not sure if hp-setup for this printer will set it up for wireless working, as I have not used it for this. However, it is worth a try. Nevertheless, initially set it up by plugging it into your PC. I imagine that bit has a USB port?

When you have all of the above installed, make sure that your printer is powered-up and plugged in. Re-boot your machine if the printer was not initially turned on.

Now, open a terminal and copy and paste this command into it:

[COLOR="Red"]sudo hp-setup[/COLOR]

It will ask for your password. Enter it.

Just follow the guided setup when the window opens.

When this has finished, copy and paste this into a terminal:

[COLOR="Red"]hp-toolbox[/COLOR] (no sudo, or password required)

This should open a window with all sorts of goodies to maintain your printer.

If this all works successfully, come back and we will then tackle the wireless issue.

Regards,
Roger :cool:

---

### Post by lucyi on 2011-07-12
Hello, if anyone is still wrestling with getting printer utilities other than print test page (clean print heads, align print heads, I tried with Synaptic Package Manager to get the files mentioned in this lovely post by Roger (ramjet_1953.)  I got the following error messages.  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_3.9.2-3ubuntu4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_3.9.2-3ubuntu4_all.deb)
  404 Not Found [IP: 91.189.92.171 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_3.9.2-3ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_3.9.2-3ubuntu4_i386.deb)
  404 Not Found [IP: 91.189.92.171 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_3.9.2-3ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_3.9.2-3ubuntu4_i386.deb)
  404 Not Found [IP: 91.189.92.171 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8-b-5ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8-b-5ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.92.171 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/sip4-qt3/python-sip4_4.7.9-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/sip4-qt3/python-sip4_4.7.9-1ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.92.171 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-qt3/python-qt3_3.17.6-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-qt3/python-qt3_3.17.6-1ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.92.171 80]


What does this mean?
Ubuntu Jaunty 9.04 (for now), Gnome. Complete noobie, 9.04 installed from a friend's CD April 2011; higher versions didn't like my computer or vice-versa so stayed with 9.04.

My old printer HP Deskjet 722C was hooked up and running fine with thus Ubuntu version, but started getting bad printing. I wanted to perform above utilities, but the utility buttons in the control or troubleshoot box were in gray. So I got a new printer, but it is not supported with this Ubuntu version and is going back to the store.  I have no printer hooked up until I can decide what I want to do next.   I am thinking about getting the ink for my old HP deskjet 722C, (I gave away the cartridges when I was borrowing someone else's AIO printer (all in one, Print, scan, Copy) so I will at least have something to work with but it needs those utilities mentioned in beginning of this antique thread.

Much obliged if anyone can answer.  This community is great!

---

### Post by pqwoerituytrueiwoq on 2011-07-12
try this
```
sudo apt-add-repository ppa:hplip-isv/ppa;sudo apt-get update;sudo apt-get upgrade
```

---

### Post by jtarin on 2011-07-12
> **lucyi said:**
> 
Much obliged if anyone can answer.  This community is great!While I realize you have a problem with your printer it is not polite in the forums to post in a thread with your problem unless the thread is marked as "solved" already. It is what is known in forum parlance as "hijacking" a thread. It is difficult enough for people to help the originator without the added difficulty of all trying to keep up with two problems in the same thread. Your co-operation is appreciated.You should start a new thread.

---

### Post by overdrank on 2011-07-12
> **jtarin said:**
> Your co-operation is appreciated.You should start a new thread.
Agreed. If you still have issue please start a new thread. Thread closed.

---

