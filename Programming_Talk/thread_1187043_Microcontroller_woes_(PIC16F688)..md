---
title: "Microcontroller woes (PIC16F688)."
date: 2009-06-14
forum: Programming Talk
---

### Post by Thesuperchang on 2009-06-14
This question is aimed at all you smart microcontroller developers out there.

I'm playing around with hardware at the moment. My demo program is designed to set pins 5 and 6 as 5V and the rest as 0V. Ground has been set to 0V and Vdd has been set to 5V. All other pins are set as inputs and fed 0V.

Pretty much what happens is when I turn it on, pins 5 and 6 rise to 5V and then immediately fall back to ground. Does anyone have any idea of why this may occur. I'll post my schematic a little later.

Device: PIC16F688
OPTIONS: Watchdog timer is disabled and CLK @ 4Mhz (defined in IDE)
CODE:
[PHP]#define HI 1
#define LO 0

void init_PIC16F688(void);

void set_bit(char *port, char bit, char state);
char tell_bit(char *port, char bit);

void main(void) {
     /////////////////////
     // Initialisations //
     /////////////////////
     init_PIC16F688();
     
     /////////////////////
     //  Begin Program  //
     /////////////////////
     set_bit( &PORTC, 4, HI );
     set_bit( &PORTC, 5, HI );

     delay_ms(1000);
     
     return;
}


void set_bit(char *port, char bit, char state) {
     if(state = HI) {
          *port |= (1 << bit);
     }
     else {
          *port &= ~(1 << bit);
     }
     
     return;
}


char tell_bit(char *port, char bit) {
     return (( *port & (1 << bit) ) >> bit);
}


void init_PIC16F688(void) {
     // For port A
     set_bit(&TRISA, 0, HI);
     set_bit(&TRISA, 1, HI);
     set_bit(&TRISA, 2, HI);
     set_bit(&TRISA, 3, HI);
     set_bit(&TRISA, 4, HI);
     set_bit(&TRISA, 5, HI);

     // For port C
     set_bit(&TRISC, 0, HI);
     set_bit(&TRISC, 1, HI);
     set_bit(&TRISC, 2, HI);
     set_bit(&TRISC, 3, HI);
     set_bit(&TRISC, 4, LO);
     set_bit(&TRISC, 5, LO);

     return;
}[/PHP]

Regards,
-C. Anderson.

---

### Post by mdurham on 2009-06-14
> and then immediately fall back to ground
How immediate is immediately? and is delay_ms(1000) really doing a delay?

---

### Post by Thesuperchang on 2009-06-14
By immediate I mean a something like a millisecond. However I concluded that every port will flash like that no matter whether they're hi or low. As for the delay_ms(1000), that should stall the program for 1 before termination.

---

### Post by leblancmeneses on 2009-06-14
a couple of problems.

state = HI
needs to be
state == HI

i notice you don't end with

while(1); // infinite loop

this is a problem in a microcontroller that is assumed to never end.
I don't think manual even discusses what happens to pins ..


the set_bit function is pretty nifty!  I might start doing this myself rather than using R* ports.
what tools you using for development?
you developing on linux or windows for microchip boards?

---

### Post by mdurham on 2009-06-14
I agree that state = HI needs to be state == HI, but it will work by accident and always execute the first "if(state = HI)" and set the bit.
The delay should allow the bits to remain high for at least 1 second though.

---

### Post by Thesuperchang on 2009-06-14
Gosh, quite the stupid blunder I made. Thanks for picking up on that. With that error, all pins were being set as inputs hence the reason why there was no output. I've rectified that error and it seems to be working a little better. However I still have the issue of premature program termination.

Pin 1 goes low and pin 2 goes hi which is good, however the program terminates immediately after which sucks. I can also make pins 1 and 2 go hi at the same time, but it still terminates right after doing so. I'm currently using the debug board.

CODE:
[PHP]#define HI 1
#define LO 0

void init_PIC16F688(void);

void set_bit(char *port, char bit, char state);
char tell_bit(char *port, char bit);

void main(void) {
     /////////////////////
     // Initialisations //
     /////////////////////
     init_PIC16F688();
     
     /////////////////////
     //  Begin Program  //
     /////////////////////

     set_bit( &PORTC, 1, LO );
     set_bit( &PORTC, 2, HI );

     for(;;) {
          set_bit( &PORTC, 2, ~(tell_bit(&PORTC, 2)) );
          set_bit( &PORTC, 1, ~(tell_bit(&PORTC, 1)) );
          delay_ms(100);
     }
     
     while(1);
     
     return;
}


void set_bit(char *port, char bit, char state) {
     if(state == HI) {
          *port |= (1 << bit);
     }
     else {
          *port &= ~(1 << bit);
     }
     
     return;
}


char tell_bit(char *port, char bit) {
     return (( *port & (1 << bit) ) >> bit);
}


void init_PIC16F688(void) {
     // For port A
     set_bit(&TRISA, 0, HI);
     set_bit(&TRISA, 1, HI);
     set_bit(&TRISA, 2, HI);
     set_bit(&TRISA, 3, HI);
     set_bit(&TRISA, 4, HI);
     set_bit(&TRISA, 5, HI);

     // For port C
     set_bit(&TRISC, 0, HI);
     set_bit(&TRISC, 1, LO);
     set_bit(&TRISC, 2, LO);
     set_bit(&TRISC, 3, HI);
     set_bit(&TRISC, 4, HI);
     set_bit(&TRISC, 5, HI);

     return;
}[/PHP]

As for the environment I'm working in, I'm using "microC for PIC" in Windows Vista. As for the programmer, I have a MICROCHIP PICkit 2 and I am using the PICkit 2 flasher software. I'd like to do my development in Ubuntu, however the tools available don't seem to cooperate with me.

---

### Post by UbuKunubi on 2009-06-15
My advice, after 6 years of commercial PIC programming, is to use assembly language.
This is important if you want the help of the community members in microchip.com.

While microchip are pushing other languages, assembly is the most strongly supported, and is proven to perform better over a translated language, this is because of the different code libraries support some PICs better than others.

Are you also aware that the same model of PIC is available in different packages, and there can be wild differences between the performance. For example a ceramic 12F629 can run at 40MHz, but the plastic packaged version will frequently reset above 10MHz? 

Also, in the code example you provide it is not clear in which bank you are operating in, when using assembly this is immediately obvious:

```


		BANKSEL		OPTION_REG

				 ;76543210

		movlw	b'00000111'

		movwf	OPTION_REG

		BANKSEL	INTCON

		CLRF	INTCON

		BANKSEL	PIR1

		CLRF	PIR1

		BANKSEL	PIR2

		CLRF	PIR2

		BANKSEL	PIE1

		CLRF	PIE1

		BANKSEL	PIE2

		CLRF	PIE2

		BANKSEL	T1CON

		CLRF	T1CON

		CLRWDT

		BANKSEL	T2CON

		CLRF	T2CON

		BANKSEL	SSPCON

		CLRF	SSPCON

		BANKSEL	CCP1CON

		CLRF	CCP1CON

		BANKSEL	RCSTA

		CLRF	RCSTA

		BANKSEL	SSPCON2

		CLRF	SSPCON2

		BANKSEL	CVRCON

		CLRF	CVRCON

		BANKSEL	ADCON0

		CLRF	ADCON0

		BANKSEL	ADCON1

		MOVLW	B'00000110'

		MOVWF	ADCON1

		BANKSEL	CMCON

		MOVLW	B'00000111'

		MOVWF	CMCON

		CLRWDT

		BANKSEL	TRISA

		MOVLW	B'00111111'

		MOVWF	TRISA

		BANKSEL	TRISB

		CLRF	TRISB

		BANKSEL	TRISC

		MOVLW	B'00001100'

		MOVWF	TRISC

		BANKSEL	TRISD

		CLRF	TRISD

		BANKSEL	TRISE

		MOVLW	B'00000001'

		MOVWF	TRISE

		BCF		STATUS,RP0

		BCF		STATUS,RP1

		CLRF	PORTA

		CLRF	PORTB

		CLRF	PORTC

		CLRF	PORTD

		CLRF	PORTE

		CLRWDT

		CLRF	TICK

		CLRF	SECOND

		CLRF	MINUTE

		CLRF	HOUR

		CLRF	DAY

		CLRF	MEX

		CLRF	DELAY

		RETURN

```

If you have any doubts about my advice please feel free to ask around in the microchip forum. 

All the best,
Ubu

---

### Post by leblancmeneses on 2009-06-15
>My advice, after 6 years of commercial PIC programming, is to use assembly language.

you can reuse your code much easier if you stick to c for low end devices/c++ for high end devices.

let the compiler focus on targeting an architecture.   assembly instruction sets differ greatly among architectures.  


another benefit of c language over assembly:
for complex applications i normally use visual studio or gcc+gdb
once you have your program running correctly then transfer to the chip.

this has saved me many hours of searching for a stupid mistake because dumb compilers microchip providers do not find.



> Pin 1 goes low and pin 2 goes hi which is good, however the program terminates 
> immediately after which sucks.

that said ... some compilers are better than others.
[COLOR=#000000][COLOR=#007700]
while(1); is useless at the moment

the transform phase in compiler may not be translating
for( ; ; ) {
to an infinite loop.
[/COLOR][/COLOR] 
wrap in a while(1) {

}

and see if it makes a difference.

also for the moment use your own function delay() which is a for loop which loops 100000 times... later you can try adding the periodic interrupt timer to keep track of time using hardware.

---

