---
title: "Need help with Tablet support (non-Wacom)"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by stalkier on 2008-06-04
Hello. I am using a Tooya Pro Tablet. I know that Ubuntu now offers Wacom support and many others have got other brands to work with tutorials. Mine, however, is not one of them. I was wondering if I could get it to work using Linux. What I am needing is to control both Pen (Absolute) and mouse (relative) settings for the device. Thanks in advance.

Tablet Model: Tooya Pro
Tablet Length: 10.0 Inch
Tablet Width: 6.25 Inch
Driver Version: 3.30
Firmware Version: 1.2

---

### Post by Nuticulus on 2009-03-28
I followed the instructions for the Wacom tablet on [https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom"), and my Tooya Pro now works wonderfully.

---

### Post by stalkier on 2009-03-28
> **Nuticulus said:**
> I followed the instructions for the Wacom tablet on [https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom"), and my Tooya Pro now works wonderfully.

Thanks so much. I pretty much gave up months ago. Now I can get it working. :D

---

### Post by iblenderppc on 2010-07-19
Hi Grp,

I got a Tooya Pro tablet (PenPower Inc) and really having tough time making it work in Linux. I followed the Wacom Ubuntu community page and did as they said and nothing works. I am in square one after trying what is mentioned in the ubuntu wacom page.

I am on Ubuntu 9.10. When I first pluged in the tablet, all I was able to do was move the mouse cursor with the tooya pro pen. Non of the buttons works. And I tried the stuff mentioned in the Wacom Ubuntu page and still the same state.

Kindly some one help, i dont want to go back to Window.

---

### Post by iblenderppc on 2010-07-19
Thngs I did from the Ubuntu Wacom page are 

I install the tools with this command
sudo apt-get install xserver-xorg-input-wacom wacom-tools
I editied the xorg.conf file and it looks like this now

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "stylus"
  Option        "USB"           "on"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "pad"
  Option        "USB"           "on"
EndSection

Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
#  InputDevice   "stylus"  "SendCoreEvents"
#  InputDevice   "pad"
EndSection

And I created a "wacom.fdi" file in " /etc/hal/fdi/policy " which contains

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

  <device>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="input.x11_options.TPCButton" type="string">on</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
        <merge key="input.x11_options.Threshold" type="string">1</merge>
        <merge key="input.x11_options.PressCurve" type="string">50,0,100,50</merge>
      </match>
    </match>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="eraser">
        <merge key="input.x11_options.TPCButton" type="string">on</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
        <merge key="input.x11_options.Threshold" type="string">1</merge>
        <merge key="input.x11_options.PressCurve" type="string">50,0,100,50</merge>
      </match>
    </match>
  </device>

</deviceinfo>

Am i missing any things here?

Kindly help.

---

### Post by Legendary_Bibo on 2010-07-19
> **iblenderppc said:**
> Hi Grp,

I got a Tooya Pro tablet (PenPower Inc) and really having tough time making it work in Linux. I followed the Wacom Ubuntu community page and did as they said and nothing works. I am in square one after trying what is mentioned in the ubuntu wacom page.

I am on Ubuntu 9.10. When I first pluged in the tablet, all I was able to do was move the mouse cursor with the tooya pro pen. Non of the buttons works. And I tried the stuff mentioned in the Wacom Ubuntu page and still the same state.

Kindly some one help, i dont want to go back to Window.

Try this. It might work. Enable permissions then run it in the terminal.

---

### Post by Favux on 2010-07-19
Hi iblenderppc,

Welcome to Ubuntu forums!

Several problems.  It sounds like they got it working with wacom on Intrepid.  By Karmic the wacom driver had a table in the wcm_usb.c that rejected non-wacom tablets.  The new xf86-input-wacom in Lucid doesn't do that anymore though.

So you may need to try another driver like WizardPen or Trust in Karmic.  With the Waltops and Ntrigs we patched the wacom code to get them to work.

Now with configuring you want to use either the xorg.conf or a .fdi but not both.  And with the xorg.conf the wacom sections aren't active because you have the wacom lines in "ServerLayout" commented out.

Hope this helps.

Edit:  By the way I checked the PenPower Inc. site and they don't appear to have a linux driver.

---

