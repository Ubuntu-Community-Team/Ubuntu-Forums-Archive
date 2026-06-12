---
title: "math.h invisible?"
date: 2006-02-24
forum: Programming Talk
---

### Post by jofre on 2006-02-24
Ok lads, this is my first C program. Should be straight forward but gcc is complaining that " undefined reference to `pow' ", and yes I have " #include <math.h> " at the start.

Any ideas why? 

Thanks a million, Jofre


Full code:
#include <stdio.h>
#include <math.h>

/* Declaring constants */
const double plank =  6.6261e-34 ; /* Planck's constant [J*s] */
const double c = 2.9979e8 ; /* speed of light [m/s] */

/* Declaring variables */
double density, intensity, wavelenght ;

int main(){
	density = ( intensity * pow(wavelenght,4) ) / ( plank * pow(c,2) ) ;

	printf("the density is %f", density) ;
}

Full answer form gcc:
$ gcc -g -Wall -o photon_density photon_density.c
photon_density.c: In function ‘main’:
photon_density.c:15: warning: control reaches end of non-void function
/tmp/ccyo0tCe.o: In function `main':
/c_code/photon_density.c:12: undefined reference to `pow'
collect2: ld returned 1 exit status

---

### Post by cstudent on 2006-02-24
You need to add the -lm (that's LM) switch when you compile to link the math.h library.

btw, you have a typo in the word wavelength. :)

---

### Post by abhaysahai on 2006-02-24
when in doubt use man
"man pow" 
 Link with -lm.

gcc -g -Wall -o photon_density photon_density.c **-lm**

Enjoy. 

Abhay

---

### Post by jofre on 2006-02-24
Thanks a million!!!

by the way, why in hell I did not found that in any of the C books I have in the office!!! (well just two, but still...)

Thanks again, Jofre.

---

### Post by Lux Perpetua on 2006-02-26
It's actually a compiler-specific issue. Some compilers don't need to be told to link the math library, but gcc does.

---

### Post by linjava on 2007-12-25
I know this is an old topic, but for those that have eclipse go to the particular project you're working on's properties by right clicking the project name in the project explorer to your left. Under GCC Linker go to the library section and simply add m (it will add the -l part so your m will turn into -lm). You should see in the build output the '-lm' at the end and you're good to go. BTW, I'm running kubuntu gutsy and using the eclipse cdt plugin with gcc.

---

### Post by virusmagic on 2008-10-10
Excuse me. I am new in both Ubuntu and Eclipse. Could you explain it a little more please?

There is no choice like GCC Linker. If you could give a screenshot I would be grateful.

THankz.

---

### Post by LaRoza on 2008-10-10
> **virusmagic said:**
> Excuse me. I am new in both Ubuntu and Eclipse. Could you explain it a little more please?

There is no choice like GCC Linker. If you could give a screenshot I would be grateful.

THankz.
Please start your own thread.

There are no screenshots needed for terminal commands, a copy and paste works just as well ;)

---

