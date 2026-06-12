---
title: "Execute program without sudo"
date: 2012-08-20
forum: Programming Talk
---

### Post by CrusaderAD on 2012-08-20
I have this program which reads from /dev/usb device but requires sudo to run it. Is there a way to execute it without using sudo?

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

---

### Post by CrusaderAD on 2012-08-20
Solution: [http://ubuntuforums.org/showthread.php?t=1878346]("http://ubuntuforums.org/showthread.php?t=1878346")

> You should make a UDEV rule that allows all permissions for the specific USB device. Something in the trend like 

KERNEL=="hiddev*", MODE="0666", NAME="usb/%k"

where "hiddev" is your usb device (see how yours is named under
/sys/bus/usb/devices/ )

place this in your /etc/udev/rules.d directory as the file 99_my.rules

to let them have effect it is most easy to reboot.

---

