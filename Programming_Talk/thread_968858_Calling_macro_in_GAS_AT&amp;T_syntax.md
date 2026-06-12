---
title: "Calling macro in GAS AT&amp;T syntax"
date: 2008-11-03
forum: Programming Talk
---

### Post by syn_stanzer on 2008-11-03
May I knw the way of calling macro in GAS AT&T syntax?
This is my codes, I wanted to call the macro itself to clarify the accuracy of the codes. Thanks

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

	.macro fft32 type
	.local b1b, c1b

        ## Do a forward FFT only

	.ifc	type, 1
		call    x32_fft
		jmp     xmiddle_1
        .endif

	## Do a squaring

	.ifc 	type, 2
		call    x32_fft
		call    xmiddle_2
	##      jmp     x32_finish_unfft
	.endif

	## Do a multiply

	.ifc 	type, 3
		call    x32_fft
		call    xmiddle_3
		jmp     x32_finish_unfft
	.endif

	## Do a multiply with pre-FFTed inputs

	.ifc 	type, 4
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

	.ifc	type, 1
	x32_fft: 
	        copy_7_words                    ## macro
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

	.ifc	type, 2
	x32_finish_unfft: 
	c1b: disp eight_reals_last_unfft, 8, 4*dist1, 8*dist1
		leal    dist1(%esi),%esi        ## Next source pointer
		addb    $256/4, %al             ## Test loop counter
		jnc     c1b                     ## Iterate if necessary
		leal    esi-4*dist1,%esi        ## Restore source pointer

        fft_3_ret                               ## macro
        .endif
        .endm
       
        fft32 2       			        ## call the macro itself, fft32

	.end
```

---

