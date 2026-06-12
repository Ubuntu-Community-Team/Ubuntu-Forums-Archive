---
title: "How to detect keypress in background?"
date: 2009-01-14
forum: Programming Talk
---

### Post by HyperHacker on 2009-01-14
I have a GTK C app that needs to know when a key is pressed, regardless of what window has focus. The program talks to a remote control that has a button to turn the display off. I use xset to turn it off, but it doesn't seem to want to stay off (it'll turn back on after 10 minutes or so).
The solution I came up with for that is that when the off button is pressed, it will set a flag to call xset every minute or so. However then if the user doesn't use the remote to turn it back on, the program will continue to turn the displays off every minute. I want it to detect keyboard activity so it knows when to stop doing that. (I'm not as concerned about the mouse; I always use the keyboard to wake it up anyway, and that way the cat won't bump it in the middle of the night.)

The best solutions I've seen are to use XGrabKey() to tell me when a key is pressed, or read /proc/interrupts. However, the X method isn't working:
```
XMainDisplay = XOpenDisplay(0);
RootWindow = DefaultRootWindow(XMainDisplay);
XGrabKey(XMainDisplay, AnyKey, AnyModifier, RootWindow, True,

	GrabModeAsync, GrabModeAsync);
XSelectInput(XMainDisplay, RootWindow, KeyPressMask);

XEvent XE;
XNextEvent(XMainDisplay, &XE);
```I get a BadAccess error on the last line (access denied even if I'm running as root when I grab the key). GTK tells me I can use gdk_x_error() to get more information, but that doesn't seem to exist (no mention of it in the GTK or GDK manuals, and Google only turns up bug reports with programs giving that message). -_-

As for /proc/interrupts, I can't find any useful information on how to parse the file to find the keyboard interrupt info. The best I found was "look for any line with the word keyboard in it", but mine has none.```
           CPU0       
  0:        144   IO-APIC-edge      timer
  1:     270933   IO-APIC-edge      i8042
  4:          4   IO-APIC-edge    
  7:          0   IO-APIC-edge      parport0
  8:          2   IO-APIC-edge      rtc0
  9:          0   IO-APIC-fasteoi   acpi
 14:     474026   IO-APIC-edge      pata_via
 15:     539925   IO-APIC-edge      pata_via
 16:   25859512   IO-APIC-fasteoi   nvidia, eth0
 17:    1907233   IO-APIC-fasteoi   CMI8738
 20:          0   IO-APIC-fasteoi   sata_via
 21:   36318310   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4, uhci_hcd:usb5
NMI:          0   Non-maskable interrupts
LOC:  111746479   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0
```That site also mentioned the format of this file is undocumented and changes often, so trying to use it seems like a bad idea.

---

### Post by pavel989 on 2009-01-14
&XE?

what is XEvent?

---

### Post by HyperHacker on 2009-01-14
It's the XEvent structure from Xlib, that's supposed to get set there to contain info about the event.

---

### Post by pavel989 on 2009-01-14
my question is passing &XE. Im sure itd throw an error if it shouldnt be such, but sometimes pointers and dereferncing can throw like bad access errors

---

### Post by HyperHacker on 2009-01-15
How would it fill in the event if it weren't a pointer?

---

### Post by pavel989 on 2009-01-16
thats not what i meant. sorta.
You should check to make sure its pointing right.

---

