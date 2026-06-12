---
title: "[SOLVED] Mouse Madness"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by @once on 2008-11-07
I recently upgraded to Intrepid Ibex and found that my mouse settings in xorg.conf had been commented out by the update manager. The default settings in Ubuntu (this should really be changed) performs a paste action when the scroll-wheel button is pressed. Almost all of the time this results in scattered bits of text in various documents and I had fixed this in Gutsy by altering the settings in xorg as under:

```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
    Option         "ButtonMapping" "1 4 3"
```

This has now been commented out as HAL manages this functionality. Following suggestions from [here]("http://mesanna.wordpress.com/2008/11/02/ubuntu-810-intrepid-ibex-mouse-configuration/") I made the following mouse.fdi profile and sent it to /etc/hal/fdi/policy/

```
<?xml version="1.0&#8243; encoding="ISO-8859-1&#8243;?>
<deviceinfo version="0.2&#8243;>
<device>
<match key=”info.capabilities” contains=”input.mouse”>
<merge key=”input.x11_driver” type=”string”>mouse</merge>
<!– mouse tweaks –>
<match key=”info.product” string="Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)">
<merge key=”input.x11_options.ButtonMapping” type=”string”>1 4 3</merge>
<merge key=”input.x11_options.ZAxisMapping” type=”string”>4 5</merge>
<merge key=”input.x11_options.Emulate3Buttons” type=”string”>true</merge>
</match>
</match>
</match>
</match>
</match>
</device>
</deviceinfo>
```

This fixes the paste problem but adds one of its own: scrolling down works but scrolling up does not. Scrolling up happened if the scroll-wheel was 'clicked' when the .xmodmap looked like this:

```
pointer = 1 4 3 9 5 6 7 8 2
```

Changing this to 

```
pointer = 1 2 3 9 5 6 7 8 4
```

stops that but does not allow the wheel to scroll as it should (again only upwards - downwards is fine). Running xev shows that scroll up is Button 9 and scroll down is Button 5. 

Any ideas? One very good idea would be for the Ubuntu team to fix the default settings in the first place and add a proper gui manager that can handle all the different settings required. The mouse is a fundamental part of the system and not being able to quickly, intuitively and adequately configure this is a major oversight.

Cheers!

---

### Post by @once on 2008-11-07
So the answer is to change .xmodmap to
pointer = 1 9 3 4 5 6 7 8 2

Which fixes the problem correctly.

---

