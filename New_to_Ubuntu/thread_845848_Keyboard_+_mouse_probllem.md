---
title: "Keyboard + mouse probllem"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by ethoxyethaan on 2008-07-01
kernel info: Ubuntu hardy heron 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

hardware: Dell latitude D830

problem: If i press a button on my keyboard my mouse freezes making it impossible to work in with 3D applications.

Example: if i press button "e" I will be unable to move my mouse cursor until i release it.

Also my touchpad is not working (laptop)

small note: I did not install the nvidia drivers from the Ubuntu Restricted drivers thing but downloaded them from Nvidia site myself and installed it.

here is my xconf:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "be"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
```


what i find odd is:

```
"Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection
```

suggestions or help please

---

### Post by kuja on 2008-07-01
Try adding ```
Option "AlwaysCore" "1"
``` to the touchpad and the mouse "InputDevice" sections.

And add "CorePointer" to the server layout section for the touchpad .... maybe that will do it.

---

### Post by ethoxyethaan on 2008-07-01
sorry for doublepost i wanted to edit => =(

---

### Post by ethoxyethaan on 2008-07-01
> **kuja said:**
> Try adding ```
Option "AlwaysCore" "1"
``` to the touchpad and the mouse "InputDevice" sections.

And add "CorePointer" to the server layout section for the touchpad .... maybe that will do it.

diden't help but thanks for trying i appreciate it.

this is my new attempt:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
        Driver          "nvidia"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth    24
        Option         "UseFBDev" "true"
        Option         "NoLogo" "True"
        SubSection     "Display"
            Depth       24
            Modes      "nvidia-auto-select"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by kuja on 2008-07-01
Take a look through your /var/log/xorg.0.log file and see if you can find anything interesting. Maybe some lines starting with (EE) or any lines to do with the synaptics touchpad.

---

### Post by ethoxyethaan on 2008-07-01
> **kuja said:**
> Take a look through your /var/log/xorg.0.log file and see if you can find anything interesting. Maybe some lines starting with (EE) or any lines to do with the synaptics touchpad.

```
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(WW) Synaptics Touchpad can't grab event device, errno=16
(--) Synaptics Touchpad touchpad found

(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(WW) Synaptics Touchpad can't grab event device, errno=16
(--) Synaptics Touchpad touchpad found
(II) 3rd Button detected: disabling emulate3Button
```

because of the messing arroung for 2 weeks there are several xconf#.new/old files.

this one was xconf.0.log

edit: [color=red]I forgot to mention that there are 2 "touchpads" or however you may call it
1 is a small blue thing in the middle of my keyboard layout
the other one is the "thouchpad" like a regular laptop".[/color]

Only 1 of them isen't working "The second one" (not the blue thing).


Edit 2: I booted from a live cd. looked up the Xconf file and it gave me the exact same settings as my current once.

So anyone have a theory why this is happening ===> :(

current: 
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
        Driver          "nvidia"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth    24
        Option         "UseFBDev" "true"
        Option         "NoLogo" "True"
        SubSection     "Display"
            Depth       24
            Modes      "nvidia-auto-select"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by tiga2001 on 2008-07-02
My system doesn't seem to be locking up, but I also have the same problem, where the pointing stick works, but the touch pad does not. All 4 mouse buttons work, however.

Weird. I restarted the computer after upgrading from kernel 2.6.24-16 to 2.6.24-19 and now the touchpad works fine.

---

