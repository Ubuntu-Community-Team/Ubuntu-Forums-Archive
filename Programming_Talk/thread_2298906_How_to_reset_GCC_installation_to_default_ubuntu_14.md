---
title: "How to reset GCC installation to default ubuntu 14.04?"
date: 2015-10-14
forum: Programming Talk
---

### Post by UkMeterman on 2015-10-14
Hi,
I have been having problems building libmodbus 3.0.6 [http://libmodbus.org/](http://libmodbus.org/)  it builds correctly on a 14.04 live cd system, but both my laptop and  desktop running 14.04 have problems. How do I get my GCC install  including any configuration to the same same as the live CD? 

To reproduce download and unpack 3.0.6.
 ./configure
 make
cd tests
./unit-test-server rtu

you make need to edit unit-test-server.c so that it uses a serial device on your system

A valid response would be waiting for an indication 


I am also getting ERROR connection reset by peer : read  

Thanks

---

### Post by ian-weisser on 2015-10-14
It probably is already the same...Unless you updated from someplace other than the Ubuntu repositories.

Here are the versions of gcc in Ubuntu:
```
$ rmadison gcc
 gcc | 4:4.6.3-1ubuntu5 | precise | amd64, armel, armhf, i386, powerpc
** gcc | 4:4.8.2-1ubuntu6 | trusty  | amd64, arm64, armhf, i386, powerpc, ppc64el**
 gcc | 4:4.9.2-2ubuntu2 | vivid   | amd64, arm64, armhf, i386, powerpc, ppc64el
 gcc | 4:5.2.1-3ubuntu1 | wily    | amd64, arm64, armhf, i386, powerpc, ppc64el

```

Note that no versions of gcc are in trusty-updates nor trusty-security.

Check your version of gcc with:
```
gcc --version
```

---

### Post by UkMeterman on 2015-10-15
Hi,
The version is correct, and I upgraded to 15.10 and still the same issue. I am going to try reinstalling 14.04 from scratch.

---

### Post by UkMeterman on 2015-10-16
Hi,
I have reinstalled 14.04 on the laptop and it seems to have fixed it, any suggestions on what to check on the desktop. If I do a diff between build on the laptop and desktop which logs would help to explain the problem?

---

### Post by steeldriver on 2015-10-16
I would think it's more likely to be a difference between the runtime libraries on the respective systems than anything to do with GCC- have you run ldd on the binary in the working and non-working case and compared library versions?

---

### Post by UkMeterman on 2015-10-16
Ldd reports not a dynamic executable.
One thing to point out the installation may have been altered in the past to support cross compiling for the raspberry pi, also various FPGA system on chip and ARM NXP tools have been installed.

---

### Post by steeldriver on 2015-10-16
You're probably looking at the wrapper script - the actual binaries are hidden in tests/.libs

In fact tests/unit-test-server seems to call .libs/**lt**-unit-test-server

You may be able to debug it further if you hack the script and change func_exec_program_core () to run the program binary inside gdb

```

# Core function for launching the target application
func_exec_program_core ()
{

      if test -n "$lt_option_debug"; then
        $ECHO "unit-test-server:unit-test-server:${LINENO}: newargv[0]: $progdir/$program" 1>&2
        func_lt_dump_args ${1+"$@"} 1>&2
      fi
      exec [COLOR=#0000ff]**gdb --args**[/COLOR] "$progdir/$program" ${1+"$@"}

      $ECHO "$0: cannot exec $program $*" 1>&2
      exit 1
}

```

The error seems to occur in modbus.c arround

```

        rc = ctx->backend->recv(ctx, msg + msg_length, length_to_read);
        if (rc == 0) {
            errno = ECONNRESET;
            rc = -1;
        }

```

FWIW there is an error report here (might be yours?) --> [https://github.com/stephane/libmodbus/issues/287](https://github.com/stephane/libmodbus/issues/287)

---

