---
title: "Boot problem"
date: 2018-07-04
forum: New to Ubuntu
---

### Post by breourzabr on 2018-07-04
Hello,

when I try to boot my Ubuntu system it always stays stuck on same point: [https://ibb.co/eyf2Gd](https://ibb.co/eyf2Gd) 

I tried to fix this problem with Boot-Repair but it didn't help. My boot-log is here: [http://paste.ubuntu.com/p/gwtCczdc6k/](http://paste.ubuntu.com/p/gwtCczdc6k/)

Can you help me? :)

Regards,
B.

[IMG]https://ibb.co/eyf2Gd[/IMG][IMG]https://ibb.co/eyf2Gd[/IMG]

---

### Post by jeremy31 on 2018-07-04
Try booting with an older kernel like 4.15.0-23, then do ```
sudo apt install haveged
```
Then see if a normal boot works

---

### Post by breourzabr on 2018-07-04
Tried on 2 older kernels but it is always the same: [https://ibb.co/j9NkMd](https://ibb.co/j9NkMd) (sorry for the bad quality).

---

### Post by bodhin2 on 2018-07-04
reboot - keep hitting or hold the shift key or if it gets to a weird page hit enter and then hold the shift.  try that.  hope that helps

---

### Post by rickdiaz on 2018-07-10
[COLOR=#545454][FONT=arial]You can repair it using the [/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**Ubuntu**[/FONT][/COLOR][COLOR=#545454][FONT=arial] installation disc or USB stick. [/FONT][/COLOR]

---

