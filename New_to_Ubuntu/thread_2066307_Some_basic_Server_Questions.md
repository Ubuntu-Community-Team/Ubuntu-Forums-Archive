---
title: "Some basic Server Questions"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by pstonge on 2012-10-04
Hey guys, new to ubuntu, but very interested in learning it.
 
I just have a few simple questions that i need to be cleared up.
 
I have to setup a ubuntu server at work with Apache2, Perl, and Squid. I can figure that out, but my main concern is;
 
Can I use/download a GUI for Ubuntu 12.04 Server?
 
If i download the 12.04 Desktop, and after i set up the above programs, can I remove the GUI, and give it that server feel, or is desktop different from server other then the GUI?
 
And also I seen when downloaded 12.04 the 64bit was recommended, would i have issues with the 32 bit?
 
 
Thanks everyone
Paul

---

### Post by 1clue on 2012-10-04
The fundamental difference between server and desktop is that the server has no GUI.

Pretty much anything you can do with server can be done with the desktop version as well, and vice versa.

You can install a GUI on server, but why uninstall it later?  If you're unfamiliar with configuring things with the command line, then use a GUI.

Ubuntu Server was built so that people who are running a data center can have a super small image that can be installed quickly and easily onto systems which have no monitor, keyboard or mouse, or which may have them hooked up to a switch so many computers can use the same peripherals.  It's also handy for virtual machines.

64/32:
If you have 32-bit hardware then the only thing that will work is a 32-bit OS.
If you have 64-bit hardware then you can choose an OS for 64, 32 or both (multi-lib).
There may still be apps which only have 32 bit support, but IMO if you have 64-bit hardware then you should choose either 64-bit or multi-lib.

---

### Post by jerrrys on 2012-10-04
Can I use/download a GUI for Ubuntu 12.04 Server?

yep, check this out

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=server+gui&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=server+gui&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by cway00 on 2012-10-04
> **pstonge said:**
> Hey guys, new to ubuntu, but very interested in learning it.
 
I just have a few simple questions that i need to be cleared up.
 
I have to setup a ubuntu server at work with Apache2, Perl, and Squid. I can figure that out, but my main concern is;
 
Can I use/download a GUI for Ubuntu 12.04 Server?
 
If i download the 12.04 Desktop, and after i set up the above programs, can I remove the GUI, and give it that server feel, or is desktop different from server other then the GUI?
 
And also I seen when downloaded 12.04 the 64bit was recommended, would i have issues with the 32 bit?
 
 
Thanks everyone
Paul

First of all I will advice you to make the move and download and install the 32bit despite the recommended notification on the 64bit server and it is based on your hardware..if they Board iwas made for 32 Bit OS or 64Bit OS  ..nd when u download the Server not the Desktop..It will end up being a black login screen..but seems u r new to Ubutu like me will advice you to download the desktop version nd after your server has been fully developed and ready for  .then you can start removing the default gui..gnome3 ..

---

### Post by 1clue on 2012-10-04
Personally I would recommend xfce.  Which means either start with server and install the xubuntu package or start with xubuntu.

---

### Post by androssofer on 2012-10-04
> **pstonge said:**
> Hey guys, new to ubuntu, but very interested in learning it.
 
I just have a few simple questions that i need to be cleared up.
 
I have to setup a ubuntu server at work with Apache2, Perl, and Squid. I can figure that out, but my main concern is;
 
Can I use/download a GUI for Ubuntu 12.04 Server?
 
If i download the 12.04 Desktop, and after i set up the above programs, can I remove the GUI, and give it that server feel, or is desktop different from server other then the GUI?
 
And also I seen when downloaded 12.04 the 64bit was recommended, would i have issues with the 32 bit?
 
 
Thanks everyone
Paul


As mentioned above the GUI is the only main difference. They also come with different programs pre-installed, but you can install whats on the other easy enough..

if your not totally comfortable with the CLI, you can try using webmin:

[http://www.ubuntugeek.com/how-to-install-webmin-on-ubuntu-12-04-precise-server.html](http://www.ubuntugeek.com/how-to-install-webmin-on-ubuntu-12-04-precise-server.html)

it allows you to configure your server remotely through a browser. and will mean you don't need to install a clunky GUI, and so save a bit of space and ram..

---

### Post by snowpine on 2012-10-04
Administering your sever using the terminal (no GUI) doesn't have to be intimidating. Here is an easy-to-follow guide for Ubuntu Server: [https://help.ubuntu.com/12.04/serverguide/](https://help.ubuntu.com/12.04/serverguide/)

---

