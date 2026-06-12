---
title: "Boot errors.. Newbie!"
date: 2020-01-16
forum: New to Ubuntu
---

### Post by marc19812 on 2020-01-16
Hi,

I'm completely new to doing anything like this so bare with me! I decided I wanted to run Retropie on my laptop and wanted to boot straight from a USB stick so I went down the route of adding Ubuntu to it. I had issues getting it to run off the USB straight from boot until I followed the guide on this site..

[https://www.dionysopoulos.me/portable-ubuntu-on-usb-hdd/](https://www.dionysopoulos.me/portable-ubuntu-on-usb-hdd/)

To my surprise it worked and boots from usb but I do get the following errors;

error: file '/boot/' not found.
error: no such device: /.disk/info.
error: no such device: /.disk/mini-info.

It does get past these and Ubunto does load (they just flash up). I wondered if there was a way of clearing them for a cleaner startup?

Any help much appreciated.

Marc

---

### Post by oldrocker99 on 2020-01-16
This is a good question; I have, in 12 years, never gotten that message. It'll just be a very small annoyance.

---

### Post by marc19812 on 2020-01-17
So I did some googling and followed the advice of updating the grub file using sudo update-grub. It cleared the above 3 errors but now I get the following...

system boot order not found initializing defaults

Again it does get past this and goes to the grub screen which I've set to timeout after 0.1 so you dont see the grub screen anymore... still annoying to have an error though!

---

### Post by kevdog on 2020-01-17
System Boot order -- Would that be a setting in the bios where you would select HDD, CDROM, Network or others like USB in a specific order?  That would be my guess I suppose.

---

