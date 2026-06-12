---
title: "My assembly code cann't jump into real mode from protected"
date: 2010-01-07
forum: Programming Talk
---

### Post by flreey on 2010-01-07
Hello,everyone. Now i am try to write a loders with nasm.I use bochs to debug.Now i can jmp into protect mode from real mode ,but when i back to the real mode, the bochs terminal just said :
Next at t=173571481
(0) [0xfffffff0] f000:fff0 (unk. ctxt): jmp far f000:e05b         ; ea5be000f0
and withoud any responds.Below is the code.

[COLOR=DarkGreen]%include "pm.inc"
org 100h
;org 7c00h
jmp label_begin

[SECTION .gdt]
label_gdt:    Descriptor    0,    0,    0
label_normal:    Descriptor    0,     0ffffh, DA_DRW
label_code32:    Descriptor    0,    segcode32len - 1, DA_C + DA_32
label_code16:    Descriptor    0,    0ffffh, DA_C
label_video:    Descriptor    0b8000h,0ffffh,    DA_DRW
;end gdt

gdt_length     equ    $ - label_gdt
gdt_ptr        dw    gdt_length - 1
        dd    0
;end gdt_ptr

selector_code32    equ    label_code32 - label_gdt
selector_code16 equ    label_code16 - label_gdt
selector_video    equ    label_video - label_gdt
selector_normal    equ     label_normal - label_gdt
;end selector

;from real to protect
[SECTION .s16]
[BITS    16]
label_begin:
mov ax, cs
mov ds, ax
mov es, ax
mov ss, ax
mov sp, 0100h

mov [label_go_back_to_real + 3], ax

;initialize code32
xor eax, eax
mov ax, cs
shl eax, 4
add eax, label_seg_code32
mov word [label_code32 + 2], ax
shr eax, 16
mov byte [label_code32 + 4], al
mov byte [label_code32 + 7], ah

;initialize code16
xor eax, eax
mov ax, cs
movzx eax, ax
shl eax, 4
add eax, label_seg_code16
mov word [label_code16 + 2], ax
shr eax, 16
mov byte [label_code16 + 4], al
mov byte [label_code16 + 7], ah


;initialize gdtr
xor eax, eax
mov ax, ds
shl ax, 4
add eax, label_gdt
mov dword [gdt_ptr + 2], eax

lgdt [gdt_ptr]

cli

in al, 92h
or al, 2
out 92h, al

mov eax, cr0
or eax, 1
mov cr0, eax

jmp dword selector_code32:0

label_real_entry:
    mov ax, cs
    mov ds, ax
    mov es, ax
    mov ss, ax

    in al, 92h
    and al, 11111101b
    out 92h, al
    sti

    mov ax, 4c00h
    int 21h

[SECTION .s32code]
[BITS 32]
label_seg_code32:
    mov ax, selector_video
    mov gs,  ax
    mov edi, (160 * 11 + 50)
    mov al, 'p'
    mov ah, 0ch
    mov [gs:edi], ax
    jmp selector_code16:0
    segcode32len equ $ - label_seg_code32

[SECTION .s16code]
ALIGN 32
[BITS 16]
label_seg_code16:
    mov ax, selector_normal
    mov ds, ax
    mov es, ax
    mov fs, ax
    mov gs, ax
    mov ss, ax

    mov eax, cr0
    and al, 11111110b
    mov cr0, eax

    mov ax, selector_video
    mov gs, ax
    mov di, (80 * 10 + 4) * 2
    mov al, 'X'
    mov ah, 0ch
    mov [gs:di], ax

label_go_back_to_real:
    jmp 0:label_real_entry

segcode16len equ $ - label_seg_code16[/COLOR]



[COLOR=SeaGreen] the pm.inc defines the macro of descriptor ,here is it's code
%macro Descriptor 3
    dw    %2 & 0FFFFh                ; segment bound 1
    dw    %1 & 0FFFFh                ; segment base 1
    db    (%1 >> 16) & 0FFh            ; segment base 2
    dw    ((%2 >> 8) & 0F00h) | (%3 & 0F0FFh)    ; ATR1 + segment bound 2 + ATR2
    db    (%1 >> 24) & 0FFh            ; segment base  3
%endmacro ; [/COLOR]


And also i don't know why i has [COLOR=SeaGreen] shl eax, 4 ,[/COLOR]when initial all of the code
[COLOR=DarkGreen];initialize code32
xor eax, eax
mov ax, cs
shl eax, 4[/COLOR] 

thanks.

---

