---
title: "How to: enable Toshiba Touchpad toggle on off function key"
date: 2008-01-26
forum: Outdated Tutorials &amp; Tips
---

### Post by beardiggin on 2008-01-26
I am running Ubuntu 7.10 Gusty on a Toshiba Tecra M7 tablet PC.  The toggle fn key for my Synaptics Touchpad was not working correctly.  I found several tutorials but none of them had all the pieces to enable the fn key properly.

To enable the toggle switch that disables your keypad I will give you three simple steps.

1.  Enable xorg to modify touchpad on the fly.
edit /etc/X11/xorg.conf by adding the {Option "SHMConfig"} line below.
----------------------------------------------------------------------
Under Section "InputDevice"  
        
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"  

EndSection 
----------------------------------------------------------------------

After completing this step restart your xserver.
<ctrl><alt><bksp>

2.  Download and unzip the files I have inlcuded.
NOTE: you should read through any script anyone gives you to make sure it will not destroy your system when you run it. 

3.  enter the following commands:
     sudo cp tosh-touchpad-toggle /etc/acpi/events
     sudo cp tosh-touchpad-toggle.sh /etc/acpi/

:) Happy toggling
That should be it.  If you have any problems, feel free to send me a message.

---

