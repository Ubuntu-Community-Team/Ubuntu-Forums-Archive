---
title: "Implementing checksum into program"
date: 2012-02-07
forum: Programming Talk
---

### Post by Eiji Takanaka on 2012-02-07
Hi there, I was just wondering if someone could point me in the right direction to implement a checksum operation in my little bash-script, i've written =), with assistance from kind-folk from ubuntu forums ;). (Although i implemented the logging and time-stamp function myself as they prove useful to cross-reference with time-stamps from other programs =P. I'm gathering cksum would be appropriate and i was thinking of trying to implement it on the code=$ line some time after the 000 denomination. 

Thus far the program is doing what i want it to...incrementing the first 4 digits of the lot, whilst keeping 000 static. The final part will be to calculate and then append the checksum to the end of the 7-digits, keeping the $code variable so that it will output the final 8 digits to the program and logs in question.

Here is my mini-program =P

> #!/bin/bash

for i in {0..9999}; do
        code=$(printf "%04d"000 $i)
        echo $(date +%H:%M:%S)
        echo $(date +%H:%M:%S) >> /home/User/log.txt
        echo 'wpa_cli wps_reg A0:00:00:00:00:00' $code
        echo 'wpa_cli wps_reg A0:00:00:00:00:00' $code >> /home/User/log.txt
        wpa_cli wps_reg 00:00:00:00:00:00 $code
        sleep 9

doneI've experimented with cksum and i'm pretty sure thats what i'll be needing its just where to insert it into the code and why, that i could do with a hand with, if possible =).

Cheers guys/gals =)

---

### Post by r-senior on 2012-02-07
Good job with the logging!

What are you creating the checksum from?

---

### Post by Eiji Takanaka on 2012-02-07
Hi senior, thanks yeah, i implemented the logging/date function after reading up some more on bash-scripting =).

O.k so i'm hoping to generate the checksum from the now 7 digits that are assigned to the $code variable. I added three static 0's after the incremented first 4 digits, i.e the program now progresses as follows...

0001000
0002000
0003000 

and so on and so forth which is awesome because thats exactly what i wanted it to do. 

So basically i now need to use what i believe is called an ean-8 calulator/generator to calculate the 8th digit checksum from the previous 7 digits, which i know are now assigned to $code. 

This section i expected to breeze, although reading up i think it might prove somewhat trickier than i first anticipated, haha oh well, learning as i go i guess

Any thoughts? =)

---

### Post by Eiji Takanaka on 2012-02-07
My first thoughts were to call a program, maybe an ean-8 module piping the $code variable into it, &  returning it with the checkdigit appended. The returned variable being called $code1. Which is then printed & logged.

---

### Post by r-senior on 2012-02-07
Hmm, unless you know better I don't think cksum does the ean-8 check digit. The algorithm appears to be:

> Check Digit Calculation

The EAN-8 check digit is calculated using modulo 10 method. Here outlines the steps to calculate EAN-8 check digit:

    From the right to left, start with odd position, assign the odd/even position to each digit.
    Sum all digits in odd position and multiply the result by 3.
    Sum all digits in even position.
    Sum the results of step 3 and step 4.
    Divide the result of step 4 by 10. The check digit is the number which adds the remainder to 10.


---

### Post by Eiji Takanaka on 2012-02-07
Yeah i was wrong on cksum. Sadly =). Haha i thought it would be as easy as piping into an allready established program but nooooo.... =P.

What i have found is a perl ean-8 module on the cpan site, and a javascript ean-8 calculator, i procured from a website. 

Which would be easiest to implement into my bash-script would you suggest?

Heres the javascript version...obviously the only part of the module i really need is the ean-8 part, it has the algorithm there allready, if i can half-inch it and translate it to bash, is that a feasible work-around? Or is transcribing from java to bash somewhat troublesome would you say?

> //Calculates the check digit for an ISBN number. 
function ISBN(strISBN) 
{ 
    var temp; 
    var ckDigit 
    var number = new String(); 
    var digits = new Array( ); 
    var i = 0; 
 
    number = strISBN; 
     
    while (i < number.length)  {        //This while statement seperates the string 
        temp = number.charAt(i);    //into characters then turns the characters into 
        temp=parseInt(temp);        //integers.  The integers are then put into an array. 
        digits[i] = temp; 
        i++;  } 
 
    //This next line computes a check digit.  If modulo 11 produces a remainder then the remainder is subtracted 
    // from 11, to produce the check digit.  When the result equals 10, it is exchanged the the Roman Numeral X. 
    ckDigit = ( (digits[0] *10) + (digits[1] * 9) + (digits[2] * 8) + (digits[3] * 7) + (digits[4] * 6) + (digits[5] * 5) + (digits[6] * 4) + (digits[7] * 3) + (digits[8] * 2) ) % 11; 
    if (ckDigit != 0)  { 
        ckDigit = 11 - ckDigit;  } 
 
    if (ckDigit == 10)  { 
        ckDigit = "X";  } 
         
    return ckDigit; 
} 
 
//Calculates the check digit for an UCC/EAN-8, UCC/EAN-13 and UCC/EAN-14 number and . 
function EAN(strEAN) 
{ 
    var temp; 
    var ckDigit; 
    var number = new String(); 
    var digits = new Array( ); 
    var i = 0; 
 
    number = strEAN; 
 
    while (i < number.length)  {        //This while statement seperates the string 
        temp = number.charAt(i);    //into characters then turns the characters into 
        temp=parseInt(temp);        //integers.  The integers are then put into an array. 
        digits[i] = temp; 
        i++;  } 
     
    if (i == 12) {    // If i = 13 then calculate a checkdigit for an EAN/UCC-13. 
     
        ckDigit = ( (digits[0] + digits[2] + digits[4] + digits[6] + digits[8] + digits[10] ) + ( (digits[1] + digits[3] + digits[5] + digits[7] + digits[9] + digits[11] ) *3) ) % 10; 
        if (ckDigit != 0)  { 
            ckDigit = 10 - ckDigit;  } 
         
        return ckDigit; } 
     
    if (i == 7) {    // If i = 7 then calculate a checkdigit for an EAN/UCC-8. 
     
        ckDigit = ( ( (digits[0] + digits[2] + digits[4] + digits[6] ) *3) + ( digits[1] + digits[3] + digits[5] ) ) % 10; 
        if (ckDigit != 0)  { 
            ckDigit = 10 - ckDigit;  } 
         
        return ckDigit; } 
 
    if (i == 13) {    // If i = 13 then calculate a checkdigit for an EAN/UCC-14. 
     
        ckDigit = ( ( (digits[0] + digits[2] + digits[4] + digits[6] + digits[8] + digits[10] + digits[12] ) *3) + ( digits[1] + digits[3] + digits[5] + digits[7] + digits[9] + digits[11] ) ) % 10; 
        if (ckDigit != 0)  { 
            ckDigit = 10 - ckDigit;  } 
         
        return ckDigit; } 
} 
 
//Calculates the check digit for a Bookland EAN number. 
//Function receives the ISBN number and "978" is added during the calculation. 
function bl_EAN(strISBN) 
{ 
    var temp; 
    var ckDigit; 
    var number = new String(); 
    var digits = new Array( ); 
    var i = 0; 
 
    number = strISBN; 
 
    while (i < number.length)  {    //This while statement seperates the string 
        temp = number.charAt(i);    //into characters then turns the characters into 
        temp = parseInt(temp);        //integers.  The integers are then put into an array. 
        digits[i] = temp; 
        i++;  } 
     
    //This next line computes a check digit.  If modulo10 produces a remainder then the remainder 
    // is subtracted from 10, to produce the check digit. 
     
    ckDigit = ( (9 + 8 + digits[1] + digits[3] + digits[5] + digits[7] ) + ( (7 + digits[0] + digits[2] + digits[4] + digits[6] + digits[8] ) * 3) ) % 10; 
    if (ckDigit != 0)  { 
        ckDigit = 10 - ckDigit;  } 
         
    temp = "978" + digits[0] + digits[1] + digits[2] + digits[3] + digits[4] + digits[5] + digits[6] + digits[7] + digits[8] + ckDigit; 
    return temp; 
} 
 
//Calculates the check digit for a SSCC number. 
function SSCC(strSSCC) 
{ 
    var temp; 
    var ckDigit; 
    var number = new String(); 
    var digits = new Array( ); 
    var i = 0; 
 
    number = strSSCC; 
 
    while (i <= number.length)  {        //This while statement seperates the string 
        temp = number.charAt(i);    //into characters then turns the characters into 
        temp = parseInt(temp);        //integers.  The integers are then put into an array. 
        digits[i] = temp; 
        i++;  } 
 
    //This next line computes a check digit.  If modulo 10 produces a remainder then the remainder 
    // is subtracted from 10, to produce the check digit. 
    ckDigit = ( ( (digits[0]+digits[2]+digits[4]+digits[6]+digits[8]+digits[10]+digits[12]+digits[14]+digits[16] ) * 3 ) + (digits[1]+digits[3]+digits[5]+digits[7]+digits[9]+digits[11]+digits[13]+digits[15] ) ) % 10; 
    if (ckDigit != 0)  { 
        ckDigit = 10 - ckDigit;  } 
         
    return ckDigit; 
} 
 
//Calculates the check digit for a UPC-A number. 
function UPC(strUPC) 
{ 
    var temp; 
    var ckDigit; 
    var number = new String(); 
    var digits = new Array( ); 
    var i = 0; 
 
    number = strUPC; 
 
    while (i <= number.length)  {        //This while statement seperates the string 
        temp = number.charAt(i);    //into characters then turns the characters into 
        temp = parseInt(temp);        //integers.  The integers are then put into an array. 
        digits[i] = temp; 
        i++;  } 
 
    //This next line computes a check digit.  If modulo 10 produces a remainder then the remainder 
    // is subtracted from 10, to produce the check digit. 
    ckDigit = ( ( (digits[0]+digits[2]+digits[4]+digits[6]+digits[8]+digits[10]) * 3 ) + (digits[1]+digits[3]+digits[5]+digits[7]+digits[9] ) ) % 10; 
    if (ckDigit != 0)  { 
        ckDigit = 10 - ckDigit;  } 
 
    return ckDigit; 
} 
 
//Calculates the check digit for a Bill of Lading number. 
function BOL(strBOL) 
{ 
    var temp; 
    var ckDigit; 
    var number = new String(); 
    var digits = new Array( ); 
    var i = 0; 
 
    number = strBOL; 
 
    while (i < number.length)  {        //This while statement seperates the string 
        temp = number.charAt(i);    //into characters then turns the characters into 
        temp=parseInt(temp);        //integers.  The integers are then put into an array. 
        digits[i] = temp; 
        i++;  } 
 
alert(i); 
 
        ckDigit = ( (digits[0] + digits[2] + digits[4] + digits[6] + digits[8] + digits[10] + digits[12] + digits[14] ) + ( (digits[1] + digits[3] + digits[5] + digits[7] + digits[9] + digits[11] + digits[13] + digits[15] ) *3) ) % 10; 
        if (ckDigit != 0)  { 
            ckDigit = 10 - ckDigit;  } 
         
        return ckDigit; 
}

---

### Post by r-senior on 2012-02-07
I'm going to bed, but have a go with this:

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char **argv)
{
        int i, odd_sum = 0, even_sum = 0, sum, check_digit;
        char *base;

        if (argc != 2) {
                fprintf(stderr, "Error: Wrong number of arguments\n");
                exit(EXIT_FAILURE);
        }

        base = argv[1];

        if (strlen(base) != 7) {
                fprintf(stderr, "Error: Argument is not 7 characters\n");
                exit(EXIT_FAILURE);
        }

        for (i = 0; i < 7; i += 2) {
                // Odd digits
                odd_sum += base[i] - '0';
        }

        for (i = 1; i < 7; i += 2) {
                // Even digits
                even_sum += base[i] - '0';
        }

        sum = odd_sum * 3 + even_sum;
        check_digit = (10 - (sum % 10)) % 10;
        printf("%s%d\n", base, check_digit);

        return(EXIT_SUCCESS);
}
```

It's C, so you'll need gcc installed. Paste that into a file called ean8.c and compile it like this:

```
$ make ean8
```

Or if that doesn't work:

```
$ gcc -o ean8 ean8.c
```

I checked a few numbers against a web-based EAN-8 check digit thingy and it seemed OK, but I have just written it in five minutes. Once you have the ean8 executable, it needs to be in your path - I'd suggest ~/bin.

Then you can just do something like:

```
answer=$(ean8 $code)
```

EDIT: When I see that amount of code, I start to think I did something wrong. I think it's because I only deal with 7 digits. ;)

---

### Post by Eiji Takanaka on 2012-02-07
cool i'll give it a scout, 

thanks for the suggestions man!

---

### Post by Eiji Takanaka on 2012-02-07
Haha aye, that javascript is for a whole host of algorithms.

O.k i've got everything set, exectuables in /bin....

So now to integrate.....

I'll let ya know how my experiments unfold :)

---

### Post by Eiji Takanaka on 2012-02-07
> #!/bin/bash

        for i in {0..9999}; do
        code=$(printf "%04d"000 $i)
        ans=$(ean8 $code) 
        echo $(date +%H:%M:%S)
        echo $(date +%H:%M:%S) >> /home/User/log.txt
        echo 'wpa_cli wps_reg 00:00:00:00:00:00' $ans
        echo 'wpa_cli wps_reg 00:00:00:00:00:00' $ans >> /home/User/log.txt
        wpa_cli wps_reg 00:00:00:00:00:00 $ans
        sleep 9

done

& output..

01:47:25
wpa_cli wps_reg 00:00:00:00:00:00  64010007
Selected interface 'wlan0'
OK

This seems to work for me, i'll confirm the ean-8 values with the online calculator, but it seems to of done the trick! 

Fascinating, so i've now called 2 programs from within this simple bash-script. And achieved the desired results.

Thanks a lot dude! 

=)

---

### Post by Eiji Takanaka on 2012-02-07
One final note if i may, 

Am i right in thinking if i redirect the output of the actual wpa_cli wps_reg command to >> /dev/null, it will tidy up the un-necessary 

"selected interface 'wlan0'
" O.K"

lines in the program?

Nevermind i can figure this out easily....whether stdout or stderr needs to be redirected, its not a biggy.

Thread solved,

Kudos to the senior citizen! ;)

---

### Post by r-senior on 2012-02-08
Good! Well done, you've learned some bash scripting along the way.

You can redirect the output of the command to /dev/null or to a log file. If it's well-behaved and sends output to stdout and errors to stderr, that should work OK.

The only other thing was that I think you put the ean8 executable in /bin. I meant ~/bin, which is /home/<your_username_here>/bin. Not a great problem but if you reinstall Ubuntu you might lose it, so keep the ean8.c file somewhere if you modify it.

---

### Post by Eiji Takanaka on 2012-02-09
I don't have a /home/bin on my system, so i'll just leave it in /bin for now. 

Thanks once again for your assistance and for the ean-module you rustled up.=)

It's a useful little program!

---

