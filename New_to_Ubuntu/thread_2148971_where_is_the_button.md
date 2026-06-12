---
title: "where is the button"
date: 2013-05-27
forum: New to Ubuntu
---

### Post by QXLIANG2013 on 2013-05-27
hi,there might be a "*shutdown*" button on the right corner of my ubuntu desktop,but it dispeared somehow,please help me to recover that,thank you!

---

### Post by hangpan on 2013-05-27
Can you post a snapshot here? The button me here seems working pretty well, it resides "right-up" corner.;)

---

### Post by QXLIANG2013 on 2013-05-27
i asked that for another newb,so i'm afraid i cann't post a snapshot,i'm curious about that button's disappearance.thank you for suggestion

---

### Post by Frogs Hair on 2013-05-27
Copy, paste, and enter the following command in the terminal  and log out and in.```
 sudo apt-get install --reinstall indicator-session 
```

---

### Post by deadflowr on 2013-05-27
> **QXLIANG2013 said:**
> i asked that for another newb,so i'm afraid i cann't post a snapshot,i'm curious about that button's disappearance.thank you for suggestion

Why can't you post a snapshot?

Even so, follow Frog Hairs advice and try reinstalling.
But another option is to try the HUD method.
Close all applications, and then press the alt key, then type shutdown into the 'type your command box.
shutdown should show, then highlight and press enter.

---

### Post by bogan on 2013-05-27
Hi!,** Qxaliang2013,**

If Frogs Hair's reinstall command did not work, try Ubuntu-Tweak; there is an option to show/remove the Shutdown item in the Tweaks>Session Indicator menu. Make sure it is unticked.

To install ubuntu-tweak you need the tualatrix ppa:
```
sudo apt-add-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
ubuntu-tweak # or enter 'ub' in the Dash search line and select 'Ubuntu Tweak'.
```When it runs you can pin it to the Launcher if you wish; Right Click and select from the drop down menu.

Chao!, **bogan**.

---

### Post by QXLIANG2013 on 2013-05-29
thanks a bunch!with your advises above i can manage it by myself then,really helpful!

---

