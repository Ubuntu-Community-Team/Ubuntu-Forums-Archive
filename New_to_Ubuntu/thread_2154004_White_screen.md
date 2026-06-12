---
title: "White screen"
date: 2013-06-13
forum: New to Ubuntu
---

### Post by Jose Ponteira on 2013-06-13
I installed the latest version of ubuntu, but now the computer starts but nothing appears on the screen.
explain, asks username and password and after entering is only the background image, the bars are not visible.
How can i solve the problem, or i need to reinstal the so?

---

### Post by grahammechanical on 2013-06-13
I do not fully understand the problem from your description of the symptions. I am guessing as to what is wrong. When you get to that desktop without the top panel or the launcher and only a background image, try right clicking the background image and selecting Change Desktop Background. That will open System Settings at the Appearance page. Click All Settings and from the next page select Software & Updates. When that utility loads select the Additional Drivers tab and wait for it to load a selection of video drivers. Change the video driver. You may have to experiment. You may need to log out and in or reboot.

Regards.

---

### Post by Jose Ponteira on 2013-06-13
I try what you say. Don't solve the problem. The left bar and the top bar don't apear.

Regards

---

### Post by Mark Phelps on 2013-06-13
It's quite involved -- but I had to use these steps when this happened to me a while back:  [http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---

### Post by Jose Ponteira on 2013-06-14
i try those steps. don't work. send a report to ubuntu and reinstal the ubuntu 13.04

---

### Post by Jose Ponteira on 2013-06-14
After reinstal the problem came back. the solution was reset the compiz with this comand:    dconf reset -f /org/compiz/

Thankyou to all who try to help.

---

