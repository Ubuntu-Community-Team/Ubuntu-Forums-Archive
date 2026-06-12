---
title: "What does this mean / do? (C++ code)"
date: 2009-03-10
forum: Programming Talk
---

### Post by Krupski on 2009-03-10
Hi all,

I'm working with someone else's small C++ program that converts raw binary input from STDIN into Intel HEX format (used typically for loading data into EPROM programmers).

There are two lines that for the life of me I can't figure out or understand what they do.

Please help me out here... the "strange" lines are highlighted in red:

```

#include <stdio.h>
#include <unistd.h>

// original author data:
// from : Jean Marc Lacroix <jeanmarc.lacroix@free.fr>
// date : 06/12/1997.


// Intel Hex format specifications

// The 8-bit Intel Hex File Format is a printable ASCII format
// consisting of one or more data records followed by an end of
// file record. Each record consists of one line of information.
// Data records may appear in any order. Address and data values
// are represented as 2 or 4 hexadecimal digit values.

// Record Format
// [:][06][0100][00][01][02][03][04][05][06][E4]
//  s  ct  addr type  1   2   3   4   5   6  ck

// : = start code (1)
// 06 = Byte Count (data only) (2)
// 0100 = Load address (4)
// 0 = Record type (0=data, 1=eof) (1)
// 01,02,03...etc = actual data (2 each)
// E4 = checksum (1)

// program starts here

typedef unsigned char t_u8;
typedef unsigned short t_u16;

// the choice for the total length (16) of a line, but the specification
// can support another value up to 255

#define LL_MAX_LINE 16

typedef struct
{
	t_u8 intel_lg_data;
	t_u16 intel_adr;
	t_u8 intel_type;
	t_u8 intel_data [LL_MAX_LINE];
	t_u8 intel_lrc;
}	t_one_line;

#define INTEL_DATA_TYPE 0
#define EXIT_OK 0

int main (void)
{
	[COLOR="Red"]**t_one_line line;**[/COLOR]

	// init for the address, please note that it is assumed that the program begin at 0

	line.intel_adr = 0;
	line.intel_type = INTEL_DATA_TYPE;

	// read the data on the standard input

	while ((line.intel_lg_data = read (0, &line.intel_data [0] ,LL_MAX_LINE )) > 0) {

		[COLOR="Red"]**t_u8 i;**[/COLOR]

		// and now for this line, calculate the lrc.

		line.intel_lrc  = line.intel_lg_data;
		line.intel_lrc += ((line.intel_adr >> 8) & 0xff);
		line.intel_lrc += (line.intel_adr &0xff);
		line.intel_lrc += line.intel_type;

		// the structure is ready, print it to stdout in the
		// right format

		printf (":%02X%04X%02X", line.intel_lg_data, line.intel_adr, line.intel_type);

		// edit all the data read

		for (i=0; i<line.intel_lg_data; i++) {
			printf ("%02X", (line.intel_data [i] & 0xff));
			// add to the lrc the data print
			line.intel_lrc +=line.intel_data [i];
		}

		// edit the value of the lrc and new line for the next

		printf ("%02X\n", (0x100 - line.intel_lrc) & 0xff);

		// prepare the new address for the next line

		line.intel_adr+=line.intel_lg_data;
	}

	// print the last line with a length of 0 data, so that the lrc is easy to
	// calculate (ff+01 = 0)

	printf(":00000001FF\n"); // canned eof
	return EXIT_OK;
}

```


Thanks!

-- Roger

---

### Post by stevescripts on 2009-03-10
The first red line, declares a variable "line" of type "t_one_line", the second a variable "i" of type "t_u8 - those typedefs are declared before main - 

See:  [http://publications.gbdirect.co.uk/c_book/chapter8/typedef.html](http://publications.gbdirect.co.uk/c_book/chapter8/typedef.html) 

for a pretty good (IMO) explanation of typdefs.

Does this helps a bit?

Steve
(who does very little compiled language programming these days...)

---

### Post by nvteighen on 2009-03-10
Those are declarations. The first one creates a variable of type t_one_line, which is a typedef'ed anonymous struct. The second one creates a variable of type t_u8, which in that code is a typedef for unsigned char.

typedef creates new type names you can use as the rest of native ones. It's very common to use it for replacing "unsigned" types or structs, because those are longer to write (**unsigned char a;** or **struct MYSTRUCT object;**).

---

### Post by Krupski on 2009-03-10
> **stevescripts said:**
> The first red line, declares a variable "line" of type "t_one_line", the second a variable "i" of type "t_u8 - those typedefs are declared before main - 

See:  [http://publications.gbdirect.co.uk/c_book/chapter8/typedef.html](http://publications.gbdirect.co.uk/c_book/chapter8/typedef.html) 

for a pretty good (IMO) explanation of typdefs.

Does this helps a bit?

Steve
(who does very little compiled language programming these days...)

I think I understand what you mean... if "line" were an int, it would be declared "int line;".

But I don't get what data "type" "t_one_line" is. Is it declaring that "line" is the entire structure and "line.xxx" are individual parts of the structure?

Thanks!

-- Roger

(edit to add):

Wouldn't this be the same thing? :

```

typedef struct
{
	t_u8 intel_lg_data;
	t_u16 intel_adr;
	t_u8 intel_type;
	t_u8 intel_data [LL_MAX_LINE];
	t_u8 intel_lrc;
}	[COLOR="Red"]**line;**[/COLOR]

```

...and then access elements like this:

```

line.intel_lg_data = 0;

```

???

Thanks again!

---

### Post by dwhitney67 on 2009-03-10
Btw, the code you posted is written in C, not C++.

In C++, there really is no need to typedef a structure.  In C it was done because some programmers were lazy and did not want to type the keyword struct when referring to a structure.  So when a typedef is used in conjunction with a struct declaration, it is in essence used as a means to create an alias for the structure name.

In C++, when one declares a structure or a class, the keywords struct and class are not necessary when declaring an object.

P.S.  typedef can also be used to define an alias for any data type, not just structures.

------------

EDIT:  I dug through some old code that I had saved.  I cannot recall who was the original author of the following code, but it appears less complex than the one you posted.  And it is in C++.  However, I do not know if it works for creating "Intel" hex-style values.  But it works on my Intel processor.
```

#include <iostream>
#include <string>
#include <bitset>
#include <sstream>


void BinToHex(const std::string& binaryStr, std::ostringstream& hexStr);

int main()
{
  std::string        binaryStr("11101111011111000011101010101101");
  std::ostringstream hexStr;

  BinToHex(binaryStr, hexStr);

  std::cout << hexStr.str()<< std::endl;
}

void BinToHex(const std::string& binaryStr, std::ostringstream& hexStr)
{
  const size_t SETSIZE = 4;
  size_t       idx  = 0;
  size_t       size = binaryStr.size();

  hexStr << std::hex;

  for (size_t i = 0; i < (size/SETSIZE); ++i, idx += SETSIZE)
  {
    std::bitset<SETSIZE> set(binaryStr.substr(idx, idx + SETSIZE));
    hexStr << set.to_ulong();
  }

  hexStr << std::dec << std::endl;
}

```

---

### Post by stevescripts on 2009-03-11
> **Krupski said:**
> I think I understand what you mean... if "line" were an int, it would be declared "int line;".

But I don't get what data "type" "t_one_line" is. Is it declaring that "line" is the entire structure and "line.xxx" are individual parts of the structure?
...


That is basically correct.

While you *could* name your structure line, doing something to denote that line is a defined type in its name is pretty standard programming style.  It let's you know (elsewhere in the code) that you are dealing with a programmer defined type, rather than a standard type.  For example, if I had written it, I would more than likely have called the structure line_t.

As dwhitney67 posted, this is C code, not C++.  Read his post carefully - he is an accomplished compiled language coder, while the rust on my C/C++ coding skills is quite thick anymore.

Steve

---

