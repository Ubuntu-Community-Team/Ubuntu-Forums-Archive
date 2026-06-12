---
title: "Fastest way to split strings?"
date: 2011-07-28
forum: Programming Talk
---

### Post by cguy on 2011-07-28
I have a file with over 100,000 lines of the following format:
ABCDEF::QWERTY.some_string_or_a_number_after_the_dot

I want to split these lines and put the parts before the :: in one file and the parts between the :: and the . in another file.

ie: ABCDEF in file1.txt
QWERTY in file2.txt


Which is the fastest way to do this? 
Perl? Python? sed? Another program?

"cut" is too slow; it'd take many hours to complete.

---

### Post by lisati on 2011-07-28
A custom program in a language of your own choice?

---

### Post by johnl on 2011-07-28
You could probably do it quickly and easily in awk, perl, sed, or a variety of other languages.

Here's a quick C program which does it.

```

/* usage: "./program out1.txt out2.txt < input.txt" */

#include <stdlib.h>
#include <stdio.h>
#include <string.h>

int main(int argc, char* argv[]) 
{
    FILE* out[2];
    char buf[512];
    
    if (argc != 3) {
        fprintf(stderr, "usage: %s <outfile1> <outfile2>\n", argv[0]);
        return 1;
    }
    
    out[0] = fopen(argv[1], "w");
    out[1] = fopen(argv[2], "w");

    if (!out[0] || !out[1]) {
        fprintf(stderr, "failed to open one of the output files\n");
        return 1;
    }

    int lineno = 0;
    while(fgets(buf, sizeof(buf), stdin)) {
        lineno++;
        char* colons = strstr(buf, "::");
        if (!colons) {
            fprintf(stderr, "warning: line %d: no '::' found", lineno);
            continue;
        }
        char* period = strstr(colons, ".");
        if (!period) {
            fprintf(stderr, "warning: line %d: no '.' found", lineno);
            continue;
        }
        *colons = '\0';
        *period = '\0';
        fprintf(out[0], "%s\n", buf);
        fprintf(out[1], "%s\n", &colons[2]);
    }

    fclose(out[0]);
    fclose(out[1]);
    
    return 0;
}

```

---

### Post by stchman on 2011-07-28
Java is the way to go.

The .split() method in the string class will fit the bill.

```

// open your input file
BufferedReader infile = new BufferedReader( new FileReader( "<your input file>" ) );

// create your two output file(s)
BufferedWriter fileOne = new BufferedWriter( new FileWriter( "file1.txt" ) );
BufferedWriter fileTwo = new BufferedWriter( new FileWriter( "file2.txt" ) );

while( true ) {
    if( infile.ready() == false )
        break;

    String[] data = infile.readLine().trim().split( "::|\\." );
    
    fileOne.write( data[ 0 ] );
    fileTwo.write( data[ 1 ] );

}

infile.close();
fileOne.close();
fileTwo.close();

```The .split method uses regex and "::|\\." indicates

 :: or .

Since . is a control character, you need to use the \\ notation.

Hope this helps.

---

### Post by cgroza on 2011-07-28
> **stchman said:**
> Java is the way to go.

The .split() method in the string class will fit the bill.
  :: or .

Since . is a control character, you need to use the \\ notation.

Hope this helps.
Java for this job? Perl has a regexp split too and it can do it in half of the java lines...

---

### Post by nvteighen on 2011-07-29
> **stchman said:**
> Java is the way to go.

The .split() method in the string class will fit the bill.


That's almost like saying that C is the way to go because it has strtok().

The best for this are Perl or the awk/sed/grep toolchain (ideal for shell scripts), not-so-closely followed by Python. Doing this with a Perl regexp is trivial, as shown below. My Perl skills are quite bad, though, and for sure there are much better ways to do this (chaining calls to split(), perhaps?)

```

#!/usr/bin/env perl

use strict;
use warnings;

sub split_my_string
{
    my $string = shift;

    if($string =~ /^(.*?)::(.*?)\.(?:.*?)$/)
    {
        return ($1, $2);
    }
    else
    {
        return ();
    }
}

my @splitted = 
    split_my_string "ABCDEF::QWERTY.some_string_or_a_number_after_the_dot";

print "$splitted[0]\n$splitted[1]\n";

```

---

### Post by Bodsda on 2011-07-29
> **cguy said:**
> I have a file with over 100,000 lines of the following format:
ABCDEF::QWERTY.some_string_or_a_number_after_the_dot
 
I want to split these lines and put the parts before the :: in one file and the parts between the :: and the . in another file.
 
ie: ABCDEF in file1.txt
QWERTY in file2.txt
 
 
Which is the fastest way to do this? 
Perl? Python? sed? Another program?
 
"cut" is too slow; it'd take many hours to complete.
 
My python approach
 
```

#! /usr/bin/env python
 
lines = open("~/sourcefile", "r").readlines()
file1 = open("~/file1.txt", "w")
file2 = open("~/file2.txt", "w")
 
for i in lines:
    file1.write(i.split("::")[0] + "\n")
    file2.write(i.split("::")[1].split(".")[0])
 
file1.close()
file2.close()

```
 
(code not tested)
Bodsda

---

### Post by LemursDontExist on 2011-07-29
> **Bodsda said:**
> My python approach
 
```

#! /usr/bin/env python
 
lines = open("~/sourcefile", "r").readlines()
file1 = open("~/file1.txt", "w")
file2 = open("~/file2.txt", "w")
 
for i in lines:
    file1.write(i.split("::")[0] + "\n")
    file2.write(i.split("::")[1].split(".")[0])
 
file1.close()
file2.close()

```
 
(code not tested)
Bodsda

To avoid reading the whole file into memory at once (which can make a big difference if you've got 100k lines):

```

with open("sourcefile", "r") as f:
    with open("file1.txt", "w") as g:
        with open("file2.txt", "w") as h:
            for line in f:
                a, b = line.split("::", 1)
                g.write(a + "\n")
                h.write(b.split('.', 1)[0] + "\n")

```

Calling the second split on the already split data should also give a bit of a speed boost since it avoids a good number of otherwise unnecessary comparisons.

How were you trying to use 'cut,' though?  It seems to me that cut ought to be fast enough to deal with 100k lines in a reasonably short time if something funny isn't going on!

---

### Post by Arndt on 2011-07-29
> **cguy said:**
> I have a file with over 100,000 lines of the following format:
ABCDEF::QWERTY.some_string_or_a_number_after_the_dot

I want to split these lines and put the parts before the :: in one file and the parts between the :: and the . in another file.

ie: ABCDEF in file1.txt
QWERTY in file2.txt


Which is the fastest way to do this? 
Perl? Python? sed? Another program?

"cut" is too slow; it'd take many hours to complete.

The fastest way to do this is the language you know best. If you only know Java, it will be Java.

But there's so much less typing to do if you know the basic Unix tools, so do learn them.

Perl and python are also good, if you know them. When I don't know how to combine the basic Unix tools to do what I want, I write a python program. But I write larger things in python, too.

With 'sed', I'd do

```
$ sed 's/^.*:://;s/\..*//' grufs >grufs2
$ sed 's/::.*//' grufs >grufs1
```

I can't believe that 'cut' would take hours. 100000 lines is actually not much.

---

### Post by Arndt on 2011-07-29
I just tried using 'cut', too. The 'sed' solution took 0.8 seconds; the 'cut' one took 0.04 seconds.

How did you imagine it would take hours?

---

### Post by cguy on 2011-07-29
> **Arndt said:**
> I just tried using 'cut', too. The 'sed' solution took 0.8 seconds; the 'cut' one took 0.04 seconds.

How did you imagine it would take hours?
0.04 seconds for processing 1 string, I suppose, which means over 1 hour to process 100,000 of them
(My strings are 50 to 100 characters long, btw)

Anyway, it'd take so much on my computer (Pentium 4, 2.8 Ghz, medium load) because each string must be generated, first, and then fed through a pipe (or a file) to the processing utility.

Last time I tried, the whole process took a little under a second per entry. Even using pre-generated strings, the chained 'cut'-s were visibly slow.


I ended up writing my own utility in C, using this (more efficient) algorithm:
- since there are two consecutive "::", I could jump over every second character and be sure that I'll land on one of the ":"
- once landed on a ":", I checked to see if it's the first one or the second one
- I put a null character in the first ":"'s place and printed my original string. The printing stopped where I had just placed the null character, of course
- I marked the first character after the old "::"
- afterwards I continued the scanning of the string, this time without skipping letters
- when I found the "." I put a null character in its place and printed the string to a file, starting from the marked position


Combined with an improved string generation method, I should see a significant improvement.
I shall try it all soon.

---

### Post by stchman on 2011-07-29
> **nvteighen said:**
> That's almost like saying that C is the way to go because it has strtok().

The best for this are Perl or the awk/sed/grep toolchain (ideal for shell scripts), not-so-closely followed by Python. Doing this with a Perl regexp is trivial, as shown below. My Perl skills are quite bad, though, and for sure there are much better ways to do this (chaining calls to split(), perhaps?)

```

#!/usr/bin/env perl

use strict;
use warnings;

sub split_my_string
{
    my $string = shift;

    if($string =~ /^(.*?)::(.*?)\.(?:.*?)$/)
    {
        return ($1, $2);
    }
    else
    {
        return ();
    }
}

my @splitted = 
    split_my_string "ABCDEF::QWERTY.some_string_or_a_number_after_the_dot";

print "$splitted[0]\n$splitted[1]\n";

```

OK.....  You succeeded in splitting the strings, but where's the file I/O?  Remember, the OP has an input file and two output files.

---

### Post by Vaphell on 2011-07-29
i just run this
```
for i in {0..100000}; do x="$i::QWERTY.$i"; x1=${x/::*/}; x2=${x/*::/}; x2=${x2/.*/}; echo $x1 $x2; done
```
it doesn't use any pipes and it finishes in 15 seconds on my amd e350 (dual core 1.6Ghz)

edit:
i generated file with dummy data (100k rows) and tested this
```
i=0; while read x; do (( i++ )); x1=${x/::*/}; x2=${x/*::/}; x2=${x2/.*/}; echo $i $x1 >> x1.txt; echo $i $x2 >> x2.txt; done < in.txt
```
17 secs

---

### Post by nvteighen on 2011-07-29
> **stchman said:**
> OK.....  You succeeded in splitting the strings, but where's the file I/O?  Remember, the OP has an input file and two output files.

Honestly, I left the file I/O to be written by the OP. I only wanted to show Perl's approach for that specific spot where it's stronger than whatever was suggested before my post.

After talking with a more seasoned Perl-hacker than I am (most people who use Perl are...), I have to recognize that my code is not the best Perl snippet that you'll find in this universe :P

---

### Post by Arndt on 2011-07-29
> **cguy said:**
> 0.04 seconds for processing 1 string, I suppose, which means over 1 hour to process 100,000 of them
(My strings are 50 to 100 characters long, btw)


For 100000, of course. Why don't you simply try it?

If each line takes one second for you, something else is using up the time somewhere.

---

### Post by stchman on 2011-07-29
Here is the full up program and the code is tested.

[PHP]
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;

/**
 *
 * @author BN
 */
public class FileIO {
    public static void main(String[] args) throws IOException {
        // create FileIO object and call the writeFiles method
        FileIO m = new FileIO();
        m.writeFiles();
    }
    
    public void writeFiles() throws IOException {
        // open your input file
        BufferedReader infile = new BufferedReader( new FileReader( System.getProperty( "user.home" ) + File.separator + "inputFile.txt" ) );

        // create your two output files
        BufferedWriter fileOne = new BufferedWriter( new FileWriter( System.getProperty( "user.home" ) + File.separator + "file1.txt" ) );
        BufferedWriter fileTwo = new BufferedWriter( new FileWriter( System.getProperty( "user.home" ) + File.separator + "file2.txt" ) );

        // loop until EOF
        while( infile.ready() == true ) {
            // split the string  
            String[] data = infile.readLine().trim().split( "::|\\." );
    
            // write the first and second token out to the file
            fileOne.write( data[ 0 ] + "\r\n" );
            fileTwo.write( data[ 1 ] + "\r\n" );
        }
        
        // close the file
        infile.close();
        fileOne.close();
        fileTwo.close();
    }
}
[/PHP]If this is overly complex, I'm sorry.

I ran this with an input file of > 100K lines and execution time of less than 0.05 seconds.

---

### Post by Arndt on 2011-07-29
> **Arndt said:**
> 

If each line takes one second for you, something else is using up the time somewhere.

It occurs to me that you maybe invoke 'cut' once for each line. That may explain the long times.

---

### Post by stchman on 2011-07-29
> **Bodsda said:**
> My python approach
 
```

#! /usr/bin/env python
 
lines = open("~/sourcefile", "r").readlines()
file1 = open("~/file1.txt", "w")
file2 = open("~/file2.txt", "w")
 
for i in lines:
    file1.write(i.split("::")[0] + "\r\n" )
    file2.write(i.split("::")[1].split(".")[0] )
 
file1.close()
file2.close()

```(code not tested)
Bodsda

Nice approach, I took the liberty of making your solution platform independent.  Only problem I see is that your approach appears to store the entire contents of the file in memory.

```

import os

lines = open( os.path.expanduser( "~" ) + os.sep + "inputFile.txt", "r" ).readlines()
file1 = open( os.path.expanduser( "~" ) + os.sep + "file1.txt", "w" )
file2 = open( os.path.expanduser( "~" ) + os.sep + "file2.txt", "w" )
 
for i in lines:
    file1.write( i.split( "::" )[0] + "\n" )
    file2.write( i.split( "::" )[1].split( "." )[0])
 
file1.close()
file2.close()

```

---

### Post by cguy on 2011-07-29
> **Arndt said:**
> It occurs to me that you maybe invoke 'cut' once for each line. That may explain the long times.
I do. And 3 times/line, like this:
echo "ABCDEF::QWERTY.oooo" | cut -d ':' -f 1 > file1.txt
echo "ABCDEF::QWERTY.oooo" | cut -d ':' -f 3 | cut -d '.' -f 1 > file2.txt
:oops:

How do you do it?

---

### Post by Barrucadu on 2011-07-29
I'm not sure about getting it down further, but you can immediately get it down to three times for the whole file like this:

```
cut -d ':' -f 1 > file1.txt < thefile
cut -d ':' -f 3 < thefile | cut -d '.' -f 1 > file2.txt
```

---

### Post by nmaster on 2011-07-29
> **Barrucadu said:**
> I'm not sure about getting it down further, but you can immediately get it down to three times for the whole file like this:

```
cut -d ':' -f 1 > file1.txt < thefile
cut -d ':' -f 3 < thefile | cut -d '.' -f 1 > file2.txt
```
good call.  i've been scratching my head wondering why the OP was having such a tough time ;)

---

### Post by cguy on 2011-07-29
> **Barrucadu said:**
> I'm not sure about getting it down further, but you can immediately get it down to three times for the whole file like this:

```
cut -d ':' -f 1 > file1.txt < thefile
cut -d ':' -f 3 < thefile | cut -d '.' -f 1 > file2.txt
```

Same thing! I just posted a working example by using that echo call instead of the I/O redirection.

---

### Post by Barrucadu on 2011-07-29
If you're doing the same thing, then you're not invoking cut three times for each line.

---

### Post by cguy on 2011-07-29
Could you elaborate how it works, then?

---

### Post by Barrucadu on 2011-07-29
Cut takes the entire file as input, and processes each line in turn, producing the output after each line has been processed. This is significantly faster than three times per line, as fork/exec (how the shell launches a new process) takes time.

---

### Post by cguy on 2011-07-29
Thanks!

---

