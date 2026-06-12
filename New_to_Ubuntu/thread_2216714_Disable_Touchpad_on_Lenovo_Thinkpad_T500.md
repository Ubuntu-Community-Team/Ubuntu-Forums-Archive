---
title: "Disable Touchpad on Lenovo Thinkpad T500"
date: 2014-04-13
forum: New to Ubuntu
---

### Post by ts1971 on 2014-04-13
Hi all,

I am new to Ubuntu and just recently installed 12.04.4L on a Lenovo Thinkpad T500.  So far I´m pretty happy with it, but there is one thing that I haven been able to figure out.  The laptop has both a touchpad and a pointing stick (the little eraser thing between the ´g´ and ´h´ keys.  I use only the pointing stick and never the touchpad.  The problem is that often when I´m using the pointing stick the bottom of my hands make contact with the touchpad which messes up my navigation and drives me crazy.  So, I´d like to disable only the touchpad, but not the pointing stick.  Under the ´System Settings´ menu there is a ´Mouse and Touchpad´ screen which has a ´Mouse´ tab and a ´Touchpad´ tab.  I´m assuming that the ´Mouse' tab controls the pointing stick (I never use an external mouse) and the ´Touchpad´ tab the touchpad.  Unfortunately, the options on the ´Touchpad´ tab don´t seem to include an entry for completely disabling the touchpad.  There is a ´Disable touchpad while typing' option, which I´ve selected, but it doesn´t really seem to have any affect.  So is there any way to disable the touchpad entirely?  

Thanks.

---

### Post by gifford on 2014-04-13
Here is a link that will help: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
I am unsure what effect this will have on the red pointing stick so you should be prepared to do some experimenting.
Here is another solution that may be less invasive to your system: [http://www.maketecheasier.com/disable-touchpad-while-typing-in-ubuntu/](http://www.maketecheasier.com/disable-touchpad-while-typing-in-ubuntu/)
Be sure to post back what works best for you.
Also, welcome to the forums!

---

### Post by ajgreeny on 2014-04-13
I think synclient is the way to go.

You need to use command ```
synclient TouchpadOff=1
``` as  Enables is 1 and Disables is 0 for TouchpadOff.  This may seem the opposite of what is needed but don't forget the command is a negative, ie Touchpad[COLOR=#ff0000]**Off**[/COLOR].

If you should need to turn the pad back on again it's simply ```
synclient TouchpadOff=0
```.

You could easily make these commands either into shell scripts, make them executable, and run them by double clicking, or you can add aliases in your hidden .bashrc file by adding the lines
```
alias tpon='synclient TouchpadOff=0'
alias tpoff='synclient TouchpadOff=1'
```
then you can turn it on and off by using **tpon** or **tpoff** in terminal.

---

### Post by ts1971 on 2014-04-13
Thank gifford and ajgreeny.  Both of your contributions were very useful.  However, it occurred to me right after I posted, that there was probably a way to just disable it in the BIOS and that that would be a lot easier than modifying startup scripts and whatnot.  Sure enough there was and so I just did that.

Thanks again!

---

### Post by monkeybrain20122 on 2014-04-13
just go to System Settings > touchpad and mouse to turn it off.

---

### Post by gifford on 2014-04-13
Monkeybrain20122...the OP had already done that.

---

### Post by OrangeCrate on 2014-04-14
> **ts1971 said:**
> Hi all,

I am new to Ubuntu and just recently installed **12.04.4L on a Lenovo Thinkpad T500**.  So far I´m pretty happy with it, but there is one thing that I haven been able to figure out.  The laptop has both a touchpad and a pointing stick (the little eraser thing between the ´g´ and ´h´ keys.  I use only the pointing stick and never the touchpad.  The problem is that often when I´m using the pointing stick the bottom of my hands make contact with the touchpad which messes up my navigation and drives me crazy.  So, I´d like to disable only the touchpad, but not the pointing stick.  Under the ´System Settings´ menu there is a ´Mouse and Touchpad´ screen which has a ´Mouse´ tab and a ´Touchpad´ tab.  I´m assuming that the ´Mouse' tab controls the pointing stick (I never use an external mouse) and the ´Touchpad´ tab the touchpad.  Unfortunately, the options on the ´Touchpad´ tab don´t seem to include an entry for completely disabling the touchpad.  There is a ´Disable touchpad while typing' option, which I´ve selected, but it doesn´t really seem to have any affect.  So is there any way to disable the touchpad entirely?  

Thanks.

I also run ThinkPads. Though you appear to have found a solution, the new 14.04 LTS release, which I'm currently using, is available in a few days (17th). There is an option in that new release to turn off the touchpad. The TrackPoint continues to work, as does an external mouse, if you wish to use one.

---

