---
title: "[SOLVED] MySQL API in C problem"
date: 2008-09-27
forum: Programming Talk
---

### Post by ricorix on 2008-09-27
Hi. I'm new in sql programming.  I've installed mysql server version 5.0.51a-3ubuntu5.1.  I've also programmed an API in C.  It runs perfectly when it is programmed to our school's server.  But when I edited the program to connect to my localhost, errors started to occur. This is the only part of the code that I've edited:


previous code:	```
if(!mysql_real_connect(&mydb,"schoolserver","user","password","database",####,NULL,0)) {
	        printf( "Failed to connect to MySQL: Error: %s\n", mysql_error(&mydb)); 
		exit(1);
	}

```


present code:
```
if(!mysql_real_connect(&mydb,"localhost","root","password","database",0,NULL,0)) {
	        printf( "Failed to connect to MySQL: Error: %s\n", mysql_error(&mydb)); 
		exit(1);
	}
```

I've got no errors in compiling it.  But this happens when I run it:


```
ricorix@Ortseam:~$ ./mydb
Logged on to database sucessfully
[I]nsert, [U]pdate, [D]elete, [Q]uery, [E]xit
i
Enter student number:200711111
Enter last name:Maestro	
Enter first name:Rix
Enter exam1:50
Enter exam2:50
Enter exam3:50
INSERT statement failed
*** glibc detected *** ./mydb: free(): invalid next size (normal): 0x08061208 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7c67a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7c6b4f0]
./mydb[0x8048fc6]
./mydb[0x80496c4]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7c12450]
./mydb[0x80489e1]
======= Memory map: ========
08048000-0804a000 r-xp 00000000 08:05 538997     /home/ricorix/mydb
0804a000-0804b000 rw-p 00001000 08:05 538997     /home/ricorix/mydb
0804b000-0806c000 rw-p 0804b000 00:00 0          [heap]
b7a00000-b7a21000 rw-p b7a00000 00:00 0 
b7a21000-b7b00000 ---p b7a21000 00:00 0 
b7b61000-b7b6b000 r-xp 00000000 08:05 301984     /lib/libgcc_s.so.1
b7b6b000-b7b6c000 rw-p 0000a000 08:05 301984     /lib/libgcc_s.so.1
b7b78000-b7b81000 r-xp 00000000 08:05 319244     /lib/tls/i686/cmov/libnss_files-2.7.so
b7b81000-b7b83000 rw-p 00008000 08:05 319244     /lib/tls/i686/cmov/libnss_files-2.7.so
b7b83000-b7b85000 rw-p b7b83000 00:00 0 
b7b85000-b7b99000 r-xp 00000000 08:05 214342     /usr/lib/libz.so.1.2.3.3
b7b99000-b7b9a000 rw-p 00013000 08:05 214342     /usr/lib/libz.so.1.2.3.3
b7b9a000-b7bae000 r-xp 00000000 08:05 319241     /lib/tls/i686/cmov/libnsl-2.7.so
b7bae000-b7bb0000 rw-p 00013000 08:05 319241     /lib/tls/i686/cmov/libnsl-2.7.so
b7bb0000-b7bb2000 rw-p b7bb0000 00:00 0 
b7bb2000-b7bbb000 r-xp 00000000 08:05 319237     /lib/tls/i686/cmov/libcrypt-2.7.so
b7bbb000-b7bbd000 rw-p 00008000 08:05 319237     /lib/tls/i686/cmov/libcrypt-2.7.so
b7bbd000-b7be4000 rw-p b7bbd000 00:00 0 
b7be4000-b7bf8000 r-xp 00000000 08:05 319249     /lib/tls/i686/cmov/libpthread-2.7.so
b7bf8000-b7bfa000 rw-p 00013000 08:05 319249     /lib/tls/i686/cmov/libpthread-2.7.so
b7bfa000-b7bfc000 rw-p b7bfa000 00:00 0 
b7bfc000-b7d45000 r-xp 00000000 08:05 319235     /lib/tls/i686/cmov/libc-2.7.so
b7d45000-b7d46000 r--p 00149000 08:05 319235     /lib/tls/i686/cmov/libc-2.7.so
b7d46000-b7d48000 rw-p 0014a000 08:05 319235     /lib/tls/i686/cmov/libc-2.7.so
b7d48000-b7d4c000 rw-p b7d48000 00:00 0 
b7d4c000-b7ee8000 r-xp 00000000 08:05 215265     /usr/lib/libmysqlclient.so.15.0.0
b7ee8000-b7f2b000 rw-p 0019b000 08:05 215265     /usr/lib/libmysqlclient.so.15.0.0
b7f2b000-b7f2c000 rw-p b7f2b000 00:00 0 
b7f2c000-b7f4f000 r-xp 00000000 08:05 319239     /lib/tls/i686/cmov/libm-2.7.so
b7f4f000-b7f51000 rw-p 00023000 08:05 319239     /lib/tls/i686/cmov/libm-2.7.so
b7f5b000-b7f5f000 rw-p b7f5b000 00:00 0 
b7f5f000-b7f60000 r-xp b7f5f000 00:00 0          [vdso]
b7f60000-b7f7a000 r-xp 00000000 08:05 301932     /lib/ld-2.7.so
b7f7a000-b7f7c000 rw-p 00019000 08:05 301932     /lib/ld-2.7.so
bfed0000-bfee5000 rw-p bffeb000 00:00 0          [stack]
Aborted

```

what's the problem with this?

the whole code for the API is attached.

---

### Post by slavik on 2008-09-27
looks like something is up with the insert ...

I've looked at your code and I have to say that it is crap!!! ... please look into sprintf() for building strings. :)

I would also change the malloc calls to be more explicit: char *msg = (char*) malloc(sizeof(char) * 1024));

edit: also, why not just do (temp != NULL) instead of the weird dereferencing and checking against \0 (took me 2 extra minutes to understand what you are doing).
there is a call to free that is segfaulting, which is weird. why don't you just allocate string arrays on the stack? ie: char temp[1024]; malloc() seems to be useless here since you know the size at compile time.

edit2: may I ask why you are using C to interface with MySQL? I've done this in the past and I hope you are not intending on doing this unless it is for a class and/or for a library that you want to write. I would prefer something with easier string handling. :) (Perl, for example)

---

### Post by dwhitney67 on 2008-09-27
After reading Slavik's comments, I too would like to see the code.  But what is an .odx file??  All I came up with is described at this [link]("http://www.fileinfo.net/extension/odx").
----------
Ah nevermind... odt (duh!), not odx.

---

### Post by ricorix on 2008-09-27
oww. sorry for the crappy code. i'm just a beginner. and yes, it is for a class.  But it already worked.  It is after I've changed the fields in mysql_real_connect that it produced that long error.

---

### Post by slavik on 2008-09-27
> **ricorix said:**
> oww. sorry for the crappy code. i'm just a beginner. and yes, it is for a class.  But it already worked.  It is after I've changed the fields in mysql_real_connect that it produced that long error.
no need to apologize. :)
but hey, you learned an easier way to do some things. :) (sprintf() and sscanf are awesome).

@dwhitney67 ... DUDE!!! odt (part of ODF) is an ISO standard and the standard format for OO Writer files. DUDE!!!

---

