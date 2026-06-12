---
title: "Touchpad issues"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by Empyreon on 2011-10-15
hey guys my touchpads right click wasnt working but the two finger scrolling was. I looked up a solution and went through it, now my right click is working but my scrolling isnt!

---

### Post by Carborundum on 2011-10-15
> **Empyreon said:**
> hey guys my touchpads right click wasnt working but the two finger scrolling was. I looked up a solution and went through it, now my right click is working but my scrolling isnt!

It would help if you explained what you did in more detail.

---

### Post by ffvieira on 2011-10-15
> **Carborundum said:**
> It would help if you explained what you did in more detail.

Yeah it would... I'm having the same problem...

---

### Post by Empyreon on 2011-10-15
i believe i did this 
Code:
sudo su
Code:
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
Code:
reboot

can be found at ([http://ubuntuforums.org/showthread.php?t=1388164]("http://ubuntuforums.org/showthread.php?t=1388164"))

---

