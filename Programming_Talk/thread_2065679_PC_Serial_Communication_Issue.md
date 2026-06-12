---
title: "PC Serial Communication Issue"
date: 2012-10-02
forum: Programming Talk
---

### Post by smartbei on 2012-10-02
Hello,
I have been trying to set up communication between an MSP430 and my computer (running Ubuntu). I have had two problems with using the serial ports (one for each of /dev/ttyACM0 and /dev/ttyS0). Note that I doubt the problem is MSP430-specific.

**/dev/ttyS0**
The first problem arises when I tried to connect the MSP directly to the motherboard serial port. When reading from /dev/ttyS0 I get the data:
```

5e4845d2d31b0abafadbaaeabafabb6acabaea1acaaafa5b2b7b
```
(in hex)
instead of:
```
Could not read distance :-(\r\n
```
The read text is of length 26, whereas the text that should arrive is of length 29. Because 29/8*7 ~= 26, my assumption was that the problem lies in the computer being configured wrong, and expecting a parity bit where none is sent. The stty output for the port is:
```

speed 9600 baud; rows 0; columns 0; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^H; eof = ^D; eol = <undef>;
eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R;
werase = ^W; lnext = ^V; flush = ^O; min = 100; time = 2;
-parenb -parodd cs8 -hupcl -cstopb cread clocal -crtscts
-ignbrk brkint ignpar -parmrk -inpck -istrip -inlcr -igncr -icrnl ixon -ixoff
-iuclc -ixany -imaxbel -iutf8
-opost -olcuc -ocrnl -onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
-isig -icanon iexten -echo echoe echok -echonl -noflsh -xcase -tostop -echoprt
echoctl echoke

```
I have tried messing with the options that look relevant, but generally it looked worse.

**/dev/ttyACM0**
/dev/ttyACM0 appears on connecting the MSP to the computer. When I try to use screen to read the output:
```

screen /dev/ttyACM0 9600
```
I get the results:
```

Cannot open line /dev/ttyACM0: Input/Output error
or 
Cannot access line /dev/ttyACM0 fpr R/W: permission denied
```
Also, if the first happens (Input/Output error), the mouse and keyboard freeze for about 5 seconds.

I have tried running screen as sudo, but this does not seem to help.

Thanks!

---

### Post by trent.josephsen on 2012-10-03
I think you're dealing with more than just parity problems. If I had to guess, I'd say you have a timing issue. Does it output the same thing every time you test?

---

### Post by smartbei on 2012-10-03
Yes, it does, exactly. That is why I assumed that is not the problem. I noticed something else - the bits I read are almost exactly the bits I wrote, **negated** and missing a few. This got me to thinking that I might have mis-wired the ground and RxD wires (although I used the port pinout diagram, so it should have been fine...). I will test this out tomorrow.

---

### Post by smartbei on 2012-10-12
Reversing the wiring did not help (when reversed, nothing is input).

What could cause timing issues? The length of the cable itself quite short, so I doubt that is the problem...

Thanks for your felp!

---

### Post by trent.josephsen on 2012-10-12
> **smartbei said:**
> What could cause timing issues? The length of the cable itself quite short, so I doubt that is the problem...
Hardware flow control being broken, miswired or not used at all. Maybe both ends don't completely agree on phase and/or frequency, so a bit is occasionally being dropped.

To be sure, I'd want to test it on a digital logic analyzer, but you probably don't have one of those just lying around...

The inversion is also interesting, but without knowing more about your setup I can't guess where it might be coming from.

You didn't mention what you're using *with* the MSP430, which seems the most relevant question at the moment. Are you using some kind of development board or is this a custom application?

---

### Post by smartbei on 2012-10-12
Sorry - I am using the launchpad. I am connected directly to the MSP UART pins though, so the launchpad itself doesn't look relevant to me (I removed the jumpers connecting the UART to the launchpad side of the board). I am using the msp430 built-in hardware UART.

The msp430 is configured as follows:
```

WDTCTL  = WDTPW + WDTHOLD; 	// Stop WDT
BCSCTL1 = CALBC1_1MHZ;      // Set DCO
DCOCTL  = CALDCO_1MHZ;
P1SEL  = RXD + TXD;                       
P1SEL2 = RXD + TXD;                       
UCA0CTL1 |= UCSSEL_2;                     // SMCLK
UCA0BR0 = 104;                            // 1MHz 9600
UCA0BR1 = 0;                              // 1MHz 9600
UCA0MCTL = UCBRS0;                        // Modulation UCBRSx = 1
UCA0CTL1 &= ~UCSWRST;                     // Initialize USCI state machine
IE2 |= UCA0RXIE;                          // Enable USCI_A0 RX interrupt

```

I think this is fine, because using the serial emulator on board the launchpad I have been able to communicate with the PC (/dev/ttyACM0), but this was giving me problems so I am trying to communicate directly.

I programmed the MSP like so:
```

	unsigned char i = 0x21;
	for (; i < 0x80; i++) {
		uart_putc(i);
	}
	for (; i > 0x20; i--) {
		uart_putc(i);
	}

```
And got the following result:
```

DB CB BB AB 9B 8B 7B 6B 5B 4B 3B 2B 1B 0B FB EB DB CB BB AB 9B 8B 7B 6B 5B 4B 3B 2B 1B 0B FB F5 ED E5 DD D5 CD C5 BD B5 AD A5 9D 95 8D 85 7D 75 6D 65 5D 55 4D 45 3D 35 2D 25 1D 15 0D 05 FD F5 ED E5 DD D5 CD C5 BD B5 AD A5 9D 95 8D 85 7D 75 6D 65 5D 55 4D 45 3D 35 2D 25 1D 15 0D 05 FD 02 03 05 07 09 0B 0D 0F 15 17 19 1B 1D 1F 21 23 25 27 29 2B 2D 2F 31 33 35 37 39 3B 3D 3F 41 43 45 47 49 4B 4D 4F 51 53 55 57 59 5B 5D 5F 61 63 65 67 69 6B 6D 6F 71 73 75 77 79 7B 7D 7F 81 83 85 87 89 8B 8D 8F 91 93 95 97 99 9B 9D 9F A1 A3 A5 A7 A9 AB AD AF B1 B3 B5 B7 B9 BB BD

```
Which is the right amount of bytes. At a glance you can see something is going on. It looks like a rotated, inverse counter, where every so often (usually close to a multiple of 0x20) the the rotation changes, and stays that way for some time...

Ideas?

Thanks a lot for your help!!!

---

### Post by trent.josephsen on 2012-10-12
Yeah, you're probably right that it's not launchpad-related. That said, I'm at a bit of a loss...

You said you're connecting it directly to the PC's serial port -- is that a regular [DE-9](http://en.wikipedia.org/wiki/D-subminiature) serial port? Because unless you have documentation to indicate otherwise, I imagine the processor can't drive the standard RS-232 (or RS-whatever) signal your PC expects; that requires high positive and negative voltages that you typically need a charge pump for. Unless by "directly" you mean you have an RS-232 converter which is directly connected.

Sorry if I'm making some dumb assumption here; I don't know anything about the MSP430 or the dev board that I didn't learn today, but I do have some experience controlling and debugging serial connections, and it sounds like your particular problem is on the opposite end of the cable from the PC.

---

