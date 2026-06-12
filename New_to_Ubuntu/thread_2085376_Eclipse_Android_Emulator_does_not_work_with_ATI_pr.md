---
title: "Eclipse Android Emulator does not work with ATI proprietory drivers ?"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by svee on 2012-11-17
I am on lubuntu 12.10 AMD E.350 processor Sony VAIO VPCY. 

I recently switched to ATI proprietary driver as I have occasional screen freeze on boot-up issues as well as HDMI related issues with open source driver.

However, once I moved to fglrx, AVD manager does not bring up the android emulator. There are no errors as such but the phone (emulator) does not come up.

Moment I reverted to open source driver, it comes up without any problem. 

Is there something I need to be doing specifically for Android emulator to work with ATI proprietary drivers ?

I am not at all happy with the default open source driver so my preference is not to keep it.

---

### Post by svee on 2012-11-20
Not sure if others tried/faced this issue as there were no replies...

Meanwhile I could work around this by installing Virtual Box and running latest iso from android x86 forum.  Then followed the instructions on this tutorial...

[http://www.mat-d.com/site/developing-android-apps-with-android-x86-and-virtual-box/](http://www.mat-d.com/site/developing-android-apps-with-android-x86-and-virtual-box/)

It served the same purpose as emulator and much much faster. Atleast till I hit limitations on some real hardware support under VM, I can use this to try out Android apps...

---

