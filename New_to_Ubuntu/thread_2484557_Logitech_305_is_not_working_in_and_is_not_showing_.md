---
title: "Logitech 305 is not working in and is not showing up in lsusb"
date: 2023-03-02
forum: New to Ubuntu
---

### Post by revoke2594 on 2023-03-02
I am trying our ubuntu on my laptop and using my keyboard and mouse that I used on my W11 machine. My keyboard works fine but my logitech 305 isn't working at all. I reseated the usb dongle a couple times and tried different ports including the one the keyboard is plugged into. Verified it isn't the batteries as I can use it on my W11 machine. Using lsusb I don't see anything from logitech and can identify everything else in that list. HardInfo also didn't have anything there.

Any ideas of things I can try?

---

### Post by ActionParsnip on 2023-03-03
Reboot the system without the USB device attached and log in. Press CTRL + ALT + T to open a terminal and run:
```

lsusb

```
Plug in the device, wait a few seconds then run:
```

dmesg | tail; lsusb; lsb_release -a; uname -a

```

What is the full output please?

---

### Post by MAFoElffen on 2023-03-03
Also waiting on the response from the OP. Most Logitech G Series mouses work out of the box on Linux.

'dmesg', when you plug and unplug the receiver should see something like:
```

[ 4376.632413] usb 1-1: new full-speed USB device number 8 using xhci_hcd

```
...with the number increasing by 1 each time you do that.

The name to look for in 'lsusb' results is "Logitech, Inc. Unifying Receiver".

If it the keyboard and mouse work on Windows (as you had said) off of a single receiver (as some do), and the keyboard works, but the mouse does not, then I would suspect something going on with the mouse.

The only time I have seen where the G305 didn't show in results was when multiple Logitech mouses were connected, and there was a conflict seeing multiple Logitech USB Dongles of the same type connected at the same time.

---

### Post by revoke2594 on 2023-03-03
It works today :oops:

I tried multiple restarts yesterday and now all of the sudden it decided to work. Thank you for taking the time to comment though.

---

### Post by mIk3_08 on 2023-03-03
> **revoke2594 said:**
> It works today :oops:

I tried multiple restarts yesterday and now all of the sudden it decided to work. Thank you for taking the time to comment though.

On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

