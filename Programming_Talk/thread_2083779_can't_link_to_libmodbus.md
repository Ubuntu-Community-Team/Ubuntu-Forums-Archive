---
title: "can't link to libmodbus"
date: 2012-11-13
forum: Programming Talk
---

### Post by tmullins on 2012-11-13
I'm using modbus for a project, and I'd like to use libmodbus. I have libmodbus5 and libmodbus-dev installed. I try to build using

```

$ gcc -O2 -g -Wall -I.. `pkg-config --cflags --libs libmodbus` (sources...)

```

but I get undefined reference to every modbus_* function I use. The output of pkg-config is:

```

$ pkg-config --cflags --libs libmodbus
-I/usr/include/modbus  -lmodbus

```

There are no static libraries from libmodbus-dev, only a dynamic library, and it has no symbols.

```

$ objdump -t /usr/lib/libmodbus.so

/usr/lib/libmodbus.so:     file format elf64-x86-64

SYMBOL TABLE:
no symbols

```

Is this a mistake in the libmodbus packaging, or am I doing something incorrectly?

---

### Post by spjackson on 2012-11-13
The library has to come after the sources, so move the pkg-config stuff to the end of the command line.

I don't think it matters where the -I flag occurs, but if it does, then keep pkg-config --cflags where it is and put pkg-config --libs at the end.

---

### Post by tmullins on 2012-11-13
That fixed it, thanks :)

---

