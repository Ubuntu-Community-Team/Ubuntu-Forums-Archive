---
title: "can't get dialup working"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-05-30
I am trying to help a friend by lending him an old laptop and can't get his dialup connection working I have tried gnome ppp and have all the stuff filled out but get the error no modem found on this machine. I know it used to use dialup with XP. Then I tried a few other machines and all give the same error. What can I do to get him connected?

---

### Post by little_penguin on 2012-05-30
If it's an old laptop with an internal modem for dial-up, as opposed to an external one that you connect by usb, then I suspect you are dealing with a "winmodem" or Windows-only modem. These do not generally work with linux as far as I am aware. Maybe someone has found a solution somewhere on the internet and I hope  you find a way to get it working. If not, maybe you could get a cheap second-hand usb external modem. Chances of getting one of those working are much higher, I think.

BTW you could try this link:

[http://ubuntuforums.org/showthread.php?t=308098](http://ubuntuforums.org/showthread.php?t=308098)

---

### Post by llamabr on 2012-05-30
Yes, internal modems are cheap, not really modem, devices.  They rely in large part on the OS to do much of the job.  Without extra hacking, they do not tend to work with linux.   Start here:

[http://linmodems.org/](http://linmodems.org/)

To see if yours is listed. If the machine has a serial port, you should try to pick up a used cheap serial port modem.  If I remember right, I used to use a US Robotics one.  It was this little thing that sat on the floor with a bunch of led's flashing all over the place.

If you decide to try to work with the winmodem, start there, and let us know where you get stuck.

---

### Post by Michael Dooley on 2012-05-30
cmcanulty:

Over four years ago, I faced a similar difficulty. Please see the page below:

[http://ubuntuforums.org/showthread.php?t=997474](http://ubuntuforums.org/showthread.php?t=997474)

It doesn't matter if your modem is a software modem or not, it still takes a bit of wrangling to get it up and running. Let us know how its going...

---

### Post by cmcanulty on 2012-05-30
the hard part is he only has dialup so I have to try and figure everything I need and put it on a flash drive as I only have cable, then go to his house and try things, So far I need to find out what modem the laptop has but don't know how to do that

---

### Post by pbpersson on 2012-05-30
You would get the make and model number of the laptop and Google it to get the details.

---

### Post by jmore9 on 2012-05-30
If you can find an old serial external modem , like at gooswill or somewhere they are really easy to get going.  No drivers needed.  But as the previous poster said first you need to figure out what kind of modem you have so you can figure out if you need drivers or other type of configuration.

---

### Post by gandaran on 2012-05-31
> **cmcanulty said:**
> the hard part is he only has dialup so I have to try and figure everything I need and put it on a flash drive as I only have cable, then go to his house and try things, So far I need to find out what modem the laptop has but don't know how to do that
to find out what hardware the laptop has use the following commands
for internal devices
```
lspci
```
external devices
```
lsusb
```
sometimes on laptops some internal devices are detected as usb devices, try the lsusb command if the lspci doesn't detect the dial-up modem.

---

