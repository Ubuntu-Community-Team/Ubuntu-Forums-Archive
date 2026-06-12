---
title: "Best programming language for making an assembler"
date: 2012-02-23
forum: Programming Talk
---

### Post by alegomaster on 2012-02-23
I am working on this little secret project in which I am making a 32-bit RISC architecture which I am planning to also make a very simple OS for it, and an assembler for the ISA that I developed.

 I am wondering what programming language that you suggest to make the assembler from. I only know how to program in C and objective-C (Its a long story how I learned objective-C) so I am hoping for a language similar to those.

---

### Post by haqking on 2012-02-23
> **alegomaster said:**
> I am working on this little secret project in which I am making a 32-bit RISC architecture which I am planning to also make a very simple OS for it, and an assembler for the ISA that I developed.

 I am wondering what programming language that you suggest to make the assembler from. I only know how to program in C and objective-C (Its a long story how I learned objective-C) so I am hoping for a language similar to those.

FASM or NASM

But you can write the assembly language into a text editor

---

### Post by alegomaster on 2012-02-23
> **haqking said:**
> FASM or NASM

But you can write the assembly language into a text editor

I am confused by what you mean? FASM and NASM are x86 assemblers.

---

### Post by haqking on 2012-02-23
> **alegomaster said:**
> I am confused by what you mean? FASM and NASM are x86 assemblers.

ahh sorry i missed the RISC part.

Spim is a emulator for mips, is this any good

[http://pages.cs.wisc.edu/~larus/spim.html#qtspim](http://pages.cs.wisc.edu/~larus/spim.html#qtspim)

---

### Post by alegomaster on 2012-02-23
I am asking what language I should use to make an assembler from, not an example assembler. Thanks though, I am actually designing my cpu with a modified MIPS instruction set.

---

### Post by alexfish on 2012-02-23
that,s interesting 

Say for instance you know the instruction set for the cpu / risk or what everdoes not come into it
the instruction set is the representation of the 0's and 1' you put in and the results is what you get out , this relates to the cpu your designing

you can call the instruction set any name you wish , general it would follow the some naming "conventions" or the accepted RE X86

can have a look here Re Microchip
[http://en.wikipedia.org/wiki/PIC_microcontroller](http://en.wikipedia.org/wiki/PIC_microcontroller)

from this you make the assembler which reads line by line each instruction and then looks up the representation as the 0's and 1's


basically you end up with a data base : instruction x = x in 0's and 1's or values in Hex

as for the assembler the front end can be any text editor,  have you look at Kate

then you need to assemble it , for that you need a program , any pragraming language will do ,

along as your program unstands how to look up the values, and place them in the correct order and the byte width in hex (byte code)

a number of years xyz ago just for fun did a visual assembler (in visual basic) for a microchip 
say if wanted a serial port function of the chip , all you had to do was drag the serial port onto the form then edit the data required for the serial port ,that was fun. since you could replicate the results before down loading ,

any BASIC programming language will do the job,

One of the members pointed out Fasm and Nasm then also there is Mpasm , they are worth looking up to see what they do

have fun

alexfish

---

### Post by ofnuts on 2012-02-24
> **alexfish said:**
> that,s interesting 

Say for instance you know the instruction set for the cpu / risk or what everdoes not come into it
the instruction set is the representation of the 0's and 1' you put in and the results is what you get out , this relates to the cpu your designing

you can call the instruction set any name you wish , general it would follow the some naming "conventions" or the accepted RE X86

can have a look here Re Microchip
[http://en.wikipedia.org/wiki/PIC_microcontroller](http://en.wikipedia.org/wiki/PIC_microcontroller)

from this you make the assembler which reads line by line each instruction and then looks up the representation as the 0's and 1's


basically you end up with a data base : instruction x = x in 0's and 1's or values in Hex

as for the assembler the front end can be any text editor,  have you look at Kate

then you need to assemble it , for that you need a program , any pragraming language will do ,

along as your program unstands how to look up the values, and place them in the correct order and the byte width in hex (byte code)

a number of years xyz ago just for fun did a visual assembler (in visual basic) for a microchip 
say if wanted a serial port function of the chip , all you had to do was drag the serial port onto the form then edit the data required for the serial port ,that was fun. since you could replicate the results before down loading ,

any BASIC programming language will do the job,

One of the members pointed out Fasm and Nasm then also there is Mpasm , they are worth looking up to see what they do

have fun

alexfish
Writing an assembler is a bit more complicated than this. To create significant programs the assembler should support macro-pos, linkable objects, etc... 

An obvious solution is to adapt an existing open-source assembler such as NASM.

---

### Post by haqking on 2012-02-24
> **alegomaster said:**
> I am asking what language I should use to make an assembler from, not an example assembler. Thanks though, I am actually designing my cpu with a modified MIPS instruction set.

I dont understand what you are asking.

You ask what language ? well the language is Assembler.

And you can write it in any text editor as i mentioned before and mentioned above,

---

### Post by alexfish on 2012-02-24
> **ofnuts said:**
> Writing an assembler is a bit more complicated than this. To create significant programs the assembler should support macro-pos, linkable objects, etc... 

An obvious solution is to adapt an existing open-source assembler such as NASM.

Hence
along as your program unstands how to look up the values, and place them  in the correct order and the byte width in hex (byte code)

long time ago we sat with these

[http://www.derivedlogic.com/Z80%20Microcomputer/z80micro.html](http://www.derivedlogic.com/Z80%20Microcomputer/z80micro.html)

---

### Post by ofnuts on 2012-02-24
> **alexfish said:**
> Hence
along as your program unstands how to look up the values, and place them  in the correct order and the byte width in hex (byte code)

long time ago we sat with these

[http://www.derivedlogic.com/Z80%20Microcomputer/z80micro.html](http://www.derivedlogic.com/Z80%20Microcomputer/z80micro.html)
I did that, too... and my first real program, that was an assembler for [this]("http://en.wikipedia.org/wiki/Texas_Instruments_TMS9900"), was in FORTRAN. However, if you want an "assembler" and not a "toy assembler", you must be prepared to handle things like
```

ONE_K equ 1024
MEMORY_LIMIT equ 64*ONE_K-1

```
and suddenly the assembler is a bit more than just looking up values and moving bytes at the right place, even if it's simpler that  a full-blown compiler.

---

### Post by alexfish on 2012-02-24
> **ofnuts said:**
> I did that, too... and my first real program, that was an assembler for [this]("http://en.wikipedia.org/wiki/Texas_Instruments_TMS9900"), was in FORTRAN. However, if you want an "assembler" and not a "toy assembler", you must be prepared to handle things like
```

ONE_K equ 1024
MEMORY_LIMIT equ 64*ONE_K-1

```and suddenly the assembler is a bit more than just looking up values and moving bytes at the right place, even if it's simpler that  a full-blown compiler.

yes you correct in what you say , fortran has the advantages ,  The OP wants a simple OS

and it is a project , you could even make life easier by looking here

[http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/RollYourOwn/index.html](http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/RollYourOwn/index.html)

---

### Post by alegomaster on 2012-02-24
> **alexfish said:**
> yes you correct in what you say , fortran has the advantages ,  The OP wants a simple OS

and it is a project , you could even make life easier by looking here

[http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/RollYourOwn/index.html](http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/RollYourOwn/index.html)

Thanks I am looking into the link you provided. For people who did not understand what I said, I asked what language I should use to code an assembler. The front end (portion you write the assembly code in) will be a text editor program.

---

### Post by haqking on 2012-02-25
> **alegomaster said:**
> Thanks I am looking into the link you provided. For people who did not understand what I said, **I asked what language I should use to code an assembler**. The front end (portion you write the assembly code in) will be a text editor program.


Well i am still being dumb then i guess, as you write assembler in assembly language

---

### Post by Barrucadu on 2012-02-25
> **haqking said:**
> Well i am still being dumb then i guess, as you write assembler in assembly language

He is not writing **assembly**. He is writing an **assembler** - a program that turns assembly code into a binary file.

---

### Post by alexfish on 2012-02-25
> **alegomaster said:**
> Thanks I am looking into the link you provided. For people who did not understand what I said, I asked what language I should use to code an assembler. The front end (portion you write the assembly code in) will be a text editor program.

Thanks..

As I mentioned earlier , re Fasm although Had already been Mentioned,, + comments To use it as

For any Purist Of Purist , will always Be purist , you Mention  C , that at the end of the day is The real solution , , by its construction , but for each cpu then you need the compiler associated ,, RE x86 and amd 64 , so if have c code as file then if want to run the program on the system it has to be compiled, cut short here. Look here , sorry last link dead: look here: [http://www.cs.sjsu.edu/~louden/cmptext/](http://www.cs.sjsu.edu/~louden/cmptext/)

so back to BASIC ,, as mentioned as a project Serial port in Visual Basic, can try googling RE , assembler with Visual Basic ,, you may find examples, 

In early days of computing , Had used a BBC computer its default language was BASIC with inline Assembler. I learned a lot from that,

The reason of mentioning Fasm and Basic , There is a program out there now called PureBasic , with an inline assembler , using FASM, you can learn a lot from that , worth looking up if of younger generation.
link
[http://flatassembler.net/examples.php](http://flatassembler.net/examples.php)

I only Mention these things Since not all readers have the Knowledge to which some have , and some readers are not members of the forum.

Also with Ubuntu coming of age So to speak , Can be a good Platform for Education, + this Forum is worth its wait in gold.

Enjoy.

alexfish

---

### Post by haqking on 2012-02-25
> **Barrucadu said:**
> He is not writing **assembly**. He is writing an **assembler** - a program that turns assembly code into a binary file.

ahh good point,. yeah my bad sorry for that, missed the different terms there.

Cheers

---

### Post by Bachstelze on 2012-02-25
> **haqking said:**
> I dont understand what you are asking.

You ask what language ? well the language is Assembler.

And you can write it in any text editor as i mentioned before and mentioned above,

The language is "assembly". The assembler is the program that translates assembly code to machine code. (Some people call the language "assembler" as well, but it's obviously not what is meant here.)

*EDIT:* Oops, didn't see there was a second page. ^^;

---

### Post by haqking on 2012-02-25
> **Bachstelze said:**
> The language is "assembly". The assembler is the program that translates assembly code to machine code. (Some people call the language "assembler" as well, but it's obviously not what is meant here.)

*EDIT:* Oops, didn't see there was a second page. ^^;

yeah it was me being blind and not reading properly.

Back to SWTOR for me ;-)

---

### Post by alexfish on 2012-02-25
one more link to look at

[http://mikeos.berlios.de/write-your-own-os.html](http://mikeos.berlios.de/write-your-own-os.html)

another one for history , 

[http://wiki.osdev.org/UEFI](http://wiki.osdev.org/UEFI)

Oh by the "little secret project"  Tut Tut ,are you going to keep it secret for ever.

[http://www.personal.kent.edu/~rmuhamma/Compilers/compiler.html]("http://www.personal.kent.edu/%7Ermuhamma/Compilers/compiler.html")

the link to Compilers By Construction may be dead . have placed link at Post #15 : where Mentioned

just in case you miss one of the Links

Have a look at this one 

[http://www.personal.kent.edu/~rmuhamma/OpSystems/os.html](http://www.personal.kent.edu/~rmuhamma/OpSystems/os.html)

---

### Post by alegomaster on 2012-02-25
Thanks! I will use those for reference. I will probably reveal my project in March 2013 (not 2012), because I have to still do a lot of work, and I don't want anybody stealing my idea.

---

### Post by alexfish on 2012-02-26
last bit in the chain

[http://harryjoy.wordpress.com/2011/08/15/assembler-in-c/](http://harryjoy.wordpress.com/2011/08/15/assembler-in-c/)

---

### Post by alegomaster on 2012-02-26
Thanks for the help. I am not starting assembler design until Summer(I might do it later) so I am going to mark this thread solved, and if I ever need help with anything, I will be sure to ask you guys. 
:-) Linus style smilely ftw)

---

### Post by alexfish on 2012-02-27
Question

Can I short cut any of this , or is there any tool that could help

MM! Possible .

What do most linux systems have

Here is a Clue

RE: binary format tcl

[http://tmml.sourceforge.net/doc/tcl/binary.html](http://tmml.sourceforge.net/doc/tcl/binary.html)

look up tcl

[http://wiki.tcl.tk/11765](http://wiki.tcl.tk/11765)

---

### Post by trent.josephsen on 2012-02-27
> **alegomaster said:**
> Thanks! I will use those for reference. I will probably reveal my project in March 2013 (not 2012), because I have to still do a lot of work, and I don't want anybody stealing my idea.

You may not realize it, because you're still new to this, but ideas are a dime a dozen.  And, frankly, nothing simple enough for someone of your experience* to develop in a matter of a few months or years is going to be of any significant economic value except as a learning tool to you.

* I admit I'm making a few assumptions about your experience -- you didn't mention a degree, so if you have one it's probably not closely related; I was amused to find a comment by myself on a post in which you claimed "basic knowledge of C, and computer science", which is only like 8 months old; and many of your posts are flavored with that elusive combination of overconfidence and naivete that means you haven't yet realized how much you don't know (an attitude with which I am intimately familiar, and which I had at the age I guess you probably are now).

TL;DR -- have fun, but don't take yourself too seriously.

---

### Post by alexfish on 2012-02-27
Though put this one for younger generation

Playing assembler:

```
#!/bin/sh
# the next line restarts using tclsh \
exec tclsh "$0" "$@"

 namespace eval asm {
    proc asm body {
        variable mem
        catch {unset mem} ;# good for repeated sourcing
        foreach line [split $body \n] {
            foreach i {label op args} {set $i ""}
            regexp {([^;]*);} $line -> line ;# strip off comments
            regexp {^ *(([A-Z0-9]+):)? *([A-Z]*) +(.*)} [string toupper $line]\
                 ->  -   label           op       args
                 puts label=$label,op=$op,args=$args
            if {$label!=""} {set sym($label) $PC}
            if {$op==""}     continue
            if {$op=="DB"}  {set mem($PC) [convertHex $args]; incr PC; continue}
            if {$op=="EQU"} {set sym($label) [convertHex $args]; continue}
            if {$op=="ORG"} {set PC [convertHex $args]; continue}
            regsub -all ", *" $args " " args ;# normalize commas
            set mem($PC) "$op $args"
            incr PC
        }
        substituteSymbols sym
        dump   sym
    }
    proc convertHex s {
        if [regexp {^([0-9A-F]+)H$} [string trim $s] -> s] {set s [expr 0x$s]}
        set s
    }
    proc substituteSymbols {_sym} {
        variable mem
        upvar $_sym sym
        foreach i [array names mem] {
            set tmp [lindex $mem($i) 0]
            foreach j [lrange $mem($i) 1 end] {
                if {[array names sym $j]==$j} {set j $sym($j)}
                lappend tmp $j
            }
            set mem($i) $tmp
        }
    }
    proc dump {_sym} {
        variable mem
        upvar $_sym sym
        foreach i [lsort -integer [array names mem]] {
            puts [format "%04d %s" $i $mem($i)]
        }
        foreach i [lsort [array names sym]] {
            puts [format "%-10s: %04x" $i $sym($i)]
        }
    }
    proc run {{pc 255}} {
        variable mem
        foreach i {A B C D E Z} {set ::$i 0}
        while {$pc>=0} {
            incr pc
            #puts "$mem($pc)\tA:$::A B:$::B C:$::C D:$::D E:$::E Z:$::Z"
            eval $mem($pc)
        }
    }

#----------------- "machine opcodes" implemented as procs

    proc ADD  {reg reg2}  {set ::Z [incr ::$reg [set ::$reg2]]}
    proc ADI  {reg value} {set ::Z [incr ::$reg $value]}
    proc CALL {name}      {[string tolower $name] $::A}
    proc DCR  {reg}       {set ::Z [incr ::$reg -1]}
    proc INR  {reg}       {set ::Z [incr ::$reg]}
    proc JMP  where       {uplevel 1 set pc [expr $where-1]}
    proc JNZ  where       {if $::Z {uplevel 1 JMP $where}}
    proc JZ   where       {if !$::Z {uplevel 1 JMP $where}}
    proc MOV  {reg adr}   {variable mem; set ::$reg $mem($adr)}
    proc MVI  {reg value} {set ::$reg $value}
 }

#-- Now testing:

 asm::asm {
        org  100     ; the canonical start address in CP/M
        jmp  START   ; idiomatic: get over the initial variable(s)
 DONE:  equ  0       ; warm start in CP/M ;-)
 MAX:   equ  5
 INCR:  db   2       ; a variable (though we won't vary it)
 ;; here we go...
 START: mvi  c,MAX   ; set count limit
        mvi  a,0     ; initial value
        mov  b,INCR
 LOOP:  call puts    ; for now, fall back to Tcl for I/O
        inr  a
        add  a,b     ; just to make adding 1 more complicated
        dcr  c       ; counting down..
        jnz  LOOP    ; jump on non-zero to LOOP
        jmp  DONE    ; end of program
        end
 }
```The source: just in case can't in tcl's cavern of Knowledge 
[http://wiki.tcl.tk/1613](http://wiki.tcl.tk/1613)

also check this out

[http://wiki.tcl.tk/3474](http://wiki.tcl.tk/3474)

alexfish

---

