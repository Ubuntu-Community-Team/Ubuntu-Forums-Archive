---
title: "problem with dividing"
date: 2008-10-19
forum: Programming Talk
---

### Post by ggankhuy on 2008-10-19
i am using bcc to produce o file but 
compiler complains there is an unidentified symbol idiv_ if I use the / to divide. 
Can someone what the problem is?

---

### Post by cabalas on 2008-10-19
Do you have any code we can look at to try and find a problem with? at the moment there isn't enough information to help.

---

### Post by ggankhuy on 2008-10-19
SURE. Here is the C function I am creating, to display an integer.

arg num is the number that is needed to be displayed. 
Down below: quotient = num / 10; line brings in error I was mentioning about. Actually I found out that it is the ld86 linker that generates error message: undefined symbol: idiv_ error message. 
I tried to use % but it will also generate similar message. 

I had to use ld86 rather than other linker because I am mixing C with asm code. Thanks!

int	printi(num) int num;
{
	#define CONFIG_PRINTI_BCD_DIGITS 16 // number of digits in char string.
	int quotient, remainder, i;
	char bcd[CONFIG_PRINTI_BCD_DIGITS];	

        /*Fill with zeros first*/

	for(i = 0; i < CONFIG_PRINTI_BCD_DIGITS; i++)
		bcd[i] = 0x30;

	bcd[CONFIG_PRINTI_BCD_DIGITS-1] = 0; /* put terminating char. */

	i = 0;

        /*divide and copy remainder to the char string backward.*/

	do
	{	
		quotient = num / 10;
		remainder = num - quotient * 10;
		num = quotient;		

		putc(remainder+0x0030);
		bcd[CONFIG_PRINTI_BCD_DIGITS-2-i] = remainder;
		i++;
	} while(quotient != 0 || i < CONFIG_PRINTI_BCD_DIGITS-2);

	prints("\nFinal: ");
	for (i = CONFIG_PRINTI_BCD_DIGITS-2; i > 0; i--)	
		putc(bcd[i]+0x0030);
	
}

---

### Post by loboc on 2008-10-20
did you include the math and iostream headers

---

### Post by ggankhuy on 2008-10-20
that is another problem. I can't find any standard C libraries anywhere in system. 
I did install build-essential package. 
But still nothing there are some linux headers. but no stdio.h, stdlib.h math.h etc. BTW, I am not using C++ so no iostream.

---

### Post by WW on 2008-10-20
What is bcc?  As far as I can tell, build-essential does not provide this command.
*EDIT:* Never mind, I found it: [http://packages.ubuntu.com/hardy/bcc](http://packages.ubuntu.com/hardy/bcc).

I've never used it, so this is just a guess, but I suspect that to use bcc, you will have to install [elks-libc](http://packages.ubuntu.com/hardy/elks-libc).  This appears to contain the appropriate libraries and header files for bcc.


If you have build-essential installed, the C headers should be in the directory /usr/include, but these won't help with bcc.

---

### Post by ggankhuy on 2008-10-23
hey last poster thanks maan, that is exactly the right one. i used synaptic to install the one.
But even I include the math.h it still throws the idiv_ undefined error.

---

