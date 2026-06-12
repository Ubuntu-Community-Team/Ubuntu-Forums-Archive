---
title: "Program blocked after an unplug."
date: 2011-08-17
forum: Programming Talk
---

### Post by Julien Valentin on 2011-08-17
Hello,

I'm currently developing a program that uses libusb with Ubuntu to deal with a device. I have an issue sometimes after an unplug: the program gets blocked when releasing the interface.
After further investigations it seems that the libusb is blocked when calling any function from the linux_usbfs_backend.
And in the syslog file I have the following lines:

kernel: [ 7441.276573] INFO: task test_transfer:3348 blocked for more than 120 seconds.
kernel: [ 7441.276580] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
kernel: [ 7441.276584] test_transfer D 00382299     0  3348   3255 0x00000000
kernel: [ 7441.276593]  f35a9e90 00200086 f70bb680 00382299 00000000 c084b860 f2605be4 c084b860
kernel: [ 7441.276609]  a66553fa 000005b4 c084b860 c084b860 f2605be4 c084b860 c084b860 f2fff400
kernel: [ 7441.276618]  a66528a2 000005b4 f2605940 7fffffff f273dc98 f2605940 f35a9ef0 c058a5ad
kernel: [ 7441.276627] Call Trace:
kernel: [ 7441.276640]  [<c058a5ad>] schedule_timeout+0x1ad/0x280
kernel: [ 7441.276647]  [<c0209d44>] ? do_sync_read+0xc4/0x100
kernel: [ 7441.276652]  [<c058b32f>] __down+0x5f/0x90
kernel: [ 7441.276657]  [<c016d489>] down+0x39/0x40
kernel: [ 7441.276662]  [<c0451a14>] usbdev_release+0x24/0xf0
kernel: [ 7441.276667]  [<c020b72f>] __fput+0xdf/0x1f0
kernel: [ 7441.276671]  [<c020b85d>] fput+0x1d/0x30
kernel: [ 7441.276676]  [<c0207d9c>] filp_close+0x4c/0x80
kernel: [ 7441.276680]  [<c0207e45>] sys_close+0x75/0xc0
kernel: [ 7441.276685]  [<c01033ec>] syscall_call+0x7/0xb

I am new to libusb and Ubuntu so I am not really sure how I can understand it: does it mean I did something wrong before or is the Kernel not responding?
Do you have any idea about what can make these logs happen?
Also after this if I kill the task the USB ports are blocked and as we use Udev to detect the usb devices it still sees the device as plugged.
Any comment would be much appreciated.
Thank you,
Julien

---

