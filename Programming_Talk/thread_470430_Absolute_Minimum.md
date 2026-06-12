---
title: "Absolute Minimum"
date: 2007-06-11
forum: Programming Talk
---

### Post by xerox on 2007-06-11
This may sound like a weird question, but I'm thinking actively today.

What is the absolute minimum requirement to boot into an operating system?

Ok, let me rephrase/explain:

Picture this. There's an old computer sitting around. It has no operating system, can only boot off of a floppy (the bios setting is locked for eternity), and is junk, as virtually nothing will run on it.

Introduce me, a new programmer. And the scenario in which this is all coming together.

What do you need, as a minimal "kernel" of sorts, to be able to boot in a command prompt that's running off a floppy disk? 

And this command prompt that I am referring to, would only have to preform a simple calculator function. [for example. Later on, I'd add functions like word processor, hardware recognition (would that be a part of this kernel?) , text web-browser, and network capability.]

So in a nutshell, my questions:

1) Minimum to-run-off-a-floppy needs
2) What sort of hardware recognition? Is it built into the machine, or will there need to be some special configuration software? 

Also, things to take into consideration when answering those far-fetched questions:

1) The computer I am referring to is a school one, and I am about to graduate from that school, so time is of essence (in about 2-3 weeks my access to the computer will end)
1A) If you're wondering how it got in that state, ask my classmate, who pressed enter and completed the much-joked-about command.
2) Maximum capacity is 1.4 MB
3) Empty computer.


Thanks for reading, and thanks in advance for replying.

---

### Post by yabbadabbadont on 2007-06-11
It's called DOS.  :D

The first version of Microsoft Word that I used ran off of a 360Kb 5-1/4" floppy after booting using a DOS floppy.  Same for the spreadsheet of the time as well as AutoCAD.  (I still have that version of AutoCAD ;))

---

### Post by 444 on 2007-06-11
One of them one-floppy Linuxes should work too. Like tomsrtbt. I assume it has an hd inside so you can copy stuff to it once in Linux and not have to worry about the 1.4m limit...

---

### Post by ankursethi on 2007-06-11
A sufficiently stripped down kernel compiled specifically for that machine (only supporting the hardware that machine has) and assuming that no extra hardware will be added in the future would do the trick. Check out linuxfromscratch.org.

I'm assuming that the BIOS is locked and you cannot boot off a CDROM only because you cannot make the changes in the BIOS. If that's the case, install GRUB on a floppy, configure it to boot the CDROM, insert the CD and the floppy and then boot the computer. Select the GRUB entry you added in the GRUB menu.

---

### Post by xerox on 2007-06-11
Ankursethi, thanks for the help. The site you gave proves interesting, and your interpretation of what I was talking about was just what I needed.

Thank you, again. :)

(This below was the reply to the first message, now not needed)
[COLOR="Navy"][True, however:

My real question there was (maybe the scenario mucked up the purpose) simply, what file* do you need written on the floppy disk in order to boot it?  Also, this file should be able to interact with** the BIOS to be able to boot. 

You suggestion though, was a good solution to my scenario (a problem in itself, i suppose).

-----
*I'm thinking, it would be something along the lines of the "autoexec.bat" file on windows.

** Not quite "interact with", more like, tell that "I am a runnable partition", sort of like the GRUB bootloader, where all the partitions listed are runnable, even though some might not be. Except that this is between the BIOS and the floppy.][/COLOR]

---

### Post by yabbadabbadont on 2007-06-11
If you go the DOS route, you create the disk with "format /s a:".  That will transfer the required files to the disk in order to make it bootable.  The exact name of the files varies depending upon which version of DOS you use.  (although the command shell is command.com, strangely enough...  ;))  If you don't want to reformat the floppy, you can use "sys a:" to transfer the system files to it to make it bootable.

Edit: If you go the linux route, then I agree with the previous poster about using tomsrtbt.  (google for it)

Edit2: [http://www.toms.net/rb/](http://www.toms.net/rb/)

---

### Post by pmasiar on 2007-06-11
Damn Small Linux or one of other "small hardware distros" should do the trick. IIRC it boots from a floppy.

---

### Post by nimrod_abing on 2007-06-11
> **xerox said:**
> Ankursethi, thanks for the help. The site you gave proves interesting, and your interpretation of what I was talking about was just what I needed.

Thank you, again. :)

(This below was the reply to the first message, now not needed)
[COLOR=Navy][True, however:

My real question there was (maybe the scenario mucked up the purpose) simply, what file* do you need written on the floppy disk in order to boot it?  Also, this file should be able to interact with** the BIOS to be able to boot. 

You suggestion though, was a good solution to my scenario (a problem in itself, i suppose).

-----
*I'm thinking, it would be something along the lines of the "autoexec.bat" file on windows.

** Not quite "interact with", more like, tell that "I am a runnable partition", sort of like the GRUB bootloader, where all the partitions listed are runnable, even though some might not be. Except that this is between the BIOS and the floppy.][/COLOR]

There are several files involved in the PC boot process whether you run Linux or Windows or *BSD. The most important ones are part of the boot loader, (e.g., stage 1, stage 1.5, and stage 2 of GRUB). Another important file needed of course is your kernel can optionally load an initrd image. Depending on your setup of your BIOS, the boot sequence will usually look for a bootable partition on your first hard disk, if none is found it will try other boot devices you have specified.

Try one of the links found here: [http://www.educypedia.be/computer/generalpcinfo.htm](http://www.educypedia.be/computer/generalpcinfo.htm)

To be bootable, a disk needs to contain a short bootstrap program in the first sector of the disk. The limit to this is 512 bytes and ideally, you write it using assembly language. The purpose of the bootstrap code is to load a larger piece of the OS or in the case of GRUB, other parts of the boot loader, into memory and run it. It's not enough to have a bootstrap program too. You need to mark the first sector as containing bootstrap code by setting the last to bytes of the 512 byte block to 0x55AA. That is, if I remember things correctly. If anyone knows better please feel free to correct me :)

---

### Post by CptPicard on 2007-06-11
Pardon me, but I think you're phrasing the question a bit strangely... I don't think there is much of an absolute minimum in terms of computer hardware that is needed in order to boot into an OS if the OS itself is near non-existent, as DOS was -- just a really basic command shell that just tossed a new program onto the CPU in its stead for its whole duration, no time sharing, not much in terms of memory or hardware abstractions... if you plan on writing your own minimal "OS", it would probably be along the lines of "find out where BIOS loads code after power gets turned on" and then just plug your command shell there. You don't even need a kernel process if you have a library of support code for hardware calls etc you compile statically into your programs.

Basic hardware requirements for your typical proper kernel OS that does memory protection are a timesharing clock in the CPU for process pre-emption and an MMU. If you intend you write your own OS from ground up to do all this for some esoteric piece of hardware, you're really good and you have too much time on your hands ;)

If you intend to use some kind of minimal Linux, on the other hand... check the kernel requirements against the box you've got. The mainstream Linux kernel requires the aforementioned features and thus doesn't run on a 286, for example, but there are pared-down forks for archaic machines. 

(I know I might be cutting corners in this explanation, forgive me... this gives the general idea anyway)

---

### Post by HackingYodel on 2007-06-12
As a learning tool I would give MenuetOS a look.
- Pre-emptive multitasking, multithreading, ring-3 protection
- Responsive GUI with resolutions up to 1280x1024, 16 million colours
- IDE: Editor/Macro Assembler for applications
- TCP/IP stack with Loopback & Ethernet drivers
- Network applications include ftp/http/mp3 servers
- Free-form application windows
- Hard real-time data fetch
- Fits on a single floppy 
[http://www.menuetos.net/index.htm](http://www.menuetos.net/index.htm)

It's all written in assembly language and pretty amazing for a floppy disk.

or if you really want to have you mind blown...

[http://www.colorforth.com/install.htm](http://www.colorforth.com/install.htm)

---

### Post by Tundro Walker on 2007-06-12
Sounds to me like someone's buying their school a new computer as his graduation present...or else he won't get to graduate...LOL!

---

