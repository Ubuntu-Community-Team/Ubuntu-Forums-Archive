---
title: "Printer difficulty"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by jmcgovern on 2008-09-17
Hey all,

Got a small problem installing my printer.  It's a Canon PIXMA iP2600.  I found instructions at [http://support-asia.canon-asia.com](http://support-asia.canon-asia.com) through this forum.  I get down to the step that says enter

```
sudo /usr/sbin/lpadmin -p [printer_name] -m [PPD_filename] -v [device_URI] -E
```

I plug in the appropriate things for my system, and it comes back as "Unable to copy PPD File!", and well..there you go. I did take note that the instructions provided were for Feisty, and im running Hardy, but they worked up to this point.  Any suggestions?  This is the last thing before my system is 100% up.  Everything else has Just Worked(TM).

---

### Post by scorchgeek on 2008-09-17
Did you enter things in the right case for the whole command? Linux commands are case-sensitive.

---

### Post by jbrown96 on 2008-09-17
I assume that you changed [printer_name] to the actual name and filled in all the fields likewise. What is the actual command that you ran?

---

### Post by jimbean on 2008-09-17
go into the search function at top right corner of screen and type in bobsong
and look in his posts you should see install brother printers

i think that the same would apply to all printers


but make sure you use the drivers from the epson web  site

---

### Post by jmcgovern on 2008-09-18
Here's the command I was attempting to use. exactly as i typed it:

s```
udo /usr/sbin/lpadmin -p iP2600_series -m /usr/share/ppd/canonip2600.ppd -v usb://Canon/iP2600%20series -E
```

I noticed, while trying to locate the .ppd file, that the owner is root.  does this affect what im trying to do?  If so, do i chown the file?

---

### Post by bikerider42 on 2008-09-18
i use turboprint it cost money 25.00 i think but, easy to set up and works great with my pixma! they do have a trial version....

---

### Post by sleimson on 2008-09-19
Hey jmcgovern, i am having the same issue as you. have u managed to resolve the ppd problem? this printer is driving me mad.

---

### Post by ihatetryingtopickaloginna on 2008-09-19
Did you try gnome-cups-manager? That's what I used. You might have to install it first.

---

### Post by sleimson on 2008-09-20
Nice one mate. it is sorted now!

---

### Post by Deerfoot on 2008-10-14
I heartily recommend TurboPrint for those using Canon Printers and having problems. I have a Canon Pixma iP1700 and Ubuntu 7.04. The printer became unusable - very frustrating! I checked out the forums and decided to try TurboPrint which was recommended. One month's free trial. Easy to set up (I'm no techie!) after a bit of tweaking and it worked wonderfully. Then I paid about AUS$50.00 to get rid of the banner. TurboPrint is great and worth the money - it has a lot going for it e.g. head cleaning, ink level checks etc. Get it!! No more stress!
Mary
Australia

---

