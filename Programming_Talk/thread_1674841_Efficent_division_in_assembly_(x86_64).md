---
title: "Efficent division in assembly (x86_64)"
date: 2011-01-24
forum: Programming Talk
---

### Post by WinstonChurchill on 2011-01-24
**EDIT: **Believe it or not, I actually do know how to spell "Efficient" - my apologies...

In what can only be described as a blatant foray into the masochistic, I decided I was going implement an HTTP webserver in amd64 assembly for Linux. The project is ongoing (and probably will be forever), but I've really been intrigued by some of the problems that I've encountered while writing it. 

The first really interesting thing I had to do was convert the size of a file returned by the fstat() syscall into ASCII digits to send in the "Content-Length:" HTTP header; so I had to convert an unsigned quadword integer into it's ASCII base-10 equivalent. Obviously, you just divide by 10 (0xA), store the remainder as the next ASCII digit, and keep going until your quotient is zero. 

I wanted to play with some different ways of doing this and their possible advantages/disadvantages, so I came up with the following to test the implementations discussed below:
```

**;;; RunTimeTester:**
%define NUMBEROFQWORDS 10000000
;========================================================================================================;
;;; The ASCII-expressed decimal representation of an unsigned qword will at most be 20 bytes long.
;;; For simplicity, we truncate this to 16 bytes of length. Unfortunately, this will limit us sending
;;; blocks of data no longer than 8.882 PiB (9094.95 TiB) - however if needed we will still be able to
;;; serve files up to the 64-bit 16 EiB (16777216 TiB) limit using chunked transfer-encoding. We will
;;; store the resulting string in r9:r10, and move it to memory once the conversion is completed.

[bits 64]                      ; 64-bit code

section .data                  ; Data segment

Filename:
db "/dev/urandom",0x00         ; NULL-terminated path for open(...) call
DataToConvert:
resq NUMBEROFQWORDS            ; Reserve space for 10 million quadwords (~76 MB)
dq 0xffffffffffffffff          ; End of array terminator

section .text
global _start
_start:

;;; Open /dev/urandom
mov rax,2                      ; open(...) is x64 syscall #2
mov rdi,Filename               ; The filename (null-terminated)
xor rsi,rsi                    ; O_RDONLY
syscall

;;; Now populate the array with random data
;;; On my laptop /dev/urandom can be read at about 3.6 MB/s
mov rdi,rax                    ; The file descriptor from before
xor rax,rax                    ; read(...) is x64 syscall #0
mov rsi,DataToConvert          ; Output to memory for conversion
mov rdx,NUMBEROFQWORDS*8       ; Length to read, in bytes
syscall

cmp rax,NUMBEROFQWORDS*8       ; If we didn't get all the data...
jne Die                        ; ...exit the program

mov r15,DataToConvert          ; Prime r15 with the source of our random data

TimeTestingLoop:

;========================================================================================================;
;=========================== ONLY THE PART INSIDE THESE LINES MAY BE CHANGED ============================;
;========================================================================================================;

;;; (Insert respective code here)

;========================================================================================================;
;=========================== ONLY THE PART INSIDE THESE LINES MAY BE CHANGED ============================;
;========================================================================================================;

add r15,8                              ; Move up to the next item in the array
cmp qword [r15],0xffffffffffffffff     ; If the new memory is equal to -1...
jne TimeTestingLoop                    ; ...we're done - otherwise keep going

Die:
;; Call exit(EXIT_ SUCCESS)
mov eax,60                             ; exit() is x64 syscall #60
xor rdi,rdi                            ; EXIT_SUCCESS = 0
syscall 

```This works extremely well, because the syscall that populates the memory with random digits will be counted in the "System" field of the 'time' command's output. So as long as we keep the above the same, it will give us a pretty accurate idea of what is faster than what.

I first implemented the division in the most obvious way:
```

**;;; Conversion1:**
mov rax,[r15]                  ; Load the quadword value to convert
mov rbx,0x000000000000000a     ; Constant for the division
mov rcx,16                     ; Counter for the expansion loop
mov rsi,0x3030303030303030     ; Constant for converting bytes to ASCII-expressed digits
xor r9,r9                      ; Zero out the registers for the result
xor r10,r10

;;; Do the first half of the conversion:
DoExpansion:
shld r9,r10,8                  ; Shift the most significant byte of r10 into r9...
shl r10,8                      ; ...and shift it into nothingness from r10 (make room for next byte)
xor rdx,rdx                    ; The dividend is taken as rdx:rax, so we must zero out rdx
div rbx                        ; Execute the divison
or r10,rdx                     ; Put the ASCII digit in the least significant byte of r10
loop DoExpansion

or r9,rsi                      ; Convert to ASCII coding
or r10,rsi                     ; (must use register for qword OR operation)

```The runtimes were:

[LIST]
[*]Intel Core 2 @ 0.8Ghz: 7.160s
[*]Intel Core 2 @ 1.3Ghz: 4.400s
[*]AMD K8 @ 2.2 Ghz: 5.730s
[*]AMD K9 @ 3.1Ghz: 4.090s
[*]AMD K10 @ 3.4Ghz: 2.790s
[/LIST]
I've always read about "Magic Divsion", and I really wanted to try it just for the fun of it - I honestly didn't expect a great deal of improvement on modern CPU's... 
```

**;;; Conversion2:**
mov rax,[r15]                  ; Load the quadword value to convert
mov rcx,16                     ; Counter for the expansion loop
mov rsi,0x000000000000000a     ; Constant for rounding to obtain the remainder
mov r8,0x199999999999999a      ; Constant for the division
xor r9,r9                      ; Zero out the registers for the result
xor r10,r10

;;; Do the first half of the conversion:
DoExpansion:
shld r9,r10,8                  ; Shift the most significant byte of r10 into r9...
shl r10,8                      ; ...and shift it out of r10 (the shld instruction doesn't)
mul r8                         ; Execute the magical division (inverse of 10 = 0x19...)
mov rdi,rdx                    ; Save the quotient (the next multiply will overwrite it)
mul rsi                        ; Multiply the decimal part of the result by 0xa to get the remainder
mov rax,rdi                    ; Restore the working quotient
or r10,rdx                     ; Put the digit in the least significant byte of r10
loop DoExpansion

mov r8,0x3030303030303030
or r10,r8
or r9,r8

```The results were startlingly faster on every CPU variant I had. The runtimes were:

[LIST]
[*]Intel Core 2 @ 0.8Ghz: 2.240s
[*]Intel Core 2 @ 1.3Ghz: 1.380s
[*]AMD K8 @ 2.2 Ghz: 0.920s
[*]AMD K9 @ 3.1Ghz: 0.660s
[*]AMD K10 @ 3.4Ghz: 0.580s
[/LIST]
The most amazing result were the AMD K8 and K9 - from 5.730s and 4.090s with 'div' to 0.920 and 0.660s with 'mul'. 

Now, I really wanted to find a way to squeeze a little more efficiency out of this. My original angle was to find a way to eliminate the second 'mul' instruction necessary to obtain the remainder, but I couldn't come up with a way to do that. I considered dividing by 8 and by 16 using right shifts, but neither is close enough to work. 

In my searching, I came across the antiquated XLATB instruction in an old assembly reference manual, and that prompted my third approach: shift all but the most significant byte of the remainder out of it's register, and use it as a memory offset for a table with the respective ASCII values stored in the right places. I really didn't think it would be faster, but it would be interesting to try, so I did it. 
```

**;;; Conversion3:**
segment .data
  ConvTable:                   
    db 0x30
    times 24 db 0x21
    db 0x31
    times 25 db 0x21
    db 0x32
    times 24 db 0x21
    db 0x33
    times 25 db 0x21
    db 0x34
    times 25 db 0x21
    db 0x35
    times 24 db 0x21
    db 0x36
    times 25 db 0x21
    db 0x37
    times 24 db 0x21
    db 0x38
    times 25 db 0x21
    db 0x39
segment .text

mov rax,[r15]                          ; Load the qword to convert
mov rcx,16                             ; Counter for the conversion loop
mov rsi,ConvTable                      ; Address of table for later XLATB instruction
mov r8,0x199999999999999a              ; Multiplicative inverse of 10d (0xa)
xor r9,r9                              ; Zero out registers for the ASCII string
xor r10,r10                            

DoConv:
shld r9,r10,8                          ; Shift the most significant byte of r10 into r9
shl r10,8                              ; (shld only shifts in, not out, so we have to discard the byte)
mul r8                                 ; Execute the division
shr rax,56                             ; Shift the most significant byte of the remainder to the least
movzx rax, byte [rsi+rax]              ; Load the value from our conversion table
or r10,rax                             ; Store the new value in r10
mov rax,rdx                            ; Restore the working quotient for the next iteration
loop DoConv                            ; ...and do it again

```(Remember that ld will string all the data segments together, so it doesn't matter where they go in the asm file). (The XLATB instruction actually still works on x86_64, but I don't use it because if forces you to put the offset for the table in rbx, and since rbx is one of the registers that aren't used for syscall arguments it seemed silly to burn it when you might want to keep some meaningful variable in it)

Yet again, I was suprised. The runtimes were:
 
[LIST]
[*]Intel Core 2 @ 0.8Ghz: 1.970s
[*]Intel Core 2 @ 1.3Ghz: 1.270s
[*]AMD K8 @ 2.2 Ghz: 0.830s
[*]AMD K9 @ 3.1Ghz: 0.590s
[*]AMD K10 @ 3.4Ghz: 0.540
[/LIST]
Again, it was faster on all four processors!

My reason for this post (other than hoping that somebody other than me would find this interesting) is to ask the following:

[LIST=1]
[*]On your processors, do you see similar time differences?
[*]In a real-world situation, would the memory reference implementation really be faster?
[*]Are there any other interesting ways of converting integers to ASCII beyond these three?
[/LIST]
Partake of the joy, forthwith.

---

### Post by NathanB on 2011-01-24
> **WinstonChurchill said:**
> This works extremely well, because the syscall that populates the memory with random digits will be counted in the "System" field of the 'time' command's output. So as long as we keep the above the same, it will give us a pretty accurate idea of what is faster than what.
It still counts toward application run time.  Always keep syscalls to a minimum -- every context switch (going from User-space to System-space and then back again) is CPU expensive.  It is always better to memory-map the file.

---

### Post by WinstonChurchill on 2011-01-25
> **NathanB said:**
> It still counts toward application run time.  Always keep syscalls to a minimum -- every context switch (going from User-space to System-space and then back again) is CPU expensive.  It is always better to memory-map the file.
You're right of course: but you can't mmap /dev/urandom - you'll get ENODEV.

---

### Post by Lux Perpetua on 2011-01-26
I like your "magic division." A few months ago, I came up with a few different divide-by-ten functions for ARM assembly that don't use division, since my emulator didn't emulate the division instruction. I don't think they're likely to be faster than yours, but I would be curious to know the results if you get around to porting them to x86_64. Anyway, here's what I did. 

My first one replaces division by multiplication (like yours), but for some reason I didn't use an expanding multiply. I don't remember why, whether it wasn't available or for some other reason. To get by with non-expanding (truncating) multiplication, I divided by 2 first and then multiplied by 0xcccccccd, the inverse of 5 mod 2^32 (for 32 bits, but the idea works for any number of bits). This gives you the correct answer if you had a multiple of 5; otherwise, it's off by a multiple of 0xcccccccd, which you can recover by looking at the top 3 bits. Here's the original code: ```
        .global divmod10
        
        @(r0, r1) = (r2 div 10, r2 mod 10)
divmod10:
        stmfd   r13!, {r3, r4, r5}
        
        and     r1, r2, #1
        mov     r3, r2, ASR #1
        ldr     r4, inv5
        mul     r0, r4, r3

        mov     r3, r0, LSR #29
        adr     r5, divmod10_table
        
        ldr     r4, [r5, r3, LSL #3]
        add     r5, r5, #4
        ldr     r3, [r5, r3, LSL #3]
        
        add     r0, r0, r4
        add     r1, r1, r3, LSL #1

        ldmfd   r13!, {r3, r4, r5}
        mov     pc, lr
inv5:
        .word 0xcccccccd
divmod10_table:
        .word 0,          0     @ 0b000
        .word 0xcccccccc, 4     @ 0b001
        .word 0x99999999, 3     @ 0b010
        .word 0x99999999, 3     @ 0b011
        .word 0x66666666, 2     @ 0b100
        .word 0x66666666, 2     @ 0b101
        .word 0x33333333, 1     @ 0b110
        .word 0,          0     @ 0b111

```

The second one is also related to your solution, but it goes further and eliminates multiplications. This seemed like a viable solution for ARM, where multiplication is more expensive than other instructions and you basically get a "free" shift with most arithmetic instructions. Thus, things like "a += a >> 4" are cheap, which I tried to exploit, but it doesn't seem like such a great idea on x86. Here's the idea, anyway: to compute x/10, we can multiply x by [binary]0.0001100110011.... We can approximate this with right-shifts as follows: 

a = x >> 4
a += a >> 1
a += a >> 4
a += a >> 8
a += a >> 16
a += a >> 32 (for 64 bits)

a is now approximately x/10, but unfortunately we have some roundoff error. In my function I corrected this by computing the remainder x - 10*a (with no multiplication: 10*a is (a << 1) + (a << 3)) and repeatedly subtracting 10 from the remainder to make it less than 10. A lookup table would probably be faster than repeated subtraction. It turns out the computed remainder is at most 49 for 32 bits, so the lookup table would be pretty small, but I don't have a rigorous proof for the number 49. (Also, I don't know the corresponding bound for 64 bits, but it should grow logarithmically in the number of bits.) Alternatively, you could recursively apply the algorithm to x - 10*a to compute the correction; there are all kinds of fun things to experiment with. Here's the original code:

```

        .global divmod10_v2
divmod10_v2:
        mov     r0,     r2, ASR #4
        add     r0,     r0,     r0, ASR #1
        add     r0,     r0,     r0, ASR #4
        add     r0,     r0,     r0, ASR #8
        add     r0,     r0,     r0, ASR #16
        
        mov     r1,     r0, LSL #1
        add     r1,     r1,     r0, LSL #3

        sub     r1,     r2,     r1
divmod10_v2_loop:
        subs    r1,     r1,     #10
        addpl   r0,     r0,     #1
        bpl     divmod10_v2_loop
        add     r1,     #10
        mov     pc,     lr

```
Note that the same trick could be used in my first algorithm to replace multiplication by 0xcccccccd with a bunch of addition-with-left-shifts: 

a = x << 2
a += a << 1
a += a << 4
a += a << 8
a += a << 16
a += a << 32 (for 64 bits)
a += x

...but I don't know if this is a win. It all depends on the relative cost of addition and (large) shifts versus multiplication. 

Another thought: surely you can get by with a much smaller lookup table in Conversion3. There's no way you need all 8 most significant bits of the fractional part; actually, I'm thinking the first 4 are enough. That could improve cache performance.

---

