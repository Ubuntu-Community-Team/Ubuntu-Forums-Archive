---
title: "Bluetooth?"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by highlyevolved on 2008-07-28
How do I get bluetooh working?

I've got the bluetooth program workng from the preferences folder and ticked all the boxes but when my phone searches for bluetooh devices it doesn't show up.

I've got a toshiba sattelie a120.

Cheers

---

### Post by UbuntuNerd on 2008-07-28
here is some info from Ubuntu on Bluetooth it should help set it up

[https://wiki.ubuntu.com/Bluetooth]("https://wiki.ubuntu.com/Bluetooth")

---

### Post by highlyevolved on 2008-07-28
Utterly confusing.

It talks about Gutsy Gibbon but I don't understand it.

I want the bluetooth to work in conjunction with my phone.

---

### Post by UbuntuNerd on 2008-07-28
Im sorry you want play your audio such as MP3's and movie output through a Bluetooth-connected with your Ubuntu machine?

---

### Post by UbuntuNerd on 2008-07-28
Ok I believe this guide is the one you want is strictly for Ubuntu hardy and to be honest most of what you need to do can be a bit confusing but just try it !!!


[http://forums.overclockers.com.au/showthread.php?t=694010]("http://forums.overclockers.com.au/showthread.php?t=694010")

---

### Post by highlyevolved on 2008-07-28
Like, I want to be able to in my phone, go to a image, go to send as, bluetooth, then have my laptop come up as a device..if that makes sense?

---

### Post by UbuntuNerd on 2008-07-28
also there seems to be a bug with what you trying to do is explain here and how to fix it

[http://technology-included.blogspot.com/2008/07/using-bluetooth-on-hardy-ubuntu-804.html]("http://technology-included.blogspot.com/2008/07/using-bluetooth-on-hardy-ubuntu-804.html")

---

### Post by c2olen on 2008-07-28
Have you got it working by now?

If the default bluemon tools doesn't do it for you, you might give "Blueman" a try. It has some nice additional features for scanning and authorizing.

Cheers

---

### Post by jjj_uk on 2008-07-28
Bluetooth on a Toshiba needs to be enabled throught the Toshset tool. You can activate it manually with the Terminal

sudo toshset -bluetooth on

or run a script which runs the tool automatically on startup: [http://www.itwriting.com/blog/333-fixing-bluetooth-on-a-toshiba-with-ubuntu.html](http://www.itwriting.com/blog/333-fixing-bluetooth-on-a-toshiba-with-ubuntu.html)

Hope this helps.

j

---

### Post by highlyevolved on 2008-07-28
Nope, and now I think I've stuffed up synapic package manger.

I just tried 
sudo toshset -bluetooth on

and it came up with bluetooth unavailable..

---

