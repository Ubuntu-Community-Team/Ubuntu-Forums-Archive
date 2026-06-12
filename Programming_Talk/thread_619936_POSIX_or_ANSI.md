---
title: "POSIX or ANSI?"
date: 2007-11-22
forum: Programming Talk
---

### Post by earendil1234 on 2007-11-22
Hi,

I am new to Linux. I just switched last night.

I would like to know whether the C compiler in Ubuntu is following ANSI Standard or POSIX Standard? AFAIK, Linux usually follows the POSIX standard...but when I search about gcc in the Ubuntu's help file, it says that it follows ANSI Standard.

I would like to use this platform for Real time programming.I heard that I could use RTAI kernel to do a real time programming.. Anyone here knows where to obtain the RTAI and how to integrate RTAI into my Ubuntu? Again, is it following the ANSI or the POSIX standard? AFAIK, POSIX is always used for RT application... 

Thanks.

---

### Post by Compyx on 2007-11-22
> **earendil1234 said:**
> Hi,

I am new to Linux. I just switched last night.

I would like to know whether the C compiler in Ubuntu is following ANSI Standard or POSIX Standard? AFAIK, Linux usually follows the POSIX standard...but when I search about gcc in the Ubuntu's help file, it says that it follows ANSI Standard.


You can tell gcc which standard to comply to by using switches on the command line.

Invoke gcc with -ansi to follow the C89/C90 standard, or use -std=c89. You can use -std=c99 to have it follow the latest standard, although gcc isn't fully C99-compliant yet.

To use posix extensions, you would use something like:
```

#define POSIX_SOURCE

```
 at the top of your sources.

Reading the manual for GCC would probably be very helpful.

---

### Post by slavik on 2007-11-22
the realtime kernel is available in synaptic, it has 'rt' at the end of the package name. :)

---

### Post by earendil1234 on 2007-11-22
@Slavik:  Thanks for the info, but I really dont have any idea how to use it with ubuntu... I used QNX before and it is all there ready for real time coding...

Could you help?

---

### Post by aks44 on 2007-11-22
> **earendil1234 said:**
> I would like to know whether the C compiler in Ubuntu is following ANSI Standard or POSIX Standard? AFAIK, Linux usually follows the POSIX standard...
gcc follows the ANSI standard, which normalizes the C language itself and its standard library.

Linux follows the POSIX standard, which normalizes what APIs the OS exposes.

As you can see both standards are totally independent, one defines how to write C code, the other one defines what Linux allows you to do.

---

### Post by earendil1234 on 2007-11-22
Thanks.

Any guide on the RT thing?
I used QNX before and it is a ready-made real time software... while in Ubuntu, I believe there are things to modify before we could code it in the RT way right?

---

### Post by slavik on 2007-11-22
```
sudo apt-get install linux-rt
```

then reboot and select the rt kernel in GRUB. :)

---

### Post by earendil1234 on 2007-11-22
Haizzz... so sorry, Slavik... I read that GRUB is the grand unified bootloader... but I dont know how you select the rt kernel in GRUB? does it mean that I can switch on the kernel every time I boot up?
If something happens to my kernel.. could I restore it?

---

### Post by slavik on 2007-11-22
you can have more than one kernel installed. then when you boot you could pick which kernel to boot. grub has a config file (/boot/grub/menu.lst)

grub does have a default option (look in the config file).

---

### Post by earendil1234 on 2007-11-23
Hey! Thanks so much Slavik for the info! :)
I have it installed and run now. :)

I would like to know about compiling a code again.
When I use the cc command, I realize that I have to insert the library linking option -lpthread for threads management and -lm for math, etc...

May I know how I know when to put these options into my cc command line? I just wonder how I should know in the first place which library I have to link? Is there a kind of 'handbook' for it?

Thanks.

---

### Post by the_unforgiven on 2007-11-25
You might want to try out [Advanced Linux Programming]("http://www.advancedlinuxprogramming.com") book.

---

