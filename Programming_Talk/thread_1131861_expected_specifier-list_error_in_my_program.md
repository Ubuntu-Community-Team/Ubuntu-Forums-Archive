---
title: "expected specifier-list error in my program"
date: 2009-04-21
forum: Programming Talk
---

### Post by GG_is on 2009-04-21
hi all,
     i am writing a program to access usb device information my program code is:

#include <libio.h>
#include <linux/usbdevice_fs.h>
#include <linux/usb/ch9.h>
#include <linux/types.h>
#include <linux/usb.h>
#include <stdio.h>
#include <fcntl.h>
#include <stddef.h>

int main() {
        struct usb_device newdev, *devptr;
        devptr=usb_get_dev(&newdev);
        return 0;
}

when i am compiling this program this is showing following error:

In file included from /usr/include/linux/usb.h:4,
                 from usbinfo.c:5:
/usr/include/linux/mod_devicetable.h:21: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:36: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:119: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:143: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:157: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:168: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:176: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:184: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:189: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:216: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:249: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:303: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:330: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:355: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:387: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
usbinfo.c: In function ‘main’:
usbinfo.c:11: error: storage size of ‘newdev’ isn’t known
usbinfo.c:12: warning: assignment makes pointer from integer without a cast

please help me about this error.
and also tell that what is means by expected specifier-list error.

---

