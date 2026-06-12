---
title: "Linking to system libs in a compatible way"
date: 2011-04-26
forum: Programming Talk
---

### Post by Abscissa on 2011-04-26
I'm on Kubuntu 10.04 and I'm trying to create a CGI app (just a basic CGI Hello World for now) that's intended to run on a shared web host where I have (sandboxed) SSH access. This is what I get when I "cat /proc/version" on that box:

Linux version 2.6.18-164.15.1.el5.028stab068.9 (root@rhel5-build-x64) (gcc version 4.1.2 20080704 (Red Hat 4.1.2-46)) #1 SMP Tue Mar 30 18:07:38 MSD 2010

(So I guess it's Red Hat.)

I'm writing this app in D, which compiles to native code and uses GCC to link on Linux. I know my way around Linux and the cmd line as a user, but I'm normally more of a Windows developer and don't know much about GCC or Linux's dynamic system libraries. (I do know how to tell my D compiler to pass switches to the linker. I just don't know much about GCC's switches.)

My test program works fine when I run it on my local system, but when I upload it to my webhost and run it there via SSH I get:

/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status
--- errorlevel 1

Personally, I can't make heads or tails of that first line, but I've been told it means the linker set it to dynamically link with a newer version of libc than what the target system has installed. Apparently, what I need to do is find out what version of libc the target machine has and tell gcc to make my app dynamically link with that version. Problem is, I don't have a clue how to do either of those things. Any help?

---

### Post by Abscissa on 2011-04-27
Sorry, I copy-pasted the wrong error message. Disregard the "/usr/bin/ld: cannot find -lgcc_s" message. That's something completely irrelevant.

Here's the real error message I got:

linux.so.2: bad ELF interpreter: No such file or directory

---

### Post by dwhitney67 on 2011-04-27
How are you building your app under Kubuntu?

---

### Post by Abscissa on 2011-04-27
$ dmd testDCGI.d

That compiles it and links it by invoking GCC with this command:

gcc testDCGI.o -o testDCGI -m32 -Xlinker -L/home/nick/dev/d/tool/dmd/linux/bin/../lib32 -Xlinker -L/home/nick/dev/d/tool/dmd/linux/bin/../lib64 -Xlinker --no-warn-search-mismatch -Xlinker --export-dynamic -lrt -lphobos2 -lpthread -lm

(In case you're wondering, phobos2 is the std lib for D v2.x)

I can adjust the params sent to GCC if needed.

It probably doesn't matter, but FWIW here's the content of testDCGI.d:

import std.conv;
import std.stdio;

void main()
{
        auto content = "<b><i>Hello world</i></b>\n";
        auto headers = 
`HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Content-Length: `~to!string(content.length);

        while(readln().length > 1) {}

        writeln(headers);
        writeln();
        writeln(content);
}

---

### Post by Abscissa on 2011-05-07
Here's a simplified version using C:

#include <stdio.h>
void main()
{
    printf("Hello\n");
}

On my local Kubuntu 10.04 system, it works:

$ gcc hello.c -o hello
$ ./hello
Hello

But if I copy the executable binary to my web host (it's either Red Hat or CentOS) and run it under ssh I get a segfault. Unfortunately, since it's a shared webhost I can't compile directly on that machine. I have to compile locally and copy the executable over.

---

### Post by SledgeHammer_999 on 2011-05-07
You're compiling it as a 32bit binary but the system you're going to run it on(red hat's OS) is 64bit and obviously it doesn't have the 32bit libs installed (ia32-libs on ubuntu)

---

### Post by Abscissa on 2011-05-07
Sorry, I forgot to mention that I had my web host switch me to a server that does have the 32-bit libs installed. But I'm still getting the exact same problems.

FWIW, On this new server, "cat /proc/version" gives me:

Linux version 2.6.9-89.35.1.EL (mockbuild@builder10.centos.org) (gcc version 3.4.6 20060404 (Red Hat 3.4.6-11)) #1 Tue Jan 18 17:34:23 EST 2011

---

### Post by SledgeHammer_999 on 2011-05-07
Do you get the same error message on this machine? ->linux.so.2: bad ELF interpreter: No such file or directory

Can you post the output of this command "ldd your_program" on the server?
This will tell us which libraries the linker can't find on the server.
Test with the C Hello World program.

---

### Post by Abscissa on 2011-05-07
Ok, the binary of the original D program is named "testDCGI.cgi", and the simplified C hello world is "testCCGI.cgi"...

On the old 64-only RedHat/CentOS server (not sure how much longer I'll have access to this):
$ ./testDCGI.cgi 
-jailshell: ./testDCGI.cgi: linux.so.2: bad ELF interpreter: No such file or directory
$ ./testCCGI.cgi 
Segmentation fault (core dumped)
$ ldd ./testDCGI.cgi
        not a dynamic executable
$ ldd ./testCCGI.cgi
        not a dynamic executable

On the new 32-bit-compatible RedHat/CentOS server (almost identical result):
$ ./testDCGI.cgi 
-jailshell: ./testDCGI.cgi: linux.so.2: bad ELF interpreter: No such file or directory
$ ./testCCGI.cgi 
Segmentation fault (core dumped)
$ ldd ./testDCGI.cgi 
        not a dynamic executable
$ ldd ./testCCGI.cgi 
ldd: exited with unknown exit code (139)

On my local Kubuntu 10.04 32-bit machine:
$ ./testDCGI.cgi

HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Content-Length: 26

<b><i>Hello world</i></b>

$ ./testCCGI.cgi
Hello
$ ldd ./testDCGI.cgi
        linux-gate.so.1 =>  (0x002eb000)
        librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0x00d59000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x00b8b000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x0087a000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x006e3000)
        /lib/ld-linux.so.2 (0x00bca000)
$ ldd ./testCCGI.cgi
        linux-gate.so.1 =>  (0x00b98000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00c50000)
        /lib/ld-linux.so.2 (0x003fb000)

---

### Post by SledgeHammer_999 on 2011-05-08
You should do a "ldd your_program" not a "ldd ./your_program". But I don't think you'll get different outputs.

Apart from this, I don't have any idea what's happening on the server or how to help you investigate it more. But is seems odd that the server's ldd can't recognize that the executables have dynamic dependencies.

---

### Post by Abscissa on 2011-05-08
I've just verified that it works if I compile from within a CentOS 4.2 VM (ie, via VirtualBox) and copy *that* executable to the server. But it would be nice to be able to compile directly in my normal physical non-VM'ed linux box.

---

