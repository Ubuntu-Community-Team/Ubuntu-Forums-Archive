---
title: "Hardy Heron E220"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by mormor on 2008-04-28
Linux cant find the modem, when I plug it in. Worked fine in 7.10. So I try a couple of fixes I find on web, but I cannot seem to get it to work. (Last time I got "broken package". So I started again, downloaded the 2.0 driver from vodafone, try to install it through Packageinstaller and get this error:

Package: Vodafone-Mobile-Connect-Driver-For-Linux
Status:  Error: Dependency is not satisfiable: Python-Twisted

Anyone have any idea on how to get it to work?

(I need very basic, babysteps yet, as I am not very confident with ubuntu.)

Thanks in advance.

---

### Post by dearingj on 2008-04-28
You'll need to install the python-twisted package.

The graphical way:
Open up Synaptics (System->Administration->Synaptic Package Manager) and search for python-twisted. Then right-click on the package and click "mark for installation". Synaptic will ask if you want to mark some other required changes, click "confirm". Click the apply button. A new window will open to confirm that you've marked everything you want to install; click its apply button.

The text-based way:
Open a terminal (Applications->Accessories->Terminal)
type in "sudo apt-get install python-twisted"
put in your password if asked (it won't show up on screen)
Press Y when it asks if you want to continue.

---

### Post by mormor on 2008-04-28
Cant find it in synaptic packagemanager, so tryed the Terminal-way, wich did not really work.

Any Ideas?

"

marius@tobor:~$ sudo apt-get install python-twisted
[sudo] password for marius: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-twisted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-twisted has no installation candidate
marius@tobor:~$ 

"

---

### Post by Michael.Godawski on 2008-04-28
I have found some python-twisted packages on this site, but which is the right I cannot tell, perhaps core and bin and the first one?:

[http://packages.ubuntu.com/search?searchon=names&keywords=python-twisted](http://packages.ubuntu.com/search?searchon=names&keywords=python-twisted)

---

### Post by dearingj on 2008-04-28
Your modem driver depends on python-twisted (the main package). Python-twisted, in turn, depends on all the packages listed here:
[http://packages.ubuntu.com/hardy/python-twisted](http://packages.ubuntu.com/hardy/python-twisted)

I think you'll need to install every one listed on that page.

---

### Post by anaconda on 2008-04-28
I use my e220 with gnome-ppp. Works like a dream.

I never got vodafones program working properly. 
(actually I got vodafones program installed and I suppose it would work, but dont know all the settings that it would need)

Oh.. and gnome-ppp doesnt use python.. and the commandline alternative wvdial doesnt use python either.

---

### Post by mormor on 2008-04-28
I got the program installed now, together with all the python thingies it wanted. The GUI is working, it locates the modem, had a smal problem though. Switching off my wlan, and connecting with the modem, made firefox go to offlinemode, and thus I could not open any webpages. But now it works.

Beta 2.0 + updated packages = Ace. Thnx for the help. Never going back to windows (except maybe xp when I want to play games:P )

---

### Post by cvmostert on 2008-05-13
Please explain how you made the connection with gnome-ppp so others who also have problems with the vodafone program can do what you did. 

Thanks!

---

### Post by spegru on 2008-06-01
Just got mine working in KDE (havn't tried gnome yet) using kppp
One thing that stumped me for ages was that Firefox was being way too clever for me and switching itself into offline mode when I disconnected my wlan
Funnily enough of course this prevented firefox from accessing any websites!
Switch offline mode off from the File menu and everything is fine!

Looks like I've had the modem itself working for ages! (I wondered why the light came on but provided no internet access?!?)

Moral: If no access even when the modem seems to be working, look out to see if your browser is in offline mode!

spegru

---

### Post by jacklsw2008 on 2008-06-08
i'm using e220 and i downloaded the vodafone linux driver for e220. it did detect the 3G signal but seems to take forever to connect. anybody knows how can i fix this?

---

### Post by Sealbhach on 2008-06-08
[QUOTE=dearingj]Your modem driver depends on python-twisted (the main package). Python-twisted, in turn, depends on all the packages listed here:
[http://packages.ubuntu.com/hardy/python-twisted](http://packages.ubuntu.com/hardy/python-twisted)

I think you'll need to install every one listed on that page. [/QUOTE]
You don't need to go through all that. You can connect using Gnome-PPP, without having to use the Vodafone driver.

[QUOTE=spegru]One thing that stumped me for ages was that Firefox was being way too clever for me and switching itself into offline mode when I disconnected my wlan.[/QUOTE]
Network Manager does that. I uninstalled Network Manager as my only external connection I'm using is the E220 dial-up.
[QUOTE=cvmostert]
Please explain how you made the connection with gnome-ppp so others who also have problems with the vodafone program can do what you did.[/QUOTE]

Install Gnome-PPP

> sudo-apt-get install gnome-ppp

You'll find it in the Applications/Internet Menu.

Click Setup:

Modem Tab:

Device: /dev/ttyUSB0
Type: Analog Modem
Speed: 460800
Phone Line: Tone
Volume: High
NB: Uncheck "Wait for Dialtone" (if checked)

Networking Tab:

Dynamic IP Address
DNS: Automatic DNS

Options Tab:

Check all Connection Options except "Send Custom Reply".

When you connect the modem to the USB, wait till the green light stops flashing, then in terminal type:

```
sudo wvdialconf

```

This will find your modem.
You may find on start-up that Gnome-PPP cannot detect modem. When this happens I just reboot and it finds it.


Let me know if this works.

---

