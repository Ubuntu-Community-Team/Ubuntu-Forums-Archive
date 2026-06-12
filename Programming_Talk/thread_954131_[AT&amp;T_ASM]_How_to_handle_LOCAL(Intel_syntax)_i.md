---
title: "[AT&amp;T ASM] How to handle LOCAL(Intel syntax) in AT&amp;T"
date: 2008-10-20
forum: Programming Talk
---

### Post by syn_stanzer on 2008-10-20
Refer to the title, does any folks here knw how to handle LOCAL(Intel syntax) in GAS AT&T?!?

Thanks in advanced

---

### Post by snova on 2008-10-20
I think GAS has an assembler directive to switch between different syntaxes, but I don't remember what it is.

---

### Post by QsM on 2008-10-20
You want to use Intel syntax? If so enter the .intel_syntax directive

---

### Post by syn_stanzer on 2008-10-20
```

	# Copyright 1998-2004 - Just For Fun Software, Inc., all rights reserved
	# Author:  George Woltman
	# Email: woltman@alum.mit.edu
	#

	# ********************************************************
	# ********************************************************
	# ********************  FFT MACROS  **********************
	# ********************************************************
	# ********************************************************

	## Perform a 32-element FFT.

	.intel_syntax
	.macro fft32
	LOCAL b1b, c1b

	## Do a forward FFT only

	.if      type EQ 1
		call    x32_fft
		jmp     xmiddle_1
        .endif

	## Do a squaring

	.if      type EQ 2
		call    x32_fft
		call    xmiddle_2
	##      jmp     x32_finish_unfft
	.endif

	## Do a multiply

	.if      type EQ 3
		call    x32_fft
		call    xmiddle_3
		jmp     x32_finish_unfft
	.endif

	## Do a multiply with pre-FFTed inputs

	.if      type EQ 4
		call    xmiddle_4
		jmp     x32_finish_unfft
	.endif

	## Do FFT levels 1,2,3
	## Values 0-31 is real data.
	##
	## On input the 32-byte cache lines hold these data values:
	##      0       16      1       17
	##      2       ...
	##      ...     ...
	##      14      ...
	## On output the 32-byte cache lines hold these data values:
	##      0       4       1       5
	##      2       ...
	##      8       ...
	##      ...

	## Do 4 eight_reals_first_fft macros
	##      distance between fft data elements is 4

	.if      type EQ 1
	x32_fft: 
	        copy_7_words
		subl    %eax,%eax
	b1b: disp eight_reals_first_fft, 4*dist1, 8*dist1, 8
		leal    dist1(%esi),%esi        ## Next source pointer
		addb    $256/4, %al             ## Test loop counter
		jnc     b1b                     ## Iterate if necessary
		leal    esi-4*dist1,%esi        ## Restore source pointer

	## End common FFT code

		ret
	.endif

	## Do inverse FFT levels 1,2,3
	## On input the 32-byte cache lines hold these data values:
	##      0       4       1       5
	##      2       ...
	##      8       ...
	##      ...
	## On output the 32-byte cache lines hold these data values:
	##      0       16      1       17
	##      2       ...
	##      ...     ...
	##      14      ...

	## Do 4 eight_reals_last_unfft macros
	##      distance between fft data elements is 4

	.if      type EQ 2
	x32_finish_unfft: 
	c1b: disp eight_reals_last_unfft, 8, 4*dist1, 8*dist1
		leal    dist1(%esi),%esi        ## Next source pointer
		addb    $256/4, %al             ## Test loop counter
		jnc     c1b                     ## Iterate if necessary
		leal    esi-4*dist1,%esi        ## Restore source pointer
        fft_3_ret
        .endif
        .endm

	fft32

        .end


```

I have this portion of macro file need to be output to .o(object file in AT&T). When I assembled it the error followings show up.

```


test5.mac:107: Error: no such instruction: `local b1b,c1b'
test5.mac:107: Error: non-constant expression in ".if" statement
test5.mac:107: Error: junk at end of line, first unrecognized character is `E'
test5.mac:107: Error: non-constant expression in ".if" statement
test5.mac:107: Error: junk at end of line, first unrecognized character is `E'
test5.mac:107: Error: non-constant expression in ".if" statement
test5.mac:107: Error: junk at end of line, first unrecognized character is `E'
test5.mac:107: Error: non-constant expression in ".if" statement
test5.mac:107: Error: junk at end of line, first unrecognized character is `E'
test5.mac:107: Error: non-constant expression in ".if" statement
test5.mac:107: Error: junk at end of line, first unrecognized character is `E'
test5.mac:107: Error: non-constant expression in ".if" statement
test5.mac:107: Error: junk at end of line, first unrecognized character is `E'

```

Could anyone understand how to handle the LOCAL in AT&T? 
Thanks

---

### Post by boz on 2008-10-21
Are those local symbols?  If so, I don't see them being used anywhere... If they are local symbols, AT&T syntax requires them to be in the form .L1, .L2, etc.

---

### Post by syn_stanzer on 2008-10-21
> **boz said:**
> Are those local symbols?  If so, I don't see them being used anywhere... If they are local symbols, AT&T syntax requires them to be in the form .L1, .L2, etc.


Hi Boz, did u mean I need to change the "LOCAL b1b, c1b" to ".L1 b1b, c1b"??

---

### Post by boz on 2008-10-21
Well, to begin with, I'm completely unfamiliar with the LOCAL keyword.  Is that supposed to declare a local variable or a local symbol?  Like I said, I couldn't see where you were using them in your code.  If they're supposed to be local variables, I suggest you just use the stack.  But, yes, if they're local symbols, you have to do:

.L1 blb
.L2 clb

Oh, never mind.  I see them now. Yeah, try the above.  They're local symbols.

---

### Post by syn_stanzer on 2008-10-21
Hi Boz, I just tested 

.L1 blb
.L2 clb

but it doesn't work as well, it comes up with the error unknown-pseudo op

---

### Post by boz on 2008-10-22
Try commenting out the LOCAL declaration entirely and in place of blb: and cbl: labels, use .1: and .2:.

[URL="http://docs.sun.com/app/docs/doc/817-5477/ennab?a=view"]
http://docs.sun.com/app/docs/doc/817-5477/ennab?a=view[/URL]

Even though that's Solaris' x86 asm, I believe it uses the same syntax.  Sorry, I have never used local symbols, so this is a learning experience for me, too.  ;)

---

