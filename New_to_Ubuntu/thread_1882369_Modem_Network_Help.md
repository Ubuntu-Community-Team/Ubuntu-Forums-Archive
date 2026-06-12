---
title: "Modem Network Help"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by lolly325 on 2011-11-17
I've got a one networking problem, please help me out !
Firstly, my modem is based for Windows that contain .exe file that need to be installed if i want to connect to the internet. without installing, i can't reach the network.

And I have Ubuntu. I've install that .exe with wine, but I can't connect anything ....
So, I need your help please....
And I post this thread from my sister's notebook that based with windows.

IS there any help for me to connect internet ?

---

### Post by arochester on 2011-11-17
Modem...Make? Model? Chipset? Details?

---

### Post by Gotlieb on 2011-11-17
Hi lolly325,

We need more details, what type of modem are you using? Ubuntu has an applet that allows you to run Internet Modem Devices which is straight forward. Please give more details, Wine might make it look like its installed but not so please DETAILS :)

---

### Post by lkraemer on 2011-11-17
lolly325,
If you are talking about a CABLE Modem, or DSL Modem, you don't need to
have Windows Software to install anything.  Some companies (like Qwest)
send a CD that installs on Windows and just puts your Username and Password
in the Setup of the Modem.

You can call your Provider and get your Username and Password and insert
those in your Modem yourself.  Most Modems have a Setup Page like
192.168.0.1, or 192.168.1.1, or some other specific address.  You can use
Google to search for the proper address according to your Specific Modem.

So, like others have posted we need more details.

lk

---

### Post by grahammechanical on 2011-11-17
You should also tell us what version of Ubuntu you are using. If you are using 11.10 Oneiric Ocelot then you should use the Dash and search for Help and read the Ubuntu Desktop Guide.

If you have a dial-up modem, then you need a program that will activate the modem when you want to connect to the Internet. Go to the Ubuntu Software Centre and search for GNOME PPP.

As the others have said, in Linux you do not need Windows drivers. In most cases the drivers are built in already.

Regards.

---

### Post by lolly325 on 2011-11-18
ok, ok,
It is a usb-stick modem.
Inside the modem, there is an .EXE file

Firstly, I've plug my modem, and I checked out my network applet, there is no modem connection ..
and, I found from google, the problem from help.ubuntu.com, but, I don't understand much....

---

### Post by lkraemer on 2011-11-18
lolly325,
USB Stick Modem.....What is the Manufacture name & model Number?  Is it for
3G/4G or Dialup Connection (Phone Line)?

OK, Open a Terminal Window (Console) and type the following Command:
```

lsusb

```

Then plug in the USB Stick Modem, wait 30 seconds, and repeat the command by depressing the
UP ARROW key on your keyboard.  You should see a difference in the two listings.  A line should
be added displaying information on your USB Device.

Please copy and paste that information to your posting or attach that information as a text file.

As an example, I've ran the command and then plugged in my USB to Serial
Adapter and I get:
```

larry@debian:~$ lsusb
Bus 002 Device 004: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5130 IMC Networks 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
larry@debian:~$ lsusb
**Bus 002 Device 007: ID 058f:9720 Alcor Micro Corp. USB-Serial Adapter**
Bus 002 Device 006: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5130 IMC Networks 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
larry@debian:~$

```

Now I can get more information by adding a couple of options to lsusb,
by adding the VENDOR : PRODUCT information 058f:9720.

```

lsusb -v -d 058f:9720

```

Post this information also.
 
lk

---

