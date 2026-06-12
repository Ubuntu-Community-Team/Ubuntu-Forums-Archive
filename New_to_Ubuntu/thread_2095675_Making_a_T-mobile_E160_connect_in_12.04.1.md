---
title: "Making a T-mobile E160 connect in 12.04.1"
date: 2012-12-17
forum: New to Ubuntu
---

### Post by gubbinator on 2012-12-17
I'm completely new to Ubuntu. I don't have a hard wired internet connection, so the E160 is my only link to the world. I've tried various things I've read here and elsewhere, and can't get the modem to work. On insertion it flashes first green then blue (same as for windows) but I can't find a way of connecting.

OS: 12.04.1 (freshly installed and not yet updated as I have no other connection)
Service provider: T-mobile
Manufacturer: Huawei
Device: E160

I've tried lsusb, and it is listed as a Huawei device, and various E-numbers (but not E160 which is what it is labelled as). The codes listed are 12d1 for manufacturer and 1003 for device.

Can anyone help and tell me what's wrong?

I don't want to give up so soon as I've been wanting to break free from windows for ages.

---

### Post by gubbinator on 2012-12-18
Bump!

Doesn't anyone know what to do? I've inserted the Huawei E160 USB modem countless times, and it's been recognised and appeared in 'system setting/network' just twice.

The first time I quickly recorded all the settings I had used for future use, and then browsed several web pages. I had thought it would be easy to repeat the first success, but it was several hours later before it worked again, but the connection was dropped without warning and the device disappeared from system setting/network.

Why is this only working occasionally? Surely it should work all the time or not at all?

---

### Post by audiomick on 2012-12-18
Hallo

Is it this one?
```
Bus 002 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem

```

I am using that right now on 10.04. Getting it going was very easy, and it works reliably.

There was a thing that had to be there that wasn't there by default. It is called usb-modeswitch. I don't think that will be missing, though, because you say the device has worked once, and I believe it is there by default now.

Getting the thing working involved a right click on the network icon and choose "edit connections" or whatever is similar. On my German language install it is "verbindungen bearbeiten" and I haven't seen an english install, so I'm not quite sure what it is called.

Anyway, in there, choose the tab for mobile broadband, click on  "new" (or is it "add"?) and follow the steps. I left at at all the default settings (I am with T-mobile in Germany) and have not had any problems with it.

I should mention:

It has worked when the device has been plugged in when the computer is started, but seems happier if the device is not plugged in until after I log in.

It takes a while for the computer to find the device. Maybe half a minute, or even a minute or so. Probably seems longer than it is, and I haven't timed it, but it is not as quick as I would like. When it has been found, generally the box for entering the pin code shows up first. I also get an icon on the desktop for the onboard storage where the windows installer is on the device.

So, the question is, have you been through that setting up process?
Is the device always visible with lsusb when it doesn't manage to make a connection?
Do you have a dual boot where you can try the device in windows?

Just for the record, what model laptop is it, do other usb devices work correctly, how old is the E160?

Oh, one more thing...
> but the connection was dropped without warning and the device disappeared from system setting/network.
If the network is bad where you are, you can lose your connection without warning. Keep an eye on the led on the device. Mine is light blue when the connection is good, a deeper blue when it is not so good, and green when it is trying to connect via the normal telephone net.
When the connection breaks, I can still chose the device out of the drop down menu I get by clicking on the network icon, and have the option to tell it to re-connect (which it will only do if the coverage is good enough, of course).

---

### Post by gubbinator on 2012-12-18
Thanks for the reply.

I've tried it quite a few more times, and still no connection. The Huawei device is listed as '12d1' and '1003' in lsusb, same as yours.

Answers to your questions:
1. It is all setup, although the 'add connection' is somewhere slightly different on 12.04. I've set it up with the exact same settings to when it worked twice briefly, but I still can't get a connection.

2. The device is always visible in lsusb, even when it isn't visible in 'system setting/network' as a mobile broadband connection.

3. The device works fine in windows 7, I'm using it right now to post to this forum.

4. The laptop is an ASUS X54C, the only other USB devices I have tried are USB memory stick which work fine and are recognised immediately. The E160 is a few years old, it's definately not the latest!

It's probably also worth mentioning that I have never seen the icon for the onboard storage with the windows drivers appear in Ubuntu. So you can see, it's a composite device, but Ubuntu is not recognising the built in CD-ROM or the modem.

---

### Post by audiomick on 2012-12-18
I don't know how much more help I am going to be, but for what it is worth...

> **gubbinator said:**
>  The Huawei device is listed as '12d1' and '1003' in lsusb, same as yours.

This is the interesting bit
```
 E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
```
If I've understood things correctly, this
> as '12d1' and '1003' is connection info related to the usb bus, and what I have included just above is the model number of the modem as recognised by the system. This will influence which drivers linux uses to try and run it. Having said that, I don't know how to influence that in any way.

> 
Answers to your questions:
1. It is all setup, although the 'add connection' is somewhere slightly different on 12.04. I've set it up with the exact same settings to when it worked twice briefly, but I still can't get a connection.

2. The device is always visible in lsusb, even when it isn't visible in 'system setting/network' as a mobile broadband connection.


Ok, so the problem is likely to be in the network manager somewhere.


> 
3. The device works fine in windows 7, I'm using it right now to post to this forum.
 the only other USB devices I have tried are USB memory stick which work fine and are recognised immediately. 


Good, so the device isn't broken, and the usb ports are working properly.


> The E160 is a few years old, it's definately not the latest!
"A few years old" is good. That means that developers have had a chance to work on it, but it is not so old that it is no longer interesting. In fact, the thing should work. I have seen problems occasionally here on the forum, but I gather that 3G dongles is something in which a lot of effort has been invested to make them work, and Huawei seems to make nearly all of those things.


> 4. The laptop is an ASUS X54C,
Ok. Good to know. I can't say anything specifically about that, but possibly someone else will be able to.

> 
It's probably also worth mentioning that I have never seen the icon for the onboard storage with the windows drivers appear in Ubuntu. So you can see, it's a composite device, but Ubuntu is not recognising the built in CD-ROM or the modem.
Yes.

How much searching have you done for other people with similar problems? That "E220" stuff that I quoted might be a good basis for a search of the forum. What is the equivalent in your lsub output?

I know this is a long post without much useful input. Sorry about that... What I am trying to impart is that the device should and almost certainly can work. I'm not much help, I know, but don't lose hope. ;)

---

### Post by gubbinator on 2012-12-18
Thanks for your reply, you've given me a bit more motivation and I've finally found something that works.

This thread here contains the solution:

[http://ubuntuforums.org/showthread.php?t=1994588](http://ubuntuforums.org/showthread.php?t=1994588)

Just substitute my own device '1003' for '1c07'

I was a bit sceptical at first, because I'd already tried editing various system files according to other threads elsewhere, but it really does work. The only thing is that the device has to be inserted before booting, or it doesn't recognise. I can live with not being able to hot plug it, but if anyone knows a solution for it I'm interested.

One other thing is that my system file edit briefly stopped working after installing all the ubuntu restricted extras, but a reboot appears to have solved that.

Edit: I've found that hot plugging works fine, the only condition is that the device HAS to be present on boot up.

---

### Post by gubbinator on 2012-12-18
This will be my second post using ubuntu instead of windows, so I think it's fair to say the problem is solved. :) Firefox and Chrome both working well too! =D>

---

### Post by audiomick on 2012-12-18
Hey, great to hear it. Have fun with Ubuntu.

---

### Post by Stephan H on 2013-02-24
Hello,

I've got the same problem: The E220/E160 just won't don anything after I setup the mobile broadband connection in the network manager.

lsusb shows exactly what is mentioned above:

```
Bus 002 Device 007: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem

```.

Now following your advice and what is said in the thread you mentioned...

> **gubbinator said:**
> 
This thread here contains the solution:

[http://ubuntuforums.org/showthread.php?t=1994588](http://ubuntuforums.org/showthread.php?t=1994588)

Just substitute my own device '1003' for '1c07'


...I don't know how to do this. /etc/modules is empty! So I could add the line```
 usbserial vendor=0x12d1 product=0x1c07
``` but there's no list of exceptions.
Consequently there's nothing to append.

Any idea what else can be done here?

Stephan

---

