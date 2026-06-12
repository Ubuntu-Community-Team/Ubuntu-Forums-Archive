---
title: "msp430 :if a button is pressed on ED create a link to the AP and blink his leds"
date: 2011-07-03
forum: Programming Talk
---

### Post by _dorina on 2011-07-03
[B]Hello, I have to do a project using TI Ez320 rf2500 kit with   msp4302274uc..,from the start I want so say that I am new with   microcontrollers and C but i am willing to learn.
I want to do a project with a smoke detector which gives a ttl signal to   the END DEVICE(1L for detecting smoke),I want to put this signal to   port  PORT2 bit0. and transmit it to ACCESS POINT,where I want to set   PORT2 bit0. as an output so it can give a signal that can trigger a   buzzer.
But up until that moment I want to make something similar to work:
I want to use an ISR at END DEVICE, when I push the button(which gives   1L signal,somehow similar with the somke detector signal(when the somke   is detected))and this is transmitted to the ACCESS POINT where I use as   outputs the two leds,and this leds must blink due to the received   signal.
Now i have a TI code ,named <txrx_simple>, this is the code :
 
#include "mrfi.h"
int main(void)
{
  BSP_Init();// disables the watchdog, initializes the MCLK at 8MHz, sets LED ports as outputs and the button port as input.
 
  P1REN |= 0x04;// enables the internal resistor of thebutton
 
  P1IE |= 0x04;//  enables interrupts
 
 
  MRFI_Init(); // initializes the 6 wires between the MSP430 and the   CC2500,powers-up the CC2500 and con&#64257;gures the CC2500 47 registers and   turns on interrupts from the CC2500;
 
  MRFI_WakeUp();// wakes up the radio, i.e. it turns on the 26MHz crystal attach to it without entering Rx or Tx mode;
 
  MRFI_RxOn() ;// switches the radio to Rx mode; from this line on, it   can receive packets,in which case the interrupt function   MRFI_RxCompleteISR is called.
 
  BCSCTL3 |= LFXT1S_2; //switches on the ACLK by sourcing it to the VLO
  TACCTL0=CCIE; //enables interrupts for Timer_A.
  TACCR0=1000; //sets the value up to which Timer_A will count
  TACTL=MC_1+TASSEL_1; //tells Timer_A to count up (MC_1) each time ACLK ticks (TASSEL_1).
 
  __bis_SR_register(GIE+LPM4_bits);// enables interrupts globally and enters LPM4 
}
 
void MRFI_RxCompleteISR()
{
  P1OUT ^= 0x02;// toggle both leds
}
 
 
#pragma vector=PORT1_VECTOR // declare that this function should be called when an interrupt of type PORT1_VECTOR happens
__interrupt void Port_1 (void)
{
  P1IFG &= ~0x04; //resets the interrupt flag
  mrfiPacket_t packet;
  packet.frame[0]=8+20;
  MRFI_Transmit(&packet, MRFI_TX_TYPE_FORCED);
  P1OUT ^= 0x01;// toggle the red led P1.0
}
 
 
and if I put it on both target boards I have the next situation: for the   start both boards are with both leds off,if I press the button on the   END DEVICE ,nothing happens,not blinking the leds on either of   boards..and if I press the button on the ACCESS POINT both leds on AP   and ED are on,but not blinking(it may have smth to do with the   frequency?)
 
Thanks in advance for any information you could give me.
Have a nice day.[/B]

---

### Post by Petrolea on 2011-07-03
First, use CODE tags to mark the code. And text isn't more readable if it is in bold.

To make a blinking led, you have to turn it on and then off. When you control a led with a program, it is always blinking, which means you have to stop it somehow, then let it blink again. But the blinking is so fast that we see it as if it wasn't blinking. That's why if you turn the led on and off, it will happen within a microsecond (depends on crystal frequency) and you won't see anything. 

So you have to turn it on, stop for few miliseconds then turn it off and so on.

---

