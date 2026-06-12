---
title: "ext2_fs.h include nigtmare"
date: 2007-02-18
forum: Programming Talk
---

### Post by ggankhuy on 2007-02-18
I have version 4.10 UBUNTU just installed on my pc.
and now I got about 100 lines of error message whenever I included ext2_fs.h file in any *.c file and compile with cc or gcc. Does someone encountered this? Thanks!
Edit/Delete Message

---

### Post by ggankhuy on 2007-02-18
well 14 views no response, so I asuume no body has encountered this problem, or nobody knows waht this problem is huh? I think ubuntu is doomed in this sense.

---

### Post by christhemonkey on 2007-02-18
Your using Warty Warthog?

> 4.10 	October 2004 	Warty Warthog	Unsupported as of April 30, 2006 

Maybe you should consider upgrading?
Or is their an explicit reason you wish to use an unsurported out of date version?

---

### Post by Tomosaur on 2007-02-18
> **ggankhuy said:**
> well 14 views no response, so I asuume no body has encountered this problem, or nobody knows waht this problem is huh? I think ubuntu is doomed in this sense.

Ubuntu is doomed because you're using an archaic version of it and you're having some crazy, obscure problem? Perhaps copy and pasting some of your code would help, at the very least?

---

### Post by christhemonkey on 2007-02-18
And i presume you have e2fslibs-dev installed?


Or linux-kernel-headers?


If not, then its silly linking to a library thats not there.

---

### Post by ggankhuy on 2007-02-18
well, Downloaded 5.04 version installed, still get the same error during compilation.
Here is my main.c file , nothing wrong with that.
==============
#include <stdio.h>
#include <fcntl.h>
//#include <linux/ext2_fs.h>
#include <string.h>
#include <sys/stat.h>
#include <time.h>

int main()
{
	printf("Hello World");		//print hello world.
	getchar();			//pause
	return 0;
}

and here is my makefile: 
========================
all : main1.o 
	gcc -g -o main1.out main1.o 

main1.o : main1.c 
	cc -c main1.c

run : all
	clear
	./main1.out
	
clean : 
	rm *.o *.out

walk	:
	gdb	./main1.out


Now create Makefile and main1.c and paste my code and put these files under same folder go into that folder and compile <make>. It compiles and runs fine but now uncomment the 
//#include <linux/ext2_fs.h> in main1.c and 
this is what I get:

root@ubuntuSgt1:~/dev/test # make
cc -c main1.c
In file included from /usr/include/linux/cpumask.h:8,
                 from /usr/include/asm/smp.h:11,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/percpu_counter.h:9,
                 from /usr/include/linux/ext2_fs_sb.h:20,
                 from /usr/include/linux/ext2_fs.h:20,
                 from main1.c:3:
/usr/include/linux/bitmap.h: In function `bitmap_empty':
/usr/include/linux/bitmap.h:15: error: `BITS_PER_LONG' undeclared (first use in this function)
/usr/include/linux/bitmap.h:15: error: (Each undeclared identifier is reported only once
/usr/include/linux/bitmap.h:15: error: for each function it appears in.)
/usr/include/linux/bitmap.h: In function `bitmap_full':
/usr/include/linux/bitmap.h:29: error: `BITS_PER_LONG' undeclared (first use in this function)
/usr/include/linux/bitmap.h: In function `bitmap_equal':
/usr/include/linux/bitmap.h:44: error: `BITS_PER_LONG' undeclared (first use in this function)
/usr/include/linux/bitmap.h: In function `bitmap_shift_right':
/usr/include/linux/bitmap.h:85: error: `__shr_tmp' undeclared (first use in this function)
/usr/include/linux/bitmap.h: In function `bitmap_shift_left':
/usr/include/linux/bitmap.h:98: error: `__shl_tmp' undeclared (first use in this function)
/usr/include/linux/bitmap.h: In function `bitmap_weight':
/usr/include/linux/bitmap.h:144: error: `BITS_PER_LONG' undeclared (first use in this function)
In file included from /usr/include/asm/smp.h:11,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/percpu_counter.h:9,
                 from /usr/include/linux/ext2_fs_sb.h:20,
                 from /usr/include/linux/ext2_fs.h:20,
                 from main1.c:3:
/usr/include/linux/cpumask.h: At top level:
/usr/include/linux/cpumask.h:15: error: variable-size type declared outside of any function
In file included from /usr/include/asm/smp.h:11,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/percpu_counter.h:9,
                 from /usr/include/linux/ext2_fs_sb.h:20,
                 from /usr/include/linux/ext2_fs.h:20,
                 from main1.c:3:
/usr/include/linux/cpumask.h: In function `next_online_cpu':
/usr/include/linux/cpumask.h:56: error: structure has no member named `val'
In file included from /usr/include/asm/smp.h:16,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/percpu_counter.h:9,
                 from /usr/include/linux/ext2_fs_sb.h:20,
                 from /usr/include/linux/ext2_fs.h:20,
                 from main1.c:3:
/usr/include/asm/fixmap.h: At top level:
/usr/include/asm/fixmap.h:72: error: `FIX_ACPI_PAGES' undeclared here (not in a function)
/usr/include/asm/fixmap.h:72: error: enumerator value for `FIX_ACPI_END' not integer constant
/usr/include/asm/fixmap.h:84: error: syntax error before "pgprot_t"
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/percpu_counter.h:9,
                 from /usr/include/linux/ext2_fs_sb.h:20,
                 from /usr/include/linux/ext2_fs.h:20,
                 from main1.c:3:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/percpu_counter.h:9,
                 from /usr/include/linux/ext2_fs_sb.h:20,
                 from /usr/include/linux/ext2_fs.h:20,
                 from main1.c:3:
/usr/include/asm/mpspec.h:8: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:9: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:10: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:12: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:19: error: `MAX_APICS' undeclared here (not in a function)
/usr/include/asm/mpspec.h:20: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:20: error: conflicting types for `mp_bus_id_to_type'
/usr/include/asm/mpspec.h:8: error: previous declaration of `mp_bus_id_to_type'
/usr/include/asm/mpspec.h:22: error: `MAX_IRQ_SOURCES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:24: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:24: error: conflicting types for `mp_bus_id_to_pci_bus'
/usr/include/asm/mpspec.h:12: error: previous declaration of `mp_bus_id_to_pci_bus'
/usr/include/asm/mpspec.h:35: error: syntax error before "id"
/usr/include/asm/mpspec.h:36: error: syntax error before "address"
/usr/include/asm/mpspec.h:37: error: syntax error before "id"
/usr/include/asm/mpspec.h:38: error: syntax error before "bus_irq"
/usr/include/asm/mpspec.h:54: error: `MAX_APICS' undeclared here (not in a function)
/usr/include/asm/mpspec.h:54: error: variable-size type declared outside of any function
In file included from /usr/include/asm/smp.h:20,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/percpu_counter.h:9,
                 from /usr/include/linux/ext2_fs_sb.h:20,
                 from /usr/include/linux/ext2_fs.h:20,
                 from main1.c:3:
/usr/include/asm/io_apic.h:26: error: syntax error before "u32"
/usr/include/asm/io_apic.h:28: error: syntax error before "u32"
/usr/include/asm/io_apic.h:34: error: syntax error before '}' token
/usr/include/asm/io_apic.h:37: error: syntax error before "u32"
/usr/include/asm/io_apic.h:39: error: syntax error before "u32"
/usr/include/asm/io_apic.h:45: error: syntax error before '}' token
/usr/include/asm/io_apic.h:48: error: syntax error before "u32"
/usr/include/asm/io_apic.h:50: error: syntax error before "u32"
/usr/include/asm/io_apic.h:54: error: syntax error before '}' token
/usr/include/asm/io_apic.h:57: error: syntax error before "u32"
/usr/include/asm/io_apic.h:59: error: syntax error before "u32"
/usr/include/asm/io_apic.h:62: error: syntax error before '}' token
/usr/include/asm/io_apic.h:120: error: `MAX_IRQ_SOURCES' undeclared here (not in a function)
/usr/include/asm/io_apic.h:120: error: conflicting types for `mp_irqs'
/usr/include/asm/mpspec.h:22: error: previous declaration of `mp_irqs'
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/percpu_counter.h:9,
                 from /usr/include/linux/ext2_fs_sb.h:20,
                 from /usr/include/linux/ext2_fs.h:20,
                 from main1.c:3:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
In file included from /usr/include/linux/percpu_counter.h:9,
                 from /usr/include/linux/ext2_fs_sb.h:20,
                 from /usr/include/linux/ext2_fs.h:20,
                 from main1.c:3:
/usr/include/linux/smp.h:33: error: syntax error before '(' token
/usr/include/linux/smp.h: In function `on_each_cpu':
/usr/include/linux/smp.h:65: error: invalid type argument of `->'
/usr/include/linux/smp.h:68: error: invalid type argument of `->'
/usr/include/linux/smp.h:68: error: `TIF_NEED_RESCHED' undeclared (first use in this function)
In file included from /usr/include/linux/ext2_fs.h:20,
                 from main1.c:3:
/usr/include/linux/ext2_fs_sb.h: At top level:
/usr/include/linux/ext2_fs_sb.h:48: error: syntax error before "u32"
/usr/include/linux/ext2_fs_sb.h:50: error: syntax error before '*' token
/usr/include/linux/ext2_fs_sb.h:55: error: syntax error before '}' token
main1.c: In function `main':
main1.c:11: error: `print' undeclared (first use in this function)
main1.c:11: error: syntax error before "hello"
main1.c:13: error: `pause' undeclared (first use in this function)
make: *** [main1.o] Error 1
root@ubuntuSgt1:~/dev/test # make
cc -c main1.c
main1.c: In function `main':
main1.c:11: error: `print' undeclared (first use in this function)
main1.c:11: error: (Each undeclared identifier is reported only once
main1.c:11: error: for each function it appears in.)
main1.c:11: error: syntax error before "hello"
main1.c:13: error: `pause' undeclared (first use in this function)
make: *** [main1.o] Error 1
root@ubuntuSgt1:~/dev/test # make
cc -c main1.c
main1.c: In function `main':
main1.c:11: error: `print' undeclared (first use in this function)
main1.c:11: error: (Each undeclared identifier is reported only once
main1.c:11: error: for each function it appears in.)
main1.c:11: error: syntax error before "hello"
main1.c:13: error: `pause' undeclared (first use in this function)
make: *** [main1.o] Error 1
root@ubuntuSgt1:~/dev/test # clear

root@ubuntuSgt1:~/dev/test # make
cc -c main1.c
main1.c: In function `main':
main1.c:11: error: `print' undeclared (first use in this function)
main1.c:11: error: (Each undeclared identifier is reported only once
main1.c:11: error: for each function it appears in.)
main1.c:11: error: syntax error before "hello"
main1.c:13: error: `pause' undeclared (first use in this function)
make: *** [main1.o] Error 1
root@ubuntuSgt1:~/dev/test # make clear
make: *** No rule to make target `clear'.  Stop.
root@ubuntuSgt1:~/dev/test # make
cc -c main1.c
main1.c: In function `main':
main1.c:11: error: `print' undeclared (first use in this function)
main1.c:11: error: (Each undeclared identifier is reported only once
main1.c:11: error: for each function it appears in.)
main1.c:11: error: syntax error before "hello"
main1.c:13: error: `pause' undeclared (first use in this function)
make: *** [main1.o] Error 1
root@ubuntuSgt1:~/dev/test # at
Garbled time
root@ubuntuSgt1:~/dev/test # make
cc -c main1.c
main1.c: In function `main':
main1.c:13: error: syntax error before "return"
make: *** [main1.o] Error 1

Perhaps you guys know waht exactly wrong with it. THanks!

---

### Post by ggankhuy on 2007-02-21
So no one can answer it???

---

### Post by Tomosaur on 2007-02-22
Strange - my initial thought was that you somehow had a corrupt version of ext_2fs.h, but that just doesn't make sense (not least because you're trying a new version of Ubuntu. I compiled your code with the uncommented ext2_fs.h include, and it compiled fine for me. Is there something weird about your system? I notice you're compiling as root, too - which isn't really a great idea. Strange things have happened to me if I compile as root. Try compiling as just a regular user, maybe?

---

### Post by ggankhuy on 2007-02-23
> **Tomosaur said:**
> Strange - my initial thought was that you somehow had a corrupt version of ext_2fs.h, but that just doesn't make sense (not least because you're trying a new version of Ubuntu. I compiled your code with the uncommented ext2_fs.h include, and it compiled fine for me. Is there something weird about your system? I notice you're compiling as root, too - which isn't really a great idea. Strange things have happened to me if I compile as root. Try compiling as just a regular user, maybe?

yes i'll try as a different user, I dont think header file is corrupt, since I just dw-d iso and burned and installed right away. happened with 4.10 exact same thing with 5.04.

---

### Post by ggankhuy on 2007-02-23
[QUOTE=christhemonkey;2176486]And i presume you have e2fslibs-dev installed?


Or linux-kernel-headers?


If not, then its silly linking to a library thats not there.[/QUOTE[/B]

e2fslibs-dev<- what is that. Ok i'll check when i get back home. I dont have ubuntu at work,

---

### Post by ggankhuy on 2007-02-24
> **christhemonkey said:**
> And i presume you have e2fslibs-dev installed?


Or linux-kernel-headers?


If not, then its silly linking to a library thats not there.

well i have the ext2_fs.h file in the correct folder and the error messages doesn't say missing file or something. But I went ahead and installed the package you mentioned thru synaptic, but still the same exact error messages. waht the heck.

---

### Post by ggankhuy on 2007-02-24
> **ggankhuy said:**
> yes i'll try as a different user, I dont think header file is corrupt, since I just dw-d iso and burned and installed right away. happened with 4.10 exact same thing with 5.04.

Stil didn't help. I create different useer and compiled, exactly same result. perplexed.

---

