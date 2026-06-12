---
title: "How to get PIC 18F2550 working"
date: 2011-08-21
forum: Programming Talk
---

### Post by stefangr1 on 2011-08-21
I've just attempted to program a microcontroller (the 18F2550 PIC processor), using the PicKit 2 PIC programmer.

I have made a very simple piece of electronics (see attached scheme), that should enable me to do in-cirtuit programming using the PIC processor, and with a single LED on one of the IO ports. There's also a 20Mhz crystal. MCLR, PGD, PGC, VSS and VDD are connected to the appropriate ports of the PicKit 2 programmer.

I have made a program using sdcc, that should turn the LED on port B0 on and off. Compiling and writing the PIC is no problem. If I read the contents of the PIC processor after programming, the code matches with that of the program.

Unfortunately, when I start the program the LED won't start blinking as suppozed. I've no idea whether this is due to software or hardware. I would be very grateful if someone with electronics skills would have a look at it...


```
#include "pic18f2550.h"

#define LED_0              PORTBbits.RB0
#define TRIS_0             TRISBbits.TRISB0

unsigned int i = 0;

void main(void)
{
	// Default all pins to digital
    ADCON1 |= 0x0F;

    
	// Make LED I/O pins be outputs
	TRIS_0 = 0;
	
    // Start with the LED on
	LED_0 = 1;

    while(1)
    {
        while(i++ < 65535);
        if (LED_0 == 0) LED_0 = 1;
        else LED_0 = 0;
        i = 0;
    }
}
```

---

### Post by stefangr1 on 2011-08-22
I managed to get things working. As it turns out, the 18f series pic processors are a bit more difficult to program, as you need to set all sorts of configuration flags.

The schema above works, but could be simplified further by removing the external oscillator.

If anyone considers programming his or her own microcontrollers: a simple piece of example software to get things working is as below, it works very well on Ubuntu using pk2cmd and sdcc. 

```
#include "pic18f2550.h"

#define LED_0              PORTBbits.RB0
#define TRIS_0             TRISBbits.TRISB0

// Set the __CONFIG words:
__code char __at __CONFIG1H _conf0 = _OSC_HS__USB_HS_1H;
    // To use the internal oscillator, change to _OSC_INTOSC__INTOSC_CLK0_RA6___USB_EC_1H
__code char __at __CONFIG2L _conf1 = _BODEN_OFF_2L;
__code char __at __CONFIG2H _conf2 = _WDT_DISABLED_CONTROLLED_2H;
__code char __at __CONFIG3H _conf3 = _MCLRE_MCLR_OFF_RE3_ON_3H;
__code char __at __CONFIG4L _conf4 = _LVP_OFF_4L;
__code char __at __CONFIG5L _conf5 = _CP_0_OFF_5L & _CP_1_OFF_5L;
__code char __at __CONFIG5H _conf6 = _CPD_OFF_5H & _CPB_OFF_5H;
__code char __at __CONFIG6L _conf7 = _WRT_0_OFF_6L & _WRT_1_OFF_6L;
__code char __at __CONFIG6H _conf8 = _WRTD_OFF_6H & _WRTB_OFF_6H & _WRTC_OFF_6H;
__code char __at __CONFIG7L _conf9 = _EBTR_0_OFF_7L & _EBTR_1_OFF_7L;
__code char __at __CONFIG7H _conf10 = _EBTRB_OFF_7H;


void delay_ms(long ms)
{
    long i;
    
    while (ms--)
        for (i=0; i < 166; i++);
}

void main(void)
{
    // Initiate Osc with 8MHz (only relevant if you use the internal oscillator)
    //OSCCON = 0x70;
    
	// Default all pins to digital
    ADCON1 |= 0x0F;

    // set pin to output
    TRIS_0 = 0;
        
    // start a loop blinking the led
    while(1)
    {
        LED_0 = 1;
        delay_ms(250);
        LED_0 = 0;
        delay_ms(250);
    }
}

```

---

