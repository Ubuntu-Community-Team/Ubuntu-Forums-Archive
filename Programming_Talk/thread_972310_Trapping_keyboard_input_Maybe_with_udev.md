---
title: "Trapping keyboard input? Maybe with udev?"
date: 2008-11-05
forum: Programming Talk
---

### Post by sickasabat on 2008-11-05
Hi,

I have a barcode scanner that ubuntu treats like a usb keyboard.
this means that the scanned barcodes are simply printed to whatever program has the focus as though I'd typed them by hand.
What I would like is for the scanned barcodes to go into a program that I write, that can run in in the background while I do other things (i.e typing on the actual keyboard). 

At the moment I have it set up so that I can get the input from the scanner in my own program but only if it's the focus. When it's not the focus I am in the same situation as before where the scanned barcode simply gets inserted into whatever I'm doing.

Having searched the forums and google I think that the answer might lie in making a set of udev rules specifically for this device. However I didn't really understand the two sites that I found that explained how to write the rules. I'm also not sure that this will have the result I'm looking for.

Any help or suggestions would be very welcome...

thanks

---

