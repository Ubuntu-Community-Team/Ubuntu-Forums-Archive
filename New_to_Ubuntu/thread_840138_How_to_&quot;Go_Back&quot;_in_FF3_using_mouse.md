---
title: "How to &quot;Go Back&quot; in FF3 using mouse"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by wariskampar on 2008-06-25
I just bought Logitech V450 mouse which has tilted scroll wheel. Using btnx I have successfully enable this extra button and I bind them to Left and Right key respectively. However, I just know that we can also use the mouse for 'Back' and 'Forward' page in FF? Having these extra tilted scroll wheel, I'm sure my mouse can handle this job. Does anybody know how to accomplish this; key assignment and what not. Thanks in advance

---

### Post by NT4usB on 2008-06-25
With tabbed browsing, I have little use for the back button...
In the URL window:
```
about:config
```filter on mousewheel or similar. Bunch of settings you can tinker with.
Since the keys to go back are Alt+Left Arrow, you may have to use two hands.

fwiw, since the scrollwheel is not so easy to click, I mapped the thumb button to act as middle click. Easier for opening and closing tabs.
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "8"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
        Option          "ButtonMapping"         "1 6 3 2 4 5"
        Option          "Resolution"            "100"
EndSection
```
```
xev
```in a terminal to see what buttons do what on your mouse.

---

