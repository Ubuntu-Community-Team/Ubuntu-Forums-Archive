---
title: "[SOLVED] web cam problem"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by rossmoore on 2008-06-19
Hi,

I've got a Dell X1530M laptop, with an integrated webcam.

It worked in Ubuntu Hardy a few weeks ago, last time I checked. It worked in Cheese and Skype.

Today I thought I'd check it out again, and it is no longer recognised in Skype. In Cheese I just get a test card - lots of colours, some fuzz in the bottom right corner. The webcam light (indicating the webcam is in use) does not light up.

I think webcams normally get mapped to something like /dev/video1, is that right? There's nothing in /dev under vid* any more.

Can anyone help me debug what's going on ?

Thanks,
Ross

---

### Post by rossmoore on 2008-06-19
Some additional information:
I ran dmesg > test.txt, and had a look at the log. I found the following

```
[   22.819450] Linux video capture interface: v2.00
[   22.828318] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   22.833662] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.833671] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   22.833756] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   22.835210] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   22.835344] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
[   22.835346] uvcvideo: Failed to initialize the device (-5).
[   22.835379] usbcore: registered new interface driver uvcvideo
[   22.835381] USB Video Class driver (v0.1.0)
```

Is this a bug with the new linux kernel update that I received a day or so ago?

---

### Post by rossmoore on 2008-06-19
OK, some more research and I'm still not much closer. I have found that, despite being an integrated webcam, it appears to be internally connected to the usb interface. If I run lsusb, I get a number of devices, but among them is:
Bus 006 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 

This webcam is listed as being supported by UVC. So why is it failing to initialize the device?

---

### Post by rossmoore on 2008-06-19
OK, well I seem to have solved it. Still a little confused though.

I ran:
```
lsmod | grep uvc
```
Which listed a number of uvcvideo related modules as installed.
```
sudo rmmod uvcvideo
```
Which then removed all the uvcvideo related modules that were listed above
```
sudo modprobe uvcvideo
```
Which then reinstalled the uvcvideo modules.

The webcam light flashed a few times and suddenly everything worked in cheese and skype.

I did try rebooting before I tried it this (the obvious solution) and it didn't help. Since running this code I have rebooted and it has stayed fixed, which is good news.

So, I don't know what went wrong, but it's OK now. I hope this little thread helps someone with a similar problem - even if it has been a bit one-sided...
:guitar:

---

