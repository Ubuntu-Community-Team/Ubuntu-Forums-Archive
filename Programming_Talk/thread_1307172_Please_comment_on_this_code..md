---
title: "Please comment on this code."
date: 2009-10-30
forum: Programming Talk
---

### Post by Krupski on 2009-10-30
Hi all,

I would appreciate if you could comment / critique the following simple program.

The main reason I am asking is that I have a "gut feeling" that I could be doing what I'm doing is a better manner.

I'm not a "programmer" and I only write little utilities, but I do wish to learn proper form and any tricks that there are to learn.

Please feel free to say anything you wish. If the code outright stinks, please say so!  ;)

Here it is:

```

// motorola s-record to binary converter

#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <ctype.h>

#undef BUFSIZ
#define BUFSIZ 1024

int readln(FILE *, char *);

int main(void)
{
	char buffer[BUFSIZ]; // line input buffer
	char rectype[2]; // record type (ascii S0, S1 or S9)
	int bytes; // number of bytes in record (including the checksum)
	int addrhi; // load address hi byte
	int addrlo; // load address lo byte
	int s_data; // binary data byte
	int n; // counter
	int x, y; // temporary hi and lo nybbles
	int checksum; // s-record checksum accumulator


	while(!feof(stdin)) {

		readln(stdin, buffer); // read one line of text

		if(strlen(buffer) >= 12) { // minimum length of s record line

			// get recordtype (S1), number of bytes, load address hi, load address lo
			sscanf(buffer, "%2s%02x%02x%02x", rectype, &bytes, &addrhi, &addrlo);

			// only convert S1 (data) records
			if(strcmp(rectype, "S1") == 0) {

				// calculate checksum
				checksum = (bytes + addrhi + addrlo + 1);

				for(n = 0; n < (bytes - 2); n++) {
					// get ascii values
					x = buffer[8 + (n * 2) + 0] - '0';
					y = buffer[8 + (n * 2) + 1] - '0';

					// correct hex if A-F
					if(x > 9) { x -= 7; }
					if(y > 9) { y -= 7; }

					// shift hi 4 bits up
					x <<= 4;

					// complete the data
					s_data = x + y;

					// add up checksum
					checksum += s_data;

					// output all but the checksum
					if(n < (bytes - 3)) {
						fputc(s_data, stdout);
					}
				}
			}

			// low order byte should be zero if checksum is good
			if((checksum & 0xFF) != 0) {
				fprintf(stderr, "Checksum error: %s\n", buffer);
				break;
			}
		}
	}
	exit(0);
}

int readln(FILE * fp, char * str)
{
	char buf[BUFSIZ];
	int len, n;

	buf[0] = 0;
	fgets(buf, BUFSIZ, fp);

	// strip any leading spaces
	sscanf(buf, "%s", buf);

	len = strlen(buf);

	// strip any trailing cr, lf or other
	while(len >= 0) {
		if(buf[len] < 0x21) { buf[len] = 0; len--; }
		else { break; }
	}

	// null terminat string
	len++;
	buf[len] = 0;

	// uppercase buffer
	for(n = 0; n < (int)strlen(buf); n++) {
		buf[n] = toupper(buf[n]);
	}

	// copy string to output
	strcpy(str, buf);
	return len;
}

```

...and this is the type of data that the program is supposed to convert to raw binary:


```

S113E070005A2BDBD7A3BDE3E3BDE3E0BDE3E3201C
S113E080D1810D260A5D2702A700BDE3F4200E5CB2
S113E090C12824BED7A3A700BDE3A120B5CC0000AE
S113E0A0DD6BCE007BDFB2BDE2C2BDE2ADCE00A42B
S113E0B03ABDE10EA700810D2716BDE2CF2711BDA1
S113E0C0E2B45CC10823E3CEE55ABDE3FC7EE04341
S113E0D0D779CEE447DFB4DEB418CE00A4E6002A34

```


...and here's what each piece means:

```

S1 - indicates a "data record"
13 - hex 13 = decimal 19 (byte count)
E070 - load address of data
00 5A 2B DB D7 A3 BD E3 E3 BD E3 E0 BD E3 E3 20 - the actual data
1C - the checksum

```


Thanks in advance!

-- Roger

---

### Post by StunnerAlpha on 2009-10-31
Ey, just wanted to point out, its good practice and style to comment at closing brackets that enclose good chunks of code. Like so:
```

                         if(strcmp(rectype, "S1") == 0) {

				// calculate checksum
				checksum = (bytes + addrhi + addrlo + 1);

				for(n = 0; n < (bytes - 2); n++) {
					// get ascii values
					x = buffer[8 + (n * 2) + 0] - '0';
					y = buffer[8 + (n * 2) + 1] - '0';

					// correct hex if A-F
					if(x > 9) { x -= 7; }
					if(y > 9) { y -= 7; }

					// shift hi 4 bits up
					x <<= 4;

					// complete the data
					s_data = x + y;

					// add up checksum
					checksum += s_data;

					// output all but the checksum
					if(n < (bytes - 3)) {
						fputc(s_data, stdout);
					}
				}//for
			}//if


```

It makes reading the code loads easier, especially if the chunk of code is too large to fit on-screen at once.

---

### Post by dwhitney67 on 2009-10-31
Your app has a bug; your 'rectype' has two characters, and indeed you declared said variable as such.  You forgot to add the extra byte for retaining the null-termination character.  Thus declare 'rectype' as such:
```

char rectype[3]; // record type (ascii S0, S1 or S9)

```

You could do a better job with readln() if you were to add on extra parameter so that you know the size of the 'str' being passed in.  As it is, you are using a globally defined value of BUFSIZ and assuming the 'str' is of that size.

Lastly, and albeit not too important, I prefer to use the ISO 1999 C standards when I write C code.  This allows me to declare a variable pretty much anywhere I want, thus permitting me to declare and initialize the variable at the same time.  For example this code could be like:
```

...
for(int n = 0; n < (bytes - 2); n++) {
	// get ascii values
	int x = buffer[8 + (n * 2) + 0] - '0';
	int y = buffer[8 + (n * 2) + 1] - '0';
...

```
If you care to use this standard, then use the -std=gnu99 or -std=c99 options when you compile.  By default, GCC uses the ISO 1989 C Standards.

---

### Post by Krupski on 2009-10-31
> **StunnerAlpha said:**
> Ey, just wanted to point out, its good practice and style to comment at closing brackets that enclose good chunks of code. Like so:
............
It makes reading the code loads easier, especially if the chunk of code is too large to fit on-screen at once.

EXCELLENT idea! I have indeed run into errors where I forgot a closing brace... that would help a lot.

Thanks!

-- Roger

---

### Post by Krupski on 2009-10-31
> **dwhitney67 said:**
> (1) Your app has a bug; your 'rectype' has two characters, and indeed you declared said variable as such.  You forgot to add the extra byte for retaining the null-termination character.

(2) You could do a better job with readln() if you were to add on extra parameter so that you know the size of the 'str' being passed in.  As it is, you are using a globally defined value of BUFSIZ and assuming the 'str' is of that size.


(1) Yup you're right. I thought that the sscanf() returned the number of characters I told it to (two), but I forgot about the end of line!

(2) I assumed the readline (specifically the fgets part) was OK because I told it to read "BUFSIZ" max characters and if the incoming line were longer, the rest would just be discarded. Is this true, or would the buffer overflow and possibly segfault?

Lastly, concerning declaring the variables at the time of usage... I usually do that. I left them as a "list" so I could "see" them better (if that makes sense).

Thanks for the comments!

-- Roger

---

### Post by dwhitney67 on 2009-10-31
> **Krupski said:**
> ...

(2) I assumed the readline (specifically the fgets part) was OK because I told it to read "BUFSIZ" max characters and if the incoming line were longer, the rest would just be discarded. Is this true, or would the buffer overflow and possibly segfault?

...
You're usage of fgets() is ok.  When I suggested you modify readln(), it was for the purpose of making it multi-purposeful.  For the current application, this suggestion is moot.  However, as a "best practices" rule, you should consider developing code that can be reusable within other applications.

---

### Post by MadCow108 on 2009-10-31
you should always use strn... (strncpy, strncmp,...) or strl... family functions instead of normal str... functions to ensure that nothing overflows their buffer.
with careful coding the unsafe functions are ok, but nobody is perfect and may miss a boundary check or a null termination and the result is mostly an exploitable security hole.
use of the save n variants avoids this in a very easy way (although there may still be bugs because of missing handling of truncated input)

also you should generally check the input before using it.
you use part of the input for array indexing without boundary checks:
x = buffer[8 + (n * 2) + 0] - '0';
here a user could provide malformed input and crash your program (or worse exploit the buffer overrun to inject own code).

if the above points are real problems is of course dependant on the purpose of your application.

another minor thing:
remember str(n)len has a linear complexity. you should save the length when once computed and reuse it.
e.g. save the return value of readln instead of calling another strlen to check if its >= 12
but this is irrelevant if the cstrings are short or the code is not performance critical

---

### Post by johnl on 2009-10-31
> **MadCow108 said:**
> you should always use strn... (strncpy, strncmp,...) or strl... family functions instead of normal str... functions to ensure that nothing overflows their buffer.
with careful coding the unsafe functions are ok, but nobody is perfect and may miss a boundary check or a null termination and the result is mostly an exploitable security hole.
use of the save n variants avoids this in a very easy way (although there may still be bugs because of missing handling of truncated input)


Just as a side note it should be mentioned that 'strncpy' can still be dangerous -- if the buffer is not large enough, strncpy will not null-terminate the data it writes into the buffer.  This can cause problems when reading or copying this string later.

AFAIK none of the other "n" functions (snprintf, etc) have this particular problem.

---

### Post by lisati on 2009-10-31
+1 for the other comments: taking care with buffer sizes is always a good idea. 

The thing I spotted was the #undef, not sure if this is always necessary. The only "precautionary workaround" I could think of would probably bloat the souce slightly.

---

