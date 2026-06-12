---
title: "Getting HD Serial #"
date: 2008-07-29
forum: Programming Talk
---

### Post by unoodles on 2008-07-29
Hello, I am trying to get the serial number off of my hard drive programatically, using C/C++. Does anyone know how I might go about doing this? It would be best if the solution was cross platform. Thanks in advance.

---

### Post by Zugzwang on 2008-07-29
Since that requires access to the hardware, having that cross-platform is hard. Your best bet is probably to rely on other tools which are developed for a lot of different platforms. The [SMARTCTL]("http://smartmontools.sourceforge.net/man/smartctl.8.html") tool can get the serial number on the command line, if you are developing in C or C++, you could just parse its output.

---

### Post by tomchuk on 2008-07-29
This should do the trick on linux, smartmontools should give you ideas on how to make it work more portably. Needs read access to the device in question that is passed in as a command line argument.
```

#include <stdio.h>
#include <fcntl.h>
#include <linux/hdreg.h>

int main(int argc, char** argv){
  unsigned short int id[256];
  int fd = open(argv[1], O_RDONLY|O_NONBLOCK);
  ioctl(fd, HDIO_GET_IDENTITY, id);
  char *c = (char *)&id[10];
  while(*c == ' ') ++c;
  printf("Serial for %s: %s\n", argv[1], c);
  return 0;
}

```

---

