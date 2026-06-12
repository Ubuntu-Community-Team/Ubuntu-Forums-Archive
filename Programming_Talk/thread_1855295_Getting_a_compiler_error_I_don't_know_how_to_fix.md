---
title: "Getting a compiler error I don't know how to fix"
date: 2011-10-05
forum: Programming Talk
---

### Post by ClientAlive on 2011-10-05
Hi,

I've been trying to find info on this on the Internet; but, so far, haven't seen anything that makes sense (or is applicable that I can tell).

I'm getting a compiler error from gcc that says: "name-of-source-file.c:###:#: warning: multi-character character constant"

I've been over and over the source code looking for anything that sticks out as being wrong with it, and comparing with the examples we have this week, and I just can't figure it out.

Can you help?

PS: "#" represents a numerical digit, in case you didn't guess. In my case there are three of the above type lines that print out.

> 
Christmas-Song-Program.c:264:6: warning: multi-character character constant
Christmas-Song-Program.c:305:6: warning: multi-character character constant
Christmas-Song-Program.c:349:6: warning: multi-character character constant


I noticed I had a lot of white space in the source file and removed some blank lines to squeeze things closer together. The result when I tried to compile again was the same except that the numbers in the lines changed to different numbers.

> 
. . . 115:6 . . .
. . . 130:6 . . .
. . . 146:6 . . .




Does anyone know what this is or what I can do to fix it?

I've attached my source file and a screenshot of the terminal window. It's cygwin on a virtual machine on my school's server by the way.

---

### Post by Barrucadu on 2011-10-05
Line 115 is "case '10':", the other erroneous lines are similar.

The single quotes indicates that this is a char (double quotes indicate a string), and so it's failing because '10' is not one character long. Additionally, you cannot compare strings that way. Furthermore, you're doing it wrong anyway as `input` is an integer, not a char or string.

**edit:** You are evidently pretty new to C, and so I decided to rewrite your code in the way I would do it, in the hope that you may learn something:

```
#include <stdio.h>
#include <assert.h>
#include <string.h>
#include <stdlib.h>

/* ***** Function Prototypes ***** */

/**
 * Function to read an integer from stdin in a given range.
 *
 * @param Minimum value
 * @param Maximum value
 *
 * @return An integer in the range [min, max]
 */
int
getint (int min, int max);

/**
 * Get the suffix for a number (st/nd/rd/th)
 *
 * @param Any positive number
 *
 * @return Suffix string
 */
char *
getsuffix (int value);

/* ***** Code ***** */

/**
 * Function to read an integer from stdin in a given range.
 */
int
getint (int min, int max)
{
  int input;

  /* Check that the min is less than the max */
  assert (min <= max);

  /* Ask for a number until we get a good one */
  do
    {
      printf ("Please enter a number %i through %i: ", min, max);
      scanf ("%i", &input);
    }
  while (input < min || input > max);

  return input;
}

/**
 * Get the suffix for a number (st/nd/rd/th) 
 */
char *
getsuffix (int value)
{
  char *out;
  char *num;
  int   digits;

  /* Check the value is > 0 */
  assert (value > 0);

  /* Get a string copy of the value */
  digits = value / 10 + 1;
  num = malloc (sizeof (char) * digits + 1); /* The length of the string representation of a number is equal to the number of digits */
  sprintf (num, "%i", value);

  /* Get the suffix */
  switch (num[digits - 1])
    {
    case '1':
      /* Silly *11 being a special case */
      out = strdup((digits >= 2 && num[digits - 2] == '1') ? "th" : "st");
      break;
    case '2':
      /* Silly *12 being a special case */
      out = strdup((digits >= 2 && num[digits - 2] == '1') ? "th" : "nd");
      break;
    case '3':
      /* Silly *13 being a special case */
      out = strdup((digits >= 2 && num[digits - 2] == '1') ? "th" : "rd");
      break;
    default:
      out = strdup ("th");
      break;
    }

  /* Free */
  free (num);

  return out;
}

/**
 * Print the 12 days of Christmas song
 */
int
main (void)
{
  /* Get the day and suffix */
  int   day    = getint (1, 12);
  char *suffix = getsuffix (day);

  /* Print the first line */
  printf ("On the %i%s day of Christmas, my true love gave to me...\n", day, suffix);

  /* Print the rest of the song */
  switch (day)
    {
    case 12:
      printf ("12 drummers drumming\n");
    case 11:
      printf ("11 pipers piping\n");
    case 10:
      printf ("10 lords a-leaping\n");
    case 9:
      printf ("9 ladies dancing\n");
    case 8:
      printf ("8 maids a-milking\n");
    case 7:
      printf ("7 swans a-swimming\n");
    case 6:
      printf ("6 geese a-laying\n");
    case 5:
      printf ("5 golden rings\n");
    case 4:
      printf ("4 calling birds\n");
    case 3:
      printf ("3 French Hens\n");
    case 2:
      printf ("2 Turtle Doves\n");
      printf ("And a Partridge in a Pear Tree.\n");
      break;
    case 1:
      printf ("A Partridge in a Pear Tree.\n");
      break;
    }

  /* Free */
  free (suffix);

  /* Done */
  return 0;
}

```

---

### Post by ClientAlive on 2011-10-06
Oh my! Now that's a lot to learn about. Well thanks Baracadu. Yes, I am very new to any kind of programming. This is my fifth program. We are in week six in my class. We started at the very, very, beginning - with the simplest possible program, "hello world" (of course we did, it's a rite of passage isn't it?). Each week we've learned about something different. This week we were learning about switch statements.

I hadn't noticed it but, apparently, whether you enclose the case in quotes or not has to do with the type of variable you use. (I think you told me that). Well, I was able to just go in and remove the quotes from each of my cases and the problem went away. Program works (though there's probably a lot better way to write something like that). I had to do it that way for my assignment though - we're expected to use switch statements.

I'd made a personal decision to use this Christmas song to learn some other stuff outside of class though. It seems to lend itself so well to a variety of concepts I'd like to explore (arrays, loops, probably some other stuff). I'm sure I sound pretty dumb now - I am, well, ignorant of programming anyway.

Thanks for writing that out for me. I'm sure it'll be a great guideline to go off of for things to learn about. Wish I could write C like that. Maybe someday soon.


:)

Jake

---

