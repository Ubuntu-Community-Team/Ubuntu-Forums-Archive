---
title: "can i compile programs written in visual studio with gcc?"
date: 2009-09-22
forum: Programming Talk
---

### Post by v1nsai on 2009-09-22
I downloaded some source code files from the internet that I wanted to compile and test out, but they were written with visual studio (hiss) and I can't find the main() function to compile.  Is it even possible to do this with g++?  I don't wanna boot into windows :(

---

### Post by Caduceus on 2009-09-22
Depends how large the program is, main() may be in another file. 

But unless the program is using windows-specific header files or otherwise has elements you don't have the compiler will spit errors.

---

### Post by hessiess on 2009-09-22
If it uses any part of the windows api, then no, not without rewriting all windows specific code with the Linux equiv. main() might be winmain().

---

### Post by phrostbyte on 2009-09-23
> **hessiess said:**
> If it uses any part of the windows api, then no, not without rewriting all windows specific code with the Linux equiv. main() might be winmain().

He can try compiling it against Winelib. [http://www.winehq.org/winelib](http://www.winehq.org/winelib)

Winelib is a native Linux library which an API that mimics WinAPI. :P

---

### Post by lisati on 2009-09-23
Random thought: Console (command line) programs can be easier to port.

---

### Post by phrostbyte on 2009-09-23
> **lisati said:**
> Random thought: Console (command line) programs can be easier to port.

Yes most definitely. Also applications which link against cross platform libraries. Also computationally intensive applications with small interfaces (eg: video codec). It all depends on the app. :)

---

### Post by v1nsai on 2009-09-23
> **hessiess said:**
> If it uses any part of the windows api, then no, not without rewriting all windows specific code with the Linux equiv. main() might be winmain().

There are only like 4 or 5 classes, I searched manually and found winmain().  Guess that means no huh?

I'll play with winelibs sometime that is something very cool that I didn't know about, but I'm trying to find a solution to a problem in my C class and I was trying to find an example of it.  Can anyone suggest an algorithm to determine if a 5 digit integer is a palindrome?  It's got me stumped haha.

---

### Post by MadCow108 on 2009-09-23
if it are only 4-5 classes porting it to linux should not be too hard (as long as they are not some crazy 1000 line classes )

is it a commandline app?
if yes then its probably enough to just change the winmain to main and maybe adjust some headers and functions calls (stprintf_s to snprintf etc).

to find out if something is a palindrome just compare the first half of the digits with the reversed second half
if they match its a palindrome

---

### Post by ve4cib on 2009-09-23
> **v1nsai said:**
> There are only like 4 or 5 classes, I searched manually and found winmain().  Guess that means no huh?

Probably not, though it's easy enough to change the code to be:

```

#ifdef WIN32
    int winmain()
#else
    int main()
#endif
{
    ...
}

```

> Can anyone suggest an algorithm to determine if a 5 digit integer is a palindrome?  It's got me stumped haha.

It's pretty easy:

```

int isPalindrome(int n) {
    int highest,lowest;
    for(int i=0; i<2; i++) {
        highest = n/(10000/(pow(10,i))) % 10; 
        lowest = n/(pow(10,i)) % 10;

        if(highest!=lowest)
            return FALSE;
    }

    return TRUE;
}

```

You only need to loop twice since comparing elements (5,1) is the same as (1,5), and comparing elements (3,3) is guaranteed to be true.  For a 7-digit number you'd need to look 3 times.  9- or 10-digits would be 5.  And so on....

All the math in the middle is just to extract the digits.  I won't explain it all; you'll have to sit down and do the math yourself.  And naturally you'll need #include cmath for the pow function.

---

