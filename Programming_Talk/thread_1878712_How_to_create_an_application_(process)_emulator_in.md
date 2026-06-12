---
title: "How to create an application (process) emulator in C?"
date: 2011-11-10
forum: Programming Talk
---

### Post by smilinggoomba on 2011-11-10
Hello.  I need help accomplishing an extremely hard, grueling, and challenging task.  I am trying to create a process emulator (an emulator that only runs one program at a time, instead of a full operating system; an example of a process emulator is the Java Virtual Machine) in C, that can be cross-platform, and be able to do graphics using "interrupts" (low level stuff).  I want it to be implemented in the following form:

A C program that uses the emulator, will be linked to the emulator; The emulator itself, will be linked to C program.

I know that this is really hard, and while I have a strong knowledge of C, I don't know enough to make such an emulator.  So, can anybody help?

Examples must be well commented.  Thanks!

---

### Post by Arndt on 2011-11-10
> **smilinggoomba said:**
> Hello.  I need help accomplishing an extremely hard, grueling, and challenging task.  I am trying to create a process emulator (an emulator that only runs one program at a time, instead of a full operating system; an example of a process emulator is the Java Virtual Machine) in C, that can be cross-platform, and be able to do graphics using "interrupts" (low level stuff).  I want it to be implemented in the following form:

A C program that uses the emulator, will be linked to the emulator; The emulator itself, will be linked to C program.

I know that this is really hard, and while I have a strong knowledge of C, I don't know enough to make such an emulator.  So, can anybody help?

Examples must be well commented.  Thanks!

I don't understand what kind of program this is. How will it be used? What does it actually emulate? A real processor, a virtual machine? What can it do apart from graphics? What graphics? Raster graphics, vector graphics? Does it address the graphics processor directly, bypassing the CPU?

What does this C program do, that is linked to the emulator?

---

### Post by 11jmb on 2011-11-10
I'm not entirely sure what you want to do here. An operating system uses virtual memory etc. to make user space applications believe that they are the only process running at any time with infinite resources.

Will this "emulator" run compiled binaries, or are you trying to make a sort of C interpreter? If that is the case, check out Ch.

Also, when you say you want to "do graphics" you have already left the realm of one process, because you will need for your program to interact with your graphics card.

---

### Post by smilinggoomba on 2011-11-10
What I want to do is almost like this:
Bundle QEMU with a foo.bin, where QEMU automatically loads the foo.bin.  Programs/Operating Systems in QEMU can use BIOS 0x10 to display graphics in real mode, and I am trying to re-create/re-implement QEMU as what I described earlier.

---

### Post by Arndt on 2011-11-10
> **smilinggoomba said:**
> What I want to do is almost like this:
Bundle QEMU with a foo.bin, where QEMU automatically loads the foo.bin.  Programs/Operating Systems in QEMU can use BIOS 0x10 to display graphics in real mode, and I am trying to re-create/re-implement QEMU as what I described earlier.

I have an idea of what you want to do now. So the native operating system would be DOS/Windows on some processor, for example x86, but you want a graphics program written for this environment to be runnable anywhere with the help of this emulator?

---

### Post by smilinggoomba on 2011-11-10
> **Arndt said:**
> I have an idea of what you want to do now. So the native operating system would be DOS/Windows on some processor, for example x86, but you want a graphics program written for this environment to be runnable anywhere with the help of this emulator?

Yes.  And I will probably fail, but I just want to learn more about C, and x86 (architecture that I will attempt to emulate).

---

### Post by ofnuts on 2011-11-10
> **smilinggoomba said:**
> Yes.  And I will probably fail, but I just want to learn more about C, and x86 (architecture that I will attempt to emulate).So you want to write a CPU emulator plus emulate some of the operating systems calls. You'll find that the actual size and complexity of the x86 instruction set (even the "user mode" instructions, even restricted to the standard stuff (no SSE, etc...)) means that you'll have to write an awful lot of code before your first emulated "Hello world!" appears on the screen. And be prepared for very long debugging sessions, because bugs may have very removed causes (a bug in the emulation of one instruction may leave some incorrect data that is used much later). 

There are IMHO much better ways to train yourself at C, learn the X86 architecture and at the same time start a group of elated supporters. Find any open-source software that takes C extensions/plugins(*) and find something useful to write (the advantage of writing plugins is that the infrastructure is already done and ironed out, you can concentrate on the real code, and you will easily find other people doing similar things who can help you out).

(*) Graphics (Gimp/Inkscape/Blender), games, language extensions (python, perl...)

---

### Post by nvteighen on 2011-11-10
Use Java?? Honestly, I don't get the idea.

No matter how hard you try, if you write this entirely in C, there will always be some point that will require recompilation in every different platform. Also, in some cases you might require conditional compilation, in order to deal with platform differences. If you write this as an emulator, it'd be the emulator which will have to be recompiled (exactly as the JVM binaries are different for each platform).

However, you then suddenly mention QEMU... and I don't see how that would fit anywhere.

---

### Post by smilinggoomba on 2011-11-11
> > **nvteighen said:**
> Use Java?? Honestly, I don't get the idea.

No matter how hard you try, if you write this entirely in C, there will always be some point that will require recompilation in every different platform. Also, in some cases you might require conditional compilation, in order to deal with platform differences. If you write this as an emulator, it'd be the emulator which will have to be recompiled (exactly as the JVM binaries are different for each platform).

However, you then suddenly mention QEMU... and I don't see how that would fit anywhere.

I didn't say USE Java, I said that the JVM is an example of a process emulator.

And I can see the confusion when I brought QEMU into the mess, but what I'm really trying to do is:

Make an emulator that comes pre-packaged with it's file to load.
Emulate a blank, x86 system with no operating system.  Bundle it with a file that can use some built-in functions from the emulator.  Have the emulator automatically boatload the file (QEMU can do this, this is where my example about QEMU came in).  And that's what I want to do.

I used C because of it's portability, and I'm not that great at it, so how can the emulator not be compiled once for all platforms?  As long as I limit myself to C Standard Library functions, I think that I'm in the clear.  So, I'm very curious to hear your reasoning.

---

### Post by smilinggoomba on 2011-11-11
> **ofnuts said:**
>  find something useful to write 
> **smilinggoomba said:**
>  and do graphics using "interrupts" 

Once I finish this, I'll do platform-independent graphics programming:

Games, Image Editors, Word Processers
Things like that.

---

### Post by nvteighen on 2011-11-11
> **smilinggoomba said:**
> I didn't say USE Java, I said that the JVM is an example of a process emulator.


I mean that you should use Java... as a joke that obviously didn't work... Forget about that.

> 
And I can see the confusion when I brought QEMU into the mess, but what I'm really trying to do is:

Make an emulator that comes pre-packaged with it's file to load.
Emulate a blank, x86 system with no operating system.  Bundle it with a file that can use some built-in functions from the emulator.  Have the emulator automatically boatload the file (QEMU can do this, this is where my example about QEMU came in).  And that's what I want to do.

Ok. I know understand what you mean. This would be more-or-less like Lisp images work: you have an executable which actually consists in a snapshot of the VM, which includes whatever you loaded into it, usually a program. That way, you just run the executable and the program you embedded gets run. The "built-in" functions in the case of a Lisp image would be the Lisp programming language itself... In your case, it'd be the x86 instruction set emulated by your emulator.

> 
I used C because of it's portability, and I'm not that great at it, so how can the emulator not be compiled once for all platforms?  As long as I limit myself to C Standard Library functions, I think that I'm in the clear.  So, I'm very curious to hear your reasoning.

OK... C is not portable at all: it requires recompilation in every single platform you want to deploy your program and you may also have to modify the source depending on the platform too. 

First, executable formats are different for different OSs. So you have to recompile your program if you want to have a PE (Windows), an ELF (GNU/Linux, BSD) or a Mach (Mac OS X) executable. Not only that... an x86 executable won't work on an ARM platform, because the CPU instruction set isn't the same. C is translated into the processor-specific ASM, but in order to get it, you have to recompile the code.

(If Windows executables worked on GNU/Linux, why would Wine exist?)

That's why Java has a different version of its JVM for all available platforms... because that's the trade-off in order to create a cross-platform VM.

---

### Post by karlson on 2011-11-11
> **smilinggoomba said:**
> Once I finish this, I'll do platform-independent graphics programming:

Games, Image Editors, Word Processers
Things like that.

Reading this I am with **nvteighen**.  Why not just use a platform portable GUI library like I don't know SWING or QT or Java with QT/Jambi with QT?  Why go with something complicated like an OS simulator.

If you need other OS to run your software install VirtualBoxes or VMWARE and install whatever you want there to see how this will work.  Unless of course the goal is to create something that would read a platform independent byte code.

---

### Post by slavik on 2011-11-11
so you want to write a virtual machine that can do graphics?

---

### Post by smilinggoomba on 2011-11-12
> **nvteighen said:**
> I mean that you should use Java... as a joke that obviously didn't work... Forget about that.



Ok. I know understand what you mean. This would be more-or-less like Lisp images work: you have an executable which actually consists in a snapshot of the VM, which includes whatever you loaded into it, usually a program. That way, you just run the executable and the program you embedded gets run. The "built-in" functions in the case of a Lisp image would be the Lisp programming language itself... In your case, it'd be the x86 instruction set emulated by your emulator.



OK... C is not portable at all: it requires recompilation in every single platform you want to deploy your program and you may also have to modify the source depending on the platform too. 

First, executable formats are different for different OSs. So you have to recompile your program if you want to have a PE (Windows), an ELF (GNU/Linux, BSD) or a Mach (Mac OS X) executable. Not only that... an x86 executable won't work on an ARM platform, because the CPU instruction set isn't the same. C is translated into the processor-specific ASM, but in order to get it, you have to recompile the code.

(If Windows executables worked on GNU/Linux, why would Wine exist?)

That's why Java has a different version of its JVM for all available platforms... because that's the trade-off in order to create a cross-platform VM.

Jeez, I forgot about that.   I totally see what you mean.

---

### Post by smilinggoomba on 2011-11-12
> **karlson said:**
> Reading this I am with **nvteighen**.  Why not just use a platform portable GUI library like I don't know SWING or QT or Java with QT/Jambi with QT?  Why go with something complicated like an OS simulator.

If you need other OS to run your software install VirtualBoxes or VMWARE and install whatever you want there to see how this will work.  Unless of course the goal is to create something that would read a platform independent byte code.

I know about Swing, and I can program some Java, but I want to learn as well as do graphics.  My programs don't need another OS to run, but the program will be the "kernel" of an operating system, loaded into an x86 emulator with BIOS interrupts capability.  I hope that this made my extremely confusing situation less confusing.

---

### Post by karlson on 2011-11-13
> **smilinggoomba said:**
> I know about Swing, and I can program some Java, but I want to learn as well as do graphics.  My programs don't need another OS to run, but the program will be the "kernel" of an operating system, loaded into an x86 emulator with BIOS interrupts capability.  I hope that this made my extremely confusing situation less confusing.

Not in the slightest.  Basically you want an OS emulator that will execute a common set of instructions but would be portable.  I am still curious why you want to do this instead of using SWING and Java.

---

### Post by smilinggoomba on 2011-11-14
> **smilinggoomba said:**
> Yes.  And I will probably fail, but I just want to learn more about C, and x86 (architecture that I will attempt to emulate).

My reasons for doing this are primarily for education, but I've tried using Swing and Java and they don't fit my needs.  For one thing, Java .class files only run on a computer that has installed Java, while the emulator that I want to create can be compiled as a PE/MACH-O/etc executable and run on Windows/Mac respectively, without prior install of *suchandsuch*.  That is my reasoning.

---

### Post by ofnuts on 2011-11-14
> **smilinggoomba said:**
> My reasons for doing this are primarily for education, but I've tried using Swing and Java and they don't fit my needs.  For one thing, Java .class files only run on a computer that has installed Java, while the emulator that I want to create can be compiled as a PE/MACH-O/etc executable and run on Windows/Mac respectively, without prior install of *suchandsuch*.  That is my reasoning.
$suchandsuch won't be a Java virtual machine, but will be a C compiler with all accessories (libs, etc...). And of course you'll have ironed out all problems related to different file systems and CPU word size and endianness, and installation conventions.

---

### Post by karlson on 2011-11-14
> **smilinggoomba said:**
> My reasons for doing this are primarily for education, but I've tried using Swing and Java and they don't fit my needs.  For one thing, Java .class files only run on a computer that has installed Java, while the emulator that I want to create can be compiled as a PE/MACH-O/etc executable and run on Windows/Mac respectively, without prior install of *suchandsuch*.  That is my reasoning.

I think you are still confused about what it is you are trying to accomplish.  Based on this description you will have a VM running compiled for the particular architecture and then you will have byte code that you define that will run on it, so the place that the GUI you will develop will only be able to run on would be on the machine that your emulator is installed on.  So what is your advantage over JVM?

If on the other hand based on your description the program would be compiled then I don't understand why would your forgo the current GUI toolkits like GTK+, QT, wxWidgets which are ported for Windows, Linux, and MacOS.  If what you are looking for is the ability to compile on one OS and run on another I would suggest looking into the possibility of OS crosscompiling, which is a completely different beast then where we have started from.

---

### Post by 11jmb on 2011-11-14
> **smilinggoomba said:**
>  For one thing, Java .class files only run on a computer that has installed Java

Any programs/bytecode that are written for your virtual machine will require your emulator to be installed, so what's the difference?

---

### Post by smilinggoomba on 2011-11-14
> **11jmb said:**
> Any programs/bytecode that are written for your virtual machine will require your emulator to be installed, so what's the difference?

Easy.  The emulator will be implemented as an object code file, which will be linked another object code file, which contains the programs.

---

### Post by DangerOnTheRanger on 2011-11-15
> **smilinggoomba said:**
> Easy.  The emulator will be implemented as an object code file, which will be linked another object code file, which contains the programs.

You realize this will be more difficult than writing your own JVM, and will be no different than bundling a JVM with your program (which 99% of commercial Java applications do), right?

Just a suggestion, but have you taken a look at Python? Using tools like PyInstaller, you can easily achieve the sort of functionality you're talking about without having to write a single line of low-level code.

---

### Post by ofnuts on 2011-11-15
> **smilinggoomba said:**
> Easy.  The emulator will be implemented as an object code file, which will be linked another object code file, which contains the programs.Since you need to have a different version of the emulator for each target architecture, you can't link it to the target code. Or you distribute a different version of the target executable for each platform... And anyway, if you start  considering linking, you have to use the various binary executable formats, that are platform dependent. Back to square one.

---

### Post by smilinggoomba on 2011-12-03
Hi everybody.  I just am posting so people don't think that I'm a help vampire.  The reason that this thread has been pretty dead recently is because I have a lot of things keeping me busy.

I am beginning with the code of the emulator's CPU, and have a function capable of adding blabla to ax while also properly incrementing ah and al.

I am working on my entry for the 20th IOCCC, and also a little amusing program.

Thanks for reading.

Best regards,
smilinggoomba

EDIT:
I also have the program's source, as of 12/10/2011.  Anybody is free to edit it, as long as if they don't claim it as entirely their work.  I would like others to expand on this code, and start building it into a big (free software/open source) project.

Here's the code:


char al = 0;/*Defines 8-bit registers*/
char bl = 0;
char cl = 0;
char dl = 0;
char ah = 0;
char bh = 0;
char ch = 0;
char dh = 0;

char[16] ax_bits; /*Defines string that holds the bit values of the 16-bit registers.*/
char[16] bx_bits;
char[16] cx_bits;
char[16] dx_bits;

FILE* file_path_to_read; /*Defines the binary file that we will read our opcodes from*/

short * ax = 0;/*Defines 16-bit registers*/
short * bx = 0;
short * cx = 0;
short * dx = 0;

int PC=0; /*Defines the program counter*/
int size_of_mem;/*Defines the size of the memory*/

int * memloc; /*Defines the virtual RAM*/


int init_memory(char * file_to_read) /*Function to initalize the virtual RAM; file_to_read's size will be the size of the virtual RAM*/
{
	int size_of_mem;
	
	file_path_to_read = fopen(file_to_read,"rb");
	fseek(file_path_to_read,0,SEEK_END); /*Seek to end of file and see where we are*/
	size_of_mem = ftell(file_path_to_read);
	rewind(file_path_to_read);
	
	memloc = malloc(size_of_mem);
}


int load_to_mem(char * file) /*Function to load binary file opcodes to memory*/
{
    file_path_to_read = fopen(file,"rb"); /*Opens the specified binary file (which opcodes will be read from)*/
    if (f != NULL) /*Loads the opcodes in the binary file to memory*/
	{
		fread(memloc,1,size_of_mem,file_path_to_read);
	}
}

int bad_opcode(char * opcode) /*bad_opcode and no_reg16 are error messages if there is an opcode related problem, or a register related problem*/
{
    printf( "Error: Opcode %s does not exist.", opcode);
	return 1;
    exit(1);
}

int no_reg16(char * reg_16)
{
    printf( "Error: 16-BIT Register %s does not exist.", reg_16 );
	return 1;
    exit(1);
}

int addtoax( int addend )
{
	ax = ax + addend;
	
	if ( al == 0x7F )
	{
		al = 0x0;
		ah = ah + addend;
	}
	
	else
	{
		al = al + addend;
	}
	return 0;
}

int movreg_16( char * reg_16, short value )
{
    if ( reg_16 == "ax" )
    {
        ax = value;
		al = ax
    }
}

int CPU()
{
    int hello;
}

int endprog()
{
	fclose(file_path_to_read);
}


END CODE
Now, who's with me!

---

### Post by smilinggoomba on 2011-12-10
> **DangerOnTheRanger said:**
> You realize this will be more difficult than writing your own JVM, and will be no different than bundling a JVM with your program (which 99% of commercial Java applications do), right?

Just a suggestion, but have you taken a look at Python? Using tools like PyInstaller, you can easily achieve the sort of functionality you're talking about without having to write a single line of low-level code.
I actually heard about Python, and think about possibly using libs like PyGame.  But, as I said earlier, I am doing this for educational purposes.  Also, I like your signature.  The sad thing is that I actually understand that :-)

---

