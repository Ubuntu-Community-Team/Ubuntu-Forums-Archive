---
title: "Suspend no longer wakes on keystroke"
date: 2013-09-06
forum: New to Ubuntu
---

### Post by lile001 on 2013-09-06
At one time, when the computer went to sleep, it would wake up on a keystroke.  Now suddenly it has to be waken by the power button.  As this happens to be way under the standing desk, it is inconvenient.  I have not been able to guess a search term on these forums to turn up an answer, nor has poking around in system settings: Power turned up anything that looked relevant.  How can I set the computer so it wakes up on a keystroke or mouse movement?  I am on Ubuntu 12.04 LTS.

---

### Post by tgalati4 on 2013-09-06
Too many beans gives you gas.  Boot into BIOS and look for a setting "Allow USB devices to Wake" or "Support Legacy USB devices".  Perhaps a BIOS setting got changed such that your keyboard is ignored.  USB keyboards need power (5VDC) to allow the wake function.  If there is no power, then you have to use the power button on the machine itself.

---

### Post by chuck5 on 2013-09-06
I have the same problem on my HP Envy dv7 laptop.  Except that when I use the power button, it shuts down and powers off.

Suggestions, please!  I can't find anything to help with this.

---

### Post by tgalati4 on 2013-09-06
In Preferences-->Power Management-->General Tab  Set the Power Button to do:

Ask Me
Suspend
Hibernate (you need a swap partition slightly bigger than your RAM, otherwise it will freeze!)
Shutdown

Welcome to the forums.  It helps to create a new post for a new problem.

---

