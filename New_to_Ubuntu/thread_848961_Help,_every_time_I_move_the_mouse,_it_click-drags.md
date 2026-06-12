---
title: "Help, every time I move the mouse, it click-drags"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by LifeTheHound on 2008-07-04
I have a Vaio UX280p, and whenever I try to move the mouse, Ubuntu thinks I'm holding down the click button and dragging.  How to disable this mouse behavior?  

In Preferences->Mouse, the touchpad settings do nothing.  Is there a driver I need?  
[img]http://www.whatwethink.com/wp-content/images/sonyvaio.jpg[/img]
The mouse is the little gray doohickey on the top-right side there.

---

### Post by apswartz on 2008-07-06
LifeTheHound, if you don't get any help it is probably because we are just not familiar with your hardware, and not that you are being ignored.

---

### Post by steveneddy on 2008-07-06
I want one.

=P~

---

### Post by apswartz on 2008-07-06
[Check out this post...]("http://www.thejoe.com/2007/05/17/ubuntu-on-vaio/")
[http://www.thejoe.com/2007/05/17/ubuntu-on-vaio/](http://www.thejoe.com/2007/05/17/ubuntu-on-vaio/)

---

### Post by Tomatz on 2008-07-06
> **LifeTheHound said:**
> I have a Vaio UX280p, and whenever I try to move the mouse, Ubuntu thinks I'm holding down the click button and dragging.  How to disable this mouse behavior?  

In Preferences->Mouse, the touchpad settings do nothing.  Is there a driver I need?  
[img]http://www.whatwethink.com/wp-content/images/sonyvaio.jpg[/img]
The mouse is the little gray doohickey on the top-right side there.

Can you replicate the behavior if you plug a usb mouse in?

---

### Post by LifeTheHound on 2008-07-06
It works fine with a USB mouse, interestingly.  I am going to check out that post about the custom install, that looks linteresting.  :)

---

### Post by apswartz on 2008-07-07
> **LifeTheHound said:**
> It works fine with a USB mouse, interestingly.  I am going to check out that post about the custom install, that looks linteresting.  :)

Great! Let us know if it works. If it does mark the thread solved. Good luck!

---

### Post by starcannon on 2008-07-07
You may need to add Option "SHMConfig" "true" to the synaptics part of your xorg.conf file to get touchpad configurator working correctly. After thats added, reboot or restart X server CTRL-ALT-BCKSPC
If you installed gsynaptics then in System-->Preferences-->Touchpad you should now be able to use the gui to modify touchpad behavior.
```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
[COLOR="Blue"]	Option         	"SHMConfig"             "true"[/COLOR]
EndSection

```

GL

---

