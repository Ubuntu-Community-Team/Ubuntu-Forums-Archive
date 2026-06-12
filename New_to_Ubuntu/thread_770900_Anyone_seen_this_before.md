---
title: "Anyone seen this before?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by muted1987 on 2008-04-27
does anyone know why this is happening to my webcam?

[IMG]http://i174.photobucket.com/albums/w85/muted_apoc/Screenshot-Camorama-VC0323-320x240.png[/IMG]



sry at lost ends bump

---

### Post by cmnorton on 2008-04-27
Check your logs under /var/log. messages and syslog are a good place to start. It would help to have more information, like did the web cam ever work, and have you installed the necessary modules to support the web cam.

---

### Post by elpichi on 2008-04-27
try another program for the webcam, happened to me that xawtv works for my cam while others didn't. maybe is a different case for you?

---

### Post by muted1987 on 2008-04-27
hey guys thx for the replys no the webcam hasnt worked before and this is the furthest ive got with it. i have installed the gspca module and it is loaded.

it looks to me as if though the signal is screwy

and i dont know where to find logs please help

---

### Post by elpichi on 2008-04-28
run the program you use for the webcam in a terminal, and check what output does it gives when you use the cam, to check for errors.

check this out.
[IMG]http://img329.imageshack.us/img329/7778/screenshotcamoramaov519if7.png[/IMG]
only happens with camorama, for me.

I think you have the driver properly installed, just camorama, can't read the image out of it very well. try xawtv.

---

### Post by Jive Turkey on 2008-04-28
try disabling compiz by pressing alt+F2 then type "metacity --replace" without quotes.  If it works you know the corruption is from that.

---

### Post by drsox1899 on 2008-04-28
Try TVTime.  Works fine for me.  Setup the Input Source to composite.  It's in the repository.

---

