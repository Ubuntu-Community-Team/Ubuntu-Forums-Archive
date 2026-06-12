---
title: "Network Programming in Assembly"
date: 2009-03-24
forum: Programming Talk
---

### Post by Drone022 on 2009-03-24
Hey, I'm looking for resources on low level network programming in assembly. This is simply out of curiousity. I have found some stuff on it through google but not much, mainly WinSock stuff. Anyone know of any books or documents which cover it comprehensively? 

Also anything written recently would be helpful, a lot of stuff seems to be over 10 years old. *nix or Windows, its all good.

I assume its something not many people would bother with, thus the lack of material.

---

### Post by mmix on 2009-03-24
see the menuetos network stack.
[http://www.menuetos.net](http://www.menuetos.net)

---

### Post by jimi_hendrix on 2009-03-24
you are my hero for doing this in assembly

---

### Post by NathanB on 2009-03-24
You can't get any lower than Syscalls.  To learn how, go to:
[http://linuxassembly.org](http://linuxassembly.org)

"A server then typically calls bind(2), listen(2), and accept(2) or select(2). A client typically calls bind(2) (though that may be omitted) and connect(2)."

A simple TLDP search of the term "socket" gives these fine results:

[http://www.google.com/cse?cx=017644269519104757279%3Agm62gtzaoky&q=socket&sa=go](http://www.google.com/cse?cx=017644269519104757279%3Agm62gtzaoky&q=socket&sa=go)

Hope that helps!

---

### Post by Frank Kotler on 2009-03-24
If you want to do it at the "Menuetos level" - write your own TCP/IP stack - I would suggest the 32-bit Menuetos. The license on the 64-bit version is... well, read it and weep...

For Linux, the first clue I can give you is that there's only one sys_socketcall (102). The various "socket", "connect", "listen"... calls are a "command" in ebx. The parameters - which vary - are pointed to by ecx (typically, they're on the stack, but don't have to be).

The only thing I've done with socket programming is to "translate" Scott Lanning's "daytime" client from Gas to Nasm. I could post either version of that (or both), if you think it would help you. Doesn't really "explain" too much...

Okay... I've also fooled a little with one of the examples from the "asmutils" package from linuxassembly.org that Nathan mentioned. (wget) Started off working okay, but I got a "redirect". I can parse out the URL where the file really is, but I need "gethostbyname" (I think) to get any farther. That one's *not* a simple sys_call. I think I need to find where Linux keeps the DNS IPs, and send a querry to one of them, get a reply, and then retry the "wget". That project's stalled...

Okay... I've also connected to the X server diectly through a socket (instead of using Xlib)... Not really "network" programming, but pretty much the same thing...

The "assembly" part of it doesn't look too difficult, but knowing what you want to do with it is mysterious. Not "assembly specific", though - information intended for C or some other language will help. Best bet might be to find some simple C example - an "echo" server/client or something - and "go by" that... Maybe this one...

[http://www.paulgriffiths.net/program/c/echoserv.php](http://www.paulgriffiths.net/program/c/echoserv.php)

Does that sound like what you have in mind?

Best,
Frank

---

### Post by Drone022 on 2009-03-25
> see the menuetos network stack.
[http://www.menuetos.net](http://www.menuetos.net)
> If you want to do it at the "Menuetos level" - write your own TCP/IP stack - 

I think I'll leave this alone for now, although it looks interesting for when I decide its time to write an OS. I've also been looking into how to write a simple bootloader and kernel in assembly and it doesnt look **that** horrific.

> For Linux, the first clue I can give you is that there's only one sys_socketcall (102). The various "socket", "connect", "listen"... calls are a "command" in ebx. The parameters - which vary - are pointed to by ecx (typically, they're on the stack, but don't have to be).

Thanks, this helped, I looked into it. The assembly doesnt seem too bad, I found some stuff relevant to the daytime client.

```

__NR_socketcall equ 102
SYS_SOCKET equ 1


lea ecx, [my_args] ; address of args structure
mov ebx, SYS_SOCKET ; subfunction or "command"
mov eax, __NR_socketcall ;c.f. /usr/src/linux/net/socket.c
int 80h

```

I also found details on creating the "sockaddr_in" structure on the stack. All very helpful stuff. Then read some bits off the network and stick em in a buffer, no problems......perhaps.

I did find a 32-bit WinAsm http client, do you know if there are any for linux? I might give it a go myself. Perhaps I could get an IRC client going. Anyway, I'll try to walk before I can run.

---

### Post by Drone022 on 2009-03-25
Hey Frank, I think you actually wrote the code that I quoted above. Do you recognise it?

---

### Post by NathanB on 2009-03-25
> **Frank Kotler said:**
> Okay... I've also fooled a little with one of the examples from the "asmutils" package from linuxassembly.org that Nathan mentioned. (wget) Started off working okay, but I got a "redirect". I can parse out the URL where the file really is, but I need "gethostbyname" (I think) to get any farther. That one's *not* a simple sys_call. I think I need to find where Linux keeps the DNS IPs, and send a querry to one of them, get a reply, and then retry the "wget". That project's stalled...

Yeah, it would be a **'mortal sin'** to link against a C library just for that *one* function!  I looked at HPA's "klibc" with hopeful eyes, but he doesn't provide an example.  More digging...

> 
[http://www.paulgriffiths.net/program/c/echoserv.php](http://www.paulgriffiths.net/program/c/echoserv.php)


Thanks for this!  Lots of good examples there.

Nathan.

---

### Post by Frank Kotler on 2009-03-27
Heh! I don't know about "mortal sin"... but I try to avoid linking against libc for "just one function" - heck, for "all of 'em"! This is foolish - the code's just sittin' there waiting for someone to call it! But I'm a "do it yourself" kinda guy... even if it's "duplicate code".

Yeah, that looks like my translation of Scott Lanning's daytime client you found, Drone022... one of 'em. Scott did something "odd" in the original - put variables on the stack without subtracting anything from esp to "make room" for 'em. Worked alright, since he didn't use the stack, nothing got clobbered, but I "fixed" that, even in my first "translation". I think what you've got there is a "simplified" version, with variables/parameters in static ".data". I don't think that's "better" - the stack is a good place for that stuff - but I think it's easier to see what's happening with the socketcalls without the stack-manipulation. I'd put 'em back on the stack for a "real program", probably.

Here's a preliminary version of an echo server (my first server). Loosely based on Paul Griffiths' example. I changed it so it'd keep echoing lines, instead of disconnecting after just one. Now it disconnects if you type "quit", and kills the server if you type "kill". Probably not the way an echo server is "supposed" to work, but I liked it.

There's an issue that I haven't dealt with in this version. There's no guarantee we're going to get everything in one "read" (or write everything in one "write"). We need routines to "keep going" until we've got/put everything. Griffiths provides such functions - credits 'em to Stevens. Everybody seems to credit Stevens ("Unix Network Programming") for these functions. Doesn't seem like that big a deal to me - maybe it will once I've tried it. :) My next step. For now, echoing short strings over a loopback connection, a plain read/write seems to work... but it isn't right.

Merely a first draft:
```

; echo server
; echos lines until "quit"
; "kill" unloads server
; runs on loopback, 127.0.0.1, and port 2002,
; no options on this model!
;
; nasm -f elf echosrv.asm
; ld -o echosrv echosrv.o

global _start

;-------------------
; should probably be in an .inc file

struc sockaddr_in
    .sin_family resw 1
    .sin_port resw 1
    .sin_addr resd 1
    .sin_zero resb 8
endstruc

; Convert numbers (constants!) to network byte order
%define hton(x) ((x & 0xFF000000) >> 24) | ((x & 0x00FF0000) >>  8) | ((x & 0x0000FF00) <<  8) | ((x & 0x000000FF) << 24)
%define htons(x) ((x >> 8) & 0xFF) | ((x & 0xFF) << 8)

AF_INET        equ 2
SOCK_STREAM    equ 1
INADDR_ANY	equ 0	; /usr/include/linux/in.h

STDIN          equ 0
STDOUT         equ 1

__NR_exit	equ 1
__NR_read       equ 3
__NR_write      equ 4
__NR_close	equ 6
__NR_socketcall equ 102

; commands for sys_socketcall
; /usr/include/linux/in.h
SYS_SOCKET	equ 1
SYS_BIND	equ 2
SYS_CONNECT	equ 3
SYS_LISTEN	equ 4
SYS_ACCEPT	equ 5
SYS_SEND	equ 9
SYS_RECV	equ 10
;------------------------

_ip equ 0x7F000001		; loopback - 127.0.0.1
_port equ 2002

; Convert 'em to network byte order
IP equ hton(_ip)
PORT equ htons(_port)

BACKLOG		equ 128	; for "listen"
BUFLEN         equ  1000

section .data

my_sa istruc sockaddr_in
    at sockaddr_in.sin_family, dw AF_INET
    at sockaddr_in.sin_port, dw PORT
    at sockaddr_in.sin_addr, dd INADDR_ANY
    at sockaddr_in.sin_zero, dd 0, 0
iend

socket_args dd AF_INET, SOCK_STREAM, 0

; first of these wants to be socket descriptor
; we fill it in later...
bind_args   dd 0, my_sa, sockaddr_in_size
listen_args dd 0, BACKLOG
accept_args dd 0, 0, 0

section .bss
    my_buf resb BUFLEN
    fd_socket resd 1
    fd_conn resd 1

section .text
 _start: 

    ; socket(AF_INET, SOCK_STREAM, 0)
    mov ecx, socket_args	; address of args structure
    mov ebx, SYS_SOCKET     ; subfunction or "command"
    mov eax, __NR_socketcall     ;c.f. /usr/src/linux/net/socket.c
    int 80h

    cmp eax, -4096
    ja exit

    mov [fd_socket], eax
    ; and fill in bind_args, etc.
    mov [bind_args], eax
    mov [listen_args], eax
    mov [accept_args], eax


    mov ecx, bind_args
    mov ebx, SYS_BIND	; subfunction or "command"
    mov eax, __NR_socketcall
    int 80h

    cmp eax, -4096
    ja exit

    mov ecx, listen_args
    mov ebx, SYS_LISTEN	; subfunction or "command"
    mov eax, __NR_socketcall
    int 80h

    cmp eax, -4096
    ja exit

again:
    mov ecx, accept_args
    mov ebx, SYS_ACCEPT	; subfunction or "command"
    mov eax, __NR_socketcall
    int 80h
    cmp eax, -4096
    ja  exit

    mov [fd_conn], eax


readagain:

    ; read(sock, buf, len)
    mov edx, BUFLEN		; arg 3: max count
    mov ecx, my_buf		; arg 2: buffer
    mov ebx, [fd_conn]	; arg 1: fd
    mov eax, __NR_read	; sys_read
    int 80h

    cmp eax, -4096
    ja exit

    mov edx, eax		; length read is length to write
    mov ecx, my_buf
    mov ebx, [fd_conn]
    mov eax, __NR_write
    int 80h
    cmp eax, -4096
    ja exit

    cmp dword [my_buf], 'quit'
    jz closeconn

    cmp dword [my_buf], 'kill'
    jz killserver

    jmp readagain

closeconn:
    mov eax, __NR_close
    mov ebx, [fd_conn]
    int 80h
    cmp eax, -4096
    ja exit
    jmp again
    
killserver:
    mov eax, __NR_close
    mov ebx, [fd_conn]
    int 80h
    mov eax, __NR_close
    mov ebx, [fd_socket]
    int 80h

goodexit:
    xor	eax, eax		; success
 exit:
    mov ebx, eax		; exitcode
    neg ebx
    mov eax, __NR_exit
    int 80h
;-----------------------


```

You can talk to that with "telnet 127.0.0.1 2002". I'll work up an echo client for it... maybe a daytime server to go with the client... some day soon...

Just wanted to get something posted before Nathan's HLA example. :)

Best,
Frank

---

### Post by Frank Kotler on 2009-03-29
tturrisi just mentioned this in the "raw sockets" thread:

[http://beej.us/guide/bgnet/output/html/multipage/index.html](http://beej.us/guide/bgnet/output/html/multipage/index.html)

"Beej's Guide To Network Programming"! How come I didn't remember that? Good intro to the subject! (not in assembly, we can't have everything) Thought it was worth mentioning...

Best,
Frank

---

### Post by jiangshi on 2012-05-04
This is not exactly a programming question, but I am wondering is anyone knows what happened to Konstantin Boldyshev and his linuxassembly.org site?

~jiangshi

> **NathanB said:**
> You can't get any lower than Syscalls.  To learn how, go to:
[http://linuxassembly.org](http://linuxassembly.org)

<snip>

Hope that helps!

---

### Post by Frank Kotler on 2012-05-04
[http://asm.sourceforge.net/](http://asm.sourceforge.net/)

The "linuxassembly" site expired, and Konstantin doesn't control it himself. Echoed here...

Best,
Frank

---

