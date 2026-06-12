---
title: "Nasm (screen offset)"
date: 2009-08-09
forum: Programming Talk
---

### Post by niiize on 2009-08-09
Started to look into assembly again after a bunch of years off. Didn't get very far with it so I'm a beginner still. I'm wondering how one can access the screen-offset in linux.


Thnk you.

---

### Post by NathanB on 2009-08-09
niiize -

Having a nice tutorial handy usually helps a great deal:

[http://tronche.com/gui/x/xlib/](http://tronche.com/gui/x/xlib/)

Feel free to post any code you are having trouble with.

---

### Post by niiize on 2009-08-09
I forgot to mention in the post that it is regular cosole mode I was referring to, and the letters offset on the screen and not pixels. also been googling alot but havn't found any thorough tutorials on linux assembly yet.

Ok. Here is some basic code for writing "hello world" to the screen using syscall 4
...
mov ecx, helloworld
mov edx, len
mov ebx, 1 ;basic output code?
mov eax, 4
int  0x80
...
How can I reach the screenoffset.  Don't know if I'm remembering wrong but back in DOS this adress was stored in DS:DI ?

Thank you

---

### Post by lisati on 2009-08-09
> **niiize said:**
> Don't know if I'm remembering wrong but back in DOS this adress was stored in DS : DI ?

Thank you

 I'd recommend brushing up on 32-bit programming (something I'll need to do if I want to learn ASM for Ubuntu as well)

---

### Post by NathanB on 2009-08-09
Modern operating systems will not allow a user-space program to have direct access to hardware (without special permission).  Read up on 'protected mode' and 'virtual memory' for the details:

[http://en.wikipedia.org/wiki/Protected_mode](http://en.wikipedia.org/wiki/Protected_mode)

[http://en.wikipedia.org/wiki/Virtual_memory](http://en.wikipedia.org/wiki/Virtual_memory)

If you are still determined to write your programs in the old style, then grab VirtualBox and load a FreeDOS image.  This will allow your programs a simulated 'direct access to hardware' without any danger of borking your computer.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

[http://www.freedos.org/](http://www.freedos.org/)

Here is an 'Etch-a-Sketch' example of using Video Mode 13h from a simple DOS program.
[PHP];      To assemble with A86:    A86 ETCH3.ASM
;
; Control Keys:
;   Up Arrow:    move up
;   Down Arrow:  move down
;   Left Arrow:  move left
;   Right Arrow: move right
;   SPACE BAR:   toggles line drawing OFF and ON
;   C:           clears the drawing
;   ESC:         quit
;
code    segment
;
row     dw      0
col     dw      0
write   db      0
;
        org     100h
        mov     ax,0013h
        int     10h
        mov     write,11
        mov     di,0A000h
        mov     es,di
reset:
;
; Light up the VGA border.
;
        mov     ax,1001h        ;function 10h, sub-function 1
        mov     bh,5            ;set color in BH (5 = magenta)
        int     10h             ;call ROM BIOS video services

        mov     row,32000
        mov     col,159

NextPixel:
        mov     ax,320
        mov     bx,row
        mul     bx
        add     bx,col
        mov     di,bx
        mov     byte [es:di],11
        mov     ah,0
        int     16h
        cmp     write,0
        jne     YesWrite
        mov     bl,write
        mov     byte [es:di],bl
YesWrite:
        cmp     ah,2Eh
        jne     NotShake
        mov     ax,0013h
        int     10h
        jmp     reset
NotShake:
        cmp     ah,48h
        jne     NotMoveUp
        sub     row,320
NotMoveUp:
        cmp     ah,50h
        jne     NotMoveDown
        add     row,320
NotMoveDown:
        cmp     ah, 4Bh
        jne     NotMoveLeft
        sub     col,1
NotMoveLeft:
        cmp     ah,4Dh
        jne     NotMoveRight
        add     col,1
NotMoveRight:
        cmp     ah,39h
        je      Toggle
        cmp     ah,01h
        je      exit
        jmp     NextPixel
Toggle:
        cmp     write,11
        jne     SetWrite
        mov     write,0
        jmp     NextPixel
SetWrite:
        mov     write,11
        jmp     NextPixel
exit:
        mov     ax,0003h
        int     10h
        int     20h
;
end [/PHP]

Get the 'a86' assembler here:
[http://eji.com/a86/](http://eji.com/a86/)

---

### Post by niiize on 2009-08-19
Thank you guys

---

