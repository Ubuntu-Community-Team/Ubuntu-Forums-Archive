---
title: "USB-&gt; Parallel port lead"
date: 2013-01-10
forum: Programming Talk
---

### Post by linuxonbute on 2013-01-10
I bought one of these leads because I thought I could use it as a simple I/O port on my laptop. I have no idea how to access it though.
I am running Ubuntu 12.04 

dmesg gives the following on plugging it in:
[176335.936201] usb 5-1: new full-speed USB device number 14 using ohci_hcd
[176336.506326] usblp0: USB Bidirectional printer dev 14 if 0 alt 0 proto 2 vid 0x1A86 pid 0x7584
[176336.506391] usbcore: registered new interface driver usblp

Any pointers as to reading and writing through it please?
I am guessing it would be some sort of file access.
( I would prefer C/C++ code or python, neither of which I am anything but a beginner with. :roll:)
Thanks

---

### Post by linuxonbute on 2013-01-12
Found what I needed to do this as I wanted so thought I would update it here in case anyone else is interested.

Using the parallel port as a data access system.
taken from [http://tldp.org/HOWTO/IO-Port-Programming-6.html#ss6.1](http://tldp.org/HOWTO/IO-Port-Programming-6.html#ss6.1)
with some bits added myself.
====================================================================================
           OR to turn bit on. AND to turn it off								
           Bit	    0	    1	    2	    3	    4	    5	    6	   7
           OR	    1	    2	    4	    8	  16	  32	  64	128
         AND	254	253	251	247	239	223	191	127

====================================================================================
The port BASE+0 (Data port) controls the data signals of the port (D0 to D7 for bits 0 to 7, respectively; states: 0 = low (0 V), 1 = high (5 V)). A write to this port latches the data on the pins. A read returns the data last written in standard or extended write mode, or the data in the pins from another device in extended read mode.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
The port BASE+1 (Status port) is read-only, and returns the state of the following input signals:
Bits 0 and 1 are reserved.
Bit 2 IRQ status (not a pin, I don't know how this works)
Bit 3 ERROR (1=high)
Bit 4 SLCT (1=high)
Bit 5 PE (1=high)
Bit 6 ACK (1=high)
Bit 7 -BUSY (0=high)
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
The port BASE+2 (Control port) is write-only (a read returns the data last written), and controls the following status signals:
Bit 0 -STROBE (0=high)
Bit 1 -AUTO_FD_XT (0=high)
Bit 2 INIT (1=high)
Bit 3 -SLCT_IN (0=high)
Bit 4 enables the parallel port IRQ (which occurs on the low-to-high transition of ACK) when set to 1.
Bit 5 controls the extended mode direction (0 = write, 1 = read), and is completely write-only (a read returns nothing useful for this bit).
Bits 6 and 7 are reserved.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Pinout (a 25-pin female D-shell connector on the port) (i=input, o=output):
1io -STROBE, 	2io D0, 	3io D1, 	4io D2, 	5io D3, 	6io D4, 	7io D5, 	8io D6,	9io D7, 
10i ACK,	 11i -BUSY,	 12i PE, 	13i SLCT, 	14o -AUTO_FD_XT,	15i ERROR, 	16o INIT, 	17o -SLCT_IN, 	18-25 Ground
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
The IBM specifications say that pins 1, 14, 16, and 17 (the control outputs) have open collector drivers pulled to 5 V through 4.7 kiloohm resistors (sink 20 mA, source 0.55 mA, high-level output 5.0 V minus pullup). 
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
The rest of the pins sink 24 mA, source 15 mA, and their high-level output is min. 2.4 V. The low state for both is max. 0.5 V. Non-IBM parallel ports probably deviate from this standard. For more information on this, see [http://www.hut.fi/Misc/Electronics/circuits/lptpower.html](http://www.hut.fi/Misc/Electronics/circuits/lptpower.html).
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Finally, a warning: Be careful with grounding. I've broken several parallel ports by connecting to them while the computer is turned on. It might be a good thing to use a parallel port not integrated on the motherboard for things like this. (You can usually get a second parallel port for your machine with a cheap standard `multi-I/O' card; just disable the ports that you don't need, and set the parallel port I/O address on the card to a free address. You don't need to care about the parallel port IRQ if you don't use it.)
=====================================================================================
This program shows a way to use it.
It needs to be run as root to work.
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/io.h>
#include <sys/types.h>
#include <fcntl.h>

#define BASEPORT 0x378 /* lp1 */

int main() {
	char c;
	int n, tem;
	
	printf("Hit any key to stop\n");
	
	//set permissions to access port
	if (ioperm(BASEPORT, 3, 1)) {perror("ioperm"); exit(1);}
	
	tem = fcntl(0, F_GETFL, 0);
	fcntl (0, F_SETFL, (tem | O_NDELAY));
	
	//main loop where actual blinking is done
	while (1) {
		//if some key is pressed, break out from loop
		n = read(0, &c, 1);
		if (n > 0) break;
		
		//write 'on' bit on all data pins and wait 1/4 second
		outb(255, BASEPORT);
		usleep(250000);
		
		//write 'off' bit on all data pins and wait 1/4 second
		outb(0, BASEPORT);
		usleep(250000);
	}
	
	fcntl(0, F_SETFL, tem);
	outb(0, BASEPORT);
	
	//take away permissions to access port
	if (ioperm(BASEPORT, 3, 0)) {perror("ioperm"); exit(1);}
	
	exit(0);
}

```

---

