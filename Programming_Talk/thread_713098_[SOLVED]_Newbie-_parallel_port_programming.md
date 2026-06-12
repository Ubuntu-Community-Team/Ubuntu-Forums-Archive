---
title: "[SOLVED] Newbie- parallel port programming"
date: 2008-03-02
forum: Programming Talk
---

### Post by checksquid on 2008-03-02
Hi all,
I'm a new Ubuntu (and Linux) user, and this forum has been amazingly helpful so far. I think I've finally found something that you haven't already answered (although I found a post that was close).

I am trying to use my parallel port to interface with an electronics project. To start, I am trying a simple "hello world" program to set all of the data pins low, then high. (The timing doesn't matter, I'm just trying to see a response.) I am using a volt meter to watch pin 2 (Data0) in reference to pin 20 (Signal Ground). Unfortunately, the voltemeter is not showing any response--it is always at 0.

Is there a utility I could use to check that the port is working? (It's an old Dell Latitude L400, and I've never used this port before. I'm running Xubuntu.)
Here is the result of dmesg | grep parport
```

[   45.284000] parport_pc 00:07: reported by Plug and Play ACPI
[   45.284000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   48.416000] lp0: using parport0 (interrupt-driven).

```

I am also not a veteran programmer--any suggestions on the code below would be an enormous help.
```

#include <stdio.h>
#include <sys/io.h>
#include <string.h>
#include <errno.h>

#define PORTBASE 0x378 //printer port base address

int main() {
  printf("hello world.\n");
  
  if (ioperm(PORTBASE, 1, 1)) {
    printf("Couldn't get the port.\n");
    perror("ioperm problem:");
  }
  
  outb(0x00, PORTBASE);
	perror("Error from outb?");
  
  outb(0xFF, PORTBASE);
	perror("Error from outb?");
  
  return 0;
}

```

That code results in the following output:
```

weston@weston-laptop:~/C_Test$ sudo gcc -o hello -O2 -Wall hello.c
weston@weston-laptop:~/C_Test$ sudo ./hello
hello world.
Error from outb?: Success
Error from outb?: Illegal seek
weston@weston-laptop:~/C_Test$ 

```

Thanks so much for any help!

---

### Post by bschleusner on 2008-03-02
Are you running it as root? If not, you may be denied access to the port, usually resulting in the oddest errors....

---

### Post by checksquid on 2008-03-02
I'm running it with "sudo", which I believe gives me root permissions (correct me if I'm wrong there--I'm new to Linux).
Could it be that I need to configure the port to a particular mode (SPP, ECP, etc.) before using it? Or could some other process be claiming the port?
Thanks for your help!

---

### Post by wiscados on 2008-03-02
it gives you some root permission, 
to get full root permission use "su",

---

### Post by bschleusner on 2008-03-02
```

[   45.284000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
```

I don't exactly understand what is meant by the 0x378 (0x778), but try setting your port base to 0x778 and see what happens.

---

### Post by checksquid on 2008-03-02
Odd, using 0x778 gives the same output, as does running it as root (now using su) with either address. Is there a safe "dummy" address that I could try to write to to see if a totally invalid address gives me the same result (in which case I'll focus on figuring out if the port works at all)?
(Thanks for  the note on "su"--that's very good to know.)

---

### Post by bschleusner on 2008-03-02
I think it is your code that doesn't work, it fails on my system as well (same error) but yet I can get my python scripts to access it.

you will need the portio module for python to run this.
```

import sys
import os
import portio

# check for root privileges
if os.getuid():
  print 'You need to be root!'
  sys.exit()

# acquire permission for I/O on lp0
portio.ioperm(0x378, 1, 1)

data = 0
portio.outb(data,0x378)

#infinite loop, ctrl+C to stop
while 1:
  data = int(raw_input("Data: "))
  portio.outb(data,0x378)
```

---

### Post by checksquid on 2008-03-03
Wow, thanks for going to all of that trouble. Following your example in python, I am able to write to the port with outb and read it back in with inb. Unfortunately, I'm still not reading anything on the multimeter. That must be something I'm doing wrong, so I'm going to have dinner and then take a good look at what I'm doing to see if it's something obvious. I'll check back in with results.
In any case, it looks like the software is making a connection, which is exciting. Thanks again for your help. This will be a good opportunity to try out python, too.

---

### Post by bschleusner on 2008-03-03
I had to use transistors to get anything to register. I will send you a picture if I get time.

---

### Post by checksquid on 2008-03-03
I think I'm beyond the edge of my electrical knowledge here. I hooked up an ancient (vacuum tube) oscilloscope to pins 2 (data0) and 20 (signal ground). I seem to be getting an AC signal of about 2 volts at 60hz. That wave is not there when I hold the oscilloscope probe in mid air.
When I write 255 to the port, it blips slightly upwards and then settles back where it was (measuring DC, not AC); when I write 0 to the port it does the opposite--blips downwards briefly. If I write the same thing twice the second write doesn't affect it. If I unplug the laptop from the wall, the amplitude drops roughly in half.
I also tried setting the port mode to SPP by writing 000 to the top three bits of 0x378+0x402, following the description here:
[http://as6edriver.sourceforge.net/Parallel-Port-Programming-HOWTO/modeselect.html](http://as6edriver.sourceforge.net/Parallel-Port-Programming-HOWTO/modeselect.html)
but it didn't seem to have any effect. (I was able to read back the data I wrote there, so it seems to have stuck.)
Curioser and curioser.

---

### Post by bschleusner on 2008-03-03
Use a different ground pin. If I remember correctly, pin 20 is labeled as ground, but it is actually ground for the strobe pin (pin 1). I am not sure though, so don't try it until you look it up.

I would test that theory right now, but I just blew out the PSU for my parallel port circuit... :(

---

### Post by checksquid on 2008-03-03
Oh no! :(
You were quite right that the ground wasn't working, but it turned out to be a problem with the cable--I must have just ohmed out the top row of connectors because the whole middle of the bottom row wasn't connected. I've got that fixed now and it's working perfectly.
Thank you so much for your help!

---

### Post by checksquid on 2008-03-03
I think I'll leave troubleshooting that C code to another project--python looks great for what I'm trying to do now. I love the command-by-command interface.

---

