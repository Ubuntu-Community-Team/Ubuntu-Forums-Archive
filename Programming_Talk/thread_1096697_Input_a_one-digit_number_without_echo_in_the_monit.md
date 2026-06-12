---
title: "Input a one-digit number without echo in the monitor(programming C)"
date: 2009-03-15
forum: Programming Talk
---

### Post by eiffenheart on 2009-03-15
I'm figuring out how to make the user input a single digit number without making an echo to the monitor. Like, make the input "invisible".

So far, I only know getch() or getchar()
but it isn't compatible with numbers.

I've tried googling it, but to no avail.

Any help is greatly appreciated.

...This is for my project/additional points for a subject of mine. ;)

---

### Post by dwhitney67 on 2009-03-15
The Ubuntu Programming Talk search engine must really suck or they are just not being used, because this same question comes up over and over again.  The two suggestions usually given are to either employ the use of ncurses or alternatively to use the following:
```

#include <stdio.h>
#include <termios.h>
#include <unistd.h>
#include <string.h>

int getch()
{
  int            ch;
  struct termios old;
  struct termios tmp;

  if (tcgetattr(STDIN_FILENO, &old))
  {
    return -1;
  }

  memcpy(&tmp, &old, sizeof(old));

  tmp.c_lflag &= ~ICANON & ~ECHO;

  if (tcsetattr(STDIN_FILENO, TCSANOW, (const struct termios*) &tmp))
  {
    return -1;
  }

  ch = getchar();

  tcsetattr(STDIN_FILENO, TCSANOW, (const struct termios*) &old);

  return ch;
}

int main()
{
  printf("Enter a single-digit number: ");
  int num = getch() - '0';
  printf("\nYou entered a %d\n", num);
  return 0;
}

```

Please refer to the man-page for 'tcsetattr' should you wish to experiment with other terminal settings that would perhaps, allow you to enter numbers with multiple-digits, not just a single-digit as per your requirement.

---

### Post by eiffenheart on 2009-03-15
I used the search engine and typed "input number without echo in monitor" and didn't seem to have what I'm looking for...

Thanks a lot.
I've been dying to have an answer for my question.
Really really thank you.

I'm going to try the program right away!

Edit:
...My Borland C++ doesn't have a termios and unistd header file.
Should I try and google for one to download? But the source file will be run in another computer(My professor's) and not mine, so I'm not sure.
Also, the compiler said that old is unknown or zero.
There's also the declaration not allowed here error and an error with undefined symbol(which I think is because the two header files are not present).

...Maybe I'll play safe and modify my plans... Stick to getch() for awhile and not use the numpad as controls.

Thanks again.

---

### Post by nvteighen on 2009-03-15
Hum... unless you want to do what dwhitney67 did, you better use ncurses... it's designed to be used for this stuff in an easier way than using direct terminal handling.

---

### Post by lisati on 2009-03-15
Isn't there a version of getch() on some compilers for Windows that doesn't echo?

---

### Post by dwhitney67 on 2009-03-15
> **nvteighen said:**
> Hum... unless you want to do what dwhitney67 did, you better use ncurses... it's designed to be used for this stuff in an easier way than using direct terminal handling.
That's debatable.  Adding a dependency to ncurses may not be in the cards.  Plus the code I presented is not difficult at all, and I wouldn't be half-surprised if ncurses employed the same.

---

### Post by Krupski on 2009-03-15
> **eiffenheart said:**
> I'm figuring out how to make the user input a single digit number without making an echo to the monitor. Like, make the input "invisible".

So far, I only know getch() or getchar()
but it isn't compatible with numbers.

I've tried googling it, but to no avail.

Any help is greatly appreciated.

...This is for my project/additional points for a subject of mine. ;)

Here's something you maybe can adapt. It's a little function that I wrote as a generic input module for console mode programs.

It returns user input as a "clean" string (characters plus a null, no newlines), plus it returns the floating point value if the input is a number and it also returns the rounded integer value (if input is a number).

Finally, it returns "true" or "false" if the first character is a "Y" (for "yes").

Hope you can make use of it.

```

//////////////////////////////////////////////////////////////////////////
// readln.c
// Last revision: 14 March 2009
// Usage: reads a line from "fp" and returns:
// (1) The string, null terminated, without newline
// (2) The double value if the string was a number
// (3) The int value (symmetric rounded) if the string was a number
// (4) "True" if the first character was "Y" or "y"
// Purpose: To get various kinds of input from a user.
//////////////////////////////////////////////////////////////////////////
// Copyright (C) 2009 Roger A. Krupski <krupski@acsu.buffalo.edu>
//
// This program is free software: you can redistribute it and/or modify
// it under the terms of the GNU General Public License as published by
// the Free Software Foundation, either version 3 of the License, or
// (at your option) any later version.
//
// This program is distributed in the hope that it will be useful,
// but WITHOUT ANY WARRANTY; without even the implied warranty of
// MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
// GNU General Public License for more details.
//
// You should have received a copy of the GNU General Public License
// along with this program.  If not, see <http://www.gnu.org/licenses/>.
//////////////////////////////////////////////////////////////////////////

int readln(FILE*, double*, int*, char*); // prototype

int readln(FILE *fp, double *fnum, int *inum, char *str)
{
	char buf[BUFSIZ]; // read into here
	int len; // string length

	// read a line
	buf[0] = 0; fgets(buf, BUFSIZ, fp);

	len = strlen(buf); // length of line

	// adjust len to ignore space, cr, lf or null at eol
	while(len >= 0) {
		if(	buf[len] == 32 ||
			buf[len] == 13 ||
			buf[len] == 10 ||
			buf[len] == 0) { buf[len] = 0; len--; }
		else { break; }
	}

	len++; // adjust len for null

	// add terminating null
	buf[len] = 0;

	// copy buffer for return to caller
	strcpy(str, buf);

	// get the floating point value of the input
	*fnum = atof(buf);

	// get symmetric rounded int value of input
	*inum = (*fnum < 0) ? (*fnum - 0.5) : (*fnum + 0.5);

	// return "true" if first char is a "Y" or "y" for yes
	sscanf(buf, "%s", buf);
	return(buf[0] == 'Y' || buf[0] == 'y');
}

```


-- Roger

---

### Post by sgosnell on 2009-03-15
The TurboC++ compiler is a Windows compiler, not Linux.  What runs on Linux isn't likely to run on Windows.  I suggest reading the Borland manual and finding a function that does what you want.  ISTR that there is one, but it's been years since I used that compiler, or indeed any Windows compiler, and my memory isn't what it used to be.

---

### Post by rich1939 on 2009-03-15
> **nvteighen said:**
> Hum... unless you want to do what dwhitney67 did, you better use ncurses... it's designed to be used for this stuff in an easier way than using direct terminal handling.

+1 for Curses in that application.

---

### Post by dwhitney67 on 2009-03-15
> **Krupski said:**
> ...
```

//////////////////////////////////////////////////////////////////////////
// readln.c
// Last revision: 14 March 2009
// Usage: reads a line from "fp" and returns:
// (1) The string, null terminated, without newline
// (2) The double value if the string was a number
// (3) The int value (symmetric rounded) if the string was a number
// (4) "True" if the first character was "Y" or "y"
// Purpose: To get various kinds of input from a user.
//////////////////////////////////////////////////////////////////////////
// Copyright (C) 2009 Roger A. Krupski <krupski@acsu.buffalo.edu>
//
// This program is free software: you can redistribute it and/or modify
// it under the terms of the GNU General Public License as published by
// the Free Software Foundation, either version 3 of the License, or
// (at your option) any later version.
//
// This program is distributed in the hope that it will be useful,
// but WITHOUT ANY WARRANTY; without even the implied warranty of
// MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
// GNU General Public License for more details.
//
// You should have received a copy of the GNU General Public License
// along with this program.  If not, see <http://www.gnu.org/licenses/>.
//////////////////////////////////////////////////////////////////////////

int readln(FILE*, double*, int*, char*); // prototype

int readln(FILE *fp, double *fnum, int *inum, char *str)
{
	char buf[BUFSIZ]; // read into here
	int len; // string length

	// read a line
	buf[0] = 0; fgets(buf, BUFSIZ, fp);

	len = strlen(buf); // length of line

	// adjust len to ignore space, cr, lf or null at eol
	while(len >= 0) {
		if(	buf[len] == 32 ||
			buf[len] == 13 ||
			buf[len] == 10 ||
			buf[len] == 0) { buf[len] = 0; len--; }
		else { break; }
	}

	len++; // adjust len for null

	// add terminating null
	buf[len] = 0;

	// copy buffer for return to caller
	strcpy(str, buf);

	// get the floating point value of the input
	*fnum = atof(buf);

	// get symmetric rounded int value of input
	*inum = (*fnum < 0) ? (*fnum - 0.5) : (*fnum + 0.5);

	// return "true" if first char is a "Y" or "y" for yes
	sscanf(buf, "%s", buf);
	return(buf[0] == 'Y' || buf[0] == 'y');
}

```

I have some comments on the code, which unfortunately might not be received well... but here goes:

1.  strlen() returns the number of characters in a string, not including the terminating null-character.  The check for a null-char in the while-loop is not needed.  You could simplify this code using strtok().

2.  Danger Will Robinson!... you are copying a string buffer into str, using strcpy(), without even knowing the number of bytes allocated to str.  You assume the callee knows the internals of your code and knows what size to allocate for str; never assume that.

3.  Your function readln() is doing way too much... converting to string, to float, and integer (using round-off?), and then checking if the first character of the line has a letter 'Y' (or 'y').  In the software engineering field, this type of development is dubbed a "kitchen sink".  Your code is too broad to be used for any practical use.

The Copyright and GPL header are probably not needed; I don't expect anyone to use this code.  It's too much bloat.

---

### Post by Krupski on 2009-03-15
> **dwhitney67 said:**
> I have some comments on the code, which unfortunately might not be received well... but here goes:

1.  strlen() returns the number of characters in a string, not including the terminating null-character.  The check for a null-char in the while-loop is not needed.  You could simplify this code using strtok().

2.  Danger Will Robinson!... you are copying a string buffer into str, using strcpy(), without even knowing the number of bytes allocated to str.  You assume the callee knows the internals of your code and knows what size to allocate for str; never assume that.

3.  Your function readln() is doing way too much... converting to string, to float, and integer (using round-off?), and then checking if the first character of the line has a letter 'Y' (or 'y').  In the software engineering field, this type of development is dubbed a "kitchen sink".  Your code is too broad to be used for any practical use.

The Copyright and GPL header are probably not needed; I don't expect anyone to use this code.  It's too much bloat.

I value your comments highly. Please feel free to comment and continue to comment on code that I post!

(1) My intent was to remove trailing spaces, carriage returns and linefeeds and return a simple null terminated string (useful for fopen). I have to include "0" in my reverse strip because I have to "hop over" the usual null that terminates the input string. The main reason I did what I did was so that I could read lines from DOS/Win (with cr/lf), lines from Unix (lf only) and even MAC (cr only) and end up with the same results.

(2) True - this could be a problem... but I always allocate "BUFSIZ" to every string I declare, so I know it's OK.

(3) Yes indeed it's the "kitchen sink". I originally wrote this function for use in a program that asks for string input, floating point input, raw strings and "yes/no" responses. I also needed integers input by the user...

As far as the GPL header... I've just gotten into the habit of putting that on all my stuff since, of course, anyone who may wish to use it is welcomed to.

Lastly, as I said in the beginning... I do value your comments so please tell me whatever you think, add any suggestions you wish... if my code outright sucks, please say so. I won't be offended.

I know when dealing with people who know more than me to keep my ears open and my mouth shut!  :D

Thanks!

-- Roger

---

### Post by dwhitney67 on 2009-03-15
> **Krupski said:**
> ...
Lastly, as I said in the beginning... I do value your comments so please tell me whatever you think, add any suggestions you wish... if my code outright sucks, please say so. I won't be offended.
...

Just so that you have a good night's sleep, let me go on record to state that your approach to coding is fine and your desire to develop reusable code is admirable.  However I wanted to recommend that you try to modularize functionality and also remove unnecessary/project-specific requirements from a library call, while at the same time, be aware of the aspects of information assurance and how it relates to software.

---

