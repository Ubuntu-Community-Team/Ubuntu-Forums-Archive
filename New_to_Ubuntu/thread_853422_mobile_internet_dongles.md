---
title: "mobile internet dongles"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by nobbydog on 2008-07-08
hi
does anyone know if the mobile internet dongles you can get from  t mobilr or 3g work on ubuntu.
nobby

---

### Post by arx-lupus on 2008-07-08
Hi,

I don't have any personal experience but you may want to have a look at this link [http://www.pharscape.org/content/blogsection/4/53/]("http://www.pharscape.org/content/blogsection/4/53/") I had saved it previously when I was considering mobile broadband.

---

### Post by strick242 on 2008-07-08
I successfully used an aircard with ubuntu.  Turns out the aircard was nothing more than a usb hub with a usb modem all internal.  What worked for me was to plug the device in and run "lsusb" (that's a small L, not a number 1).  

The result I was looking for was like this:
Bus 006 Device 002: ID 1199:0019 Sierra Wireless, Inc.

The list that comes back should give you product name and manufacturer info for all usb devices.  
Find the one that corresponds to your device.  
In my case it was a Sierra AC595.  Make note of the vendor and product id (the 1199:0019 in the example above).  
I then ran "sudo modprobe usbserial vendor=0x1199 product=0x0019".  
The 0x1199 and 0x0019 were the id's in my case, your's will more than likely be different.  
After this, it was just a matter of using a dial up connection.  I used gnome-ppp.  It is available via apt-get or synaptic.  gnome-ppp wouldn't autodetect my modem.  
I believe I chose dev/ttyusb0 as my modem.  
The rest of the info you would get from your provider (Dial up number, username, and password)  
I hope this helped.

---

### Post by fatality_uk on 2008-07-08
I bought 5 for my old company. Huawei E220 from VodaFone.
They worked out the box. There's even a great little Linux client for it.

[https://forge.betavine.net/](https://forge.betavine.net/)

Look here and search for the Linux client

Here's the Linux client on Ubuntu in operation
[http://amalheiro.files.wordpress.com/2007/09/vodafoneconnected.jpg](http://amalheiro.files.wordpress.com/2007/09/vodafoneconnected.jpg)

---

### Post by t0p on 2008-07-08
> **nobbydog said:**
> hi
does anyone know if the mobile internet dongles you can get from  t mobilr or 3g work on ubuntu.
nobby

Somewhere on this forum, someone has posted instructions on how to use these GPRS/3G dongles with ubuntu.  I haven't got a link for it, but if you use the search function I'm sure you'll find it.

If you can't find it: the process involves using the program **wvdial**, which is installed by default on ubuntu.  In my sig is a link to a tutorial on using a mobile phone as a modem: the process is basically the same.

---

### Post by Sub101 on 2008-07-08
The links within this thread should have all the info you need:

[HTML]http://ubuntuforums.org/showthread.php?t=783240[/HTML]

---

### Post by AB34125 on 2008-07-14
> **fatality_uk said:**
> I bought 5 for my old company. Huawei E220 from VodaFone.
They worked out the box. There's even a great little Linux client for it.



Does any one know if 3 Australia use this Dongle for there 3g modem?

---

### Post by nobbydog on 2008-12-05
Hi aLL
Just installed ubuntu 8-10 on my laptop.and i can't get the cube working i have ticked all the boxes.but the cube does not work.
any ideas!
ALSO i set my e mail up wrong how can i reset it up
How do i startv a new thread forgotten?
thanks nobby

---

### Post by scorp123 on 2008-12-05
> **t0p said:**
>  the process involves using the program **wvdial**, which is installed by default on ubuntu.   With the new Ubuntu 8.10 you don't even need "wvdial" anymore :D  ... My **Novatel Wireless MC950D** 3G USB-modem now "just works" with Ubuntu's "Network Manager". You plug-in the modem, you tell "Network Manager" that you want to use the "Wireless Broadband" connection, a pop-up lets you pick your country and provider .... aaaaand you're in. Done. :D

---

### Post by scorp123 on 2008-12-05
> **nobbydog said:**
> Hi aLL
Just installed ubuntu 8-10 on my laptop.and i can't get the cube working i have ticked all the boxes.but the cube does not work.
any ideas!
ALSO i set my e mail up wrong how can i reset it up
How do i startv a new thread forgotten?
thanks nobby You should open a new thread for that question ... :)

---

### Post by hellomoto on 2008-12-05
I am currently connected with my mobile internet dongle and its great! I have been using it the last 3 months with no problems. My speed is about 0.7 - 1mb. 

I am using:

Hardy
WVdial to connect.
Huawei E220 HSDPA Modem (lsusb: ID 12d1:1003)
Network 3 (pay as you go)

I found the setup very simple and didn't have any problems.
Just for information: There is a full feature on mobile Broadband in this months "linux format".
If anyone wishes for my config file for WVdial or help with setup please just let me know. :D

---

### Post by mohitsoni on 2008-12-29
Read the article [Connecting to the Internet on Ubuntu Linux using GPRS, Bluetooth enabled mobile]("http://codebasket.blogspot.com/2008/12/connecting-to-internet-on-ubuntu-linux.html") on CodeBasket. Hope, this will solve your problem.

---

