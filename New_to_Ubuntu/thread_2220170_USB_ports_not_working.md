---
title: "USB ports not working"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by mo11 on 2014-04-26
im booting Ubuntu 12.04 from my usb stick n everything was working great but then eventually the other 2 usb ports stopped responding when i plugged something in, yesterday both worked until i restarted ubuntu now its the same, i know nothings wrong with the ports cause i can plug my usb stick that has ubuntu into one of the other 2 turn on my laptop n it boots up fine but the other 2 usb ports that arent being used arent working even if i have something plugged in them before turning my laptop on, any ideas?

---

### Post by david98 on 2014-04-27
Try the following commands to see what output you get. gksudo lshw | less and lsusb with at least 1 usb device connected.

---

### Post by mo11 on 2014-05-01
> **david98 said:**
> Try the following commands to see what output you get. gksudo lshw | less and lsusb with at least 1 usb device connected.

only shows the 1 connected with Ubuntu on it, shows nothin for the other one i had connected

---

### Post by mörgæs on 2014-05-01
How does a live boot of 14.04 work?

---

### Post by sandyd on 2014-05-01
Moved to Absolute Beginners Section

---

### Post by mo11 on 2014-05-01
> **mörgæs said:**
> How does a live boot of 14.04 work?

r u asking if the usb ports work in 14.04? i tried n no they're still refusing to work for some reason, by some miracle a few days ago they worked, then i restart n nothing

---

### Post by llamabr on 2014-05-01
Try disabling the usb2 module:

```
sudo rmmod ehci-hcd
```

Then, plug your usb in, count to 15, and do:

```
dmesg | tail
```

and post the output

---

### Post by mo11 on 2014-05-02
> **llamabr said:**
> Try disabling the usb2 module:

```
sudo rmmod ehci-hcd
```

Then, plug your usb in, count to 15, and do:

```
dmesg | tail
```

and post the output

for the sudo rmmod ehci-hcd it said "ERROR: Module ehci_hcd does not exist in /proc/modules"

---

### Post by geral-k on 2014-05-04
@llamabr: You cannot disable the USB modules when using the latest kernels, because they are now built-in.

---

### Post by llamabr on 2014-05-04
> **geral-k said:**
> @llamabr: You cannot disable the USB modules when using the latest kernels, because they are now built-in.

Thanks, Ubuntu, for dumbing down something I love a little bit more.

---

### Post by mo11 on 2014-05-04
once again i booted up my laptop with Ubuntu 12.04 n the other USB ports started working again, but now i turned my laptop back on n their not working, so if i cant fix this problem then i just have to reboot ubuntu about 30 times or until the usb ports work again....

---

### Post by squakie on 2014-05-05
Look through the syslog files (/var/log/syslog and archieved ones as well) and see if there are any error messages for USB controllers, etc..  If you find errors in the log, post them back here along with a few lines before and after the error.

---

### Post by geral-k on 2014-05-05
It would also help to post the [FONT=tahoma]dmesg[/FONT] parts concerning your USB devices. Plug the same USB device into each of your USB connectors and post the pertinent dmesg part. For example, run [FONT=palatino linotype]dmesg -C[/FONT]; plug the device; run [FONT=palatino linotype]dmesg | tail[/FONT]. It may be helpful to repeat this procedure with other types of USB devices.

Sorry, this needs some detective work and patience.

---

### Post by mo11 on 2014-05-08
checked the syslog didnt notice any errors

---

### Post by mo11 on 2014-05-08
> **geral-k said:**
> It would also help to post the [FONT=tahoma]dmesg[/FONT] parts concerning your USB devices. Plug the same USB device into each of your USB connectors and post the pertinent dmesg part. For example, run [FONT=palatino linotype]dmesg -C[/FONT]; plug the device; run [FONT=palatino linotype]dmesg | tail[/FONT]. It may be helpful to repeat this procedure with other types of USB devices.

Sorry, this needs some detective work and patience.

u mean plug a usb in 1 port test it then plug that same one in another port? or use the usb stick already plugged in with ubuntu on it n Plug that one in another port?

---

### Post by geral-k on 2014-05-09
Supposing Ubuntu boots fine using port 1, then plug your stick into this port and boot. Then plug another USB device (for example another USB stick) into each of the remaining free ports, and report the results from applying the previously described procedure for every port. Then repeat the cycle using a different kind of USB device (for example, an external disk). Please make a full and clear report. This may help us find whether there is a problem in any of the ports.

Also, since you have mentioned it: can you boot Ubuntu flawlessly using any of the USB ports? Or does it boot only if you use a certain port?

You have not mentioned what notebook brand and model you are working with. Please do so.

---

