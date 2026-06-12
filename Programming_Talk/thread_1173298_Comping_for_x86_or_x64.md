---
title: "Comping for x86 or x64"
date: 2009-05-29
forum: Programming Talk
---

### Post by Dolf123 on 2009-05-29
Hello,

I'm new to Ubuntu and I quite like it. I've loaded my visual studio project and I want to know how I can compile that project for both x86 and x64?

I'm using the Codeblocks IDE and the GCC compiler.

I see quite some specific procressors, but I don't want any of that. I just want to be able to specifcy either x86 or x64, like in visual studio.

How can I do this?

I'm using a 64 bit version of ubuntu on an amd athlon 64, so I was worried GCC automatically spits out a x64 version of the compiled program.

Cheers,

---

### Post by johnl on 2009-05-29
Hi,

By default you are probably compiling for 64-bit since you are running a 64-bit system.  To verify, find your executable and issue the command 'file' on it:

> 
$ file my-program
my-program: ELF _64-bit_ LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, not stripped


To compile as a 32-bit executable, pass "-m32" to gcc.  You should then see:


> 
$ file my-program
my-program: ELF _32-bit_ LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, not stripped


Hope this helps.

---

### Post by Dolf123 on 2009-05-30
Thanks, the file did say I'm creating 64 bit executeables.


 "error: gnu/stubs-32.h: No such file or directory
test.cpp: In function &#8216;int main()&#8217;:"

With -m32, it looks like it's missing header files for 32 bit. How do I get those? And how could I have find them myself? I have been looking around in the synaptic packet manager, but is there any naming convention for those files that I could have used to find them?


And one last thing, which is a programming question, I always assumed that sizeof( int ) in an x64 executable would give me 8, why does it give 4? A (void*) does give me 8, which is understandable if you want to be able to reach the entire memory range... But isn't the ideal size 8 on a x64 system?

Or should I manually select the "ideal" type for the right system? long's and double's for the x64 version, and floats and int's for the x86 version?

Is that also the reason why people typedef build-in types?

---

### Post by Habbit on 2009-05-30
You need to install the following packages in order for -m32 to work:
[LIST]
[*]gcc-multilib
[*]g++-multilib
[*]ia32-libs-dev
[/LIST]

---

### Post by Dolf123 on 2009-05-30
Thanks for the help. Can't find the ia32-libs-dev in the synaptic package manager though.

---

### Post by Habbit on 2009-05-30
> **Dolf123 said:**
> Thanks for the help. Can't find the ia32-libs-dev in the synaptic package manager though.
Oh, sorry, maybe its name has changed since I last did this setup. My apt can't find it either, but says that "ia32-libs" replaces it.

---

### Post by Dolf123 on 2009-05-30
Ok thanks, I do have that.

Now I am getting compile errors with my -m32 compile option switched on ( I did do a rebuild ):

obj/Debug/messagingsystem.o: In function `__gnu_cxx::new_allocator<std::_List_node<MessageListener*> >::allocate(unsigned int, void const*)':
messagingsystem.cpp:(.text._ZN9__gnu_cxx13new_allocatorISt10_List_nodeIP15MessageListenerEE8allocateEjPKv[__gnu_cxx::new_allocator<std::_List_node<MessageListener*> >::allocate(unsigned int, void const*)]+0x38): undefined reference to `operator new(unsigned int)'


It can't find "operator new" .. I'm not using "operator new", but the std::list class is..

It also gives a lot of messages like this:
 /usr/bin/ld: i386 architecture of input file `obj/Debug/messagingsystem.o' is incompatible with i386:x86-64 output

That might have something to do with it ?

I'm using codeblocks, I went to "Other options" in "Compiler settings" where I typed -m32

---

### Post by Dolf123 on 2009-05-30
I found it, I went to the file that gave me the errors and I specified some "custom commands" on it .. -m32.

I can't believe there isn't a project-wide setting I can use to have them all -m32 or not? It should just be in the compiler options.

---

### Post by Habbit on 2009-05-30
Maybe Code::Blocks is still configured for x86-64 output and is telling that to the linker, look for an option called "Platform" or "Architecture" (I don't know the program that well). Regarding the "undefined referente to new" message, are you compiling with g++ or gcc? If you are using gcc you need to explicitly link the C++ library in: "-lstdc++"

---

### Post by Dolf123 on 2009-05-30
g++, but it wasn't an unrelated warning, it only popped up when I have -m32 on.

I'll look for the ouput, but in the compiler options I can only find CPU architecture tuning ...

Edit: Weird ... both g++ theProblemFile.cpp and g++ -m32 theProblemFile.cpp work, but not with the option in CodeBlocks, but I can google this from here, thanks alot

---

