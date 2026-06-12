---
title: "Replace /dev/input/event6 kbd handler for scanner"
date: 2009-03-31
forum: Programming Talk
---

### Post by Quentusrex on 2009-03-31
I have two scanners, one a barcode scanner and one a RFID scanner. They both work through the 'fake being a keyboard' input manner. I want to replace this with the ability to have a script listen or be called when an input event happens with either of the scanners. And a while(1){} loop won't work because I dont' want the script eating up the processor...

Also I would prefer the script be written in Perl, though I can use python, or C. 

Here is some of the info that might be useful:

root@quentusrex-desktop:/dev/input# lsusb
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 05e0:1200 Symbol Technologies DS6608 Bar Code Scanner
Bus 004 Device 003: ID 03f0:4d11 Hewlett-Packard PSC 1400
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 413c:2105 Dell Computer Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 15ba:0010 Olimex Ltd. 
Bus 001 Device 003: ID 413c:3012 Dell Computer Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


and:

root@quentusrex-desktop:/dev/input# cat /proc/bus/input/devices
....
I: Bus=0003 Vendor=15ba Product=0010 Version=0111
N: Name="Olimex Ltd. MOD-RFID125-USBSTICK Tag Keyboard"
P: Phys=usb-0000:00:12.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:12.0/usb1/1-1/1-1:1.0/input/input8
U: Uniq=OL22A6D00011556
H: Handlers=kbd event6 
B: EV=120013
B: KEY=e080ffdf01cfffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=05e0 Product=1200 Version=0110
N: Name="?Symbol Technologies, Inc, 2002 Symbol Bar Code Scanner"
P: Phys=usb-0000:00:13.1-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:13.1/usb4/4-2/4-2:1.0/input/input9
U: Uniq=S/N:1A8E37C782A2FC488BD97FCFF5C05D63 Rev:NBRMIAAR3
H: Handlers=kbd event7 
B: EV=120013
B: KEY=1000000000007 ff9f207ac14057ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=1f

and:

root@quentusrex-desktop:/dev/input# ls -al by-id/
total 0
drwxr-xr-x 2 root root 140 2009-03-31 19:18 .
drwxr-xr-x 4 root root 300 2009-03-31 19:18 ..
lrwxrwxrwx 1 root root   9 2009-03-31 16:26 usb-Dell_Dell_USB_Keyboard-event-kbd -> ../event2
lrwxrwxrwx 1 root root   9 2009-03-31 16:26 usb-Dell_Dell_USB_Optical_Mouse-event-mouse -> ../event1
lrwxrwxrwx 1 root root   9 2009-03-31 16:26 usb-Dell_Dell_USB_Optical_Mouse-mouse -> ../mouse1
lrwxrwxrwx 1 root root   9 2009-03-31 18:18 usb-Olimex_Ltd._MOD-RFID125-USBSTICK_Tag_Keyboard_OL22A6D00011556-event-kbd -> ../event6
lrwxrwxrwx 1 root root   9 2009-03-31 19:18 usb-_Symbol_Technologies__Inc__2002_Symbol_Bar_Code_Scanner_S.N:1A8E37C782A2FC488BD97FCFF5C05D63_Rev:NBRMIAAR3-event-kbd -> ../event7

---

### Post by Quentusrex on 2009-03-31
My goal is to have a headless box connected to different scanners, and when something is scanned a script is called, which connects to a database, and if it finds the item, then play sound file yes.wav, else play sound file no.wav.

---

### Post by Quentusrex on 2009-04-01
Here is my code so far: 

use strict;
use warnings;
use Linux::Input;
use Data::Dumper;
use Device::USB;

my $usb = Device::USB->new;
$usb->debug_mode(2);

#(0x15ba, 0x0010) Olimex
#(0x05e0, 0x1200) Symbol
my $dev = $usb->find_device(0x05e0, 0x1200);
print Dumper($dev);


  my $js1 = Linux::Input->new('/dev/input/event7');
  while (1) {
    while (my @events = $js1->poll(0.01)) {
      foreach (@events) {
	print Dumper($_);
      }
    }
  }


Currently it will properly detect and analyze the device, but any input events are skipped. It is as if they are read by something else first.

---

### Post by Zugzwang on 2009-04-01
> **Quentusrex said:**
> [...] And a while(1){} loop won't work because I dont' want the script eating up the processor...


They don't eat up "the processor". Try the following C++-program as an example (I don't know perl):
```

#include <iostream>
using namespace std;

int main () {
  std::string command = "";

  while (command!="exit") {
    getline (cin,command);
    cout << "You typed: " << command << endl;
  }
  return 0;
}

```
Compile it, run it and then switch to a different terminal to run "top". Press "u" and enter your username. You will see that your application (e.g., a.out) will be almost at the bottom, which means that almost no computation power is spent at the busy waiting part.

---

### Post by Quentusrex on 2009-04-01
Ok, it seems that works fine. I don't know what was causing the CPU spike... I tested a while loop and the CPU was suddenly slammed. 

So, now... How to read the events from the event file, and how to remove the kbd event handler...

---

