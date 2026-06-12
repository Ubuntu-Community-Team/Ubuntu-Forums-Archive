---
title: "Toggling an LED on the Parallel Port"
date: 2007-10-20
forum: Programming Talk
---

### Post by linuxpyro on 2007-10-20
I'm working on a simple C program to toggle an LED on the parallel port.  Basically, I'm just trying to make it blink, switching between on and off every second.  This is what I've got:

```

#include <stdio.h>
#include <unistd.h> /* needed for ioperm() */
#include <sys/io.h> /* for outb() and inb() */


#define DATA 0x378

int main(void)
 {
 
  if (ioperm(DATA,3,1)) {
	printf("Sorry, you were not able to gain access to the ports\n");
 	printf("You must be root to run this program\n");
 	exit(0);
 	}
 while(1){
   printf("LED should turn on.\n");	
   outb(0x08,DATA);
   sleep(1);
   printf("LED should turn off.\n");
   outb(0x00,DATA);
   sleep(1);
   }
 }

```

I compile that using gcc -O2 parallelout.c -o parallout.  The problem is, when I run this it doesn't blink the LED, which is on pin 5 (should be Data 3, I believe).  I've tried a similar program without the while loop and with just one outb line (to set the pin as high or low), and it seems to work; I can turn the LED on or off this way.  But for some reason when I try the program above the LED just stays on.

Any ideas?  I'm using Gutsy right now, and parallel port support is enabled in my BIOS.  This is sort of my first attempt at working with the parallel port, though I'm somewhat familiar with C.  

Thanks for any info...

---

### Post by Wybiral on 2007-10-20
Looks like you're sending your data to two different ports instead of sending two different messages to the same port. Unfortunately I'm not very familiar with parallel port programming so this is just a guess (based on the input format for outb).

---

### Post by DavidBell on 2007-10-20
How similar was the 'similar' program, can it run say four commands on,off,on,off? The documents are not very clear for outb() but there is also outb_p() that *'pauses until the I/O is complete'* that may be worth trying.

Does this need to be accurate? I've only done a little bit of parallel port stuff, in windows if you want sub-50-millisecond timing you need a real mode device driver because of multithreading, my guess you would need something similar in Linux.

DB

---

### Post by bobbocanfly on 2007-10-20
```
   outb(0x08,DATA);
   *snip*
   outb(0x00,DATA);
```

I dont know much about parallel ports but to me that doesnt look right. Are you wanting to send the messages to two different addresses?

---

### Post by DMills on 2007-10-20
Actually outb does put the address as the second argument, so that is right (This is the opposite to most msdos implementations). 

Is sleep returning non zero for some reason?

Regards, Dan.

---

### Post by linuxpyro on 2007-10-27
OK, sorry to leave this for a while, but I figured out that it must be something with my parallel port.  I tried the program on a different machine and it worked fine.

Thanks anyway, and sorry for not noticing this earlier...

---

### Post by kausled on 2008-06-06
What is the command for switching on the DataPin 0 or D5 ?
Is it outb(0x00,BASE); outb(0x05,BASE); ?
:guitar:

---

