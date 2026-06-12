---
title: "Parallel Port"
date: 2012-05-18
forum: Programming Talk
---

### Post by wkellen on 2012-05-18
I am working on parallel port interfacing. I downloaded parapin. I wrote a program and compiled. Everything ran as I expected, but my pins are not changing state. I added the "set_pin" and "clear_pin" lines to try to force them to set the way I wanted. They show all "high" except for pins 2-9. It keeps playing the mp3 over and over because it shows those pins as high. I was going to apply 5v DC to these pins to make the mp3 file play. Without the 5v it still shows as high. Any ideas? 

```


#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

#include "parapin.h"

#define doorbellf 11
#define doorbellb 12
#define doorsensorf 13
#define doorsensorb 14
#define windowloop 15

#define siren 1
#define light 2



int main()
{
  int i;

  if (pin_init_user(LPT1) < 0)
    exit(0);

  pin_input_mode(LP_PIN[doorsensorb]);
  pin_output_mode(LP_DATA_PINS);
  pin_output_mode(LP_PIN[siren]);
  clear_pin(LP_PIN01 | LP_PIN02 | LP_PIN03 | LP_PIN04 | LP_PIN05 | LP_PIN06 | LP_PIN07 | LP_PIN08 | LP_PIN09 | LP_PIN10 | LP_PIN11 | LP_PIN12);
  set_pin(LP_PIN13 | LP_PIN14 | LP_PIN15);
    
  printf("\nstarting\n");
  for(;;){

int result = pin_is_set (LP_PIN[doorbellf] | LP_PIN[doorbellb] | LP_PIN[doorsensorf] | LP_PIN[doorsensorb] | LP_PIN[windowloop]);

if (result & LP_PIN[doorbellf]){
    printf("Someone is at the front door!\n");
    system("sudo mplayer /usr/share/audio/doorbell.mp3");
}

if (result & LP_PIN[doorbellb]){
    printf("Someone is at the back door!\n");
    system("sudo mplayer /usr/share/audio/doorbell.mp3");
}

if (!result & LP_PIN[doorsensorf]){
    printf("The front door is open!\n");
}

if (!result & LP_PIN[doorsensorb]){
    printf("The back door is open!\n");
}

if (!result & LP_PIN[windowloop]){
    printf("There is a window open!\n");
}

system("sleep 1");

}
return 0;
}


```

---

### Post by pbrane on 2012-05-19
Depending on how many total inputs you need, you should consider only using the data pins. Also it might be worth finding out what kind of chip your LPT port is using and make sure the pins are bidirectional. Any printer|port drivers you have loaded may be affecting your readings. If your BIOS or kernel driver has set the port mode to SPP the data pins may not be bidirectional. I know from my own experience with parallel ports programming that some pins are inverted, I assume parapin is taking that into account?

Also your doorsensorb pin is an input only pin, no need to try to change its mode.

And you are running your program as root, correct?

---

### Post by wkellen on 2012-05-19
> **pbrane said:**
> Depending on how many total inputs you need, you should consider only using the data pins. Also it might be worth finding out what kind of chip your LPT port is using and make sure the pins are bidirectional. Any printer|port drivers you have loaded may be affecting your readings. If your BIOS or kernel driver has set the port mode to SPP the data pins may not be bidirectional. I know from my own experience with parallel ports programming that some pins are inverted, I assume parapin is taking that into account?

Also your doorsensorb pin is an input only pin, no need to try to change its mode.

And you are running your program as root, correct?

According to the documentation I was following from parapin, I can't use just the data pins, because they can only be set as input or output as a group. I can't set them individually. As the program evolves I will need to have output pins also.

I was suspecting the port chip also. According to the terminal, it is in ECP mode. Not sure about the drivers. I'll look into that. Maybe parapin has a driver included that I need to install to be able to take control of the port.

I didn't know about the inverted pins.

"doorsensorb" is set as pin 14. According to the documentation from parapin, that is an in/out pin. 1, 2-9, 14, 16, and 17 can be set to input or output. 2-9 are "ganged" and can only be mode set as a group. 10, 11, 12, 13, and 15 are input only pins. Like I say, this is according to the documentation and could be wrong. 

Yes I am running it as root. If I dont, it gives me an I/O error.

Thanks for the help.

---

### Post by pbrane on 2012-05-19
> **wkellen said:**
> According to the documentation I was following from parapin, I can't use just the data pins, because they can only be set as input or output as a group. I can't set them individually. As the program evolves I will need to have output pins also.

I was suspecting the port chip also. According to the terminal, it is in ECP mode. Not sure about the drivers. I'll look into that. Maybe parapin has a driver included that I need to install to be able to take control of the port.

I didn't know about the inverted pins.

"doorsensorb" is set as pin 14. According to the documentation from parapin, that is an in/out pin. 1, 2-9, 14, 16, and 17 can be set to input or output. 2-9 are "ganged" and can only be mode set as a group. 10, 11, 12, 13, and 15 are input only pins. Like I say, this is according to the documentation and could be wrong. 

Yes I am running it as root. If I dont, it gives me an I/O error.

Thanks for the help.

Yes the data register (pins 2 - 9) can only be in output mode (or input if bidirectional) as a group. There are three registers in the parallel port, data, control and status. You can find documentation and this on the web.

Since you are using the parapin software this shouldn't matter, I would think it would just work.

---

