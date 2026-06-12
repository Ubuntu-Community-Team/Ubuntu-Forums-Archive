---
title: "[SOLVED] Using Nokia 6288 as a modem?"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by ricardojcampo on 2008-10-28
G'Day Fellows,

I would like to use my Nokia 6288 as a modem to connect to the internet. I am very new to Linux/Unbuntu so I don't know where to start, or what to use. Any help will be greathly appreciated.

---

### Post by AlanR8 on 2008-10-28
Evening

I use my Nokia 6280 as a modem, in fact connected that way now! It took me a while trawling for info but here's what I do. Thanks to all who've posted in the past as I've used info from these posts and other forums.

Find the file in your /etc folder called wvdial.conf 

MAKE A COPY OF THE ORIGINAL FIRST

Then edit the file as root. I use Kubuntu (KDE) so my command is:

> sudo kate /etc/wvdial.conf

If you use a Gnome desktop you'll substitute "kate" with the name of your text editor.

When the file opens, delete the current contents and paste the following into the file:

> [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99#
Password = A
Username = B
Stupid Mode = 1

This works in the UK on the Vodafone network. You may have to find out what the user name and password is for your provider and you may have to change the default number to call. (Phone = *99#)

Save the file.

To connect, I plug the phone into the USB port, select "Default Mode" on the phone then open a command line window.

Type:

> sudo wvdial

Provide the root password when requested and you will see something like this:

> alan@SONY:~$ sudo wvdial
[sudo] password for alan: 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Oct 28 22:14:41 2008
--> Pid of pppd: 7253
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]&#1072;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#1072;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#1072;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#1072;[06][08]
--> local  IP address 10.179.1.228
--> pppd: &#65533;&#65533;[06][08]&#1072;[06][08]
--> remote IP address 10.6.6.6
--> pppd: &#65533;&#65533;[06][08]&#1072;[06][08]
--> primary   DNS address 10.203.129.68
--> pppd: &#65533;&#65533;[06][08]&#1072;[06][08]
--> secondary DNS address 10.203.129.68
--> pppd: &#65533;&#65533;[06][08]&#1072;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#1072;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#1072;[06][08]
--> Connect time 27.5 minutes.


This means you're connected! Have fun. 

I'm sitting in central London in my sad hotel room, and with the 6280 being a 3G phone, connection speed is more than acceptable.

---

### Post by ricardojcampo on 2008-10-29
Thank you Alan, I'll give it a try. It is good to know you are doing exactly what I want to do.

Cheers,

Ric.

---

### Post by ricardojcampo on 2008-11-01
Thanks Alan, it works perfectly. I am connecting to the internet using my phone right now. 

cheers,

Ric

---

### Post by AlanR8 on 2008-11-01
Now there's a result! 

Just installed Ibex on both my Sony and EeePC today and it works there to.......

---

