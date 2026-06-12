---
title: "EasyPen M406 working like a mouse"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by TheManno1 on 2012-08-10
I can use my tablet similar to a mouse but I can't use it for drawing.I have the hold the touchpad on my mouse while drawing on the tablet for the tablet to draw.
[https://www.youtube.com/watch?v=a1Qx8Si8iUw&feature=youtu.be](https://www.youtube.com/watch?v=a1Qx8Si8iUw&feature=youtu.be)

Ubuntu Precise 12.04 32 bit.

---

### Post by Favux on 2012-08-10
Hi TheManno1,

What app is that you are drawing in?

Please post the output of this command run in a terminal:
```
lsusb
```
and also this one:
```
xinput list
```

---

### Post by TheManno1 on 2012-08-14
The app I am using is pencil  morenva project version
[http://morevnaproject.org/packages/](http://morevnaproject.org/packages/)

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0402:9665 ALi Corp. Gateway Webcam
Bus 002 Device 003: ID 062a:4101 Creative Labs 
Bus 001 Device 006: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 004: ID 0458:5005 KYE Systems Corp. (Mouse Systems) 

 xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; MOSART Semi. 2.4G Keyboard Mouse            id=12    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; Genius EasyPenM406                          id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; 1.3M WebCam                                 id=10    [slave  keyboard (3)]
    &#8627; MOSART Semi. 2.4G Keyboard Mouse            id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=15    [slave  keyboard (3)]

---

### Post by Favux on 2012-08-14
When you press the left button of the mouse you are getting a left click or Button 1 1 press.  That should be the default setting for the stylus tip, i.e Button 1 with a left click.  Where 1 is left click, 2 middle click, 3 is right click.

I'm pretty sure Pencil uses Gtk+ so we don't need to worry about the Qt evdev bug:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Category:Tablet_setup_in_applications](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Category:Tablet_setup_in_applications)

According the the DIGI*mend* project's "Tablet support status" page the Genius EasyPen M406 (KYE EasyPen M406) isn't supported yet:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)
[http://sourceforge.net/apps/mediawiki/digimend/index.php?title=KYE_EasyPen_M406](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=KYE_EasyPen_M406)

Nick does have diagnostics for this tablet but it may not hurt to send him another set:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend)

Other than the fact he is the only developer so far for the DIGI*mend* project and has a backlog, the problem with this model is the multifunction or jog dial.  He has to figure out a driver for it.  Otherwise "The  EasyPen M406 protocol isn't HID-compatible and requires creating synthetic devices. The bug number for this is 3530654."

We could try placing the pen on the Wacom driver in the meantime and see if that gets us anywhere.  Or fool around with evdev.  And I think I got the WizardPen driver to compile, mostly.  Either way see if the default kernel HID stuff is good enough for this tablet to get us something.  But that could turn into quite the adventure.  :)

---

### Post by TheManno1 on 2012-08-15
How do I send him a diagnostic and what should be in the diagnostic.
Also is their anyway to fix it?

---

### Post by TheManno1 on 2012-08-20
Bump

---

### Post by Favux on 2012-08-20
Hi,

As I said above Nick already has the diagnostics for your M406:  [http://sourceforge.net/tracker/?func=detail&aid=3530654&group_id=233297&atid=1089171](http://sourceforge.net/tracker/?func=detail&aid=3530654&group_id=233297&atid=1089171)

The diagnostics are on the model page:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=KYE_EasyPen_M406](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=KYE_EasyPen_M406)  You could check this page and make sure that's your model.  And that page is linked through the Tablet support page:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

So I don't know if Nick would want more diagnostics on that model but you could ask him on the mailing list:  [https://lists.sourceforge.net/lists/listinfo/digimend-users](https://lists.sourceforge.net/lists/listinfo/digimend-users)

If he does you would follow the instructions here:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Collecting_tablet_diagnostics](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Collecting_tablet_diagnostics)

Also by contacting him via the mailing list he'd be able to contact you to test the new driver when he has one ready to test.


Otherwise without having the kernel fixed we would be experimenting to see if we can work with what the kernel currently does with your tablet and get at least the pen tip working.  As I said earlier we could for example try to get the WizardPen driver working and then see if your tablet's pen would work with that.  But no guarentee we could get it working.

---

### Post by Ksee on 2012-12-24
> **Favux said:**
> I'm pretty sure Pencil uses Gtk+ so we don't need to worry about the Qt evdev bug

Pencil is not GTK app. It's QT-based.

---

