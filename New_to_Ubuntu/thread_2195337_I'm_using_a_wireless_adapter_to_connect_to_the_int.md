---
title: "I'm using a wireless adapter to connect to the internet. Can it work in Ubuntu?"
date: 2013-12-23
forum: New to Ubuntu
---

### Post by rmorabia on 2013-12-23
I'm using a wireless adapter for Windows. It comes with a CD, but will it work in Ubuntu? I don't want to be left stranded after I install it.

---

### Post by deadflowr on 2013-12-23
Most likely.
Do you know what wireless adapter it is?
Some work straight out of the box.
Others need a little work.
And a few need a lot of work.

If you can tell us what it is, we might be able to figure out which level of getting to work will be needed.

---

### Post by rmorabia on 2013-12-23
I think I own this adapter: [http://www.belkin.com/us/F7D2102/p/P-F7D2102/](http://www.belkin.com/us/F7D2102/p/P-F7D2102/)
(Either that, or it's a very similar model.)

Do you know if it would work?

---

### Post by deadflowr on 2013-12-23
It seems like it should work.
Although their is the possibility that a tweak or two will be needed.
[http://ubuntuforums.org/showthread.php?t=2103172](http://ubuntuforums.org/showthread.php?t=2103172)

But that thread is a year old, and two version of Ubuntu later.
Don't know how well support for that card has come in that year.
Might be better, might be worse.

---

### Post by paulwillliamkoehn on 2013-12-23
i have the same problem with this card
[http://www.belkin.com/us/F9L1001-Belkin/p/P-F9L1001/](http://www.belkin.com/us/F9L1001-Belkin/p/P-F9L1001/)
does not even light up when plugged in

---

### Post by rmorabia on 2013-12-23
Thank you! I'll take a look at the link and see what I can do.

---

### Post by joe4ska on 2013-12-23
Earlier versions appear to have worked see
[http://www.cyberciti.biz/tips/linux-usb-wireless-compatibility-adapter-list.html](http://www.cyberciti.biz/tips/linux-usb-wireless-compatibility-adapter-list.html)

If you have a DVD Rom burn an iso to a live DVD and boot from the dvd and try to connect
If you have a extra USB port and a USB flash drive you can create a live ISO to that as well.
If you are able to activate it during the live session testing i'm 99% sure it will work after installation.
Most of these USB drivers that are supported are on the Linux Kernel level so if it worked with other distributions it should work with Ubuntu.

That being said Belkin doesn't actually say it supports Linux for that device so testing it in a live session may be the only way to know for sure.

You can download Ubuntu and get iso instructions here: [URL="http://www.ubuntu.com/download/desktop"]http://www.ubuntu.com/download/desktop

[/URL]Consider purchasing a new wifi adapter that openly says it supports linux [http://www.newegg.com/Product/Product.aspx?Item=N82E16833166079](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166079)

or even one that is Freedom Friendly and will work with every distribution such as this one
[https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-usb-adapter-gnu-linux-tpe-n150usb](https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-usb-adapter-gnu-linux-tpe-n150usb)

---

### Post by vasple on 2013-12-23
If you can't make it work with the open-source drivers you can download the windows ones (you are looking for a .inf  file  i think) and the use then install the ndisgtk graphical wrapper tool to use them on your wireless adapter.

---

### Post by squakie on 2013-12-24
If you are going to use a live session from USB or DVD, why not:

- plug in the device

- in a terminal window type:

lsusb <press enter>

or, even better:

lsusb | grep Wireless

Just copy and paste that output and post it back here.  It will provide all the information we need (manufacturer:productid).

---

