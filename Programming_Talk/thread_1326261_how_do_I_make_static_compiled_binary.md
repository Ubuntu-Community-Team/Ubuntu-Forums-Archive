---
title: "how do I make static compiled binary"
date: 2009-11-14
forum: Programming Talk
---

### Post by Paul S on 2009-11-14
I'm not a developer and don't have time to become one.  But, I'm using a program that I'd like to make more portable by having it statically linked.

The developer setup to compile as a linked binary with the following command in the Makefile:

        gcc sphinx3_livesegment.c -I/usr/include/sphinxbase -I/usr/include/sphinx3 -lsphinxad -ls3decoder -lm -o sphinx3_livesegment

This creates a binary with the following links:

$ ldd sphinx3_livesegment
        linux-gate.so.1 =>  (0x004dd000)
        libsphinxad.so.0 => /usr/lib/libsphinxad.so.0 (0x001d1000)
        libs3decoder.so.0 => /usr/lib/libs3decoder.so.0 (0x00cdd000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00a08000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x001d8000)
        libsphinxbase.so.1 => /usr/lib/libsphinxbase.so.1 (0x00115000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x00835000)
        libblas.so.3gf => /usr/lib/libblas.so.3gf (0x00e03000)
        /lib/ld-linux.so.2 (0x005b1000)
        libgfortran.so.3 => /usr/lib/libgfortran.so.3 (0x0031c000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00d97000)

I would like to create a statically compiled binary (with the libraries part of the binary).  I've tried the following with no success:

$ gcc sphinx3_livesegment.c -static -I/usr/include/sphinxbase -I/usr/include/sphinx3 -lsphinxad -ls3decoder -lm -o sphinx3_livesegment
sphinx3_livesegment.c: In function ‘process_stdin’:                                                                                                          
sphinx3_livesegment.c:259: warning: format not a string literal and no format arguments                                                                      
/tmp/ccmrc3qr.o: In function `reset_beam':                                                                                                            
sphinx3_livesegment.c:(.text+0x74): undefined reference to `cmd_ln_access'                                                                                   
     < snipped  pages of errors >
/home/paul/voicekey.bld/sphinx-bld/sphinx3/src/libs3decoder/libsearch/blkarray_list.c:83: undefined reference to `_E__pr_warn'
collect2: ld returned 1 exit status

Can anyone tell me what command should work?

I'm running karmic if that matters.

TIA

---

### Post by nvteighen on 2009-11-14
Your command is the correct one. Are you sure you do have the static libraries installed?

---

### Post by Paul S on 2009-11-14
> **nvteighen said:**
> Your command is the correct one. Are you sure you do have the static libraries installed?

Thanks for the reply.

I think it's all there .. checked as follows:

$ ldd sphinx3_livesegment           
        linux-gate.so.1 =>  (0x0024a000)                                                  
        libsphinxad.so.0 => /usr/lib/libsphinxad.so.0 (0x00f6b000)                        
        libs3decoder.so.0 => /usr/lib/libs3decoder.so.0 (0x00d0b000)                      
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00476000)                            
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x0060c000)                            
        libsphinxbase.so.1 => /usr/lib/libsphinxbase.so.1 (0x00294000)                    
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x001c3000)                
        libblas.so.3gf => /usr/lib/libblas.so.3gf (0x00c23000)                            
        /lib/ld-linux.so.2 (0x0014a000)                                                   
        libgfortran.so.3 => /usr/lib/libgfortran.so.3 (0x002cb000)                        
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00869000)                                  

$ ls -l /usr/lib/libsphinxad.so.0*                                                                     
lrwxrwxrwx 1 paul paul    20 2009-11-12 15:28 /usr/lib/libsphinxad.so.0 -> libsphinxad.so.0.0.0               
-rwxr-xr-x 1 paul paul 49719 2009-08-30 19:48 /usr/lib/libsphinxad.so.0.0.0                                   

$ ls -l /usr/lib/libs3decoder.*
-rw-r--r-- 1 paul paul 2369292 2009-08-30 19:53 /usr/lib/libs3decoder.a
-rwxr-xr-x 1 paul paul    1064 2009-08-30 19:53 /usr/lib/libs3decoder.la
lrwxrwxrwx 1 paul paul      21 2009-11-12 15:28 /usr/lib/libs3decoder.so -> libs3decoder.so.0.0.6
lrwxrwxrwx 1 paul paul      21 2009-11-12 15:28 /usr/lib/libs3decoder.so.0 -> libs3decoder.so.0.0.6
-rwxr-xr-x 1 paul paul 1624109 2009-08-30 19:53 /usr/lib/libs3decoder.so.0.0.6                     

$ ls -l /lib/tls/i686/cmov/libm*
-rw-r--r-- 1 root root 149392 2009-10-07 04:52 /lib/tls/i686/cmov/libm-2.10.1.so
-rw-r--r-- 1 root root  13800 2009-10-07 04:52 /lib/tls/i686/cmov/libmemusage.so
lrwxrwxrwx 1 root root     14 2009-11-05 08:19 /lib/tls/i686/cmov/libm.so.6 -> libm-2.10.1.so

$ ls -l /lib/tls/i686/cmov/libc*
-rwxr-xr-x 1 root root 1319364 2009-10-07 04:52 /lib/tls/i686/cmov/libc-2.10.1.so
-rw-r--r-- 1 root root  181780 2009-10-07 04:52 /lib/tls/i686/cmov/libcidn-2.10.1.so
lrwxrwxrwx 1 root root      17 2009-11-05 08:19 /lib/tls/i686/cmov/libcidn.so.1 -> libcidn-2.10.1.so
-rw-r--r-- 1 root root   38360 2009-10-07 04:52 /lib/tls/i686/cmov/libcrypt-2.10.1.so               
lrwxrwxrwx 1 root root      18 2009-11-05 08:19 /lib/tls/i686/cmov/libcrypt.so.1 -> libcrypt-2.10.1.so
lrwxrwxrwx 1 root root      14 2009-11-05 08:19 /lib/tls/i686/cmov/libc.so.6 -> libc-2.10.1.so

$ ls -l /usr/lib/libsphinxbase.*
-rw-r--r-- 1 paul paul 866700 2009-08-30 19:48 /usr/lib/libsphinxbase.a
-rwxr-xr-x 1 paul paul    865 2009-08-30 19:48 /usr/lib/libsphinxbase.la
lrwxrwxrwx 1 paul paul     22 2009-11-12 15:28 /usr/lib/libsphinxbase.so -> libsphinxbase.so.1.0.0
lrwxrwxrwx 1 paul paul     22 2009-11-12 15:28 /usr/lib/libsphinxbase.so.1 -> libsphinxbase.so.1.0.0
-rwxr-xr-x 1 paul paul 591410 2009-08-30 19:48 /usr/lib/libsphinxbase.so.1.0.0

$ ls -l /lib/tls/i686/cmov/libpthread*
-rwxr-xr-x 1 root root 116920 2009-10-07 04:52 /lib/tls/i686/cmov/libpthread-2.10.1.so
lrwxrwxrwx 1 root root     20 2009-11-05 08:19 /lib/tls/i686/cmov/libpthread.so.0 -> libpthread-2.10.1.so

$ ls -l /usr/lib/libblas.so.3gf*
lrwxrwxrwx 1 root root     16 2009-11-12 15:42 /usr/lib/libblas.so.3gf -> libblas.so.3gf.0
-rw-r--r-- 1 root root 550804 2008-11-04 20:20 /usr/lib/libblas.so.3gf.0

$ ls -l /lib/ld-linux.so.2
lrwxrwxrwx 1 root root 12 2009-11-05 08:19 /lib/ld-linux.so.2 -> ld-2.10.1.so

$ ls -l /usr/lib/libgfortran.so.3*
lrwxrwxrwx 1 root root     20 2009-11-12 15:42 /usr/lib/libgfortran.so.3 -> libgfortran.so.3.0.0
-rw-r--r-- 1 root root 805948 2009-10-14 19:52 /usr/lib/libgfortran.so.3.0.0

$ ls -l /lib/libgcc_s.so.1
-rw-r--r-- 1 root root 116272 2009-10-14 19:47 /lib/libgcc_s.so.1

This leaves linux-gate.so.1 as missing.  But a google search shows that it's only a phantom library in memory in x86 kernels [http://www.trilithium.com/johan/2005/08/linux-gate/](http://www.trilithium.com/johan/2005/08/linux-gate/)   so I guess it shouldn't be a problem.

regards

---

### Post by apmcd47 on 2009-11-16
From the cc man page:

> 
       -static
           On systems that support dynamic linking, this prevents linking with
           the shared libraries.  On other systems, this option has no effect.


Also you need to search for library files ending in .a rather than .so* (so stands for shared object)

Andrew

---

### Post by Paul S on 2009-11-16
> **apmcd47 said:**
> From the cc man page:



Also you need to search for library files ending in .a rather than .so* (so stands for shared object)

Andrew

I used ldd to determine which files to search for.  None of those are .a files.  But, is there another way to check for missing files (other than ldd)?

---

### Post by apmcd47 on 2009-11-16
Oops! I missed the bit where you were actually using the -static option.

It looks like a compiler error rather than a linking error. I suggest first try moving the -static to just before the -l switches.

If you still have a problem try:
```
gcc -c sphinx3_livesegment.c  -I/usr/include/sphinxbase -I/usr/include/sphinx3
```

This will build the binary without linking it. If you continue to get an error it's probably in the code rather than the libraries.

As far as the libs are concerned, check the paths of all the libraries you found using ldd and see if corresponding lib*.a files exist. These are the static libraries. If they don't exist you need to install them

Andrew

---

