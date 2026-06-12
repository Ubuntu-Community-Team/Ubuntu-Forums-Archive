---
title: "Can't find Huawei 3 USB wireless modem in Ubuntu 8.04?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Sealbhach on 2008-04-26
Hi,
I've just set up a dual boot so I can choose Vista or Hardy Heron. (A bit scary but it worked!).

Now, I'm a total noob (obligatory lol!) and I'm having trouble getting on to the Interweb with my wireless modem.

For a start, Hardy can't see it. If I load Ubuntu and stick the modem into the USB slot, nothing happens, nothing at all.

I've Googled and seen workarounds involving writing code but I'm not at all keen on that route, I'm a noob (lol!).

It's a Huawei E220 HSDPA USB wireless modem.

Is there a driver I can dowload while in Vista, stick it on a thumb drive, then boot up Ubuntu and install it that way?

Writing scripts/commands or whatever is too scary for me.

Thank,
Sealbhach. (n00b, l0l!)




.

---

### Post by daengbo on 2008-04-26
This:
[http://blog.charlvn.za.net/2008/02/huawei-e220-3g-usb-modem-on-ubuntu.html](http://blog.charlvn.za.net/2008/02/huawei-e220-3g-usb-modem-on-ubuntu.html)
or this:
[http://ubuntuforums.org/showthread.php?p=1776667](http://ubuntuforums.org/showthread.php?p=1776667)

may help.

---

### Post by Sealbhach on 2008-04-26
Thanks!.

I already tried the Vodafone driver, saved it on a thumb drive but it's a .rpm file and Ubuntu doesn't seem to recognise it. It's says it's the "wrong archive type".

I'd be a bit out of my depth with writing code.

If Linux is going to succeed it needs to work right out of the box - so that noobs like me can use it. I haven't had any of these problems with Vista.

Anyway, what do I do with this .rpm file? Thanks for your help.


.

---

### Post by Sealbhach on 2008-04-26
Bump.

Noob here.

What do I do with an .rpm type file?

Doesn't open for me.


It's for a wirelss modem driver.


S.

---

### Post by daengbo on 2008-04-26
The link I gave you is NOT to an RPM file. The blog specifically links to a DEB file for Ubuntu Gutsy. Use that. Follow the directions on the page.

As for "writing code," typing commands into a terminal is not writing code. Just follow the directions.

---

### Post by Sealbhach on 2008-04-26
OK, thanks. It's daunting to even type commands, since I'm not so sure what I might be doing. If Linux is to be more popular, it needs to be idiot proof so people like me can use it.:)

If you mean [this page]("https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=19") there's loads of them.

So, shall I pick this one, it's a .deb file?

[https://forge.vodafonebetavine.net/frs/download.php/119/vodafone-mobile-connect-card-driver-for-linux_2.0.beta1_i386.deb](https://forge.vodafonebetavine.net/frs/download.php/119/vodafone-mobile-connect-card-driver-for-linux_2.0.beta1_i386.deb)



.

---

### Post by daengbo on 2008-04-27
The link you gave will work, and is the most up-to-date, but you didn't need to go to that much trouble. The link I gave you:
[http://blog.charlvn.za.net/2008/02/huawei-e220-3g-usb-modem-on-ubuntu.html](http://blog.charlvn.za.net/2008/02/huawei-e220-3g-usb-modem-on-ubuntu.html)
links directly to the file you need and give you specific directions on what to do.

Don't worry that you don't understand every command. Just copy and paste.

---

### Post by Sealbhach on 2008-04-27
YAY!!

I did it! I got connected!  Not exactly sure what I did but it was a combination of messing about with GnomePPP, putting "*99#* as the phone number.

and doing these things [here]("http://www.boards.ie/vbulletin/showpost.php?p=55779679&postcount=8"):


> Here are the steps. There is a lot to remember so I suggest saving it to a memory stick in windows and then when you load up in ubuntu you can copy and paste. Alternatively print it out... if anything is unclear post a message up here asking.



1. Open a terminal window. This can be done by clicking Applications in the top left, then accessories and finally terminal



2 In the terminal window, type sudo gedit /etc/resolv.conf Put in your password when it asks. This will open a window like notepad. In this window you should type



nameserver 208.67.222.222

nameserver 172.30.140.69



3. Click save and close the window.



4. In a terminal window (either the one you already opened or a new one) type sudo gedit /etc/ppp/peers/provider (Again put in your password) In this window you should replace the text you see with..... 



user "user"



connect "/usr/sbin/chat -v -f /etc/chatscripts/pap -T *99#"



# Serial device to which the modem is connected.

/dev/ttyUSB0



# Speed of the serial line.

460800



# Assumes that your IP address is allocated dynamically by the ISP.

noipdefault

# Try to get the name server addresses from the ISP.

#usepeerdns

# Use this connection as the default route.

defaultroute



# Makes pppd "dial again" when the connection is lost.

persist



# Do not ask the remote to authenticate.

noauth



# pppd will detach from controlling terminal when connection is up

updetach



# no compression - ppp is used only until the modem

novj

novjccomp

nopcomp

nodeflate



# put in a default gateway even if one was present before

replacedefaultroute



# if connection has failed, redial in this number of seconds

# don't use too low - 3 seems to drive modem crazy

holdoff 5



5. In a terminal window type sudo gedit /etc/chatscripts/pap ( again it will ask for password) and replace any text with....



ABORT BUSY

ABORT VOICE

ABORT "NO CARRIER"

ABORT "NO DIALTONE"

ABORT "NO DIAL TONE"

"" ATZ

OK ATE0V1&D2&C1S0=0+IFC=2,2

OK AT+CGDCONT=1,"IP","three.co.uk"

OK ATDT*99#

CONNECT ""



6. Attach your modem. In a terminal window type modprobe usbserial vendor=0x12d1 product=0x1003



What I have just written can be very off putting to someone who is new to linux. Its just unfortunate that there are no linux drivers for your modem. Fortunately you should never have to do anything like this again with ubuntu. Its all clicking with the mouse.



If you try the steps above and it works, post back and we can create an icon on the desktop that will start the modem on its own in future so you don't have to go near the terminal.



Any time you start up Ubuntu, you may have to run the 

modprobe usbserial vendor=0x12d1 product=0x1003

in the terminal.

Thanks to everybody here who helped me so much!!!!:grin::grin::grin:



.

---

