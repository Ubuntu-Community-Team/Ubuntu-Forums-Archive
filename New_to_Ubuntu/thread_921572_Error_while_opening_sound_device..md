---
title: "Error while opening sound device."
date: 2008-09-16
forum: New to Ubuntu
---

### Post by luckymancvp on 2008-09-16
When I start a sound recorder , It appears a dialog : Error while opening sound device.Please check your hardware.    I'm using main Giga 945 . 
How to solve?

---

### Post by eggdeng on 2008-09-16
Post the output of aplay -l and the make and model of your box. Is sound working OK apart from that?

---

### Post by luckymancvp on 2008-09-16
Here:

[PHP]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/PHP]

main GA-945GCM-s2

---

### Post by eggdeng on 2008-09-16
Routing problems are the order of the day with these Intel HDA cards. The fix (where there is one & there often is) is different for each make & model, which is why you need to post that specific info. What you posted earlier was the model of your motherboard; what would be helpful would be something along the lines of LG Express P1 Dual or Toshiba satellite A130 etc.
You can get an idea of what you need to do by loking at [http://ubuntuforums.org/showthread.php?t=920728]("http://ubuntuforums.org/showthread.php?t=920728") or [http://ubuntuforums.org/showthread.php?t=919078]("http://ubuntuforums.org/showthread.php?t=919078")

---

### Post by markbuntu on 2008-09-16
There is specific help for your ALC883 here:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

There are also software problems that will cause that message, like is some other application has taken control of your sound card and will not let your recording software access it. You can fix that problem by using my guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

