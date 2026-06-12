---
title: "Assembly Boot Loader"
date: 2006-01-05
forum: Programming Talk
---

### Post by richardhp on 2006-01-05
I have searched the forums, and the internet, for a solution to my problem.

I am writing a bootstrap loader for my computer as a sort of mini-project. I know a bit of assembly and am assembling it using as86. I have got some code from the internet and have cobbled together a boot sector on a floppy disk that loads up a second sector and prints something on the screen.

This is all very nice but I want to develop it further with the idea of keyboard inputs to make basic decisions etc. and make it into a mini os.

I haven't been able to find anything on this so far and was wondering if anyone can help. I am using int 16h to recieve keyboard input but I am not sure if bios supports this or whether I need keyboard drivers or something.

Here is the code for the second sector that gets loaded into memory then executed:

entry start

start:
	call clear_screen
        mov     ah,#0x03          ;cursor position      
        xor     bh,bh
        int     0x10

        mov     cx,#26            ;      
        mov     bx,#0x0007        ;      
        mov     bp,#mymsg	  ; 
        mov     ax,#0x1301        ;      
        int     0x10              ;
	call get_key

loop1:  jmp     loop1		  ;

clear_screen: 

	mov ah,#00 		  ;set int10h to set video mode 
	mov al,#03 		  ;select video mode
	int 0x10   		  ;clear the screen and set video mode
	ret

get_key:
	mov     ah,0x00          ;Read Key opcode
        int     0x16
        cmp     al,0x00          ;Special function?
        jz      get_key          ;If so, don't echo this keystroke
        cmp     al, 0x0d         ;Carriage return (ENTER)?
        jne     get_key
	mov	ah,0x09		 ;print character to stdout
	int	0x10

mymsg:
        .byte  13,10
        .ascii "Handling BIOS interrupts"

Any ideas???

---

### Post by coredump on 2006-01-05
Oh wow, I havn't had to refer to my copy of Ray Duncan's IBM ROM BIOS book in years!  But now it's all coming back to me...

Now, you're using BIOS function 00H and INT 16H to read a key, which is fine.  But you only call it once, and you ignore any non-ASCII keys.  Then, you use INT 10H function 09H to write it to the screen (also fine).  But I note that INT 10H function 09H needs some other parameters apart from the ASCII code, like a replication count in CX and page and attribute codes in BX.  I wonder if they're not getting set properly?

If I were you, I'd try outputting a fixed ASCII code with INT 10H function 09H, just to make sure that's working OK (the error may be in either the keyboard read calls or the screen output calls).  Then, I'd make a loop around the 'get_key' function so that you can output as much ASCII as you care to type in.

That way, you'll know that the ASCII-to-screen is OK, and you'll not get fooled by extraneous scancodes in the buffer from the keyboard's power-up state (or its reset state).

Great to see some assembler again!  Do let us know how you get on.

---

### Post by richardhp on 2006-01-08
cheers, will give that a go...

Ok, here's what i've done so far. I have altered it a little so that the routine getting character input is looped :

get_key:
	mov     ah,#0x00          ;Read Key opcode
        int     0x16

	mov	bh,#00
	mov	bl,#00
	mov	cx,#0x01
	mov	ah,#0x09		 ;print character to stdout
	int	0x10
	jmp get_key

But it just prints the startup message, then has a flashing cursor after it. As soon as I try and type something in it just freezes. I will keep trying though

---

### Post by coredump on 2006-01-08
In way way 'freezes'?  Does the cursor stop flashing?  I'd be surprised if it did, since it's being flashed in hardware by the 6845.  If you simply get no output, then you might suspect that the char-output routine isn't working.  That's why I'd suggest testing it with a few ASCII codes hard-coded in the program first.  Then you'll know that output is OK when you use it with ASCII codes from the input routine.

---

### Post by richardhp on 2006-01-08
Ok silly me. What you said first time should have worked, since I accidentally set the foreground colour to black so nothing showed up. That's why I thought it had frozen because the cursor disappeared etc. 

Anyway, thanks alot it now works like a charm. Hopefully I can move on now to something a little more complicated.

---

### Post by coredump on 2006-01-08
Ah, black text on a black background -- that'll be hard to read!

Glad to hear that it's all working properly now.

Oh, and just a thought: if you're using INT 16h function 00h, you won't be able to read the "enhanced" function keys (F11, F12, etc.).  If you want to read all the keys on a post-1987 keyboard, you'll need INT 16h function 10h.  There's also some trick to tell whether or not you have an "enhanced" keyboard, but I forget what it is right now.  I can look it up if you need it.

---

### Post by richardhp on 2006-01-10
will do

---

### Post by richardhp on 2006-05-06
Ok having fixed my problems, I have now got a roughly working kernel.

It is very simple but if you are interested then you can copy the code and use it for youself.

If anyone comes up with any ideas then feel free to post them and I will put them into my kernel. I know assembly is not that popular these days but I still like it!

Have a look at this: [http://linuxgazette.net/issue79/krishnakumar.html](http://linuxgazette.net/issue79/krishnakumar.html)

It is a good introdction to the concept of writing a bootstap loader. All I did was use the bootsector code to load up my own kernel. The code for which I will include here:

[http://www.electronicsponge.150m.com/kernel1.asm](http://www.electronicsponge.150m.com/kernel1.asm)

---

### Post by supirman on 2006-05-06
You can allow your kernel to use C code if you switch the processor to protected mode.  Also, if you download an emulator like bochs you can debug your code line by line so you can make sure things are working properly.  Bochs will let you use it's internal debugger, which will step through each assembly instruction, or you can compile it with gdb support so you can debug C if you'd like.  I had to port my company's bootloader from ppc to x86 so most of this is still pretty fresh in my head.

---

### Post by richardhp on 2006-05-26
that sounds neat, will give bochs a go.

i know about switching to protected mode but what sort of C code can i write? when i tried things like:

printf("Hello");

and looked at the assembly output of gcc it did some stuff with the registers, then had "call printf" which I presume is a system call. when i tried to assemble that it came up with an error saying unknown function printf or something like that.

I don't know much about this so how do i go about writing machine executable C code and how do i get it to output in flat-file format rather than with headers etc.

---

### Post by rplantz on 2006-05-26
[QUOTE=richardhp]
i know about switching to protected mode but what sort of C code can i write? when i tried things like:

printf("Hello");

and looked at the assembly output of gcc it did some stuff with the registers, then had "call printf" which I presume is a system call. when i tried to assemble that it came up with an error saying unknown function printf or something like that.[/QUOTE]

printf is a function in the C standard library, not a system call.

You need to link your assembly language with the appropriate C libraries.

I write in the gnu assembler, as. My hello world program looks like ```

# helloWorld.s
# Displays "Hello world." on the screen
# Robert G. Plantz -- 11 Jan. 2004

        .data                  # the data segment
hello:
        .string "Hello world.\n"

        .text                  # switch to text segment
        .globl  main

main:
        pushl   %ebp           # save caller's base pointer
        movl    %esp, %ebp     # establish our base pointer

        pushl   $hello         # pass address to function
        call    printf         # print the text string
        addl    $4, %esp       # delete the argument

        movl    $0, %eax       # return 0
        movl    %ebp, %esp     # restore stack pointer
        popl    %ebp           # restore caller's base pointer
        ret                    # back to calling function

```

I assemble it with ```

as --gstabs -o helloWorld.o helloWorld.s

```

(The --gstabs option allows you to use the debugger, gdb, on the final program.)

The gnu linker is ld. But if you use gcc, it will automatically go directly to the linking phase and link in the appropriate libraries:
```

gcc -o helloWorld helloWorld.o

```

---

### Post by richardhp on 2007-02-12
i got that to compile in linux and ran it in the bash prompt which worked great. How would i incorporate this into a boot loader program. can i get gcc to output a flat-binary that will still run when i boot into it?

also can i use gcc with the as86 or will i have to re-write all my code to as syntax?

---

