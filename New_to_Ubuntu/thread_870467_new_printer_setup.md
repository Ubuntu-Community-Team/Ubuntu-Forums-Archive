---
title: "new printer setup"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-25
hi I got an HP printer C7200.  It's real nice but I don't know what to do to get it started.  this is as far as I got   when I double click setup.exe an install wizard pops up  starts to check my system then disappears.  I don't know much about setting anything up so any help is appreciated.

---

### Post by phidia on 2008-07-25
From the Gnome desktop click on System>Admin>Printing when the printing manager opens click the "New Printer" tab. Select HP and use the recommended driver. 
BTW exe file are for windows or wine only.

---

### Post by Sef on 2008-07-25
> hi I got an HP printer C7200. It's real nice but I don't know what to do to get it started. this is as far as I got when I double click setup.exe an install wizard pops up starts to check my system then disappears. I don't know much about setting anything up so any help is appreciated.

Just plug it in.  It will work [out of the box]("http://hplip.sourceforge.net/models/photosmart/photosmart_7200_series.html") (ootb.)  Nothing needed to install.

---

### Post by adamogardner on 2008-07-25
my driver isn't listed  I have photosmart 7200.  should I go with another?  where is mine?

how does it work out of the box?  I think I need a driver.

---

### Post by adamogardner on 2008-07-25
oh hey I think it's working....

---

### Post by Sef on 2008-07-25
> my driver isn't listed I have photosmart 7200. should I go with another? where is mine?

how does it work out of the box? I think I need a driver.

The driver is provided with the kernel.  The very bottom of the link is Ubuntu.  Have you plugged your printer in and see if it prints?  If not, what happens? Any error messages?

---

### Post by Bucky Ball on 2008-07-25
> oh hey I think it's working....

It is or it isn't? Please let us know and let us know how you got it working if it is. :)

As Sef mentioned, the driver is in the kernel (along with a million others).

---

### Post by adamogardner on 2008-07-25
i notice the right click doesn't let me print.  what are the avenues to print something.  I know the print icon on firefox.  i guess I know how to print word documents too from icon.  how else?  cli?    the printer works  I'm so pleased.

---

### Post by jimrz on 2008-07-25
<ctrl> + P

---

### Post by adamogardner on 2008-07-25
yes I realized that one too.  been using all the other ctrl combos so why not?  Hey so orget all that.  What is xsane and how do I work a scanner?

---

### Post by Sef on 2008-07-25
> i notice the right click doesn't let me print. what are the avenues to print something. I know the print icon on firefox. i guess I know how to print word documents too from icon. how else? cli? the printer works I'm so pleased.

There is not a right click on the icon to print for GNU/Linux.  There is  command line to print, but I am not sure what it is at the moment.

---

### Post by Sef on 2008-07-25
> What is xsane and how do I work a scanner?

Xsane is for scanning.  Applications > Graphics > Xsane Image Scanner

If you have an HP PSC, it almost always works out of the box (ootb.)

---

### Post by ramjet_1953 on 2008-07-25
Here is a listing for your printer in the Linux Printing Database:

[http://openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C7200](http://openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C7200)

By far the best way to install HP printers is to use [COLOR="Blue"]hp-setup[/COLOR], as you also can then use [COLOR="Blue"]hp-toolbox[/COLOR]. Hp-Toolbox allows you full control over your printer, including head cleaning and ink level monitoring.

Firstly, you need to install the Python qt3 bindings.
In a terminal copy and paste this code:

```
sudo apt-get install python-qt3
```

Now, check that you have the [COLOR="Blue"]hplip[/COLOR] package installed, by doing a search for it in Synaptic package manager.

Once you have confirmed that [COLOR="Blue"]hplip[/COLOR] is installed, open a terminal and copy and paste this command into it:

```
sudo hp-setup
```

A window will open and guide you through the setup.

A test page will then be printed.

Now you can open [COLOR="Blue"]hp-toolbox[/COLOR] and see all of the goodies available:

In a terminal copy and paste this code:

```
hp-toolbox
```

If hp-toolbox has not automatically been inserted into your menu, you can add it manually by navigating to [COLOR="Blue"]System>Preferences>Main Menu[/COLOR].

Regards,
Roger :cool:

---

### Post by Sef on 2008-07-25
> By far the best way to install HP printers is to use hp-setup, as you also can then use hp-toolbox. Hp-Toolbox allows you full control over your printer, including head cleaning and ink level monitoring.

Easy way to install the HPLIP Toolbox:

Applications > Add/Remove > Search: HPLIP > Click on the box next to HPLIP Toolbox > apply changes > apply > close.

To find the toolbox: System > Preferences > HPLIP Toolbox.

---

### Post by adamogardner on 2008-07-25
My main man Roger!  you gave me the hp-toolbox.

---

### Post by jsmac8218 on 2008-11-28
RAMJet_1953

Your post above was the biggest help, thank you. I am also trying to connect my Ubuntu 8.04 to an HP Photosmart C7280 using a wireless connection. I can ping the printer using the printer IP address and my laptop is connected to my netwoirk wirelessly, I can see all my shared drives and the Internet, but, when I run hp-setup and choose 1-network/wireless it does not auto detect the printer. I selected "Find Manually" and entered the IP address and it says "0 devices found on network at address 192.168.1.108" Since I use several wireless PCs on this network I hard set the IP address on the printer so I am sure that is the right IP address.

I really do not know anything about Linux and only got this far because of this post, HPLIP version installed on my new PC is 2.8.2-0ubuntu8 which came with ubuntu 8.04 and my new Dell mini 9. Any help is appreciated.

---

