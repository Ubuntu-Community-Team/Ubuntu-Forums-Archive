---
title: "Can't remove onscreen keyboard on resume or unlock in 12.04"
date: 2014-01-12
forum: New to Ubuntu
---

### Post by desconocido on 2014-01-12
I installed Ubuntu 12.04, had problems with keyboard not working (now solved - see [http://neopatel.blogspot.in/2012/10/ubuntu-1204-toshiba-satellite-l875d.html](http://neopatel.blogspot.in/2012/10/ubuntu-1204-toshiba-satellite-l875d.html)) and turned on the Universal Access Onscreen keyboard.

I turned the Onscreen Keyboard off again. It does not appear at login, on startup nor on restart. But it always appears on resume from suspend or unlock from locked. 

Is there any way to turn it off? Is there a settings file?

---

### Post by joachim_altmann on 2014-01-12
Hi,
I had a similar behaviour. I firstly deactivated autostart of onboard, but afterwards I simply deinstalled the package with the software center. I do not which of these worked, but onboard does not show any longer. This is of course only an alternative if you do not need onboard.

---

### Post by desconocido on 2014-01-12
That's good. I had not noticed Onboard on the Application menu.

I ran Onboard and found a preference "Show when unlocking the screen" which I turned off. I think that did it. I will check tomorrow.

---

