---
title: "I have downloaded ubuntu iso file but cant write to usb"
date: 2015-05-29
forum: New to Ubuntu
---

### Post by shazia2 on 2015-05-29
I am a new linux user recently installed debian stable 8 from windows through unetbootin but now i would like to come to ubuntu. I have downloaded ubuntu iso file but cant write to usb as here in debian i cant install unetbbotin either from repository or direct download as nothing happens when I doble click the unetbootin file event its executable mark. i tried various other commands options also searched fro google but all had some problems. please advice me how to make my usb bootable with ubuntu preferly with unetbootin ?

---

### Post by coffeecat on 2015-05-29
I find unetbootin very irritating and don't use it now. Have a look at this tutorial thread:

[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)

If you want to add the mkusb PPA repository in debian, this might help:

[http://www.webupd8.org/2014/10/how-to-add-launchpad-ppas-in-debian-via.html](http://www.webupd8.org/2014/10/how-to-add-launchpad-ppas-in-debian-via.html)

What I do with Ubuntu ISOs is a simple dd of the ISO directly to the USB stick. You don't have to format the stick first. That would work in debian. Of course, you need to be very careful when you use dd - sudodus mentions this a little way down in his post. If you are comfortable with using dd and you know what you are doing, that is what I would recommend. Quick and easy, but potentially destructive if you get of=device wrong.

---

### Post by shazia2 on 2015-05-29
As you mentioned i did 

 sudo add-apt-repository ppa:mkusb/ppa

 but results says command not found

---

### Post by coffeecat on 2015-05-29
Did you look at my second link?

---

