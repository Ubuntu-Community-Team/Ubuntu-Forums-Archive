---
title: "errors in the console before Lubuntu Core starts"
date: 2015-06-20
forum: New to Ubuntu
---

### Post by Xpdin on 2015-06-20
I am beginner Linux user...


I have just installed Lubuntu Core (Minimal installation).


Every time after restart, before Lubuntu starts it appears 4-5 lines on the console with some errors. 

Because the screen console disappears fast I only saw something about firmware, and it seems that are the same errors every time.


Can someone tell me please how can I find out which are those errors and repair them?


Thank you.

---

### Post by dino99 on 2015-06-20
you should find these errors logged either into /var/log/syslog or /var/log/dmesg or ~/Xorg.0.log

---

### Post by vasa1 on 2015-06-20
> **dino99 said:**
> you should find these errors logged either into /var/log/syslog or /var/log/dmesg or ~/Xorg.0.log
I used to see them in the second one you mentioned: /var/log/dmesg.

They too related to ["firmware"]("http://ubuntuforums.org/showthread.php?t=2216631&p=12985897#post12985897").

---

### Post by Xpdin on 2015-06-20
```
[COLOR=#000000]* /var/log/syslog*[/COLOR]
```

It seems that these are the errors which I was talking about...

```
[   11.211797] b43 ssb0:0: Direct firmware load failed with error -2
[   11.211804] b43 ssb0:0: Direct firmware load failed with error -2
[   11.235638] b43 ssb0:0: Falling back to user helper
[   11.255344] b43 ssb0:0: Direct firmware load failed with error -2
[   11.255350] b43 ssb0:0: Falling back to user helper


[   11.258275] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found
[   11.258285] b43-phy0 ERROR: Firmware file "b43-open/ucode13.fw" not found
[   11.258290] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.



```

Some ideas how to correct them please?

thank you.

---

### Post by brian80 on 2015-06-20
It seems that you don't have your wireless driver installed and hence the errors.
Are you using a wired or wireless connection?
To solve this issue you need to install the driver and you can do that by running this command in terminal.
```
sudo apt-get install firmware-b43-installer
```
Let me know if you need any help.

---

### Post by Xpdin on 2015-06-21
No more errors any more...

Thank you brian80

---

