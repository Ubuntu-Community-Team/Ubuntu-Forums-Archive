---
title: "Is this practical?"
date: 2008-10-14
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-10-14
is creating an old style CLI OS like DOS or Unix practicle??

i would probably have to do it in C right?

---

### Post by loell on 2008-10-14
that would be like reinventing command line?
doing it on perl or python would probably be better, if you want to create a CLI utility.

---

### Post by jimi_hendrix on 2008-10-14
ya kinda as a hobby...like mikeOS

---

### Post by LaRoza on 2008-10-14
It took Linus 6 months to get nowhere during his work on Linux (it wasn't called that then).

Writing your own OS is really hard and technical and extremely boring. 

Remember, Linus wrote the kernel, not the tools. The compiler and utilities were part of GNU.

---

### Post by adamogardner on 2008-10-14
why is it boring and difficult to make?

---

### Post by snova on 2008-10-14
I speak from much experimentation.

It's difficult because at the kernel level, any teeny tiny mistake makes the whole thing screw up, and it's nearly impossible to figure out why.

For example, I had a printf() bug at one point that made it impossible to get debugging output (how do you debug the debugger?). I forget what I did to solve it, but it involved hardcoding VGA accesses at key points in the code to figure out where the infinite loop was (I don't even think it was in printf).

Fortunately it doesn't take long to get a hack of a serial port working (unless that's where the bug is :)), so you can send dumps down that way and read it later with a text editor. Especially when the console driver is broken.

You *can* do it in C++. All you need are a few extra compiler options to disable RTTI and exceptions, and a macro or two to "fix" name mangling (which interacts badly with assembly code).

As for practicality, it depends on what you mean by "practical". If you're referring to actual development, prepare for a lot of work. On the other hand, if you're asking whether it's practical to write a CLI os instead of a GUI, certainly! Frequently (especially in the server world) you don't even want a GUI. Besides, building a GUI would at least double the development time to the "interesting" stage.

As to the compiler and utilities, why bother writing a compiler when you can just use GCC? If you ever get to the point where a compiler would be a valuable addition to the OS, that'd be different, but there's plenty of time to think about that. Until then, just compile everything from Linux.

Utilities are another thing. I think a quick and buggy set of basic coreutils wouldn't be nearly as hard.

I wouldn't mind helping, though. I love this stuff, even though I never get anywhere. :)

---

### Post by Mister.Vash on 2008-10-14
Best place to go for more information on where to get started is here [http://wiki.osdev.org/Main_Page](http://wiki.osdev.org/Main_Page)

---

### Post by jimi_hendrix on 2008-10-15
by practicle i ment would it be insanely hard or not and i think that was answered

---

### Post by snova on 2008-10-15
Well, there's a difference between "hard" and "long". It's probably both, but mostly long.

I have several kernels lying around. None of them do much, but the most recent one can dump multiboot information to a serial port (Bochs). It dies when the timer goes off, though...

If you like, I can make a tarball out of it and attach it. It might be a good starting point, or at least informational.

---

### Post by jimi_hendrix on 2008-10-15
will i absolutly need to know assembly or can i use something higher up and more portable like C?

---

### Post by snova on 2008-10-15
How else could it be that Linux is written in C? :)

Assembly is not optional for certain things though. Fortunately these little bits don't usually require great knowledge of it, just enough to get it done. Snippets like port IO, CLI/STI, reloading GDTR/IDTR, ISR's, and so on.

---

### Post by jimi_hendrix on 2008-10-15
so basically if i googled i could find code snippits to do the job for me?

also what assembly language would be the best?

---

### Post by snova on 2008-10-15
I just copied the bits I needed from a tutorial, and some from Linux.

As for assembly choices, there are two primary dialects. There's GAS, which has an AT&T syntax and is already on your system. Of course, people like to complain that GAS was written as a backend for GCC, which always feeds it perfect code.

The other one is Nasm, which I recommend. Intel syntax is, to me, much easier to read and write.

If you want to use inline assembly (which has its place), you *have* to use GAS in those contexts.

A few suggested resources:

[LIST]
    [*] Intel reference documentation. Get the general one and the system ones, and maybe the instruction references if you want.
    [*] wiki.osdev.org - Lots of useful things.
    [*] Brans Kernel Tutorial - Very good to start with. The page is broken right now, but the text is unobscured. [http://www.osdever.net/bkerndev/index.php](http://www.osdever.net/bkerndev/index.php)
    [*] Bochs (bochs.sourceforge.net). It's an emulator that's pretty easy to set up.
    [*] DL malloc (g.oswego.edu/dl/html/malloc.html) - it's a malloc() implementation. With a little bit of tweaking it's quite easy to get it working in a kernel until you write an actual memory manager. Until then, though, this works well.
[/LIST]

A floppy disk image is needed to use Bochs. I don't remember how I made mine, but I'm fairly certain there's a way to do it without an actual floppy drive.

Or, I could just attach a tarball with a pre-made GRUB floppy, a few initial source files (not sure how much of it works), and a Bochs configuration. A little bit of pre-made infrastructure might be helpful. Especially since I got enough of it working to be able to use printf(). :)

---

### Post by jimi_hendrix on 2008-10-15
NASM = linux only, correct?

---

### Post by Hendrixski on 2008-10-15
C is basically the best assembly language known to man, and it was developed for the express purpose of writing UNIX. I don't know why you'd want to learn assembly, unless you were working on designing chips and stuff. Maybe if you were writing a compiler. I learned it at University and it was utterly useless and I've forgotten it since.

You should contribute to an existing OS, like BSD, Linux, ReactOS, BeOS, etc. etc. You will probably have much more fun than if you were to re-implement it from scratch.

---

### Post by jimi_hendrix on 2008-10-15
well i dont even want a gui...yet...and doing it from scratch is a learning experience

and i asked about nasm because snova said i would need it...same with osdev.org

---

### Post by snova on 2008-10-15
Nasm is cross-platform.

The point isn't to write a full-fledged OS, the point is that it's fun.

C is not assembly. And assembly would probably be useless for designing chips. I'd be using Verilog for that.

Unless you meant microcontrollers and whatnot, but that's another matter. Assembly *would* be useful there. But you can use C in that field, too- Small Device C Compiler (SDCC).

---

### Post by nvteighen on 2008-10-16
> **snova said:**
> 
The point isn't to write a full-fledged OS, the point is that it's fun.


Yup; very true.

> 
C is not assembly. (...)


Of course not, because the semantics involved are different (ol' Linguist's principle: each language is a unique system of meaning), but it's designed to fit Assembly and many of the ways C has are because of that: the fact that there are no data types, but just data lengths, the use of pointers, the low-levelness and the lack of almost everything makes C to be a "portable Assembly" or a "wrapper around Assembly", like some people say (unless you start using libraries and therefore break that portability).

---

### Post by jimi_hendrix on 2008-10-16
anyone have any good tutorials for this type of thing

i got some preliminary info from the wiki that someone posted earlier but i cant seem to find a complete tutorial that doesnt involve a floppy drive...

---

### Post by snova on 2008-10-16
Why are you trying to avoid floppy drives?

Sure, they're obsolete, but it's easy to get a bootable floppy image working.

It may even be *better* this way- when you implement a disk driver and filesystem support, the bootloader won't get in the way. That, and should you accidentally mess up the HD, that's one less thing to fix when everything important is on the floppy.

If you're avoiding floppies because you don't have a floppy drive, you're already going about it the wrong way. It's not a good idea to test it on real hardware (especially yours!)- you might accidentally break something. Take my advice and use the Bochs emulator- it's in the repository. It comes with an example configuration file, just tweak it a little and use that.

If you're having trouble creating a bootable floppy image, I've got about twelve. Just ask...

---

### Post by jimi_hendrix on 2008-10-16
i dont have a floppy dive, dont want to buy one, and dont own any floppies

i will try boch's and i do have old un needed hardware i can use

---

### Post by snova on 2008-10-16
Like I said- you don't need one and you're better off not using a real one.

I think I did something with loopback devices...

Oh! I remember now. Follow these instructions exactly.

```

dd if=/dev/zero of=image bs=1024 count=1440
mke2fs image # Answer 'y'
sudo mount -t ext2 -o loop image /mnt
mkdir -p /mnt/boot/grub
cp /boot/grub/stage{1,2} /mnt/boot/grub
cat >/mnt/boot/grub/menu.lst <<EOF
color cyan/blue white/blue

title   My Kernel
root    (fd0,0)
kernel  /kernel.bin
EOF
sudo umount /mnt
/sbin/grub --batch --device-map=/dev/null <<EOF
device (fd0) ./image
root (fd0)
setup (fd0)
quit
EOF

```

Bochs should be able to boot the image now. Grub will fail though, until you actually write your kernel and put it at /kernel.bin (on the floppy, of course).

Here's the Bochs configuration file I use (modified slightly):

```

cpu: count=1, reset_on_triple_fault=1
megs: 32
# Replace this with the location of your floppy disk image
floppya: image=emulation/floppy.img, status=inserted
mouse: enabled=0

# This enables a serial port for debugging (really helpful!).
# Anything you write to the port will be output to this file.
com1: enabled=1, mode=file, dev=serial.out

```

Actually writing the kernel is another matter. The tutorial I suggested (Brans Kernel Development Tutorial) was what I started with. It has to be adapted a little bit, but it can be downloaded and viewed offline.

---

### Post by jimi_hendrix on 2008-10-16
i dont have a floppy disk so waht should i do

---

### Post by snova on 2008-10-16
Those instructions will work without one. I tested them as I wrote them (don't like giving out useless help) just to make sure, and "file image" correctly reports:

```
image: x86 boot sector; GRand Unified Bootloader, stage1 version 0x3, 1st sector stage2 0x60, code offset 0x48
```

When you get a kernel ready to test, mount the image and copy it, unmount it, and run bochs.

---

### Post by jimi_hendrix on 2008-10-16
ok one last thing snova since you seem to know what your doing

got any good tutorials?

---

### Post by LaRoza on 2008-10-17
> **jimi_hendrix said:**
> ok one last thing snova since you seem to know what your doing

got any good tutorials?

Google ;)

This is the easy part.

---

### Post by snova on 2008-10-17
It seems a lot of the tutorials out there either focus on one specific thing or are incomplete.

Seriously though- Brans Kernel Development Tutorial is really good to start with. It goes from a VGA driver to GDT/IDT/ISR/PIC/Keyboard drivers, which is pretty much all you need to get off the ground.

It's all written in C, so it'll take a little tweaking to get C++ working. And then a little more to get out of flat binary formats and back to good ol' ELF...

Since the website seems to be broken, I've attached the archive. For once I bzipped it instead of using 7zip.

Also, since I've offered several times and really want give it to you whether or not you want it, also attached is some starting code I've been messing with. It's written in C++, and has a working printf() implementation... but not much else. The build system is also written in SCons, so you'll have to install that too- sorry, but it's my favorite tool to use.

Oh, and the build system automatically updates the floppy image. You'll need sudo permissions, sadly, to mount the image loopback (and unmount it again when it's finished). It doesn't work from a GUI, though, unless sudo is set up to disable authentication (i.e. not ask for a password).

There's also a KDevelop project file and a Makefile (but it just calls scons). Emulation is set up, with a few helper scripts... Just compile and run emulation/runbochs.bash and it should work! But you won't see anything, just to let you know- all the output goes to a serial port, which has been mapped to a file named "com1.out". You'll have to write a video driver by yourself if you want output to the screen, but until then, debugging output should be painless.

---

