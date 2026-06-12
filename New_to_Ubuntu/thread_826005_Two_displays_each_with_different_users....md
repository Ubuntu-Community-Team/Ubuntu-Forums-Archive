---
title: "Two displays each with different users..."
date: 2008-06-11
forum: New to Ubuntu
---

### Post by keepitsimpleengr on 2008-06-11
I've got two nvidia GeForce 8 graphics cards, each with a single monitor-- and want to run independent sessions as different users (for testing) from one console.  

I'm running Ubuntu 8.04 LTS/Gnome 2.22.2 with kernel 2.6.24-18-generic x86_64 and nvidia 169.12 (envyNG).

I'm comfortable ):P with Linux servers (RedHat & SUSE) but am :confused: by X windows and window managers.

Some ideas about where to start would be great :), but a step by step howto would be wonderful\\:D/.

Thanx for listening.

Current xorg.conf attached

---

### Post by Inxsible on 2008-06-11
> **keepitsimpleengr said:**
> [snip]current Xorg.conf Attached.....NOT !! :lolflag:

If you want you could probably try installing VMWare or Virtualbox and run a different OS in there. Is that what you are looking for?

Even if you have two graphics cards and two monitors(on the same machine, right?), you still have only one processor and one RAM, so I don't think it'd be possible to run two kernels at the same time unless one is in virtualization.

If you are testing the same distro ..then you can simply create the same username in the guest OS as well as you have in the host.

---

### Post by keepitsimpleengr on 2008-06-11
Yikes!

# xorg.conf (X.Org X Window System server configuration file)

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	Option	    "TwinView" "0"
	Option	    "metamodes" "nvidia-auto-select +0+0"
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "nvidia-auto-select +0+0"
	Identifier "Screen1"
	Device     "Videocard1"
	Monitor    "Monitor1"
	DefaultDepth     24
	Option	    "TwinView" "0"
	Option	    "metamodes" "1440x900_75 +0+0"
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "nvidia"
	VendorName  "NVIDIA Corporation"
	BoardName   "GeForce 8800 GTX"
	BusID       "PCI:1:0:0"
	Screen      0
EndSection

Section "Device"
	Identifier  "Videocard1"
	Driver      "nvidia"
	VendorName  "NVIDIA Corporation"
	BoardName   "GeForce 8800 GTX"
	BusID       "PCI:10:0:0"
	Screen      1
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection


Section "InputDevice"

    # generated from default
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "Emulate3Buttons" "no"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection


Section "Files"
EndSection

Section "Monitor"

 ### Comment all HorizSync and VertSync values to use DDC:
	Identifier   "Monitor0"
	VendorName   "Unknown"
	ModelName    "HP LP3065"
 ### Comment all HorizSync and VertSync values to use DDC:
	HorizSync    49.3 - 98.5
	VertRefresh  60.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Unknown"
	ModelName    "Samsung SyncMaster"
 ### Comment all HorizSync and VertSync values to use DDC:
	HorizSync    30.0 - 81.0
	VertRefresh  59.0 - 75.0
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

### Post by keepitsimpleengr on 2008-06-11
Two users, same kernel, same OS, same CPUs

One user runs an app, 2nd user monitors from second display.

---

### Post by bsimpson63 on 2008-11-14
Did you ever figure out how to do this?  I'm trying to accomplish the same thing.

---

