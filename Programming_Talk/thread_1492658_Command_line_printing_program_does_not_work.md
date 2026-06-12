---
title: "Command line printing program does not work"
date: 2010-05-25
forum: Programming Talk
---

### Post by Quarg on 2010-05-25
Hello again (if you've already seen my other post pertaining to this problem)
I have done some more research (maybe it could be called banging my head on a wall) into printing arguments from the command line in x86_64 assembly language using NASM syntax. this works:
```

section .data
        
section .bss
	Text_file:   resb 50

global _start
 _start:
	mov rsi, [rsp+8]     ; Since the stack starts out with 
                             ; argc on top, then argv[0] this
                             ; moves argv[0] into source index.
                                                   
	mov rdi, Text_file   ; pointer to where we want to 
                             ; move the string
	mov rcx, 6           ; how may times to we increment? 6
	cld                  ; clear direction flag
	rep movsb            ; blast string at [rsp+8]to Text_file
	
	mov rcx, Text_file  ; The following prints out Text_file
	mov rbx, 1
	mov rdx, 6
	mov rax, 4
	int 80h

```
every time that works. It prints out the first argument. My question is, why, if I do this:
```

 mov rax, 4     ;write to file linux syscall
 mov rbx, 1     ; file descriptor - 1 for STDOUT, console.
 mov rcx, [rsp+8] ;SHOULD move the pointer for argv[0] into rcx.
                  ;rcx is the location to read from.
 mov rdx, 5       ; size of buffer to read - 5 is good, doesn't 
                  ; matter yet.
 int 80h          ; call Linux in and have it do the dirty work.

```
It DOESN'T WORK! I simply do not get it - and I've spent the last hour on this problem. Any ideas as to what I'm doing wrong?

---

### Post by NathanB on 2010-05-25
Looks like you are attempting to use 32-bit syscalls from a 64-bit Operating System.  That certainly is not going to work.  I believe it is clear you will want to learn how to program in 32-bit assembly language before you even think about trying to write any 64-bit code.

Please visit those links we posted earlier.  Take some time to actually read those books & tutorials and follow the exercises given.  If you have any problems understanding specific parts of that instructional material, just ask us a question here.  But, please do not ask us to do your homework for you.  See:  [http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

Nathan.

---

