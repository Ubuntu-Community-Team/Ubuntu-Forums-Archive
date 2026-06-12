---
title: "ASUS EeePC screen brightness at login"
date: 2014-12-25
forum: New to Ubuntu
---

### Post by ha62791 on 2014-12-25
My EeePC 1015CX is installed with Ubuntu 14.04.
The screen brightness is set to maximum at every startup.

In the folder /sys/class/backlight/
there are two folders:
eeepc-wmi/ (max brightness is 11)
psb-bl/ (max brightness is 100)

In terminal with root access,
the following works on changing the screen brightness:
```
echo X > /sys/class/backlight/psb-bl/brightness
```
where X is a value between 0-100

I've tried putting the following line in /etc/rc.local before the "exit 0", as suggested from other posts:

```
echo 3 > /sys/class/backlight/eeepc-wmi/brightness
```
OR

```
echo 22 > /sys/class/backlight/psb-bl/brightness
```

OR both,

but none of them works, and brightness remains at maximum at every startup.

Any way to run the line with root access at login ?

---

### Post by ha62791 on 2014-12-29
:pI solved it by adding sleep 10 before the writing to brightness file.
Ref: [http://askubuntu.com/questions/208112/how-do-i-add-more-than-one-command-to-etc-rc-local](http://askubuntu.com/questions/208112/how-do-i-add-more-than-one-command-to-etc-rc-local)

```
[FONT=Ubuntu Mono](sleep 10; echo 42 > /sys/class/backlight/psb-bl/brightness)&[/FONT]
```

Interesting thing is, I don't need to wait for 10 seconds for the brightness to go down.
The brightness is tuned down at login.

---

