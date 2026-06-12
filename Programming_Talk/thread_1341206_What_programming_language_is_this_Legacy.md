---
title: "What programming language is this? Legacy"
date: 2009-11-29
forum: Programming Talk
---

### Post by MCBTunes on 2009-11-29
I found a notebook that has hand written code my dad wrote many years ago. I am hoping you guys can help me identify it as I haven't been around very long. 

Here are some of the distinguishing features:
-uses REM for comments
-every line is numbered and there are many goto's
eg 
17 IF T$ = "CB" THEN 20
18 GOTO 15
-? appears to be the print command 
eg 
210 ? "Enter the ... (I)"

I'd like to use his code within a web service I am designing in java with the use of the exec command if I can.

Thoughts?

---

### Post by qalimas on 2009-11-29
I've not been around too long either, but it reminds me of BASIC.


I know Windows batch files use rem for comments, so that is also a possibility?

Edit: I think '?' is for input, that reminds me of the BASIC variant my TI-89 uses.

---

### Post by grayrainbow on 2009-11-29
> **qalimas said:**
> I've not been around too long either, but it reminds me of BASIC.


I know Windows batch files use rem for comments, so that is also a possibility?
Microsoft first product is BASIC, so it's normal for .bat files to have similarities to BASIC.
[http://en.wikipedia.org/wiki/BASIC]("http://en.wikipedia.org/wiki/BASIC")
But "?" as PRINT is not familiar to me.

---

### Post by lisati on 2009-11-29
Yes, looks like BASIC, and "?" for "PRINT" is one I've seen before. 
REM is also commonly used for comments in BASIC

Most likely it's a "BAS" file, not a "BAT" file.

---

### Post by nvteighen on 2009-11-29
Yup, it clearly seems to be a BASIC dialect:

1. Type definition suffixed to the variable's name (T$)
2. = used in If instead of ==.
3. REM
4. Line numbers

---

### Post by grizzler on 2009-11-29
Using ? for PRINT or INPUT vaguely reminds me of BASIC for the Commodore VIC-20 or Commodore 64. Only about thirty years ago, so I could be mistaken... ;)

---

### Post by lisati on 2009-11-29
> **grizzler said:**
> Using ? for PRINT or INPUT vaguely reminds me of BASIC for the Commodore VIC-20 or Commodore 64. Only about thirty years ago, so I could be mistaken... ;)

None of the dialects of basic I've used ever used "?" for input, it was a shorthand for "print".

---

### Post by Krupski on 2009-12-02
> **MCBTunes said:**
> I found a notebook that has hand written code my dad wrote many years ago. I am hoping you guys can help me identify it as I haven't been around very long. 

Here are some of the distinguishing features:
-uses REM for comments
-every line is numbered and there are many goto's
eg 
17 IF T$ = "CB" THEN 20
18 GOTO 15
-? appears to be the print command 
eg 
210 ? "Enter the ... (I)"

I'd like to use his code within a web service I am designing in java with the use of the exec command if I can.

Thoughts?

Looks like BASIC to me.

The "?" is a shortcut for "PRINT"

Although usually the "?" token shows as "PRINT" when the program is listed.

For example...

Type this:

10 ?"Hello there"

Then list it:

10 PRINT"Hello there"

---

### Post by ricegf on 2009-12-02
The BASIC for Atari computers (e.g., 800, 400, 1200xl) also used "?" as the print command, and left it as "?" when you listed the program. The other syntax also perfectly matches Atari as well - though the explosion of home computers in the mid-1980's left no shortage of BASIC dialects from which to choose. ;-)

To reuse the code, you can find some free BASIC compilers at [http://www.thefreecountry.com/compilers/basic.shtml](http://www.thefreecountry.com/compilers/basic.shtml). Vintage BASIC looks promising...

---

### Post by wmcbrine on 2009-12-02
> **ricegf said:**
> though the explosion of home computers in the mid-1980's left no shortage of BASIC dialects from which to choose.Many of them (including Atari, Commodore and TRS-80 versions) were just Microsoft BASIC, modified to fit the particular system. One notable exception was Sinclair BASIC. I can rule that one out here -- it didn't use "?" for PRINT. But I don't think we have enough info to narrow it down much further.

---

### Post by bit mad on 2009-12-02
Oh stop it, please, you're making me feel so old :D

As someone who cut his teeth back in the early 1980s on BASIC machines like the ZX80 / 81 / Spectrum *( switched on straight into a BASIC interpreter running from the ROM - only a few kB of RAM, pitiful screen res, bleeps sound only, no external storage except via audio on cassette tapes! )* ... it's almost hard to believe that anyone could fail to recognise it, LOL

That's progress for ya :P

As for running the code now.... well... BASIC was so simple back then that straightforward text based stuff should be easy to convert. If the code was drawing to the screen at specific coordinates, it could get a bit more hairy though.

---

### Post by fiddler616 on 2009-12-02
> **qalimas said:**
> 
Edit: I think '?' is for input, that reminds me of the BASIC variant my TI-89 uses.
The question mark operator is meaningless in all TI-BASIC variants, but is the default output when using the input statement. Examples:

```
:Input X
:Disp X
```
outputs
```
?3
    3
```
(where three is an arbitrary number I inputted)
Meanwhile,
```
:Input "Enter a number:",X
:Disp X
```
outputs
```
Enter a number:3
    3
```
(note: no question mark since a string was provided.)

---

### Post by openuniverse on 2009-12-03
.

---

### Post by underquark on 2009-12-03
Yeh, it's a BASIC variant.  I last used it in earnest on an Apple II in 1981.  The processor - 6502 - was also very "basic" and Apple had actually printed - on paper - the entire OS ROM so to do anything fast we often just dropped a few POKES and PEEKS into the BASIC program to use machine code and access subroutines in the ROM.

IF there are lots of GOTOs it might be very old (or very limitted), i.e. predating the GOSUB command.

---

### Post by lisati on 2009-12-03
That reminds me. One Z80-based machine I once had (it died some time round 1992 or '93 in a puff of acrid smoke when being turned on) seems to have had firmware related to that of the TRS-80. To cut a long and potentially boring story short, I was able to adapt an ASM listing for the TRS-80 in a magazine to re-enable "ON ... GOTO" and "ON ERROR" in my machine - the code was still in ROM but the tokens had been hijacked for use with the minimal sound and graphics capabilities of my machine. Due to laziness on my part I didn't completely decode lines that used the reinstated functions, which consequently were displayed as something like "ON SOUND GOTO" instead of "ON ERROR GOTO" - a nice way of obfuscating source!

---

### Post by nvteighen on 2009-12-03
> **underquark said:**
> 
IF there are lots of GOTOs it might be very old (or very limitted), i.e. predating the GOSUB command.

Yeah, the GOSUB command... That's also very old... QuickBASIC did a great job by introducing SUBs and FUNCTIONs (SUBs are what in C are "void returning functions") that you called using the normal function calling syntax **f(args, ...)**. IMO, QBASIC was a pretty well planned improvement and correction of BASIC. MS QuickBASIC 4.5 (from which the well-known QBASIC 1.1 descended as a subset, lacking compiler and linker) had a native compiler that explicitly forbid the usage of GOTO... if you wanted to create a standalone executable, you had to use structured programming.

Sad that QuickBASIC was replaced by Visual Basic...

---

### Post by openuniverse on 2009-12-03
.

---

### Post by Puzzled Guy on 2009-12-05
Why not ask your dad?

---

