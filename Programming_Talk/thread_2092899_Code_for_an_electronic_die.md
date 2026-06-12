---
title: "Code for an electronic die"
date: 2012-12-09
forum: Programming Talk
---

### Post by ahsansag93 on 2012-12-09
i am a student of engineering.
i want to make an electronic dice ..which will consist of 6 leds.
i am trying to make its code in compiler but still i am getting the same output means that i am not getting my numbers generate again again..
 here is my code .plz help me..:(

#include<16f877a.h>
#include <stdlib.h>
#include <stdlibm.h>
#define RAND_MAX 2


void main() {

setup_adc_ports(NO_ANALOGS);
   set_tris_b (0b00000000);
  
   int i;
    srand(i);
   i=rand()%100;
  
   {
  if (1) 
  i=1;
  output_b(0b00000001);
    
}
{
if (2) 
  i=2;
  output_b(0b00000010);
 
{

if (3) 
  i=3;
  output_b(0b00000100);
}
 
 {
 if (4) 
  i=4;
  output_b(0b00001000);
  
 }
 {
 if (5) 
  i=5;
  output_b(0b00010000);
 }
 {
 if (6)
 if (2) 
  i=6;
  output_b(0b00100000);
 }
}
}

---

### Post by MG&amp;TL on 2012-12-09
I'm not familiar with the engineering library you're using to (presumably) write to LEDs. 

However, have you run your code on a PC to check you're getting random numbers? If you have, then you've got a problem with your LED code.

Also, there's some fairly dodgy code in here, I'm not sure what you're even trying to do, but:

```
if (1) 
```

will always be true. As will any other number but 0. 

As for your braces...are you sure that's where you meant to put them?

---

### Post by Some Penguin on 2012-12-09
Aside from the nonsensical code pointed to by the above poster, which is presumably a bad attempt at a switch statement...

```

int i;
srand(i);

```

Using an uninitialized variable to initialize the PRNG?  That's some bad practice, right there.  Turn on your compiler's warnings and listen to them.

---

### Post by Vaphell on 2012-12-09
cant you use bit shifting to produce proper values instead of typing them all?
looks like **1<<(i-1)** is what you want.

---

### Post by tgalati4 on 2012-12-09
apt-cache search dice

brings up:

dicelab - evaluate the statistical distribution of dice rolls

You might want to look at the source code to get some ideas.

---

