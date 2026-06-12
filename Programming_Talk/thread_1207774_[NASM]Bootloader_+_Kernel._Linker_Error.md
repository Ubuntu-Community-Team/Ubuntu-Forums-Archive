---
title: "[NASM]Bootloader + Kernel. Linker Error"
date: 2009-07-08
forum: Programming Talk
---

### Post by 2words4uready on 2009-07-08
Heres the bootloader.
```

;boot.asm
           jmp 07C0h:start     ; Goto segment 07C0

    ; Declare the string that will be printed
    msg     db  'Loading BCSOS.....'


    start:
	; Update the segment registers
	mov ax, cs
	mov ds, ax
	mov es, ax
	mov si, msg     ; Print msg
    print:
	lodsb           
	cmp al, 0       
	je kernel
	mov ah, 0Eh     
	mov bx, 7
	int 10h
	jmp print       
    kernel: 
	[bits 32]
	[extern _k_main]
	call _k_main
	jmp kernel


    times 510-($-$$) db 0
    dw 0AA55h
```

Heres my simple kernel.
```

//kernel.c
void _k_main()
{
  int num;
  char ch;

  char *text_video = (char*)0xB8000;
  char attrib = 0x07;
  char *str="Kernel Loaded";

  while(*str!=0)
  {
    *text_video = *str;
    *text_video++;
    *text_video = attrib;
    *text_video++;
    *str++;
  }
  return;
}
int main()
{
	
}

```

I compile the object files. Then when i attempt to link this error occurs
```

boot.o: In function `start':
boot.asm:(.text+0x22): relocation truncated to fit: R_386_16 against `.text'
```

Im typing this to link the files.
```
ld -oformat=bin -o boot.bin boot.o kernel.o

```

Anyone have any idea why the error occurs?

---

### Post by jinksys on 2009-07-08
This won't run.

A first stage bootloader, which is what boot.asm seems to be, simply takes control of the machine and loads a second stage bootloader that can load the kernel.  The first stage needs to be 512 bytes in size and have the appropriate signature at the end of it.  I see a few things wrong with your code.  First you do not tell the linker that the memory addresses start at zero, [ORG 0].  Second, you have barely enough bytes to load the secondary bootloader, you can't be linking C code into the mix.

[Here]("http://organicdesign.co.nz/Writing_a_boot_loader_in_assembler") is a tutorial to help you.

Personally, if writing an operating system is what you want to accomplish, don't write a bootloader and use GRUB.  Bootloaders are hell to code, plus you can do most of your coding in a higher level language.

---

### Post by 2words4uready on 2009-07-08
So. How would I use grub? Is there a tutorial as to using grub as a bootloader to load my kernel etc?

---

### Post by jinksys on 2009-07-08
> **2words4uready said:**
> So. How would I use grub? Is there a tutorial as to using grub as a bootloader to load my kernel etc?

Here's a tutorial that will walk you through creating a simple C kernel and booting it.

[http://wiki.osdev.org/Bare_bones](http://wiki.osdev.org/Bare_bones)

Also, check out [www.osdev.org](www.osdev.org) for forums and a wiki.  You'll probably find better help from a forum specifically targeted toward hobbyist OS developers.

---

### Post by 2words4uready on 2009-07-08
Ok, i appreciate your help. Im gonna check out those tutorials.

---

