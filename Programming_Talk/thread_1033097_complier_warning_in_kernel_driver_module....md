---
title: "complier warning in kernel driver module..."
date: 2009-01-07
forum: Programming Talk
---

### Post by hardyn on 2009-01-07
i am getting a warning when trying to build a kernel driver for the sensoray 626 IO-board.

now i know its a warning but it seems like it might be kind of important.  I have not hacked any C for a loooong time and certainly no kernel hacking; what do you make of this:


/sensoray/s626drv.c:969: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type


969: request = request_irq (irq, handleallinterrupts, flags, board->name, dev_id)

handleallinterupts: static void handleallinterrupts( int irq, void *dev_id, struct pt_regs *regs)


the definition for request_irq is as follows:

int request_irq (unsigned int irq, void (*handler) (int, void *, struct pt_regs *), unsigned long irqflags, const char *devname, void *dev_id);


It looks like the second argument is expecting a pointer, but i cant seem to get a cast to respond properly; i may be asking a noobish question so please be nice

thanks in advance.

---

### Post by dwhitney67 on 2009-01-07
I threw together some C code based on the information from your post to see if I could duplicate/test the issue you are getting when you compile.  I could not.

```

struct pt_regs
{
  int spare;   // placeholder
};


void handleAllInterrupts(int irq, void* devId, struct pt_regs* regs)
{
  // ...
}


int request_irq(unsigned int irq,
                void (*handler)(int, void*, struct pt_regs*),
                unsigned long irqflags,
                const char* devName,
                void* devId)
{
  struct pt_regs regs;  // this is made up
  handler(irq, devId, &regs);
  return 0;
}


int main()
{
  unsigned int  irq   = 10;
  unsigned long flags = 0x00;
  const char*   name  = "foo";
  unsigned int  devId = 0;

  int request = request_irq(irq, handleAllInterrupts, flags, name, &devId);

  return 0;
}

```

Please verify if your code is similar, and if you are still having trouble, post the relevant portions of your code (in its entirety) that you believe are causing the issue.

P.S.  I made up the definition of devId in the main() function; you did not specify in the OP how this was declared.  Other parts of the code were also made-up so as to get the code to compile.

---

### Post by hardyn on 2009-01-07
Thanks for the help;

If you care to have a look at the original code i will refer you here:

[http://www.sensoray.com/downloads/s626_mar07.zip](http://www.sensoray.com/downloads/s626_mar07.zip)

it had to be hacked a little to play nice with ubuntu; but i cannot eliminate the warning.

request_irq seems to be a system function as it is not in the above driver code s626drv.c.


a little more backing information can be found here: [http://kubuntuforums.net/forums/index.php?topic=3100596.0](http://kubuntuforums.net/forums/index.php?topic=3100596.0)


Thanks for your help.

---

### Post by dwhitney67 on 2009-01-07
I've attempted to build your kernel module, however I have hit two snags:

1.  linux/config.h does not exist (either on Ubuntu or Fedora)... or I just could not find it!

2.  KERNEL_24 from the Makefile is reporting a value of 0, which implies that I am compiling with a kernel version other than 2.4 (which is correct; I'm using 2.6.27).

Thus this version of handleallinterrupts() is being used:
```

irqreturn_t handleallinterrupts( int irq, void *dev_id, struct pt_regs *regs )

```
I believe the correct signature for the irq handler (for a 2.6.x kernel) should be:
```

irqreturn_t handler(int irq, void* dev_id);

```

P.S.  Example driver header files I found that use request_irq() are:
```

/lib/modules/`uname -r`/build/include/asm-x86/floppy.h
/lib/modules/`uname -r`/build/include/sound/initval.h

```

P.S.S.  After commenting out the include for "linux/config.h" and changing the signature of handleallinterrupts(), here is the result:
```

 make all
make -C /lib/modules/2.6.27.9-73.fc9.i686/build M=/home/whitney/Download/ubuntu SUBDIRS=/home/whitney/Download/ubuntu
make[1]: Entering directory `/usr/src/kernels/2.6.27.9-73.fc9.i686'
  LD      /home/whitney/Download/ubuntu/built-in.o
  CC [M]  /home/whitney/Download/ubuntu/s626drv.o
  LD [M]  /home/whitney/Download/ubuntu/s626.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/whitney/Download/ubuntu/s626.mod.o
  LD [M]  /home/whitney/Download/ubuntu/s626.ko
make[1]: Leaving directory `/usr/src/kernels/2.6.27.9-73.fc9.i686'

```

---

### Post by hardyn on 2009-01-07
nice!

thank you.

after kernel 2.6 config.h was renamed to autoconfig.h

i fixed this by linking config.h to autoconfig.h; changing the include would work too.

thank you.

---

