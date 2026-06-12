---
title: "Critique please"
date: 2009-02-03
forum: Programming Talk
---

### Post by Krupski on 2009-02-03
Hi all,

I am a (very) amateur programmer. All self taught, not one drop of formal programming instruction.

Anyway, I've been reading up on C programming conventions and techniques.

In most of the code I write (which is in assembler), I am fanatical about documentation. Virtually every line of code has a comment, because I can come back to an old program I wrote even a month ago and wonder "what the heck was on my mind?". The comments help immensely.

Anyway, I've been getting into C programming and my big concern is programming "style". Not to impress a C guru, but for understandability and readability in the future.

Everyone seems to have "their idea" of proper coding style, and I want to follow "proper" style, but with an emphasis on readability and understandability.

So, with that introduction, please take a look at the attached piece of code and tell me what you think about the comments, indentation, coding style, anything you can think of.

Don't be shy to criticize... I WANT to know what's right and wrong.

Thanks in advance to all!

```

//////////////////////////////////////////////////////////////////
// cpus.c - by roger a. krupski (krupski@acsu.buffalo.edu)
// last update tuesday, 03 feb 2009
//////////////////////////////////////////////////////////////////
// purpose and description: this program opens files found
// in the "/sys/devices/system/cpu" directory and looks for
// the "cpuinfo_cur_freq" file for each processor. each file
// contains the current frequency for it's cpu in kilohertz. we
// read this file, then convert the number to hertz by dividing
// the number by 1e3 (1000). next we run the file through
// a loop that checks the value, divides by 1e3 (1000) and
// counts each iteration through the loop so that we get
// two things: (1) the number in the range of 1 to 9 and
// (2) the "1e3" multiplier which tells us if it's kilohertz,
// megahertz, etc...
// we add all the numbers we find together, then divide by
// how many we found to obtain the average. finally we print
// the average number and a string which tells which multiplier
// to use (i.e. kilohertz, megahertz, etc..)
// we look for a maximum of 16 files (should be enough) :-)
//////////////////////////////////////////////////////////////////
// note that this program does not actually measure the cpu
// frequency, it merely reports the contents of the acpi-cpufreq
// files which theoretically contain vaild data.
//////////////////////////////////////////////////////////////////
// this code is public domain feel free to download it
// and use it for any purpose you like.
//////////////////////////////////////////////////////////////////

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main(void)
{
    FILE *infile;
    char buffer[BUFSIZ];
    int c, mult;
    float f = 0, n = 0;
    char *plural[16]={
    // array for plural (i.e. "cpu" or "cpus")
    "",  "",  "s", "s", "s", "s", "s", "s",
    "s", "s", "s", "s", "s", "s", "s", "s" };

    // prefix for hertz, kilohertz, megahertz, gigahertz
    // terahertz, petahertz and exahertz. nuts, huh? :-)
    char *hertz[7]={ "", "k", "M", "G", "T", "P", "E" };

    for((c = 0); (c < 16); (c++)) {
        // generate filename to look for if acpi-cpufreq is used
        sprintf(buffer, "/sys/devices/system/cpu/cpu%d/cpufreq/cpuinfo_cur_freq", c);
        infile = fopen(buffer, "r"); /* try to open the file, readonly */

        // if unable to open the first file, then probably acpi-cpufreq
        // isn't loaded (or isn't working)
        if((infile == NULL) && (c == 0)) {
            fprintf(stderr, "cpus: failed to find any cpu info\n");
            fflush(stderr);
            return(-1); // exit w/error
        }

        if(infile != NULL) {
            fgets(buffer, BUFSIZ, infile); // read the file into buffer
            fclose(infile); // close the file
            f += (atof(buffer) * 1e3); // convert freq to hertz, then add it to "f"
            (n++); // count this one
        }
    }

    (f /= n); // average f in hertz
    (mult = 0); // initialize multiplier (index into "hertz" array)

    while (f >= 1e3) { // derive multiplier for hertz, kilohertz, etc..
      (f /= 1e3);
      (mult++);
    }

    if(mult > 6) { // prevent segfault if f is a wacked out number
        fprintf(stderr, "Frequency out of range!\n");
        fflush(stderr);
        return(-1); // exit w/error
    }

    sprintf(buffer, "%f", n); // convert float to string
    sscanf(buffer, "%d", &c); // convert string to int

    // send results to stdout
    fprintf(stdout, "Average of %d CPU core%s: %.3f %sHz.\n", c, plural[c], f, hertz[mult]);
    fflush(stdout);
    return(0); // exit no error
}

```

---

### Post by wmcbrine on 2009-02-03
Some weird use of parens there, e.g. around "n++" as a single statement. You don't need them with "return", either. And personally I'd insert spaces after "if" and "for".

This bit is silly:

```

    sprintf(buffer, "%f", n); // convert float to string
    sscanf(buffer, "%d", &c); // convert string to int

```

You could just do this:

```

    c = (int)n;

```

Really though, n should've been an int in the first place.

No comment on the specific comments here, but in general you should find that C needs less commenting than assembly does.

As I look at it... I'd also use printf(...) instead of fprintf(stdout, ...). That last fflush() is superfluous (the buffer *will* be flushed, since the program is closing), and all the fflush(stderr) calls are superfluous as well (due to the nature of stderr -- it's unbuffered). The "plural" array is a bit silly as well, hardwiring mostly duplicate values for up to 16 cores -- I'd remove the array, and replace "plural[c]" in the last printf with something like '(c > 1) ? "s" : ""'.

Oh, and you're using mostly C++-style comments (the double slash) rather than C-style (slash, asterisk). That's valid in C99, and in many compilers' extensions to C89, but not in pure C89. And just personally, I don't like the use of 1e3 in place of 1000.

So, to combine most of what I've said, and leaving out the opening comment block:

```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main(void)
{
    FILE *infile;
    char buffer[BUFSIZ];
    int c, n, mult;
    float f = 0;

    // prefix for hertz, kilohertz, megahertz, gigahertz
    // terahertz, petahertz and exahertz. nuts, huh? :-)
    char *hertz[7] = {"", "k", "M", "G", "T", "P", "E"};

    for (c = 0, n = 0; c < 16; c++) {
        // generate filename to look for if acpi-cpufreq is used
        sprintf(buffer, "/sys/devices/system/cpu/cpu%d/cpufreq/cpuinfo_cur_freq", c);
        infile = fopen(buffer, "r"); /* try to open the file, readonly */

        // if unable to open the first file, then probably acpi-cpufreq
        // isn't loaded (or isn't working)
        if (infile == NULL && c == 0) {
            fprintf(stderr, "cpus: failed to find any cpu info\n");
            return -1; // exit w/error
        }

        if (infile != NULL) {
            fgets(buffer, BUFSIZ, infile); // read the file into buffer
            fclose(infile); // close the file
            f += atof(buffer) * 1000; // convert freq to hertz, then add it to "f"
            n++; // count this one
        }
    }

    f /= n; // average f in hertz
    mult = 0; // initialize multiplier (index into "hertz" array)

    while (f >= 1000) { // derive multiplier for hertz, kilohertz, etc..
        f /= 1000;
        mult++;
    }

    if (mult > 6) { // prevent segfault if f is a wacked out number
        fprintf(stderr, "Frequency out of range!\n");
        return -1; // exit w/error
    }

    // send results to stdout
    printf("Average of %d CPU core%s: %.3f %sHz.\n", n, (n > 1) ? "s" : "", f, hertz[mult]);
    return 0; // exit no error
}

```

---

### Post by cmay on 2009-02-03
a while ago i started to learn c on my own. i never comment as good as this and when i come back to my notes sometime later i am sometimes lost. this is great documented but as far as being c code it is to the best of knowledge only newer compilers that supports delphi /c++ style comments which you use. i would use the ordinary c 
[php]/*i am a c comment*/ [/php] style comments at all times if it is c i am writing and reserve the c++ [php]// i am a c++[/php] comment style for c++. but other than that its great. 
btw , i am very new to programming so i am not even the right one to give any critique so feel free to just ignore me :)

---

### Post by Krupski on 2009-02-03
> **wmcbrine said:**
> This bit is silly:

```

    sprintf(buffer, "%f", n); // convert float to string
    sscanf(buffer, "%d", &c); // convert string to int

```

You could just do this:

```

    c = (int)n;

```

Really though, n should've been an int in the first place.


Thanks for the comments. I didn't know about the (int)n thing... that was the only way I knew how to make an int out of a float.

And, I made n a float because it's used in the (f /= n); averaging calculation... so I divide a float by a float to avoid a warning.

[COLOR="Red"]**(edit to add): I found that dividing a float by an int did NOT result in a warning under GCC. However, LCC-Win32 complains with a "Possible loss of precision" warning.**[/COLOR]

As far as the parentheses, I have a book called "Practical C Programming" by O'Reilley and one of their "rules of thumb" is "put parentheses around everything" (mostly to insure that things are evaluated in the DESIRED order rather than depending on standard order of operations).

I just got into the habit of putting EVERYTHING in parentheses.

For "fprintf", I like to use it so that I can either use "stderr", "stdout" or a file descriptor to send my output to and not have to change any other code.

Sticking "fflush()" after everything is, I know, superfluous, but I maintain that habit after I solved a VERY annoying problem a long time ago where I wrote a program that printed the "marching stars" thing (i.e. [*******]" to show progress and, of course, the individual stars didn't print, ALL of them printed at the end of the program. That's where I learned about needing "fflush()" and I now use it just out of habit because (1) It can't hurt and (2) it will avoid accidentally running into another problem like I had in the past.

For the "plural" thing... thanks for the '(c > 1) ? "s" : ""' idea... that's a lot nicer than my method, and it also avoids the need to check for the unlikely event of an out of range subscript (which would cause a segfault). Wonderful idea!

Concerning comments, the /* this is a comment */ style is SUCH a pain to use and when commenting out pieces of code for debugging, it causes all kinds of grief because more things end up commented out than I expect. The "//" method is so much nicer!  :)

Concerning 1e3 vs 1000... yeah I guess 1000 makes more sense at a glance. I'm an engineer and seeing "1e6" or "1e3" registers in my mind as quickly as "1000000" or "1000" does... but probably 1000 would be a better choice.  How about if I use 0x3E8 instead?  :D

Oh well... thanks so much for the critique and the ideas. You've helped me a bunch! Thanks again! [IMG]http://www.gunsnet.net/forums/images/smilies/xyxthumbs.gif[/IMG]

-- Roger

---

### Post by Krupski on 2009-02-03
> **cmay said:**
> a while ago i started to learn c on my own. i never comment as good as this and when i come back to my notes sometime later i am sometimes lost. this is great documented but as far as being c code it is to the best of knowledge only newer compilers that supports delphi /c++ style comments which you use. i would use the ordinary c 
[php]/*i am a c comment*/ [/php] style comments at all times if it is c i am writing and reserve the c++ [php]// i am a c++[/php] comment style for c++. but other than that its great. 
btw , i am very new to programming so i am not even the right one to give any critique so feel free to just ignore me :)

I've read (and discovered on my own) that the more comments, the better. I've looked at some of my very old code (before I commented everything) and asked "what on EARTH was I doing there?"

If I couldn't figure out my OWN code, how is someone else supposed to?

That's why I comment everything I can, and I make sure to use descriptive comments.

Lots of people do things like (n = 10); // set n to 10

A comment like that is "duh... no kidding!"

So, I make full sentence comments like:

(n = 10); // initialize the loop counter so that we read 10 elements

...or something like that.

Concerning comments, the only C compilers I use are GCC/G++ in Linux and LCC-Win32 in Windows. Both are C++ compilers and accept the "//" comment syntax.

I try mostly to write code in ANSI, or at least write code that will compile equally well in either Windows or Linux.

Since LCC-Win32 has a nice IDE and debugger, I like to write my code under LCC, then copy it over to Linux. Most of the time, it compiles 100% without any changes.

I don't write "apps" or windowed stuff. All my code is for utilities which read files, modify files, translate files, whatever. In other words, all my stuff is "console mode" code.

I come from the good old(?) days of MS-DOS and I'm comfortable at the command line (actually more comfortable than in a GUI).

I've also done a lot of development with the old operating system from Microware (yes, MicroWARE, not Microsoft) called "OS-9".

It was a multi tasking, multi user UNIX like operating system which ran on many different platforms, including my favorite, the Radio Shack TRS-80 Color Computer 3. It ran fine in 128K of memory and was swimming in 512K (yes, K, not MEG or GIG).

It's too bad that GOOD operating systems like OS-9 or UNIX (or others) didn't end up "under the hood" of Windows.

I really hope and pray that someday Linux reaches critical mass and overtakes Microsoft... not that I hate Microsoft (well I do but let's not go there!)... but because I want to use a PC that's functional and stable and runs like a jet fighter without needing the latest and greatest hardware.

Oh well... enough dreaming... :D


-- Roger

---

### Post by lloyd_b on 2009-02-03
I would suggest using "exit()" rather than "return" when exiting a program.  While in "main()" the two are synonymous, in any other function they are *not*.

When exiting with error codes, it's good practice to use different errors codes for different errors.  Make "-1" a "Cannot open cpu0 info file", and "-2" a "frequency out of range".  While this is trivial for *this* program, on more complex projects having specific error codes for different problems is very useful.

Why are you initializing "mult" in the code, rather than in the declaration, as you do for "f" and "n"?

I question the need to convert the frequency into Hertz - can CPUs scale down that far?  It would be simpler to just do your calculations in kHz instead, and save yourself some multiplications (even if CPUs *can* scale down that far, I doubt you'll ever see a Linux system actually running at an average of less than 1kHz :)).

Your "while" loop to determine the proper prefix *could* be redone as a single-line "for" loop:```
for ( ; f >= 1e3; f /= 1000, mult++);
``` (I won't say this is *better*, but it does reduce the number of lines of code).

Lloyd B.

---

### Post by cmay on 2009-02-03
> . I've looked at some of my very old code (before I commented everything) and asked "what on EARTH was I doing there?"
me too :)

---

### Post by wmcbrine on 2009-02-03
> **Krupski said:**
> Thanks for the comments. I didn't know about the (int)n thing... that was the only way I knew how to make an int out of a float.Yeah, I figured. :)

> *And, I made n a float because it's used in the (f /= n); averaging calculation... so I divide a float by a float to avoid a warning.*I don't get a warning from gcc with n as an int. Does lcc complain?

> *... "put parentheses around everything" (mostly to insure that things are evaluated in the DESIRED order rather than depending on standard order of operations).*I hope you can see how this doesn't apply to a single-expression statement. :)

> *That's where I learned about needing "fflush()" and I now use it just out of habit because (1) It can't hurt*You've mentioned readability and understandability as goals. When I saw those fflush()es, my first thought was "Why is he doing an fflush() here?". So then I had to parse through the whole thing to figure out that the answer is "no reason". That's not a big deal here, but it could be in a longer program. So, in that sense, it could hurt.

---

### Post by Krupski on 2009-02-03
> **wmcbrine said:**
> I don't get a warning from gcc with n as an int. Does lcc complain?

Yes. It issues a warning "Possible loss of precision".

---

### Post by Krupski on 2009-02-03
> **wmcbrine said:**
> I hope you can see how this [parentheses around everything] doesn't apply to a single-expression statement. :)

Yes I know :)

As I said, it's just a habit.

---

### Post by Krupski on 2009-02-04
> **lloyd_b said:**
> I would suggest using "exit()" rather than "return" when exiting a program.  While in "main()" the two are synonymous, in any other function they are *not*.

Yeah... I screwed up there.

Please tell me if I'm right about these assumptions:

(1) exit() is meant to end and exit the entire program (i.e. "main()")

(2) return() is meant to return data to a caller

(3) return() can return any data type to the caller

(4) return() can return more than 1 data to the caller [COLOR="Red"]**<--oops this is wrong!**[/COLOR]

(5) data returned to a caller via "return()" must be global or else they "go away".


Thanks again for all your help!

-- Roger

---

### Post by wmcbrine on 2009-02-04
First, I want to reiterate that it's return, not return(). It's not a function.

Values passed by return don't need to be global. What you can't return is a pointer to a local variable. For instance, this is fine:

```

int count(void)
{
    int i = 27;
    return i;
}

```

This is not:

```

char *greet(void)
{
    char hi[] = "hello";
    return hi;
}

```

---

### Post by Greyed on 2009-02-04
> **Krupski said:**
> So, with that introduction, please take a look at the attached piece of code and tell me what you think about the comments, indentation, coding style, anything you can think of.

Only two things I can think of is first, pick a brace style and stick to it.  You're opening main with the brace on the next line but your ifs, fors and such have the brace on the same line.

Second, comment a lot less.  A **lot** less.  In assembler you're writing more for the machine than the human.  As you move up in languages you're writing more for the human and less for the machine.  As such you should focus on writing the code in a way to convey your meaning to the human as well as the machine.  Use meaningful variable names.  Also obvious things, don't comment.  For example, "return(0) // exit no error".  Forgiving that it should have been something else we, as programmers, should know by convention that returning 0 means no error.  If not, we'll learn quickly enough.  I think a full 4/5ths of your comments aren't needed.

Now, I know that early programming classes tell us to comment, comment, comment.  And that's great for early programming classes because newbie programmers rarely comment enough.  However there is a balance.  You can comment too much.  That balance is tipped when you consider maintainability of the code in question.  Sure, commenting every line may make it easier to noodle out what's happening 6-12 months down the line.  But when you comment too much it means you're doubling your work load later on.  You have to update the code and the comments.  If you update the code and not the comments then you're in a situation which is worse than having no comments.  That being comments which are misleading.

So comment what you need to comment.  Describe what the function is supposed to do and let the code speak for itself.  If there is no way to maintain both the readability and the code's functionality; IE, you need to sacrifice readability for some other reason, then use a comment to clarify.

---

### Post by maximinus_uk on 2009-02-04
> **Greyed said:**
> ....comment a lot less.  A **lot** less.  In assembler you're writing more for the machine than the human.  As you move up in languages you're writing more for the human and less for the machine.  As such you should focus on writing the code in a way to convey your meaning to the human as well as the machine.

Agree, but more importantly DON'T write a comment that justs re-iterates what the code says. For example, in assembly you might have:

```
inc    bx        ;increment index counter
```

Whereas in C:

```
counter+=1;      // increment counter
```

This last comment is not needed, but it's amazing how many coders I've seen doing this sort of thing.

By choosing good names for variables and functions you can cut down a lot on comments.

Personally I tend to comment on almost every line for assembly, on every 4-5 lines in Python and perhaps only for every function in Lisp :D

---

### Post by nvteighen on 2009-02-04
The commenting style I use is the following: Start each function with a description of what it does, what arguments it expects and what it returns (describing all possible return values). That clarifies stuff a lot, as it prepares the reader to what the code is supposed to do. Then, I just comment those places where it might not be clear what I'm doing with respect to the function's goal (some "clever trick")...

---

### Post by wmcbrine on 2009-02-04
> **Greyed said:**
> You're opening main with the brace on the next line but your ifs, fors and such have the brace on the same line.IIRC, though, that's standard K&R-style indentation. Certainly it's what you get from "indent -kr". I wouldn't argue with indent. :)

---

### Post by Krupski on 2009-02-04
> **maximinus_uk said:**
> Agree, but more importantly DON'T write a comment that justs re-iterates what the code says. For example, in assembly you might have:

```
inc    bx        ;increment index counter
```

Whereas in C:

```
counter+=1;      // increment counter
```

This last comment is not needed, but it's amazing how many coders I've seen doing this sort of thing.

By choosing good names for variables and functions you can cut down a lot on comments.

Personally I tend to comment on almost every line for assembly, on every 4-5 lines in Python and perhaps only for every function in Lisp :D

I'm a commenting maniac in assembler!  :) I comment every line. Here's a tiny snippet of a program:

```

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; legal character found, write it to buffer
; legal character is either a space or 0 thru 9
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

char    ldx     #buffer         ;point to buffer
        ldab    curpos          ;get cursor position
        cmpb    #promptlen      ;at end?
        bhs     chrout          ;at end, can't do anything

        abx                     ;x points to current char
        staa    0,x             ;write char to buffer

        incb                    ;move fwd 1 position
        stab    curpos          ;update cursor position

        bsr     output          ;echo char to term

chrout  bra     main            ;return to main loop

```

I guess I'll have to cut back on the C code comments a little though... :)

-- Roger

---

### Post by Krupski on 2009-02-04
> **wmcbrine said:**
> IIRC, though, that's standard K&R-style indentation. Certainly it's what you get from "indent -kr". I wouldn't argue with indent. :)

I know I should probably do:

int
main (void) {
....
....
}

...but it just looks so WEIRD!  :)

---

### Post by OrangeCrate on 2009-02-04
> **Krupski said:**
> Hi all,

**I am a (very) amateur programmer. All self taught, not one drop of formal programming instruction.**

<snip>

```

//////////////////////////////////////////////////////////////////
**// cpus.c - by roger a. krupski (krupski@acsu.buffalo.edu)**
// last update tuesday, 03 feb 2009

<snip>


```

acsu.buffalo.edu = State University of New York at Buffalo

Are you sure you're not asking these kind people to do your homework for you? I believe there's a policy here on the forums disallowing that.

---

### Post by Krupski on 2009-02-04
> **OrangeCrate said:**
> acsu.buffalo.edu = State University of New York at Buffalo

Are you sure you're not asking these kind people to do your homework for you? I believe there's a policy here on the forums disallowing that.

Nope. I'm not a student. I'm staff. My b'day is 05 January 1957 and I'm 52.

Check it out if you doubt me: [[COLOR="Blue"]**LINK**[/COLOR]]("http://www.buffalo.edu/directory/find-people-detail-page.html?uid=krupski&query=krupski")

When I had homework, the hottest high tech I owned was a 4 function calculator that ran for about 15 minutes on a 9 volt battery.

Computers were multi-million dollar machines that only .gov and .edu owned and were connected to with 134.5 baud Anderson Jacobsen terminals (or KSR-33 teletypes at 110 baud).

No offense taken though... if I saw a person asking questions with an "edu" email, I'd be suspicious too.

-- Roger

---

### Post by OrangeCrate on 2009-02-04
> **Krupski said:**
> Nope. I'm not a student. I'm staff. My b'day is 05 January 1957 and I'm 52.

Check it out if you doubt me: [[COLOR="Blue"]**LINK**[/COLOR]]("http://www.buffalo.edu/directory/find-people-detail-page.html?uid=krupski&query=krupski")

When I had homework, the hottest high tech I owned was a 4 function calculator that ran for about 15 minutes on a 9 volt battery.

Computers were multi-million dollar machines that only .gov and .edu owned and were connected to with 134.5 baud Anderson Jacobsen terminals (or KSR-33 teletypes at 110 baud).

**No offense taken though... if I saw a person asking questions with an "edu" email, I'd be suspicious too.**

-- Roger

My apologies.

The kids usually get run off pretty quick, when they try that, and I guess I just happened to notice the address, and beat the others to the punch, that this isn't the place to have someone do their homework.

I'm old enough, that the two required computer courses for my MBA, were covering Fortran and Cobal. I got through both of those, by the skin of my teeth.

Any tips on my golf game?

:)

---

### Post by Krupski on 2009-02-04
> **OrangeCrate said:**
> My apologies.

The kids usually get run off pretty quick, when they try that, and I guess I just happened to notice the address, and beat the others to the punch, that this isn't the place to have someone do their homework.

I'm old enough, that the two required computer courses for my MBA, were covering Fortran and Cobal. I got through both of those, by the skin of my teeth.

Any tips on my golf game?

:)

No apology necessary. I would have asked the same thing of a person asking a bunch of questions with an .edu email address.

In school, I wrote Fortran programs... in batch (punch cards!). It was a real treat to be able to sit down at a terminal and use the mainframe 200 miles away at 110 baud. No cards... just keypresses (and lots of syntax errors!)

There was no monitor. The display was paper. You can imagine that we went through LOTS of paper!

As an EE student, we didn't do much with computers... simply because there weren't any yet. Control systems were analog. The closest we got to digital logic was NAND, NOR, AND amd OR gates (as well as having to design a 2 input XOR gate on paper!)

Graphs were made with pencil and paper. Curves were fit with a French curve, not a computer.

I didn't learn computers or programming in school simply because we didn't HAVE computers (at least "personal" computers) back then.

As uber-cool high tech devices though, I've always liked them and used them since a friend of mine and I BUILT our own computer with 256 bytes of SRAM and toggle switches for address and data input.

I then graduated to the Cromemco Z-80, the Radio Shack COCO-II, COCO-III and finally a 386SX PC with a WHOPPING 4 megabytes of ram on it.

Now I run an Intel Core 2 Quad machine at 2.66 GHz. with 8 gigs of ram.

How things have changed...

-- Roger

(p.s. sorry I don't know beans about golf!)  :)

---

### Post by lloyd_b on 2009-02-06
> **Krupski said:**
> Yeah... I screwed up there.

Please tell me if I'm right about these assumptions:

(1) exit() is meant to end and exit the entire program (i.e. "main()")

(2) return() is meant to return data to a caller

(3) return() can return any data type to the caller

(4) return() can return more than 1 data to the caller [COLOR="Red"]**<--oops this is wrong!**[/COLOR]

(5) data returned to a caller via "return()" must be global or else they "go away".


Thanks again for all your help!

-- Roger

#1 is correct, but an additional note should be added - the value will be ANDed against 0x0377 before being passed to the calling program, so the range is very limited.

#2 is absolutely correct, though another poster's comment is correct - you should use "return 13", rather than "return(13)".  "return" is NOT a function.

#3 and #5 relate - what is actually happening is that the value you're giving to the "return" statement is being pushed onto the stack, and passed back to the caller that way.  So you *can* return any type of value, but *should* avoid returning some types. 

A couple of examples of "don't do this":
1.  Don't return structure ("struct ...") constructs via a "return" if you can possibly help it.  Imagine the overhead involved if you're pushing a 5kB structure onto the stack, and then popping it off again when the function returns to the caller...

2.  Do not return pointers to local variables within the function, as the system may reclaim this memory for other use once the function returns.  

In both of the above examples, a common solution is to "malloc()" a block of memory, copy the data to be returned into that block, and then return a pointer to that block of memory.  Just don't forget to "free()" it when you're done with it, else you'll have a classic "memory leak".

As for #4, you *can* "return" multiple things indirectly, by "return"ing a struct, but for reasons stated above this should probably be avoided.

And one side note: I don't see *any* problem with your braces style.  It's standard K&R style to put the open brace on the same line as the if/while/for/etc, but to put the open brace for a *function* on a line following the function.  Note that this is the braces style used by almost all of the Linux kernel code.

(FYI: in the pre-ANSI days, C commonly used a somewhat different method for declaring the types of function parameters:
```
int myfunc(a, b, c)
    int a;
    char b;
    float c;
{
...
}
```
I believe this is the origin of the "functions should have their open brace on a line following the function declaration" convention.  Even though this syntax is obsolete, I would stick with the K&R style, since it's used by so many programmers.)

Lloyd B.

---

### Post by Mr.Macdonald on 2009-02-06
One thing is don't comment that much, it just annoying and pointless, I doubt you plan to release this program so don't worry about the license and goals of the project. I didn't even look at your code because you wrote a page of comments!

---

### Post by Krupski on 2009-02-06
> **lloyd_b said:**
> #1 is correct, but an additional note should be added - the value will be ANDed against 0x0377 before being passed to the calling program, so the range is very limited.

#2 is absolutely correct, though another poster's comment is correct - you should use "return 13", rather than "return(13)".  "return" is NOT a function.

#3 and #5 relate - what is actually happening is that the value you're giving to the "return" statement is being pushed onto the stack, and passed back to the caller that way.  So you *can* return any type of value, but *should* avoid returning some types. 

A couple of examples of "don't do this":
1.  Don't return structure ("struct ...") constructs via a "return" if you can possibly help it.  Imagine the overhead involved if you're pushing a 5kB structure onto the stack, and then popping it off again when the function returns to the caller...

2.  Do not return pointers to local variables within the function, as the system may reclaim this memory for other use once the function returns.  

In both of the above examples, a common solution is to "malloc()" a block of memory, copy the data to be returned into that block, and then return a pointer to that block of memory.  Just don't forget to "free()" it when you're done with it, else you'll have a classic "memory leak".

As for #4, you *can* "return" multiple things indirectly, by "return"ing a struct, but for reasons stated above this should probably be avoided.

And one side note: I don't see *any* problem with your braces style.  It's standard K&R style to put the open brace on the same line as the if/while/for/etc, but to put the open brace for a *function* on a line following the function.  Note that this is the braces style used by almost all of the Linux kernel code.

(FYI: in the pre-ANSI days, C commonly used a somewhat different method for declaring the types of function parameters:
```
int myfunc(a, b, c)
    int a;
    char b;
    float c;
{
...
}
```
I believe this is the origin of the "functions should have their open brace on a line following the function declaration" convention.  Even though this syntax is obsolete, I would stick with the K&R style, since it's used by so many programmers.)

Lloyd B.

Thanks for the info! Thinking about it, I finally realized the difference between "exit" and "return". I feel stupid. :)

I very rarely return values from functions that I write anyway (via the return(); function). I usually declare some public variables and just put the data into them (because I usually have to return more than one value anyway).

I do braces the way I do because it makes debugging easier. For example, if I do this:

```

if(answer != 0) {
    fprintf(stdout, "Something went wrong!\n");
    fflush(stdout);
}

```

I can temporarily disable that code with simple comment marks:

```

if(answer != 0) {
[COLOR="Red"]**//**[/COLOR]    fprintf(stdout, "Something went wrong!\n");
[COLOR="Red"]**//**[/COLOR]    fflush(stdout);
}

```

I also like to use "fprintf" rather than "printf" because then I can just replace "stdout" with a file pointer and write to a file with minimal changes (i.e. I'm lazy!)  :)

Well thank again for the comments. I'm learning slowly but surely. Too bad they didn't have computer science classes when I was in school (heck we didn't even have COMPUTERS or decent CALCULATORS!).

Never too late to learn though.

Thanks again!

-- Roger

---

### Post by Krupski on 2009-02-06
> **Mr.Macdonald said:**
> One thing is don't comment that much, it just annoying and pointless, I doubt you plan to release this program so don't worry about the license and goals of the project. I didn't even look at your code because you wrote a page of comments!

That's something I picked up from the book "Practical C Programming" by O'Reilley. They suggest a big comment block at the beginning of a program that states the basic goals and function of the code. It's supposed to help the programmer (or a different programmer) get a better feel of what's going on (in addition to lots of comments spread all over).

It seems like a good idea... as long as the comments actually help.

For example, writing "x = 10;" then commenting "set x to 10" is totally worthless, but "x = 10; // initialize scan index" may help a lot.

I give lots of credence to the things written in that book because they make lots of sense, AND whenever I follow their examples, my problems seem to go away (or at least diminish). :)

All in all, I think too many comments are better than not enough comments. They don't make the executable any larger and they *may* help a future programmer use or modify the code more easily.

I also do a LOT of Motorola 68HC11 and MC6809 assembler programming. In assembler, virtually EVERY line needs a comment. Otherwise, I'll be asking myself in a week "what did I do the LDD #$FE00 for?" :)

Oh well, thanks for your comments and input!

-- Roger

(edit to add): The big block at the beginning of my source was not a "license", but (hopefully) a description of what the code does and, in fact, the code was marked as "public domain".

---

### Post by wmcbrine on 2009-02-06
> **Krupski said:**
> I very rarely return values from functions that I write anyway (via the return(); function).**return** is not a function. Come on, say it with me now.

> *I usually declare some public variables and just put the data into them (because I usually have to return more than one value anyway).*There's another way to handle that, which you'll see used quite often, including in the standard library:

```

int somefunc(int *ret_a, char *ret_b)
{
    *ret_a = 123;
    strcpy(ret_b, "hello");

    return 456;
}

```

This function returns three values -- one on the stack, and two via pointers.

---

### Post by pp. on 2009-02-07
> **Krupski said:**
> For example, writing "x = 10;" then commenting "set x to 10" is totally worthless, but "x = 10; // initialize scan index" may help a lot.

The statement "x = 10" has at least two problems:

The variable probably shouldn't be called "x". The name should be indicative of the purpose, such as "characterBeingInspected".

The statement probably should not use a literal value. Why is the value "10" used? Is that an arbitrary limit, an intrinsic property of the problem being solved, or a guessed value? A named constant would be helpful in most cases, such as "numberOfCharactersToInspect".

Of course, if it was common knowledge what the "x" stands for in your context, and if any other value than "10" would be noteworthy or eyebrow-raising, then "x = 10" would be just fine.

---

### Post by nvteighen on 2009-02-07
> **lloyd_b said:**
> 
A couple of examples of "don't do this":
1.  Don't return structure ("struct ...") constructs via a "return" if you can possibly help it.  Imagine the overhead involved if you're pushing a 5kB structure onto the stack, and then popping it off again when the function returns to the caller...


Hm... it depends on what you're doing. Usually, when you return a structure is when you're doing C OOP and return a pointer to a new structure allocated through malloc(). For example, the fopen() function returns a (FILE *), which is a pointer to a data structure. In that case, there's no overhead as pointers are all of the same size.

But returning a structure isn't totally bad. It may be inefficient in some circumstances, but it's definetely not something we could consider a "mistake" neither a "bad practice" (such as non-constant global variables).

---

### Post by Krupski on 2009-02-07
> **wmcbrine said:**
> **return** is not a function. Come on, say it with me now.


Yes... I know. I wrote it as "return()" because return CAN return a number back to the calling function.

In fact, it says at "http://www.acm.uiuc.edu/webmonkeys/book/c_guide/" that "Using the return statement without an expression creates an undefined result."

So, I always stick a number into it, even if it's just zero.

It seems like programming is similar to religion... everyone has their own idea of how things "must" be.  :)

Thanks for the reply.

-- Roger

---

### Post by Krupski on 2009-02-07
> **pp. said:**
> The statement "x = 10" has at least two problems:


I just used it as an example... the first thing that came to mind. It could have been the infamous "i" or it could have been something cool like "buffer_index" bu since it was just an example, I chose "x".  :)

---

### Post by Krupski on 2009-02-07
> **wmcbrine said:**
> 
```

int somefunc(int *ret_a, char *ret_b)
{
    *ret_a = 123;
    strcpy(ret_b, "hello");

    return 456;
}

```

This function returns three values -- one on the stack, and two via pointers.

Now THIS is really cool! I see what you're doing (I think).

Obviously(?), "456" is returned by the function itself while the other two vars are "inside" the function somehow.

Please clarify for me... I'll use your exact example... am I doing it right?


```

int somefunc(int *ret_a, char *ret_b); // declare sub function

int main(void)
{
    int z; // where we put return values
    int a; //
    char b; //

    z = somefunc(a, b); // call function

    fprintf(stdout, "somefunc returned: a=%d, b=%s, z=%d\n", a, b, z);
    fflush(stdout);

    exit (0); // return, no error
}

int somefunc(int *ret_a, char *ret_b)
{
    *ret_a = 123;
    strcpy(ret_b, "hello");

    return 456;
}

```

Result on TTY:

somefunc returned: a=123, b=hello, z=456

Am I right?

Thanks!

-- Roger

(p.s. sorry I'm not being a lazy a--, I'm just at a Windows computer now and I can't test the code in a compiler).

---

### Post by Krupski on 2009-02-07
> **wmcbrine said:**
> This function returns three values -- one on the stack, and two via pointers.

OK! I just got a hold of a machine with Linux on it and tested the code. There were a few minor errors, but it's all fixed now. Here's what I have:


```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int somefunc(int *ret_a, char *ret_b); // declare sub function

int main(void)
{
    int z = 0; // where we put return values
    int a = 0;
    char b[BUFSIZ] = "";

    z = somefunc(&a, b); // call function

    fprintf(stdout, "somefunc returned: a=%d, b=%s, z=%d\n", a, b, z);
    fflush(stdout);

    exit (0); // return, no error
}

int somefunc(int *ret_a, char *ret_b)
{
    *ret_a = 123;
    strcpy(ret_b, "hello");

    return 456;
}

```

...and it outputs: "somefunc returned: a=123, b=hello, z=456" Yay!

I had to pre-initialize the variables so that they wouldn't produce junk if the sub function didn't set them (yeah I always think "what if").

Another problem was that you had "b" declared as just a char (with no room for 5 characters). So, the string copy of "hello" to the single byte char overwrote other stuff and made the program output gibberish.

Best thing is, I now know how to easily and reliably pass data to a sub function which will be VERY useful to me.

One more question if I may... how would I pass data TO a sub function?

I'll want the sub function to take in data, operate on it and then return the results.

If I set "a" and "b" first, THEN call the sub function, will that data be available in "*ret_a" and "*ret_b" as long as I don't change them?

Thanks again for the help... this one was a real winner for me!

-- Roger

---

### Post by wmcbrine on 2009-02-07
> **Krupski said:**
> Yes... I know. I wrote it as "return()"I was more concerned with the fact that you called it "the return() **function**" than the use of parentheses. It's not a function, and that's important. (The parens are merely unnecessary.)

> *In fact, it says at "http://www.acm.uiuc.edu/webmonkeys/book/c_guide/" that "Using the return statement without an expression creates an undefined result."*With a function that's not declared to return void, perhaps. A bare "return;" in a void function is certainly defined. Then again, there's no reason to use it in a void function, except to return early.

> *Obviously(?), "456" is returned by the function itself while the other two vars are "inside" the function somehow.*Eh, not quite. What I'm using there are pointers... don't tell me you haven't come across pointers yet? Pointers are really important. They're also a big stumbling block for a lot of people; but they shouldn't be for you, since you're coming from an asm background. Basically, using a pointer is like doing register indirect addressing. (BTW, if you haven't done it yet, you should try the "compile to assembly" mode of your compiler. That will give you an assembly-language listing that you can compare to the original. In gcc, it's "-S".)

The example should look more like this:

```

int somefunc(int *ret_a, char *ret_b); // declare sub function

int main(void)
{
    int z; // where we put return values
    int a; //
    char b[10]; //

    z = somefunc(&a, b); // call function

    fprintf(stdout, "somefunc returned: a=%d, b=%s, z=%d\n", a, b, z);
    fflush(stdout);

    exit (0); // return, no error
}

int somefunc(int *ret_a, char *ret_b)
{
    *ret_a = 123;
    strcpy(ret_b, "hello");

    return 456;
}

```

The differences here are:

1. In passing "a", I took the address rather than passing it directly. This is what the function is expecting, since it's declared to take a pointer to an int, rather than an int. "&" is the address operator; "*" is the dereference operator (also used to declare pointers).

2. I allocated some string storage for "b" -- an array of char, rather than a single char. Then, using "b" by itself becomes an implicit pointer to the start of the string.

Geez, you keep adding replies as I'm typing...

> *Another problem was that you had "b" declared as just a char*No, *you* had "b" declared as just a char. I didn't declare "b" at all. :)

> *If I set "a" and "b" first, THEN call the sub function, will that data be available in "*ret_a" and "*ret_b" as long as I don't change them?*Exactly so.

---

### Post by Krupski on 2009-02-07
> **wmcbrine said:**
> I was more concerned with the fact that you called it "the return() **function**" than the use of parentheses. It's not a function, and that's important. (The parens are merely unnecessary.)

With a function that's not declared to return void, perhaps. A bare "return;" in a void function is certainly defined. Then again, there's no reason to use it in a void function, except to return early.

Eh, not quite. What I'm using there are pointers... don't tell me you haven't come across pointers yet? Pointers are really important. They're also a big stumbling block for a lot of people; but they shouldn't be for you, since you're coming from an asm background. Basically, using a pointer is like doing register indirect addressing. (BTW, if you haven't done it yet, you should try the "compile to assembly" mode of your compiler. That will give you an assembly-language listing that you can compare to the original. In gcc, it's "-S".)

The example should look more like this:

```

int somefunc(int *ret_a, char *ret_b); // declare sub function

int main(void)
{
    int z; // where we put return values
    int a; //
    char b[10]; //

    z = somefunc(&a, b); // call function

    fprintf(stdout, "somefunc returned: a=%d, b=%s, z=%d\n", a, b, z);
    fflush(stdout);

    exit (0); // return, no error
}

int somefunc(int *ret_a, char *ret_b)
{
    *ret_a = 123;
    strcpy(ret_b, "hello");

    return 456;
}

```

The differences here are:

1. In passing "a", I took the address rather than passing it directly. This is what the function is expecting, since it's declared to take a pointer to an int, rather than an int. "&" is the address operator; "*" is the dereference operator (also used to declare pointers).

2. I allocated some string storage for "b" -- an array of char, rather than a single char. Then, using "b" by itself becomes an implicit pointer to the start of the string.

Geez, you keep adding replies as I'm typing...

No, *you* had "b" declared as just a char. I didn't declare "b" at all. :)

Exactly so.

Yup... thanks again! You're right... you didn't declare b... I did, and *I* forgot to give it a sufficient size.

Believe it or not, I am still stumped with C pointers. In assembler, I understand things like this:

(1) ldx $1000 ; load x with the data in location hex 1000 and 1001 (16 bit)

(2) ldx #$1000 ; load x with the value "hex 1000"

(3) ldx [$1000] ; load x with the data in the address *pointed to* by hex 1000 (for example, if there is a $1234 stored at location $1000,$1001 then load X with the data in $1234,$1235 (16 bits).


Now, in C I'm still not sure what the "*" and "&" things do. I use them only because I see examples and I try "&", "*" or nothing at all until it works right, but I have no clue what they do.

Things like "char c;" and "char &c;" and "char *c" have me stumped. I have read all online and in my own books and for some reason, I'm just not getting it.

I hate just "trying them" and then using the one that works. First of all, it's plain wrong. Secondly, it may "work" on a fluke but be wrong and yield incorrect results or a core dump in the future.

If you can explain to me with * and & do, you will accomplish something that many people and many books, so far, have failed to do.

Thanks again!

-- Roger

---

### Post by Krupski on 2009-02-07
> **wmcbrine said:**
> Eh, not quite. What I'm using there are pointers... don't tell me you haven't come across pointers yet? 

OK let me see if I understand this so far... tell me if I'm right:

Let's say I declare an int:

int s;

...and on this computer an "int" takes up 4 bytes.

Now, let's say "s" got placed at **physical address** 1000, 1001, 1002, 1003.

Now, let's say I give "s" a value:

s = 123;

The contents of physical memory would be set to 00,00,00,7B

(forget about big and little endian for now!)

Now, the variable "&s" points to the ADDRESS of the variable s (that is, it points to 1000).

Correct so far?

Now, if I want to modify the contents of "s" with a local function (which would normally have no direct access to "s"), can I then modify the data by using "&s"?

If so, how would I do it? Would I say "&s = 321;" which changes the contents of variable "s" from "123" to "321".

Am I right?

If so, does this also work with strings?

For example, if I say buffer[10] = "hello"; and "buffer" gets allocated memory at 2000,2001...2010, and address 2000 contains ascii "h", 2001 contains ascii "e", etc...

Can I then use "&buffer" to point to physical address 2000 and, if I want to, modify the string like this:

strcpy(&buffer, "goodbye");

All right so far? (I bet not!)

If I'm right... then what the heck does the star ("*") do?

Yes, when it comes to pointers, I am clueless. Hopefully you can help me out.

Thanks!

-- Roger

---

### Post by wmcbrine on 2009-02-07
> **Krupski said:**
> OK let me see if I understand this so far... tell me if I'm right:

Let's say I declare an int:

int s;

...and on this computer an "int" takes up 4 bytes.

Now, let's say "s" got placed at **physical address** 1000, 1001, 1002, 1003.

Now, let's say I give "s" a value:

s = 123;

The contents of physical memory would be set to 00,00,00,7BOK so far.

> *Now, the variable "&s" points to the ADDRESS of the variable s (that is, it points to 1000).*I'd say that &s *is* the address of s, or that it points to s, not that it points to the address of s (which implies double indirection). Also, "&s" is not itself a variable. However, you could assign its value to a variable:

```

int s;
int *t;

s = 123;
t = &s;   /* t == 1000 */

```


> *If so, how would I do it? Would I say "&s = 321;" which changes the contents of variable "s" from "123" to "321".*More like (to follow the above example) "*t = 321;". "&" gives you the address of something; "*" takes an address, and lets you access the something.

> [i]For example, if I say buffer[10] = "hello"; and "buffer" gets allocated memory at 2000,2001...2010, and address 2000 contains ascii "h", 2001 contains ascii "e", etc...

Can I then use "&buffer" to point to physical address 2000 and, if I want to, modify the string like this:

strcpy(&buffer, "goodbye");

All right so far? (I bet not!)[/i]In this case, it's a convention of C that the bare array name serves as a pointer, so it should just be strcpy(buffer, "goodbye"). That is to say, in your example, "buffer[0]" is 'h', but "buffer" is effectively 2000.

---

### Post by tom66 on 2009-02-07
If getting an error/warning/problems from dividing float by int (or the other way around), do something like the following:

```
floatVar = floatVar / (intVar + 0.0f);
```

which casts to float, as does:

```
floatVar = floatVar / (intVar + 0.0);
```

and:

```
floatVar = floatVar / (float)intVar;
```

---

### Post by Krupski on 2009-02-07
> **wmcbrine said:**
> OK so far.


OK I get it all now... and I also understand the use of the star (*). 

That is going to be SO handy... I used to pass data back and forth between functions with public variables. What a pain.

Pointers are going to make it SO much easier.

Thanks for all the help. You explained to me in 10 minutes something that many people and many books couldn't get through to me. Thanks!!!

-- Roger

---

### Post by nvteighen on 2009-02-08
> **Krupski said:**
> Yes... I know. I wrote it as "return()" because return CAN return a number back to the calling function.

As wmcbrine has told you, return is not a function. It's a statement.

> 
In fact, it says at "http://www.acm.uiuc.edu/webmonkeys/book/c_guide/" that "Using the return statement without an expression creates an undefined result."

So, I always stick a number into it, even if it's just zero.


Well, that's not completely true. If you declare your function as 'void', then your function is meant to not return anything. So, there you not only can, but **must** use 'return' without a value.

Here you have an example (with a pointer, too :))
```

#include <stdio.h>

void some_function(int *number)
{
    if(*number == 0)
        return;
    else
        *number = 1;
}

int main(void)
{
    int a = 56;
    some_function(&a);

    printf("%d\n", a);

    return 0;
}

```

EDIT: That's just an example... it's actually a really bad design, as we could make some_function() return an integer. But sometimes, you need functions that don't return anything...

---

### Post by CptPicard on 2009-02-08
> **nvteighen said:**
> As wmcbrine has told you, return is not a function. It's a statement.

Unless it was a continuation... :p but it's not, of course ;)

---

### Post by nvteighen on 2009-02-08
> **CptPicard said:**
> Unless it was a continuation... :p but it's not, of course ;)
:p But let's not confuse people, right?

---

### Post by CptPicard on 2009-02-08
> **nvteighen said:**
> :p But let's not confuse people, right?

But... but... I enjoy the primal reactions that result :p

Of course on further thought, return *is* a continuation. A kind of automatic escape continuation that is created implicitly at the function call point.

---

