---
title: "HOW TO get TTY id from a c programm"
date: 2009-05-23
forum: Programming Talk
---

### Post by _dino_ on 2009-05-23
Hi experts,
I am trying to get TTY id from my c program.  Something like this:

int TTYID = get_tty();

so I can then use it for something like:

if (TTYID = 1){
  ...
} else {
  ...
}

How do I do this from my c program?

Regards,
_dino_

---

### Post by deepclutch on 2009-05-24
no idea about programming at all.but :
1)tty command list current std input tty id.
2)w and who -also lists.
3)/proc/tty directory lists the driver used for tty and other informations.

---

### Post by stroyan on 2009-05-24
The ttyname() function will return the path to your current tty device, if the process has one.  You can find that using "man -k tty".  Use "man ttyname" to read details about the function.

---

### Post by lloyd_b on 2009-05-24
> **_dino_ said:**
> Hi experts,
I am trying to get TTY id from my c program.  Something like this:

int TTYID = get_tty();

so I can then use it for something like:

if (TTYID = 1){
  ...
} else {
  ...
}

How do I do this from my c program?

Regards,
_dino_

I'm not sure exactly what you mean by "TTY id".  

If you want the name of the device file (such as "/dev/tty0"), you can easily obtain it by using the "ttyname()" function, passing it 0 as the fd.  You can then do a "strcmp()" of that against a string constant to see if it matches some predefined value.

Alternately, you can call the "fstat()" function, using fd 0 again, and check the value of "st_rdev", to get the global device ID for that tty device.

Which makes more sense depends on exactly what it is you're trying to do (you don't provide much information).

Lloyd B.

---

### Post by lensman3 on 2009-05-24
Take a look at the man page "man 4 tty".  The controlling terminal for a process is always "/dev/tty".

We used to use the following code snippet to test if an open file was terminal or a file:



   if(	lseek( file, 1L, 0 )  <= 0  )	  /* lseek doesnt work on a console */
      return 1;

   lseek( file, 0L, 0 );		  /* put it back ... */
   return 0;

As I recall, stdin, stdout, and stderr where always assigned the file file handles 0,1,2 respectively.  These are always created and assigned by any starting program in Unix/Linux.  The first available file handle after that is always 4.  See "man stdin".

You might look over the code for curses.  It might do what you want to do.

---

### Post by lloyd_b on 2009-05-25
> **lensman3 said:**
> Take a look at the man page "man 4 tty".  The controlling terminal for a process is always "/dev/tty".

We used to use the following code snippet to test if an open file was terminal or a file:



   if(	lseek( file, 1L, 0 )  <= 0  )	  /* lseek doesnt work on a console */
      return 1;

   lseek( file, 0L, 0 );		  /* put it back ... */
   return 0;

As I recall, stdin, stdout, and stderr where always assigned the file file handles 0,1,2 respectively.  These are always created and assigned by any starting program in Unix/Linux.  The first available file handle after that is always 4.  See "man stdin".

You might look over the code for curses.  It might do what you want to do.

That's a convoluted way of doing it (at least on *nix systems) - the "isatty()" function is much simpler:```
if (isatty(fd))
    printf("File Descriptor is a tty\n");
else
    printf("File Descriptor is NOT a tty\n");
```

Lloyd B.

---

