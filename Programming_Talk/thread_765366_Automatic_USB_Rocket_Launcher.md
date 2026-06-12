---
title: "Automatic USB Rocket Launcher"
date: 2008-04-24
forum: Programming Talk
---

### Post by sharpycore on 2008-04-24
Hello,
I've just been given a USB Rocket Launcher that looks a lot of fun but is only controllable from Windows using the packaged software. Since I'm coming to the end of my degree, I'm trying to come up with some projects to start development on partly for fun and partly to build a portfolio.
So I was wondering if anyone had any pointers on how I'd go about programming for a USB device? I assume it plugs in, and then you send some control codes to the port which the device responds to. Maybe I could install the software that came with the rocket launcher in windows and find an application that can listen to the data going out through the USB port to find out what the control codes are that way.
I'd really like an end result involve capturing images from a webcam and analysing them to pick out moving objects which the rocket launcher then aims at and fires. I think that would be a lot of fun. I'm mostly a Java programmer, but I believe Java doesn't really play with USB ports. Would this be a good time to learn C then?
Any help would be incredible,
Thanks!
Tom

---

### Post by LaRoza on 2008-04-24
> **sharpycore said:**
> Hello,
I've just been given a USB Rocket Launcher that looks a lot of fun but is only controllable from Windows using the packaged software. Since I'm coming to the end of my degree, I'm trying to come up with some projects to start development on partly for fun and partly to build a portfolio.
So I was wondering if anyone had any pointers on how I'd go about programming for a USB device? I assume it plugs in, and then you send some control codes to the port which the device responds to. Maybe I could install the software that came with the rocket launcher in windows and find an application that can listen to the data going out through the USB port to find out what the control codes are that way.
I'd really like an end result involve capturing images from a webcam and analysing them to pick out moving objects which the rocket launcher then aims at and fires. I think that would be a lot of fun. I'm mostly a Java programmer, but I believe Java doesn't really play with USB ports. Would this be a good time to learn C then?
Any help would be incredible,
Thanks!
Tom

I know of two such programs. One in C and the other in Python. The Python one is better I think.

C: [http://lukecole.name/usb_missile_launcher.php](http://lukecole.name/usb_missile_launcher.php)

Python: (webcams too) [http://blog.taragana.com/index.php/archive/how-to-control-usb-missile-launcher-on-linux/](http://blog.taragana.com/index.php/archive/how-to-control-usb-missile-launcher-on-linux/)

---

### Post by sharpycore on 2008-04-24
Oh, beaten to it :( Thanks very much for the pointer though! I'll probably still write the app just for the fun of figuring out myself but looking at those for ideas will help.
Tom

---

### Post by LaRoza on 2008-04-24
> **sharpycore said:**
> Oh, beaten to it :( Thanks very much for the pointer though! I'll probably still write the app just for the fun of figuring out myself but looking at those for ideas will help.
Tom

Yeah, I don't know if they work in Hardy, maybe you could work on that? If you do, let me know if you need testers. I have a USB Rocket Launcher ([http://www.thinkgeek.com/geektoys/warfare/8a0f/](http://www.thinkgeek.com/geektoys/warfare/8a0f/)) like all true geeks. I haven't tried to use it much in Linux.

---

