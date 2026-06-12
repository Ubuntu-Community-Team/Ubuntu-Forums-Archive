---
title: "C send pitch to /dev/dsp"
date: 2008-10-04
forum: Programming Talk
---

### Post by Dr Small on 2008-10-04
I am a novice at learning C, and probably attempting something outside my realm of short handed knowledge.

I have downloaded the source for 'beep', and basically want to do what beep does (sends a frequency level to the external speaker), only I want to send it to my physical speakers, through the sound card, through /dev/dsp.

I really don't know where to begin, but I did find this:
[http://www.oreilly.de/catalog/multilinux/excerpt/ch14-05.htm#EX-14-2](http://www.oreilly.de/catalog/multilinux/excerpt/ch14-05.htm#EX-14-2)

The problem with that program, is it is reading input from a Microphone and then outputting it back out to the speakers. I would like to have command line options for frequency level and the such, like beep does. I could use beep's framework, if I could figure out how to send it to /dev/dsp.

If anyone has any insights or hints, I would love to hear them.

Dr Small

---

### Post by dwhitney67 on 2008-10-04
Command line options are passed to a C program via the main() function's argv[] array.  The number of options passed is held in argc.  So, an optional way to declare your main() function is:

[php]
int main( int argc, char **argv )
{
  // argc contains the number of command-line arguments
  // At a minimum, this number is set to 1.

  // argv is an array of strings.
  // The first element, argv[0], always contains the program
  // name.
  // The other command-line arguments, if any, start at index 1
  // and run until (argc-1).
}
[/php]

If you want to pass command line arguments in a similar style like other *nix use, then I suggest you create a function that employs getopt().  Here's a complete example that demonstrates how to obtain a frequency value from the command line:

[PHP]
#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>


// Function declaration(s)
//
void parseOptions( int argc, char **argv, unsigned int *freq );


// Main function implementation
//
int main( int argc, char **argv )
{
  unsigned int frequency = 10;  // default to 10 Hz (?)

  parseOptions( argc, argv, &frequency );

  printf( "frequency = %u\n", frequency );

  // ...

  return 0;
}

// parseOptions() implementation
//
void parseOptions( int argc, char **argv, unsigned int *freq )
{
  // The arguments to expect; thus far only 'f'.  The colon after
  // the letter 'f' indicates that a value is expected when this
  // option is given.
  const char * OPTION_LIST = "f:";

  int opt = -1;

  while ( (opt = getopt( argc, argv, OPTION_LIST )) != -1 )
  {
    switch ( opt )
    {
      case 'f':
          *freq = atoi( optarg );     // save the frequency value
          break;

      default:
          fprintf( stderr, "Usage: %s [-f frequency]\n", argv[0] );
          exit( 1 );
    }
  }
}
[/PHP]

To compile this program:
```
gcc -Wall -pedantic -std=gnu99 sound.c -o sound
```

Then to run it, try each of these:
```
./sound
./sound -f 20
./sound -w
```

---

### Post by Dr Small on 2008-10-05
Thanks for the demonstration. That looks simple enough. Now, I just need to find out how to send the frequency pitch to /dev/dsp so it will output on my speakers.

Dr Small

---

