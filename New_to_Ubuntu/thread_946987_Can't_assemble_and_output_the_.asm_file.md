---
title: "Can't assemble and output the .asm file"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by syn_stanzer on 2008-10-13
```
;; Perform a 32-element FFT.

fft32 MACRO type
	LOCAL	b1b, c1b

;; Do a forward FFT only

	IF	type EQ 1
	call	x32_fft
	jmp	xmiddle_1
	ENDIF

;; Do a squaring

	IF	type EQ 2
	call	x32_fft
	call	xmiddle_2
;;	jmp	x32_finish_unfft
	ENDIF

;; Do a multiply

	IF	type EQ 3
	call	x32_fft
	call	xmiddle_3
	jmp	x32_finish_unfft
	ENDIF

;; Do a multiply with pre-FFTed inputs

	IF	type EQ 4
	call	xmiddle_4
	jmp	x32_finish_unfft
	ENDIF



	IF	type EQ 1
x32_fft:
	copy_7_words
	sub	eax, eax
b1b:	disp eight_reals_first_fft, 4*dist1, 8*dist1, 8
	lea	esi, [esi+dist1]	;; Next source pointer
	add	al, 256/4		;; Test loop counter
	jnc	b1b			;; Iterate if necessary
	lea	esi, [esi-4*dist1]	;; Restore source pointer

;; End common FFT code

	ret
	ENDIF


	IF	type EQ 2
x32_finish_unfft:
c1b:	disp eight_reals_last_unfft, 8, 4*dist1, 8*dist1
	lea	esi, [esi+dist1]	;; Next source pointer
	add	al, 256/4		;; Test loop counter
	jnc	c1b			;; Iterate if necessary
	lea	esi, [esi-4*dist1]	;; Restore source pointer

	fft_3_ret
	ENDIF
	ENDM
```

Hey guys when I try to assemble this with MASM32 it says that there is an error and needed "END" at the end. The problem is when I added the "END" at the end of the code it still pop out the error. Anyone of you could help because I need to get it done urgent.
Thanks

---

