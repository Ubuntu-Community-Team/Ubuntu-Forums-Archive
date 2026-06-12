---
title: "Read a USB scale, any language"
date: 2012-08-20
forum: Programming Talk
---

### Post by CrusaderAD on 2012-08-20
I've got a Dymo USB plug and play scale I'd like to read from. Problem is there is ZERO support from the manufacturer or seller. Does anyone know how I'd get started developing something to read the weight from this scale?

---

### Post by CrusaderAD on 2012-08-20
I've made some progress. I'm using the script found [here]("http://steventsnyder.com/reading-a-dymo-usb-scale-using-python/"). But now I'm getting this error:

> usb.core.USBError: [Errno 16] Resource busy

Any ideas?

---

### Post by steeldriver on 2012-08-20
do you know at what point in the script you get that error?

have you tried running it with elevated privileges (sudo)? if so it may be something to do with udev rules / permissions?

I am just guessing here though... I'm impressed you've got this far

---

### Post by CrusaderAD on 2012-08-20
Thanks for the reply! I've been running this with sudo. If I don't, I get a permission issue. This is the complete error:

> Traceback (most recent call last):
  File "scale.py", line 12, in <module>
    device.set_configuration()
  File "/usr/local/lib/python2.7/dist-packages/usb/core.py", line 547, in set_configuration
    self._ctx.managed_set_configuration(self, configuration)
  File "/usr/local/lib/python2.7/dist-packages/usb/core.py", line 92, in managed_set_configuration
    self.backend.set_configuration(self.handle, cfg.bConfigurationValue)
  File "/usr/local/lib/python2.7/dist-packages/usb/backend/libusb10.py", line 503, in set_configuration
    _check(_lib.libusb_set_configuration(dev_handle, config_value))
  File "/usr/local/lib/python2.7/dist-packages/usb/backend/libusb10.py", line 403, in _check
    raise USBError(_str_error[ret], ret, _libusb_errno[ret])
usb.core.USBError: [Errno 16] Resource busy

---

### Post by Zugzwang on 2012-08-20
Can you output the last few (scale related) lines that "dmesg" produces when executed a few seconds after the scale is plugged in? Probably it is attached as a virtual serial port.

---

### Post by CrusaderAD on 2012-08-20
Sure:

> [185636.592060] usb 7-2: new low-speed USB device number 6 using uhci_hcd
[185636.843237] generic-usb 0003:1446:6A78.0007: hiddev0,hidraw2: USB HID v1.01 Device [X.J.GROUP USB Post Scale] on usb-0000:00:1d.1-2/input0

---

### Post by steeldriver on 2012-08-20
there's some places suggesting that on Linux you need to do an additional step of calling device.detach_kernel_driver ?

[http://comments.gmane.org/gmane.comp.python.pyusb.user/312](http://comments.gmane.org/gmane.comp.python.pyusb.user/312)

---

### Post by Zugzwang on 2012-08-20
So your scale is already handled by a driver, which is causing the "device busy" error. You may of course circumvent that driver and do someting with pyusb - but I don't see why this should be necessary or wise. You will need to find out where under /dev/ the scale has been mounted. I'm guessing input0, or usb/something. Then, you can use one of the many scripts around that are meant to deal with such scales:

[https://gist.github.com/503896](https://gist.github.com/503896)
[http://www.linuxquestions.org/questions/linux-hardware-18/installing-a-usb-scale-503125/](http://www.linuxquestions.org/questions/linux-hardware-18/installing-a-usb-scale-503125/)

---

### Post by CrusaderAD on 2012-08-20
> **steeldriver said:**
> there's some places suggesting that on Linux you need to do an additional step of calling device.detach_kernel_driver ?

[http://comments.gmane.org/gmane.comp.python.pyusb.user/312](http://comments.gmane.org/gmane.comp.python.pyusb.user/312)

It doesn't quite explain how to deploy this fix very well, although it looks like this person had a similar problem.

---

### Post by CrusaderAD on 2012-08-20
> **Zugzwang said:**
> So your scale is already handled by a driver, which is causing the "device busy" error. You may of course circumvent that driver and do someting with pyusb - but I don't see why this should be necessary or wise. You will need to find out where under /dev/ the scale has been mounted. I'm guessing input0, or usb/something. Then, you can use one of the many scripts around that are meant to deal with such scales:

[https://gist.github.com/503896](https://gist.github.com/503896)
[http://www.linuxquestions.org/questions/linux-hardware-18/installing-a-usb-scale-503125/](http://www.linuxquestions.org/questions/linux-hardware-18/installing-a-usb-scale-503125/)

Hm I know it's mounted in > /dev/usb/hiddev0 I'll keep messing with it.

---

### Post by CrusaderAD on 2012-08-20
I made some serious progress with this code in C#:

```
#include <stdlib.h>
#include <stdio.h>
#include <sys/ioctl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <asm/types.h>
#include <fcntl.h>
#include <unistd.h>
#include <linux/hiddev.h>

#define EV_NUM 5


int main (int argc, char **argv) {

  int fd = -1;
  int i;
  struct hiddev_event ev[EV_NUM];
  char name[100];

  if (argc != 2) {
    fprintf(stderr, "usage: %s hiddevice - probably /dev/usb/hiddev0\n", argv[0]);
    exit(1);
  }
  if ((fd = open(argv[1], O_RDONLY)) < 0) {
    perror("hiddev open");
    exit(1);
  }

  ioctl(fd, HIDIOCGNAME(100), name);

  printf("OK name = %s\n", name);
  
  printf("Reading values .. \n");

      read(fd, ev, sizeof(struct hiddev_event) * EV_NUM);
      for (i = 1; i < 2;i++) {
          printf("%d\n", ev[i].value);

  }

  close(fd);

  exit(0);
}
```

It's result is 361 (36.1 oz) which equals 2 lbs, 4.1 oz. Does anyone know how to execute this without sudo privileges?

---

### Post by trent.josephsen on 2012-08-20
> **CerealCypher said:**
> I made some serious progress with this code in C#

C, surely?

---

### Post by CrusaderAD on 2012-08-20
> **trent.josephsen said:**
> C, surely?

Yes, C. [Credit]("http://www.linuxquestions.org/questions/linux-hardware-18/installing-a-usb-scale-503125/").

---

### Post by steeldriver on 2012-08-20
> **CerealCypher said:**
> Does anyone know how to execute this without sudo privileges?

I have no experience but I *think* it's a matter of writing a suitable udev rule 

[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

---

### Post by CrusaderAD on 2012-08-20
Solved! Sudo question answered [Here]("http://ubuntuforums.org/showthread.php?t=2044999"). Thanks everyone!

---

