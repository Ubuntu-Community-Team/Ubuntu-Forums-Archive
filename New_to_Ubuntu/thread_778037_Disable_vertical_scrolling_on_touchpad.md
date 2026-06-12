---
title: "Disable vertical scrolling on touchpad"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by AndrewZorn on 2008-05-01
Here is my mouse section in xorg:
> Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
	Option		"VertScrollDelta"	"0"
	Option		"TapButton1" "1"
#	Option		"TapButton2" "3"
#	Option		"TapButton3" "2"

#	Option          "MaxTapTime"            "120"
#	Option          "MaxTapMove"            "150"
	Option          "VertTwoFingerScroll"   "1"
	Option          "HorizTwoFingerScroll"  "1"
	Option          "VertEdgeScroll"        "false"
	Option          "HorizEdgeScroll"       "false"
	Option          "Emulate3Buttons"       "true"
#	Option          "SHMConfig"             "true"
EndSection
I really like the two-finger scrolling, but really hate the vertical edge scrolling.  Using VertEdgeScroll 0 does **not** work, and I have no idea why... I found the VertScrollDelta 0 trick somewhere, but that simply makes it to where the scrolling goes nowhere (and thus disables the two-finger scroll!).

Any ideas?

EDIT and if I do **synclient VertEdgeScroll=0** it 'fixes' it, and disables the vertical edge scrolling.  I could put this in startup, but WHY is it happeneing?  I have it 0d out in the xorg!

---

### Post by kaotikzen on 2009-07-10
The problem is that in later versions of Ubuntu, X has hotplugging enabled by default.  With hotplugging enabled, many(see all) devices do not use the xorg.conf file like they did in prior versions of X.  That's why the default install has an empty xorg.conf file.

Instead your driver preferences are managed in hal (I think).  So to disable your vertical edge scrolling you will first need to copy the appropriate policy file and edit it.

```
$ sudo cp /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi /etc/hal/fdi/policy/

$ sudo nano /etc/hal/fdi/policy/11-x11-synaptics.fdi

```

The default file is decently foolproof to edit as each policy line is commented.  In any case you want to hunt down the xml tag where **key="input.x11_options.VertEdgeScroll"** and change the value from *true* to *false*.

This is what mine looks like for comparison:
[HTML]
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="SynPS/2 Synaptics TouchPad">
      <append key="info.capabilities" type="strlist">input.touchpad</append>
    </match>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLES:
        Switch on shared memory, enables the driver to be configured at runtime-->
	<merge key="input.x11_options.SHMConfig" type="string">false</merge>

	<!-- Maximum movement of the finger for detecting a tap-->
	<merge key="input.x11_options.MaxTapMove" type="string">2000</merge>

	<!--Enable vertical scrolling when dragging along the right edge-->
	<merge key="input.x11_options.VertEdgeScroll" type="string">false</merge>

	<!--Enable vertical scrolling when dragging with two fingers anywhere on the touchpad-->
	<merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>

	<!--Enable horizontal scrolling when dragging with two fingers anywhere on the touchpad-->
	<merge key="input.x11_options.HorizTwoFingerScroll" type="string">false</merge>

	<!--If on, circular scrolling is used-->
	<merge key="input.x11_options.CircularScrolling" type="string">false</merge>

	<!--For other possible options, check CONFIGURATION DETAILS in synaptics man page
        -->
    </match>
  </device>
</deviceinfo>
[/HTML]

I've tried to get this to take effect by restarting hal, but I think it requires a full restart of X as well (so that X can inherit your settings from hal perhaps??), saving the changes and restarting the computer is easier (to me).

Good luck!

---

