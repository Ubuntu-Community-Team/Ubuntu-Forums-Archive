---
title: "Need opinion of my code please"
date: 2009-02-08
forum: Programming Talk
---

### Post by Krupski on 2009-02-08
Hi all,

I'm re-writing an old program I did years ago. This program prompts the user for numerical data input, string data input and answers to yes/no questions (everything is a "no" unless explicitly answered as a "Y").

It asks for LOTS of input, so I thought a single, "generic" line input function that returned everything would be appropriate and efficient.

By the way, this is not a school project or homework, and I'm not a student - let's get that out of the way. :)

Please look at the following code (all I care about now is the FUNCTION I wrote (in bold), not the quick-n-dirty main() which is used to test it).

Comments, advice, improvements, criticisms all welcomed!

Thanks!

-- Roger

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

**int readline(float *number, char *string);** // prototype for readline

int main(void) // just for testing
{

    char string[BUFSIZ];
    int yesno, idx;
    float number;

    while(1) {

        fprintf(stdout, "\nType a string or number: ");
        fflush(stdout);

        yesno = readline(&number, string);

        fprintf(stdout,
            "String value: %s, "
            "Float value: %f, "
            "Int value: %d"
            "\n",
            string, number, (int)(number + 0.5));

        fprintf(stdout, "Hex values of raw buffer data:\n");

        for((idx = 0); (idx <= strlen(string)); (idx++)) {
            fprintf(stdout, "%02X ", string[idx]);
        }

        if(yesno) {
            fprintf(stdout, "\n'Yes' returned true\n");
        } else {
            fprintf(stdout, "\n'Yes' returned false\n");
        }

        fflush(stdout);
    }
    exit(0);
}


[B]
// read a line of data from stdin and give me
// the floating point value if it's a number,
// the characters if it's a string or a true
// or false if it's a Yes or non-yes.

int readline(float *number, char *string)
{
    char buf[BUFSIZ];
    int len;

    // read a line from stdin
    fgets(buf, BUFSIZ, stdin);
    len = strlen(buf);

    // remove cr, lf, nulls and other crap
    while((buf[len] == 0x0d) ||
          (buf[len] == 0x0a) ||
          (buf[len] == 0x00)) {
          (len--);
    }

    // terminate the line with a null
    (buf[len+1] = 0);

    // copy buffer for return to caller
    strcpy(string, buf);

    // get the floating point value of the input
    *number = atof(buf);

    // remove leading spaces, tabs etc. and check for "Y"
    sscanf(string, "%s", string);
    if(toupper(string[0]) == 'Y') {
        return(1); // non zero = true
    } else {
        return(0); // zero = false
    }
}
[/B]

```

---

### Post by wmcbrine on 2009-02-09
The part where you remove nulls is pointless -- you're using strlen() to find the end of the string, and working backwards from there. But strlen() stops at the first null, so there won't be any before that point.

*sscanf(string, "%s", string);* is sick. You're well on your way to the obfuscated C contest. But I like it. :D

The last five lines could be condensed to:

```

return (toupper(string[0]) == 'Y');

```

---

### Post by scourge on 2009-02-09
- Why name a macro BUFSIZ and not BUFSIZE?
- Instead of calling fflush(stdout) everywhere, you can just disable buffering once and for all with setbuf(stdout, NULL)
- "yesno" is a funny name for a variable. Why not call it "ok" instead, and use the bool type from stdbool.h?
- No need for fprintf if you're writing to stdout, printf works just fine.
- Don't use strlen() in a tight for loop, because not all compilers can optimize it properly. Instead store the length in a temporary variable.
- Like wmcbrine said, removing the nulls is pointless. The same applies to the "terminate the line with a null" thing. The string is already guaranteed to be null-terminated by fgets.
- "return" is a statement, not a function. So it's confusing when you use it like a function with the parenthesis.

Other than that, nice code.

---

### Post by Krupski on 2009-02-09
> **wmcbrine said:**
> The part where you remove nulls is pointless -- you're using strlen() to find the end of the string, and working backwards from there. But strlen() stops at the first null, so there won't be any before that point.

*sscanf(string, "%s", string);* is sick. You're well on your way to the obfuscated C contest. But I like it. :D

The last five lines could be condensed to:

```

return (toupper(string[0]) == 'Y');

```

Thanks for the comments.

The reason I back up and strip everything off the tail end is that I want the code to work equally well in Windows console mode and Linux.

The buffer contents after reading an input line DIFFER between Linux and Windows (specifically there is newline junk in the buffer when compiled under Windows).

Therefore, I strip out anything on the tail that may be there and just put a null at the end.

I know it seems foolish, but I needed to do it.

The "sscanf(string, "%s", string);" thing I do is to remove any leading spaces or tabs in a line before I look for the "Y" character.

If I entered "Y", it would return true. If I entered "(space)Y", it would return false.

Is there a better way to accomplish this than using sscanf?

By the way, this function is for a program that generates complex waveforms.

It asks for a filename, checks for a dupe, then asks for a sample rate and a bit width, then asks for "Frequency (0):", "Magnitude(0):" and "Phase(0):" where the (0) is actually 0,1,2,3,4 as many as you wish to enter.

Then all the magnitudes are summed and adjusted to 1.0, a check is done for Nyquist (i.e. too high a frequency for the sample rate) and finally a 44 byte .WAV header is generated and the desired inputs are output as sine waves with the correct frequencies, magnitudes and phases.

My old version of this program did a "fgets" and type conversion for EACH input. It was (is) a hideous mess... which is why I want to redo it better.

As far as the "Yes/No" part of the function, there are parts of the program that require answers such as "Magnitude is 1.5, normalize it to 1.0? (y/N)" (answer != Y is the default).

It also asks "The file 'demo.wav' already exists, overwrite it? (y/N)"

There are a few other places where Yes/No is required (like Nyquist - generate anyway?)

Obviously, the line input function is going to be the heart of the new code, so I want to be sure it's right.

Thanks again for your comments... and please feel free to comment more if you have any!

-- Roger

---

### Post by maximinus_uk on 2009-02-09
Whats up with

```
(len--);
```

When you can just use

```
len--;
```

Extra parentheses are just look a bit confusing to me (and I speak as a lisp programmer... ;))

---

### Post by Krupski on 2009-02-09
> **scourge said:**
> - Why name a macro BUFSIZ and not BUFSIZE?
- Instead of calling fflush(stdout) everywhere, you can just disable buffering once and for all with setbuf(stdout, NULL)


"BUFSIZ" is a compiler defined value!

(from **[http://www.delorie.com/gnu/docs/glibc/libc_226.html](http://www.delorie.com/gnu/docs/glibc/libc_226.html)**):

[COLOR="Red"][B]"int BUFSIZ
    The value of this macro is an integer constant expression that is good to use for the size argument to setvbuf. This value is guaranteed to be at least 256.
    The value of BUFSIZ is chosen on each system so as to make stream I/O efficient. So it is a good idea to use BUFSIZ as the size for the buffer when you call setvbuf."[/B]
[/COLOR]

As for the STDOUT thing... thanks! I didn't know buffering could be disabled!

-- Roger

---

### Post by Krupski on 2009-02-09
> **maximinus_uk said:**
> Whats up with

```
(len--);
```

When you can just use

```
len--;
```

Extra parentheses are just look a bit confusing to me (and I speak as a lisp programmer... ;))

Yeah I know... I'm just stuck with what they say in the book "Practical C Programming" by O'Reilly... "Put parentheses around everything"  :)

---

### Post by Krupski on 2009-02-09
> **scourge said:**
> - No need for fprintf if you're writing to stdout, printf works just fine.

I use fprintf() so that I can send data to the console or to a file merely by changing the file pointer.

---

### Post by wmcbrine on 2009-02-09
> **Krupski said:**
> The reason I back up and strip everything off the tail end is that I want the code to work equally well in Windows console mode and Linux.I wasn't saying anything about stripping CRs and LFs, just the nulls. It's pointless to try to strip them because they *will not be there*. This is *guaranteed* by the nature of strlen(). That's how it works -- it counts forward until it hits a null.

```

size_t strlen(const char *c)
{
    size_t len = 0;

    while (*c++)
        len++;

    return len;
}

```

(Just an example implementation, but that's how they all work.)

> *The "sscanf(string, "%s", string);" thing I do is to remove any leading spaces or tabs in a line before I look for the "Y" character.*Yeah, I got that. Like I said, it's a somewhat perverse way to do it -- the source and destination being the same and all. Many people would frown on that. But I think it's kind of a neat trick. :)

> *Is there a better way to accomplish this than using sscanf?*In this particular case, I think the line could best be replaced with nothing at all, because why would anyone type "<space>Y"? (And if they did -- don't they deserve  to suffer for it?)

---

### Post by wmcbrine on 2009-02-09
> **scourge said:**
> - Instead of calling fflush(stdout) everywhere, you can just disable buffering once and for all with setbuf(stdout, NULL)Even better, he could just not worry about flushing things that don't need to be flushed...

> [i]- No need for fprintf if you're writing to stdout, printf works just fine.

- "return" is a statement, not a function. So it's confusing when you use it like a function with the parenthesis.[/i]

> **maximinus_uk said:**
> Whats up with

```
(len--);
```

When you can just use

```
len--;
```

Extra parentheses are just look a bit confusing to me (and I speak as a lisp programmer... ;))

I brought these points up in the "Critique please" thread, but he seems committed to his bad habits.

---

### Post by Krupski on 2009-02-09
> **wmcbrine said:**
> In this particular case, I think the line could best be replaced with nothing at all, because why would anyone type "<space>Y"? (And if they did -- don't they deserve  to suffer for it?)

I think the program should be as robust as possible. Besides, anything BUT a "y" is interpreted as "no", and I would hate to hit "y", expect a yes and then have it not work as I expected.

This program is just for me anyway... it's not a "product". What I'm going to use it for is to brutally test an FFT algorithm by making it analyze complex waveforms with weird amplitudes, phases and even Nyquist foldovers.

Think of it like this... if the program prompted you:

"Make user suffer horribly? (y/N): " and, being sadistic, you typed " y" and the user DIDN'T suffer horribly, wouldn't you be coming after the programmer with a pitchfork?  LOL! :)

-- Roger

---

### Post by Krupski on 2009-02-09
> **wmcbrine said:**
> Even better, he could just not worry about flushing things that don't need to be flushed...

Sometimes things do need to be flushed. Like a progress indicator I once did that was SUPPOSED to do the "stars" thing (like this: [*******]) and, although it worked, the stars didn't print one by one, they ALL printed at the end.

Out of fear of that happening again, I stick a fflush() in just in case.

Anyway... I ran into a VERRRY strange problem with my program. The function itself reads an entire string correctly (proven with debug printf's in the subroutine), but the RETURNED string stops at the first SPACE!!!

For example, if I enter "hello there joe", the entire string "hello there joe" is present in both "string" and "buf" after the strcpy() call, but upon return, "string" only contains "hello" (!!!) What the heck???

Look at this (in LCC-Win32):

```

C:\WINDOWS\lcc\projects\default\lcc>readline.exe

Type something: hello there joe

String value: "hello"
Float value: "0.000000"
Int value: "0"

Hex values of raw buffer data:
68 65 6C 6C 6F 00

'Yes' returned false

Type something:

```


THIS has me totally stumped!

-- Roger

(edit to add): The TAB character is also stripped!!! If I enter "hello(tab)there(tab)joe", it still just returns "hello"

What the HECK?????

---

### Post by Krupski on 2009-02-09
> **wmcbrine said:**
> I wasn't saying anything about stripping CRs and LFs, just the nulls. It's pointless to try to strip them because they *will not be there*. This is *guaranteed* by the nature of strlen(). That's how it works -- it counts forward until it hits a null.


Yes but I don't want the CR or LF either... in case I next use the data for an fopen().

---

### Post by Krupski on 2009-02-09
Oh just kick me now. I am SUCH an idiot!!!

I found why my return string was being chopped... I did sscanf() to "string" instead of to "buf".

How annoying when a program does exactly what you tell it to... :)

---

### Post by nvteighen on 2009-02-09
My concern about the route you're taking is that it sounds me a lot to what you do in Visual Basic: design a user interface and then make the implementation work according to the UI.

That's a mistake, IMO. You want to code a FFT program, so what I'd do in your case is to code the functionality and some test cases and then start worrying about the UI. 

The line reading should not be the core of your program.

Maybe you've heard bout "top-down" programming? This consists in creating the caller code before the callee code (the client before the server) by establishing the interface. That's a technique, but it's usually referred to the programming interface not the user interface. And it means you have your design really well-planned in advance and that you'll stick with it.

For example, if you already have a FFT library, then "top-down" could be an option.

But usually, "bottom-up" programming (to write the callee code before the caller code) is easier. It's true that it makes you implement stuff from the very ground and that makes you start coding from the lowest level of abstraction... which is really boring. But then, you end up doing what you want.

---

### Post by Krupski on 2009-02-09
> **nvteighen said:**
> That's a mistake, IMO. You want to code a FFT program, so what I'd do in your case is to code the functionality and some test cases and then start worrying about the UI.

No... the line input function is going to be used for a complex waveform generator which will be used to TEST a different program (the FFT program).

Also, I want a good solid line input function just to have in my "toolbox" which is why I'm spending time on it.

Lastly, I'm rather a newbie at C programming, so I want to learn how to do it, and do it right... that's why I nitpick the questions.

For example, I'm *FINALLY* figuring out how pointers work in C... and now I've run into another oddity that makes no sense to me.

If I may... here's what's confusing me (the latest version of the line input code and a main() to test it):


```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

int readline(float *number, char *string); // prototype for readline

int main(void) // just for testing
{
    float number; // returned number
    char string[BUFSIZ]; // returned string
    int answer, idx; // generic vars

    while(1) { // keep looping unless a null line

        fprintf(stdout, "\nType something: ");

        [COLOR="Red"]**answer = readline(&number, string); // call function**[/COLOR]

        if(strcmp(string, "") == 0) { break; } // if blank line exit

        fprintf(stdout, // info for debugging
            "\n"
            "Returned values\n"
            "===============\n"
            "\nBUFSIZ value     : %d"
            "\nString value     : %s"
            "\nString length    : %ld"
            "\nFloat value      : %f"
            "\nInt value virgin : %d"
            "\nInt value rounded: %d"
            "\n",
            BUFSIZ, string, strlen(string), number,
            (int)(number), (int)(number + 0.5)); // round the int

        fprintf(stdout, "\nHex values of raw buffer data:\n");

        for((idx = 0); (idx <= strlen(string)); (idx++)) {
            fprintf(stdout, "%02X ", string[idx]);
        }

        fprintf(stdout, "\n\n\"Yes\" returned ");

        if(answer) { fprintf(stdout, "true\n"); }
        else       { fprintf(stdout, "false\n"); }
    }

    fprintf(stdout, "\nBlank entered - Bye!\n\n");
    exit(0);
}


// read a line of data from stdin and return
// the floating point value if it's a number,
// the characters if it's a string and a true
// or false if it's(Y)es or !=(Y)es.

int readline(float *number, char *string)
{
    char buf[BUFSIZ]; // read into here

    // read a line from stdin
    fgets(buf, BUFSIZ, stdin);

    // copy buffer for return to caller
    strcpy(string, buf);

    string[strlen(string) - 1] = 0; // remove newline

    // get the floating point value of the input
    *number = atof(string);

    // remove leading spaces, tabs etc. and check for "Y"
    sscanf(buf, "%s", buf);
    return(toupper(buf[0]) == 'Y'); // return true or false
}

```

Why do I call the function with a pointer to the float "number" but not to the array "string"?

And, in the readline function itself, I understand why the indirection is used to copy data to "number", but why is "string" treated normally (i.e. how does it's value "get back" to the caller)?

I *thought* that I should call the function like this: 

```

answer = readline(&number, &string);

```

...and return all the values like this:

```

strcpy(*string, buf);

```

...and manipulate the string like this:

```

*string[strlen(*string) - 1] = 0;

```

But of course this is wrong. Why do I use "&" and "*" for the float but not for the array (string)?

MAN am I confused now!

Any help will be GREATLY appreciated... and anyone else who would like to chime in please do so.

Thanks!

-- Roger

---

### Post by Krupski on 2009-02-09
> **nvteighen said:**
> Maybe you've heard bout "top-down" programming? This consists in creating the caller code before the callee code

I do a lot of pretty complicated programming in Motorola 68HC11 assembly language (THAT I'm good at!)  :)

The way I program is to write a whole bunch of little subroutines to do my dirty work. These are where I have to know port addresses, bit patterns and such.

Then after these are written, I can write a simple core. For example... a digital clock (in pseudo-code):

```

main
    bsr   readclock ;get current time
    bsr   bcdtoasc  ;convert bcd data to ascii
    bsr   lcdout    ;display time on lcd display
    bsr   keyscan   ;read input
    cmpa  #esc      ;did user press escape?
    bne   main      ;nope, read and display clock again
    rts             ;yes, exit


```

So you see once I have "readclock" and "lcdout" etc... all written and debugged, then I don't have to "think" anymore. I don't need to remember the port address of the LCD display or which bit means "busy". I just call "lcdout" and it works.

I guess this would be called "bottom-up" programming, huh?  :)

-- Roger

---

### Post by nvteighen on 2009-02-10
> **Krupski said:**
> 
Why do I call the function with a pointer to the float "number" but not to the array "string"?

And, in the readline function itself, I understand why the indirection is used to copy data to "number", but why is "string" treated normally (i.e. how does it's value "get back" to the caller)?

I *thought* that I should call the function like this: 


Because there are no arrays in C :) An array (an therefore also strings) are just a pointer to the first element it contains. So, that's why you don't use &string, because string is already a pointer.

When you do a[9], what you're actually doing is *(a + 9). It's just syntactic sugar... Try it.

So, if you are aware that those are just pointers, everything clears itself up.

> **Krupski said:**
> 
So you see once I have "readclock" and "lcdout" etc... all written and debugged, then I don't have to "think" anymore. I don't need to remember the port address of the LCD display or which bit means "busy". I just call "lcdout" and it works.

I guess this would be called "bottom-up" programming, huh?  :)


That's bottom-up, yeah.

---

### Post by Krupski on 2009-02-10
> **nvteighen said:**
> Because there are no arrays in C :) An array (an therefore also strings) are just a pointer to the first element it contains. So, that's why you don't use &string, because string is already a pointer.

When you do a[9], what you're actually doing is *(a + 9). It's just syntactic sugar... Try it.

So, if you are aware that those are just pointers, everything clears itself up.


OK, tell me if I'm getting all this right...

For example:

```

int x, p, z; // just declare vars

x = 10; // simply set x to 10

p = &x; // p points to the physical memory location of x

for((z = 0); (z < 4); (z++)) {
    print %0X p[z]; // pseudo print
}

... displays 00 00 00 0A (the data stored in memory pointed to by p which holds x)

*p = 7; // put the value 7 into x's memory location

x = 7; // does the same exact thing

// looking at p[0,1,2,3] would now show "00 00 00 07"

p = 7; // BAD - makes p worthless (no longer points to x)


```


Am I on target here?

Thanks!

-- Roger

---

### Post by nvteighen on 2009-02-10
> **Krupski said:**
> 
Am I on target here?


Almost: That p[z] stuff will segfault as you will be looking for an array where there's no memory allocated for it.

I hope this C code explains it well. Compile and run to see the segfault.

```

/* THIS SEGFAULTS ON PURPOSE */
#include <stdio.h>

int main(void)
{
    int number = 42; /* A little number saved somewhere in our memory... */

    printf("number = %d\n", number);

    int *pointer = &number; /* pointer is the memory address of number. */
    
    *pointer = 0; /* We change whatever pointer is pointing to... */

    printf("number = %d\n", number); /* So, number is now 0 */

    int array[8]; /* Ok, array is a pointer to the first element, but this
                   * notation makes the program allocate 8 spaces in the
                   * stack. */

    /* If you happen to do this:
     * 
     * int *array;
     *
     * Then, to make that an array, you have to use dynamic allocation with
     * malloc(), calloc() and friends. It's just an allocation issue, not the
     * nature of array, which in both cases is a pointer. */

    int i;
    for(i = 0; i < 8; i++)
    {
        array[i] = i; /* Identical to *(array + i) = i. We can do this because
                       * we allocated memory after array[0]. */

        printf("array[%d] = %d\n", i, array[i]);
    }

    /* But... this will segfault at pointer[1], because we only have pointer[0]
     * (i.e. *pointer) allocated. */
    for(i = 0; i < 8; i ++)
    {
        pointer[i] = i;
        printf("pointer[%d] = %d\n", i, pointer[i]);
    }

    return 0;
}

```

EDIT: I know, it's over-commented, but it's for educational purposes ;)

---

### Post by Krupski on 2009-02-10
> **nvteighen said:**
> Almost: That p[z] stuff will segfault as you will be looking for an array where there's no memory allocated for it.

Ah I C (no joke intended!) :)

I just tested your code in Win-LCC32 and it didn't crash... it ran fine. I'll try it in Linux in a few minutes.

Thank you so much for the code snippet and the comments. The comments really help explain everything.

My mistake was thinking like raw machine code. For example, if I stored a 32 bit number in RAM at location hex 1000, physically in memory it would look like this (pseudo-code):

```

var1    equ         $1000       ;32 bit variable

        load_reg32  #$12345678  ;load a 32 bit number
        stor_reg32  var1        ;store to $1000-$1003
    

```

Now, if I run a debugger and look at ram, I will see this:

```

$1000 $12
$1001 $34
$1002 $56
$1003 $78
$1004 (undefined as yet)

```

So then I thought that if the variable located at $1000 was called "x" in C, that &x would have the value of $1000 and I could look at the 4 individual bytes of the int (i.e. &x+0, &x+1, &x+2 and &x+3)

But, I see now that &x points to the "spot" where the data is stored and simply referencing that spot is all that's necessary.

And, I now also see that "spot+1" is pointless, probably undefined and has nothing to do with "x".

... I think I've got it now.  :)

Thanks again!

-- Roger

---

### Post by Krupski on 2009-02-10
Just ran the code in Ubuntu 8.10 64 bit and it segfaults as expected, but it prints all 8 (0 thru 7) indices before it crashes!

VERY strange!

Here's the run under Linux:

```

root@michael:~/c-progs# gcc -Wall -o test ptr-test.c 
root@michael:~/c-progs# ./test
number = 42
number = 0
array[0] = 0
array[1] = 1
array[2] = 2
array[3] = 3
array[4] = 4
array[5] = 5
array[6] = 6
array[7] = 7
pointer[0] = 0
pointer[1] = 1
pointer[2] = 2
pointer[3] = 3
pointer[4] = 4
pointer[5] = 5
pointer[6] = 6
pointer[7] = 7
Segmentation fault
root@michael:~/c-progs# 

```

It *should* segfault when "pointer[1] = 1" is attempted, but it goes all the way through before faulting.

And... I wonder why it doesn't crash at ALL under Win LCC-32?

Very strange.

-- Roger

---

### Post by nvteighen on 2009-02-10
It's not strange: it all depends on what you have on memory. When you access memory illegally, you get undefined behaivor until it finally segfaults. But, if you run it through gdb, it will tell you that the error was trying to access pointer[1].

But, don't say you were running this as root!?

---

### Post by Krupski on 2009-02-10
> **nvteighen said:**
> It's not strange: it all depends on what you have on memory. When you access memory illegally, you get undefined behaivor until it finally segfaults. But, if you run it through gdb, it will tell you that the error was trying to access pointer[1].

But, don't say you were running this as root!?

I know... I know... not supposed to use root for a normal login...

This IS, however, just a test install using WUBI on a Windows machine.

I would never do any such foolishness on my REAL Linux machine!

---

