---
title: "/dev/ttys0, with a lower-case &quot;s&quot;"
date: 2008-03-14
forum: Programming Talk
---

### Post by Dro Kulix on 2008-03-14
Hiya, friends.

When trying to explain (to a guy who seems to use everything but Linux--FreeBSD, OS X, and Windows) what serial ports look like in /dev under Linux, I was able to readily explain that /dev/ttyS[0123] correspond to COM[1234] in Windows.  What I was not able to explain, though, is why a listing of such needs to be case-sensitive.  The program should be making a list of, among other things, the glob /dev/ttyS*.  On my system, that's this:

```
$ ls -1 /dev/ttyS*
/dev/ttyS0
/dev/ttyS1
/dev/ttyS2
/dev/ttyS3
```

His code treats that glob as if it's case-insensitive and lists something more like this:

```
$ ls -1 /dev/tty[Ss]*
/dev/ttys0
/dev/ttyS0
/dev/ttys1
/dev/ttyS1
/dev/ttys2
/dev/ttyS2
/dev/ttys3
/dev/ttyS3
/dev/ttys4
/dev/ttys5
/dev/ttys6
/dev/ttys7
/dev/ttys8
/dev/ttys9
/dev/ttysa
/dev/ttysb
/dev/ttysc
/dev/ttysd
/dev/ttyse
/dev/ttysf
```

So, I'm pretty sure I'm right, but if I knew what these "/dev/ttys*" devices (with a lower-case "s") were, I'd be able to solidify my argument.  I tried to Google for it, but Google, itself being case-insensitive, didn't turn up anything helpful.

So, anyone know what these things are?

---

### Post by LaRoza on 2008-03-14
's' == 115
'S' == 83

The ancient DOS convention of using all uppercase letters (they were at the time all uppercase) is found in Windows as well.

*nix based operating systems make a distinction.

(I don't know if the S and s distinction matters in this case, they may be an alias for the other, I will research. I have no experience or knowledge of this area)

This has both, but doesn't make a distinction: [http://tldp.org/HOWTO/Modem-HOWTO-9.html](http://tldp.org/HOWTO/Modem-HOWTO-9.html)

Wikiepedia has only the uppercase S version: [http://en.wikipedia.org/wiki/Serial_port#.22Virtual.22_serial_ports](http://en.wikipedia.org/wiki/Serial_port#.22Virtual.22_serial_ports)

---

### Post by Dro Kulix on 2008-03-14
Here's why I doubt they're merely aliases:

```
crw-rw-rw- 1 root tty     3, 48 2008-02-19 13:00 /dev/ttys0
crw-rw---- 1 root dialout 4, 64 2008-02-19 13:00 /dev/ttyS0
crw-rw-rw- 1 root tty     3, 49 2008-02-19 13:00 /dev/ttys1
crw-rw---- 1 root dialout 4, 65 2008-02-19 13:00 /dev/ttyS1
crw-rw-rw- 1 root tty     3, 50 2008-02-19 13:00 /dev/ttys2
crw-rw---- 1 root dialout 4, 66 2008-02-19 13:00 /dev/ttyS2
crw-rw-rw- 1 root tty     3, 51 2008-02-19 13:00 /dev/ttys3
crw-rw---- 1 root dialout 4, 67 2008-02-19 13:00 /dev/ttyS3
```

The node numbers are entirely different, and I'm pretty sure that means they refer to different hardware.  Also, the lower-case ones have all the hex digits 0-f whereas only the first four of the upper-case exist.

---

### Post by Dro Kulix on 2008-03-14
That was a good lead, actually, because it said to look in the Linux devices.txt file in the kernel docs.  It says:

```
  3 char    Pseudo-TTY slaves
          0 = /dev/ttyp0    First PTY slave
          1 = /dev/ttyp1    Second PTY slave
            ...
        255 = /dev/ttyef    256th PTY slave

        These are the old-style (BSD) PTY devices; Unix98
        devices are on major 136 and above.
```

and goes on to say

```
  4 char    TTY devices
          0 = /dev/tty0     Current virtual console

          1 = /dev/tty1     First virtual console
            ...
         63 = /dev/tty63    63rd virtual console
         64 = /dev/ttyS0    First UART serial port
            ...
        255 = /dev/ttyS191  192nd UART serial port

        UART serial ports refer to 8250/16450/16550 series devices.

        Older versions of the Linux kernel used this major
        number for BSD PTY devices.  As of Linux 2.1.115, this
        is no longer supported.  Use major numbers 2 and 3.
```

Thanks for the tip. Now I have ammo. :-)

---

### Post by LaRoza on 2008-03-14
> **Dro Kulix said:**
> 
Thanks for the tip. Now I have ammo. :-)

Ah good. I had to leave to catch a bus, so I didn't get to research it more.

---

