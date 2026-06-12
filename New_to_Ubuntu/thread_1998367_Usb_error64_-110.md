---
title: "Usb error/64 -110"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by htcrwn148 on 2012-06-06
Ok i have a problem. whenever i try to use my flash drive to put files into it from ubuntu 11.04 natty kernel 2.6.38-15 generic
 and either its spits out an error or it just "unmounts" or ejects the flash drive. SOmetimes it even writes some sort of error on it and the next time i try to use it, it says there is an error on it. 

here is the latest dmesg ---> [http://pastebin.com/YCv4KJFS](http://pastebin.com/YCv4KJFS)

Please help me. I think i found the same issue on launchpad
here ---> 
[https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/735466](https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/735466)

idk if its the same, i would like help either finding a fix, or if the launchpad link is the same problem as mine, how do i go about fixing it with the fix that is said to be released in that bug report?

---

### Post by matt_symes on 2012-06-06
Hi

Unusual request. Does your built in webcam work ?

Install cheese and try that with the webcam.

Post back the results. 

Kind regards

---

### Post by htcrwn148 on 2012-06-06
my camera works fine under cheese. (i wasnot using it at the time of the error)

---

### Post by matt_symes on 2012-06-07
Hi

> [75247.320032] usb 1-3: device descriptor read/64, error -110

You are getting a timoeut error with the pen drive when trying to read the device descriptor.

```
#define ETIMEDOUT       110     /* Connection timed out */
```

Try from a LiveCD and see if the pen drive works from there first and to eliminate hardware problems.

The reason i asked about your webcam is because you are getting a similar timeout error there as well and your webcam is USB (i think).

> uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 2: -110 (exp. 2).

Kind regards

---

### Post by htcrwn148 on 2012-06-26
i dont know if this is a related issue. perhaps i should make or find another post, but my hd is filled by this file "uvcctrl-udev.log" i found the bug on lp, but i dont see the fix, i just deleted the file, but i dont know what to do  to fix it, or should i wait for some update?

---

### Post by matt_symes on 2012-06-26
Hi

> **htcrwn148 said:**
> i dont know if this is a related issue. perhaps i should make or find another post, but my hd is filled by this file "uvcctrl-udev.log" i found the bug on lp, but i dont see the fix, i just deleted the file, but i dont know what to do  to fix it, or should i wait for some update?

uvcctrl-udev.log: That looks like a webcam udev log (uvcvideo is your webcam driver).

Can you post the link to the LaunchPad bug please (is it the same link as posted in your first post ?)

Kind regards

---

### Post by htcrwn148 on 2012-07-03
SOrry it takes me a while to check the forums, but this is the bug that i found. i think this is the one that is affecting me. (as i had 90gigs in that log file.)
[https://bugs.launchpad.net/ubuntu/+source/libwebcam/+bug/811604](https://bugs.launchpad.net/ubuntu/+source/libwebcam/+bug/811604)

---

### Post by matt_symes on 2012-07-03
Hi

Do you still get the same problems when running from a LiveCD/USB ?

Kind regards

---

