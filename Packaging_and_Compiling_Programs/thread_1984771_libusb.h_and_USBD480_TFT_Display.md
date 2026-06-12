---
title: "libusb.h and USBD480 TFT Display"
date: 2012-05-22
forum: Packaging and Compiling Programs
---

### Post by qake on 2012-05-22
Hey community of ubuntu.

Hope that this is the correct forum this time : )

I'm studying basic embedded electronics in Denmark and for my final  project, I have together with my internship-company decided to make a  user-interface on a USBD480 TFT Display. ( [http://forum.lcdinfo.com/](http://forum.lcdinfo.com/) )

However, after a month of googlin' and three weeks before deadline, I have decided to post the very edge of my problem.

The display has a library from their manufacturer of which I can use  commands, but it needs to be interfaced with use of a USB to an ARM  processor which has built-in Linux .

$gcc test.c

```
#include </home/admin/arm-linux-gcc/libusb/libusb-1.0.9/libusb/libusb.h> 
 
int main (int argc, char **argv) //  
{
    usb_init();

    return 0; 
}
```Output:

```
admin@linux-machine:~/ALEX_GCC$ gcc test.c
/tmp/cchkSBid.o: In function `main':
test.c:(.text+0x7): undefined reference to `usb_init'
collect2: ld returned 1 exit status
admin@linux-machine:~/ALEX_GCC$ 
```The questions that I have are:

What do I need to do to fix the "undefined reference" problem?

If not *libusb*, which library would you recommend for this project and why?


Any help is appreciated

Sincerely, Qake

---

### Post by Bachstelze on 2012-05-22
You need to pass the proper linked flags, so that the linker will pick libusb. Normally, you would do:

```
gcc -o test test.c -lusb-1.0
```

But you won't be able to use the ARM library on your computer, since it's probably not ARM...

---

### Post by qake on 2012-05-23
> **Bachstelze said:**
> You need to pass the proper linked flags, so that the linker will pick libusb. Normally, you would do:

```
gcc -o test test.c -lusb-1.0
```But you won't be able to use the ARM library on your computer, since it's probably not ARM...

Thanks for answer.

The project has to be built for an ARM processor which has a Linux shell built-in and the company has given me their version of ubuntu virtual machine with the ARM GCC compiler on it.

I cannot seem to find any libusb files other than the ones I have downloaded and a file called "usb_libusb.c" in "admin/projects/linux_platform_packages/avrdude/current", which is empty btw.

Should I download a fresh libusb folder and install it in a specific folder?

Sincerely, Qake

---

### Post by Bachstelze on 2012-05-23
If your project uses libusb and you want to build it for ARM, you will need an ARM version of libusb. If none is provided for you, you can always compile your own (assuming you want to use a standard libusb and not a modified version...).

---

### Post by qake on 2012-05-24
> **Bachstelze said:**
> If your project uses libusb and you want to build it for ARM, you will need an ARM version of libusb. If none is provided for you, you can always compile your own (assuming you want to use a standard libusb and not a modified version...).

The programmer from my internship told me that I could use libusb to finish my project and that he would use some time to make it run on ARM processor.

At the moment I am trying to make it possible to display anything on the LCD using Linux and the USB ports on my computer - which would be the first step

The "libusb" that I have in the folder "/home/admin/arm-linux-gcc/libusb/libusb-1.0.9/libusb/libusb.h" is one that I have downloaded from a link at [http://www.libusb.org/](http://www.libusb.org/)

Again, any help is appreciated.

Sincerely, Qake

---

### Post by Bachstelze on 2012-05-24
Something else: the function usb_init() is part of the old libusb. libusb 1.0 uses libusb_init()... You should always compile C with all warnings on, otherwise the compiler will let you do stupid things. So make up your mind, which libusb do you want to use?

---

### Post by qake on 2012-05-24
I'v just found this topic at codingforums [COLOR=Blue](link: [http://www.codingforums.com/archive/index.php/t-211585.html](http://www.codingforums.com/archive/index.php/t-211585.html))[/COLOR] where this guy has the same problem with libusb.

I have altered the code to this and now it can compile (:KS)

```

/* Compile using: 

gcc -Wall -lusb-1.0 -lm test.c -o test

*/

#include <stdio.h> 
#include <libusb-1.0/libusb.h>
 
int main (int argc, char **argv) //  
{    
    struct libusb_context *context;
    libusb_init(&context); 
    return 0; 
}

```Which are the downsides of using the newest libusb rather than the old one?

In the code above I use the new libusb

Sincerely, Qake

---

### Post by Bachstelze on 2012-05-24
```
gcc -Wall -lusb-1.0 -lm test.c -o test
```

might work but is wrong. You should compile with

```
gcc -Wall -o test test.c -lusb-1.0 -lm
```

> Which are the downsides of using the newest libusb rather than the old one?

No idea, I have never used either. :D The old one is probably obsolete and kept only because some old programs use it. You should probably use the new one for new programs.

---

### Post by qake on 2012-05-24
> **Bachstelze said:**
> ```
gcc -Wall -lusb-1.0 -lm test.c -o test
```might work but is wrong. You should compile with

```
gcc -Wall -o test test.c -lusb-1.0 -lm
```No idea, I have never used either. :D The old one is probably obsolete and kept only because some old programs use it. You should probably use the new one for new programs.

Okay, thanks a lot - I would not figure out which order to place those lines :rolleyes: 

I will try my luck using the new libusb, thank you for that ;)

---

