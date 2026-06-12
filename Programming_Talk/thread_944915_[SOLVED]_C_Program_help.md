---
title: "[SOLVED] C Program help"
date: 2008-10-11
forum: Programming Talk
---

### Post by nzadLithium on 2008-10-11
Hey,
I'm posting here coz it won't let me post anywhere else that seems to have anything to do with it :S
So...
I'm trying to read the /proc/bus/input/devices using c

Im trying to grab out all the lines that are to do with the name of a device, or its event number.

This is what i've got ```
#include <stdio.h>
#include <string.h>

int main()
{
   FILE * pFile;
	char mystring [256];
   char arraystring [60][256];
	int i = 0;

   pFile = fopen ("/proc/bus/input/devices", "r");
	while (!feof(pFile))
	{
		fgets(mystring, 256, pFile);
		if (((strstr(mystring, "Name")) != NULL) || ((strstr(mystring, "Handlers")) != NULL))
		{
			strcpy(arraystring[i], mystring);
			i++;
		}
	}
   fclose (pFile);
	i = 0;
	
	while (arraystring[i] != NULL)
	{
		puts(arraystring[i]);
		i++;
	}
	return 0;
}
```

Now this does get it all out, but at the end it also adds:
```
:&#9149;&#9500;=37;44:&#9226;&#9474;=01;32:*.&#9500;&#9618;&#9148;=01;31:*.&#9500;±&#8805;=01;31:*.&#9149;&#9524;±&#8805;=01;31:*.&#9618;&#9148;&#9496;=01;31:*.&#9500;&#9618;&#8805;=01;31:*.&#9484;&#8805;&#9252;=01;31:*.&#9484;&#8805;&#9492;&#9618;=01;31:*.&#8805;&#9227;&#9147;=01;31:*.&#8805;=01;31:*.Z=01;31:*.&#9229;&#8805;=01;31:*.±&#8805;=01;31:*.&#9225;&#8805;2=01;31:*.&#9225;&#8805;=01;31:*.&#9500;&#9225;&#8805;2=01;31:*.&#9500;&#8805;=01;31:*.&#9229;&#9226;&#9225;=01;31:*.&#9148;&#9147;&#9492;=01;31:*.&#9496;&#9618;&#9148;=01;31:*.&#9148;&#9618;&#9148;=01;31:*.&#9618;&#9228;&#9226;=01;31:*.&#8805;&#9146;&#9146;=01;31:*.&#9228;&#9147;&#9227;&#9146;=01;31:*.7&#8805;=01;31:*.&#9148;&#8805;=01;31:*.&#9496;&#9147;±=01;35:*.&#9496;&#9147;&#9226;±=01;35:*.±&#9227;°=01;35:*.&#9225;&#9492;&#9147;=01;35:*.&#9147;&#9225;&#9492;=01;35:*.&#9147;±&#9492;=01;35:*.&#9147;&#9147;&#9492;=01;35:*.&#9500;±&#9618;=01;35:*.&#9474;&#9225;&#9492;=01;35:*.&#9474;&#9147;&#9492;=01;35:*.&#9500;&#9227;°=01;35:*.&#9500;&#9227;°°=01;35:*.&#9147;&#9532;±=01;35:*.&#9149;&#9524;±=01;35:*.&#9492;&#9532;±=01;35:*.&#9147;&#9228;&#9474;=01;35:*.&#9492;&#9146;&#9524;=01;35:*.&#9492;&#9147;±=01;35:*.&#9492;&#9147;&#9226;±=01;35:*.&#9492;2&#9524;=01;35:*.&#9492;&#9488;&#9524;=01;35:*.&#9146;±&#9492;=01;35:*.&#9492;&#9147;4=01;35:*.&#9492;4&#9524;=01;35:*.&#9492;&#9147;4&#9524;=01;35:*.&#9524;&#9146;&#9225;=01;35:*.&#9472;&#9500;=01;35:*.&#9532;&#9508;&#9524;=01;35:*.&#9516;&#9492;&#9524;=01;35:*.&#9618;&#9149;°=01;35:*.&#9148;&#9492;=01;35:*.&#9148;&#9492;&#9524;&#9225;=01;35:*.°&#9484;&#9228;=01;35:*.&#9618;&#9524;&#9227;=01;35:*.°&#9484;&#9227;=01;35:*.±&#9484;=01;35:*.&#9229;&#9484;=01;35:*.&#9474;&#9228;°=01;35:*.&#9474;&#9516;&#9229;=01;35:*.&#8804;&#9508;&#9524;=01;35:*.&#9618;&#9618;&#9228;=00;36:*.&#9618;&#9508;=00;36:*.°&#9484;&#9618;&#9228;=00;36:*.&#9492;&#9227;&#9229;=00;36:*.&#9492;&#9227;&#9229;&#9227;=00;36:*.&#9492;&#9488;&#9618;=00;36:*.&#9492;&#9147;3=00;36:*.&#9492;&#9147;&#9228;=00;36:*.&#9146;±±=00;36:*.&#9148;&#9618;=00;36:*.&#9516;&#9618;&#9524;=00;36:
&#9618;&#9228;&#9226;=01;31:*.&#8805;&#9146;&#9146;=01;31:*.&#9228;&#9147;&#9227;&#9146;=01;31:*.7&#8805;=01;31:*.&#9148;&#8805;=01;31:*.&#9496;&#9147;±=01;35:*.&#9496;&#9147;&#9226;±=01;35:*.±&#9227;°=01;35:*.&#9225;&#9492;&#9147;=01;35:*.&#9147;&#9225;&#9492;=01;35:*.&#9147;±&#9492;=01;35:*.&#9147;&#9147;&#9492;=01;35:*.&#9500;±&#9618;=01;35:*.&#9474;&#9225;&#9492;=01;35:*.&#9474;&#9147;&#9492;=01;35:*.&#9500;&#9227;°=01;35:*.&#9500;&#9227;°°=01;35:*.&#9147;&#9532;±=01;35:*.&#9149;&#9524;±=01;35:*.&#9492;&#9532;±=01;35:*.&#9147;&#9228;&#9474;=01;35:*.&#9492;&#9146;&#9524;=01;35:*.&#9492;&#9147;±=01;35:*.&#9492;&#9147;&#9226;±=01;35:*.&#9492;2&#9524;=01;35:*.&#9492;&#9488;&#9524;=01;35:*.&#9146;±&#9492;=01;35:*.&#9492;&#9147;4=01;35:*.&#9492;4&#9524;=01;35:*.&#9492;&#9147;4&#9524;=01;35:*.&#9524;&#9146;&#9225;=01;35:*.&#9472;&#9500;=01;35:*.&#9532;&#9508;&#9524;=01;35:*.&#9516;&#9492;&#9524;=01;35:*.&#9618;&#9149;°=01;35:*.&#9148;&#9492;=01;35:*.&#9148;&#9492;&#9524;&#9225;=01;35:*.°&#9484;&#9228;=01;35:*.&#9618;&#9524;&#9227;=01;35:*.°&#9484;&#9227;=01;35:*.±&#9484;=01;35:*.&#9229;&#9484;=01;35:*.&#9474;&#9228;°=01;35:*.&#9474;&#9516;&#9229;=01;35:*.&#8804;&#9508;&#9524;=01;35:*.&#9618;&#9618;&#9228;=00;36:*.&#9618;&#9508;=00;36:*.°&#9484;&#9618;&#9228;=00;36:*.&#9492;&#9227;&#9229;=00;36:*.&#9492;&#9227;&#9229;&#9227;=00;36:*.&#9492;&#9488;&#9618;=00;36:*.&#9492;&#9147;3=00;36:*.&#9492;&#9147;&#9228;=00;36:*.&#9146;±±=00;36:*.&#9148;&#9618;=00;36:*.&#9516;&#9618;&#9524;=00;36:
=01;35:*.&#9492;&#9147;±=01;35:*.&#9492;&#9147;&#9226;±=01;35:*.&#9492;2&#9524;=01;35:*.&#9492;&#9488;&#9524;=01;35:*.&#9146;±&#9492;=01;35:*.&#9492;&#9147;4=01;35:*.&#9492;4&#9524;=01;35:*.&#9492;&#9147;4&#9524;=01;35:*.&#9524;&#9146;&#9225;=01;35:*.&#9472;&#9500;=01;35:*.&#9532;&#9508;&#9524;=01;35:*.&#9516;&#9492;&#9524;=01;35:*.&#9618;&#9149;°=01;35:*.&#9148;&#9492;=01;35:*.&#9148;&#9492;&#9524;&#9225;=01;35:*.°&#9484;&#9228;=01;35:*.&#9618;&#9524;&#9227;=01;35:*.°&#9484;&#9227;=01;35:*.±&#9484;=01;35:*.&#9229;&#9484;=01;35:*.&#9474;&#9228;°=01;35:*.&#9474;&#9516;&#9229;=01;35:*.&#8804;&#9508;&#9524;=01;35:*.&#9618;&#9618;&#9228;=00;36:*.&#9618;&#9508;=00;36:*.°&#9484;&#9618;&#9228;=00;36:*.&#9492;&#9227;&#9229;=00;36:*.&#9492;&#9227;&#9229;&#9227;=00;36:*.&#9492;&#9488;&#9618;=00;36:*.&#9492;&#9147;3=00;36:*.&#9492;&#9147;&#9228;=00;36:*.&#9146;±±=00;36:*.&#9148;&#9618;=00;36:*.&#9516;&#9618;&#9524;=00;36:
5:*.&#9474;&#9516;&#9229;=01;35:*.&#8804;&#9508;&#9524;=01;35:*.&#9618;&#9618;&#9228;=00;36:*.&#9618;&#9508;=00;36:*.°&#9484;&#9618;&#9228;=00;36:*.&#9492;&#9227;&#9229;=00;36:*.&#9492;&#9227;&#9229;&#9227;=00;36:*.&#9492;&#9488;&#9618;=00;36:*.&#9492;&#9147;3=00;36:*.&#9492;&#9147;&#9228;=00;36:*.&#9146;±±=00;36:*.&#9148;&#9618;=00;36:*.&#9516;&#9618;&#9524;=00;36:
AGER=&#9484;&#9146;&#9228;&#9618;&#9484;/&#9228;&#9492;&#9618;&#9149;&#9500;&#9226;&#9148;-&#9229;&#9226;&#9149;&#9488;&#9500;&#9146;&#9147;:/&#9500;&#9492;&#9147;/.ICE-&#9508;&#9532;&#9227;&#9474;/6825
US.UTF-8
&#9508;&#9532;&#9227;&#9474;:&#9618;&#9225;&#9149;&#9500;&#9148;&#9618;&#9228;&#9500;=/&#9500;&#9492;&#9147;/&#9229;&#9225;&#9508;&#9149;-AW±&#9225;&#9618;&#9532;&#9147;J0&#9484;,±&#9508;&#9227;&#9229;=°&#9228;°&#9618;9596&#9229;61°6119&#9229;3&#9228;43&#9225;5148°11&#9229;°°

S&#9226;±&#9492;&#9226;&#9532;&#9500;&#9618;&#9500;&#9227;&#9146;&#9532; °&#9618;&#9508;&#9484;&#9500;

```

I have no idea what all this is, or why its doing it.

And then my prompt now looks like:
&#9228;&#9492;&#9618;&#9149;&#9500;&#9226;&#9148;@&#9228;&#9492;&#9618;&#9149;&#9500;&#9226;&#9148;-&#9229;&#9226;&#9149;&#9488;&#9500;&#9146;&#9147;:·/D&#9226;&#9149;&#9488;&#9500;&#9146;&#9147;/&#9524;&#9226;&#9532;&#9500;&#9148;&#9227;&#9484;&#9146;&#9228;&#9500;&#9148;&#9484;-0.3$ 
instead of cmaster@cmaster-desktop:~$

wtf is going on? What did i break? XD

Any idea's how to fix? Thanks :D

---

### Post by tang0delta on 2008-10-11
Hi. I only have a basic knowledge of C as I only started learning but is it possible that you've made some sort of semantic error when trying to output the contents of your "arrayString" array. I know from my experience with java that an array which isnt referenced properly in code will lead to jibberish being output when trying to print the arrays contents? hope this gets you thinking along the right lines?

---

### Post by Rocket2DMn on 2008-10-11
Moved to Programming Talk.

---

### Post by LaRoza on 2008-10-11
> **nzadLithium said:**
> And then my prompt now looks like:
&#9228;&#9492;&#9618;&#9149;&#9500;&#9226;&#9148;@&#9228;&#9492;&#9618;&#9149;&#9500;&#9226;&#9148;-&#9229;&#9226;&#9149;&#9488;&#9500;&#9146;&#9147;:·/D&#9226;&#9149;&#9488;&#9500;&#9146;&#9147;/&#9524;&#9226;&#9532;&#9500;&#9148;&#9227;&#9484;&#9146;&#9228;&#9500;&#9148;&#9484;-0.3$ 
instead of cmaster@cmaster-desktop:~$

wtf is going on? What did i break? XD

Any idea's how to fix? Thanks :D

That happens when you out put certain content. I know the fix (besides restarting the terminal) but I can't remember it at the moment...

Nothing is broken, and restarting the terminal will clear it. I will try to remember the command.


<edit>
Type "reset".

[http://tldp.org/HOWTO/Keyboard-and-Console-HOWTO-4.html](http://tldp.org/HOWTO/Keyboard-and-Console-HOWTO-4.html)

---

### Post by dwhitney67 on 2008-10-12
I fixed the code such that now it will work.  Compile it with:
```
gcc -Wall -pedantic -std=gnu99 devices.c -o devices
```

[php]
#include <stdio.h>
#include <string.h>


int main()
{
  const size_t MAX_LINE_SZ = 256;
  const size_t MAX_RESULTS = 100;

  char   results[ MAX_RESULTS ][ MAX_LINE_SZ ];
  size_t numResults = 0;

  FILE * devices = fopen( "/proc/bus/input/devices", "r" );

  if ( devices )
  {
    while ( !feof(devices) && numResults < MAX_RESULTS )
    {
      char line[ MAX_LINE_SZ ];

      fgets( line, MAX_LINE_SZ, devices );

      if ( strstr( line, "Name"     ) != NULL ||
           strstr( line, "Handlers" ) != NULL )
      {
        strncpy( results[ numResults ], line, strlen(line) );
        ++numResults;
      }
    }

    fclose( devices );
  }
	
  for ( size_t i = 0; i < numResults; ++i )
  {
    printf( "%s", results[i] );
  }

  return 0;
}
[/php]

---

### Post by nzadLithium on 2008-10-12
thx dwhitney :D
just another question now
what do these do: -pedantic -std=gnu99
:p

TY :D

---

### Post by nzadLithium on 2008-10-12
ah i think i get it. Pedantic just makes it more picky, and the std option sets the gcc standard version?

---

### Post by dwhitney67 on 2008-10-12
> **nzadLithium said:**
> thx dwhitney :D
just another question now
what do these do: -pedantic -std=gnu99
:p

TY :D

pedantic:  issue all warnings when code does not adhere to strict ISO C and C++ standards.

-std=:  specify which version of the compiler to use; in the case I recommended, using the gnu99, which is the 1999 standard for GNU C.  There is also a ISO (?) C99 (c99) standard.  By default, gcc uses the C89 (c89) (a 1989 standard).

---

### Post by nzadLithium on 2008-10-12
Yours seems to be almost the same as my way I think? The only crucial difference I can see is you limited the size to 100. I think this would probably cut off all the stuff that was at the bottom with the one I wrote (I probably wrote it badly but oh well :p).

So were all those crazy characters actually a part of the file?

---

### Post by slavik on 2008-10-12
gnu99 is the incomplete implementation of the ISO C99 standard (I believe that there is no compiler that support C99 to the fullest).

---

### Post by nzadLithium on 2008-10-12
Ok now that i tried mine that way I have a feeling I was wrong about that last assumption :S 

So could you explain why your way gets rid of them while mine doesnt? 

Thanks :D

---

### Post by dwhitney67 on 2008-10-12
> **nzadLithium said:**
> Yours seems to be almost the same as my way I think? The only crucial difference I can see is you limited the size to 100. I think this would probably cut off all the stuff that was at the bottom with the one I wrote (I probably wrote it badly but oh well :p).

So were all those crazy characters actually a part of the file?
The code I wrote and your are very similar; the 100 size was something I arbitrarily picked, similarly to the number 60 you picked.

Your original code was fine, except that you did not check to ensure that the index to arraystring did not exceed 60.  Had there been more than 60 results, your program would probably have crashed.

The other issue with your original code was the outputting of the data.  You should have used a for-loop instead of the while loop.  The number of results are contained in the variable "i".  Thus the for-loop would be:
[php]
for ( int n = 0; n < i; ++n )
{
  printf( "%s", arraystring[n] );
}
[/php]
Note, I used printf() in lieu of puts().  The reason is because the strings already have a newline character in them, and there is no need to output another (and that is what puts() does).

---

### Post by iponeverything on 2008-10-12
Terminal issue:

typing "reset" in the terminal should fix the it up it again.

Programing issue:

no idea :)

---

### Post by nzadLithium on 2008-10-12
Ok i'm really confused now, i just changed the strcpy to a strncpy like you did, and now all that extra stuff down the bottom is in plane english, it appears to be reading information from somewhere else???

I have a whole lot of stuff about various extensions, eg *.xpm=01;35:
and then when it finishes all of that it gives me the same output as the PATH environment variable, and a little bit more stuff, then it segfaults :p

Isn't feof meant to stop it at the end of file? where is all this other info coming from :S

---

### Post by nzadLithium on 2008-10-12
ah so was this caused by it acessing memory it wasn't meant to have (since i exceeded the 60 or something? )

---

### Post by dwhitney67 on 2008-10-12
> **nzadLithium said:**
> ah so was this caused by it acessing memory it wasn't meant to have (since i exceeded the 60 or something? )
I hope by now you understand why your original code was printing "garbage".  You were printing information beyond the bounds of your array.  That conditional statement within the while-loop is bogus.

The number of results is contained in the variable "i", which I personally did not like the name; so I renamed it to numRecords.  The same with "arraystring" name and the "mystring".  I renamed them.

The constants I created were done so that it would be easy to change a value without having to search through all of the code to change other values.

I also checked to ensure the file was properly opened; you assumed it was.

I also checked to ensure that if there happened to be more than MAX_RESULTS found in the file, that I would limit my findings to MAX_RESULTS.  Hence the additional condition paired to the feof() in the first while-loop.

---

### Post by nzadLithium on 2008-10-12
ah k yep i think i get it :D

just one last question :p

in my original one i told it to keep printing out the array until it had reached one that had nothing in it (== NULL). Why didn't any of them equal NULL? :S

I don't get that bit, theoretically if I've been copying lines out of the file, and then suddenly it comes to a part of the array nothing is copied to shouldn't that part of the array be equal to NULL?

Thx for answering my dumb questions :D

---

### Post by LaRoza on 2008-10-12
> **nzadLithium said:**
> 
in my original one i told it to keep printing out the array until it had reached one that had nothing in it (== NULL). Why didn't any of them equal NULL? :S

Because it didn't happen to == NULL.

> 
I don't get that bit, theoretically if I've been copying lines out of the file, and then suddenly it comes to a part of the array nothing is copied to shouldn't that part of the array be equal to NULL?


Ah, then you misunderstand how it works. On your disk, there is a table showing where everything is. That is used to find files. The actually data on the disk could be anything. Same with RAM.

Just because the end of the array was reached, it doesn't mean the data stored after it is suddenly nonexistant.

---

### Post by nzadLithium on 2008-10-12
Lol you lost me again XD

so
The array starts empty.
I got the data from the file, and put it into the array, the data was supposed to stop reading at feof so it should have stopped at end of file.

Then the array should now contain data that I have put in it, as well as a whole lot of empty 'slots' afterwards (which are there coz I didn't put completely full the array). Right? 

Like this
I declare array bob[4]
bob should now contain NULL,NULL,NULL,NULL right?
then i place i into bob[0], j into bob[1]
it should now be i,j,NULL,NULL right?

I must really be missing something XD
thx so much for putting up with my stupidity :D

---

### Post by dwhitney67 on 2008-10-12
> **nzadLithium said:**
> ah k yep i think i get it :D

just one last question :p

in my original one i told it to keep printing out the array until it had reached one that had nothing in it (== NULL). Why didn't any of them equal NULL? :S

I don't get that bit, theoretically if I've been copying lines out of the file, and then suddenly it comes to a part of the array nothing is copied to shouldn't that part of the array be equal to NULL?

Thx for answering my dumb questions :D

I don't guarantee the code below to always work, nor recommend it for that matter, but had you changed the conditional in your while-loop (as shown below), then you would not have had a problem in the first place and you probably would not have learned anything today!
[php]
int n = 0;
while (arraystring[n][0] != NULL)   // note that I am checking the first character
{
  printf( "%s", arraystring[ n++ ] );
}
[/php]

---

### Post by LaRoza on 2008-10-12
> **nzadLithium said:**
> so
The array starts empty.

No, the array starts out as a pointer to a memory address. If you don't the memory addresses to be a particular value, then they equal what happens to be there.

It is Random Access Memory.

That is why you should initialise pointers. You can zero and array if you want, how I leave as an excercise to the reader (there are two methods)
> 
I got the data from the file, and put it into the array, the data was supposed to stop reading at feof so it should have stopped at end of file.

Yes, it did. But the memory addresses after that still exist.

Your RAM (your computer's RAM) is a bunch of memory slots that can be accessed easily at any point (picture, a bunch of mail boxes on a wall). When you put something into them, you overwrite (remove) what was in them, but anything can be in them until you do that.

When your program ended, it is likely that the values of that array were still in those memory slots, until they happened to be overwritten (this is one method of retrieving data from a computer system, but examining the RAM. Usually used for forensics).

> 
Then the array should now contain data that I have put in it, 

Yes.

> 
as well as a whole lot of empty 'slots' afterwards
No. 

> 
(which are there coz I didn't put completely full the array). Right? 

Why would they be empty? When you put the data into those slots, and the program ends, does the program remove all that data? No. For local variables, when they go out of scope, the space is freed so any other program can put data there, but the old data is there until then. For malloced data, it is there until it is freed or the program ends (modern OS's free the data).

> 
Like this
I declare array bob[4]
bob should now contain NULL,NULL,NULL,NULL right?

No, it is a pointer to a memory address (random) and allocates 4 slots in a row on the stack.

> 
then i place i into bob[0], j into bob[1]
it should now be i,j,NULL,NULL right?

No, it is "i", "j" and whatever happens to be there.


```

~/p$cat p.c
#!/usr/bin/tcc -run

int main(void)
{
    int array[4];
    array[0] = 4;
    array[1] = 2;
    printf("array[0] == %d\narray[1] == %d\narray[2] == %d\narray[3] == %d\narray[4] == %d\n",array[0],array[1],array[2],array[3],array[4]);
    return 0;
}
~/p$./p.c
array[0] == 4
array[1] == 2
array[2] == 134743872
array[3] == -1075795872
array[4] == -1075799988
~/p$

```

Note, array[4] isn't declared. C is dumb. Array indices are just shorthand for pointer arithmatic. array[4] is just five slots after the memory address of array[0] (which is &array[0] or array). The memory is readable there, so I can print its value, but writing to it would be...dangerous. It could be junk. It could be some process that doesn't matter. Or it could be a process that does matter.

It would result in a segfault if it were important, but buffer overflows are not something to fool around with.

---

### Post by dwhitney67 on 2008-10-12
> **nzadLithium said:**
> 
...
The array starts empty.
...
Not necessarily when programming in C.  You may think it is empty, but it could contain cr*p that is in memory.

If you want to be certain that it is empty, then set it to be full of nulls:
[php]memset( arraystring, 0, sizeof(arraystring) );[/php]

---

### Post by nzadLithium on 2008-10-12
I understand now :D Never count memory as empty unless you've emptied it yourself :D

Thx for all your help :)

---

### Post by LaRoza on 2008-10-12
> **nzadLithium said:**
> I understand now :D Never count memory as empty unless you've emptied it yourself :D

Thx for all your help :)

I added the code to help.

---

### Post by lisati on 2008-10-12
> **nzadLithium said:**
> I understand now :D Never count memory as empty unless you've emptied it yourself :D 

Thx for all your help :)

That's great, and says it better than I could (I'd probably say something like "It's always safest to initialise variables so that you know for sure what's there - sometimes you might get lucky if you don't but chances are you'll end up with rubbish values and obscure bugs.")

---

### Post by nvteighen on 2008-10-12
> **nzadLithium said:**
> Yours seems to be almost the same as my way I think? The only crucial difference I can see is you limited the size to 100. I think this would probably cut off all the stuff that was at the bottom with the one I wrote (I probably wrote it badly but oh well :p).

So were all those crazy characters actually a part of the file?
That's binary garbage. You continued looping through the file though your variable was already full (thank God you weren't using gets() but fgets()!). So the rest went into stdout's buffer without any "format" (i.e. you didn't segment it into anything by storing it in a variable), which is flushed after you printed with puts().

The solution dwhitney67 gave you is just to avoid anything get into stdout's buffer by stopping to read when the variable's full.

Of course, that solution is pretty limiting, and you'll probably want to be able to read stuff without a fixed limit. That's possible, but it will make you enter into the realms of dynamic memory allocation (which is not a bad thing, but a tricky one).

EDIT: Man, I missed a whole page!!

---

### Post by LaRoza on 2008-10-12
> **nvteighen said:**
> 
EDIT: Man, I missed a whole page!!

Reading that, I only saw "man page".

---

