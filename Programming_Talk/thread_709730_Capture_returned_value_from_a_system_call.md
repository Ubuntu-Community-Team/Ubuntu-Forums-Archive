---
title: "Capture returned value from a system call"
date: 2008-02-27
forum: Programming Talk
---

### Post by JPotter on 2008-02-27
I have a completed C program that is run multiple times by a second C program to compare sorting algorithms. I want to return a float value from my program and capture it in my outer C program.

can I declare my main function as a float?
[PHP]float main(void)
{
float value;
blah blah blah;
return value;
}[/PHP]

secondly, I am using a system call to run my program:
[PHP]system(call_string);[/PHP]

How can I capture the output of my program for use in the outer program?

BTW: the return value of system() is related to the success or failure of the operation.

---

### Post by Mr. C. on 2008-02-27
You can't change the calling convention of a C program.  The main() call returns at int, period.

C programs return 0 for success, and non-zero for failure.  If you want to return a value, output it to STDOUT and capture that value with the appropriate system or library calls (see: man popen)

MrC

---

### Post by lnostdal on 2008-02-27
can't do that via `system' .. try IPC/pipes instead: [http://www.cs.cf.ac.uk/Dave/C/node23.html](http://www.cs.cf.ac.uk/Dave/C/node23.html)

..also see the man-pages for these functions..

---

### Post by lloyd_b on 2008-02-27
The *simplest* way to get the data back is to write it to a file, and then read that from the calling program. 

Unless you are looping *very* quickly on that subprogram, the overhead of doing this shouldn't be too high (it'll probably be much less than the overhead of the system() call anyway...).

There are several other ways to get the data back (shared memory, SysV IPC, pipes, etc.), but unless you desperately need better performance I'd stick with the "write it to a file" approach.

Lloyd B.

---

### Post by Mr. C. on 2008-02-27
Writing the data to a file requires synchronization of the file name between the two programs, cleanup, and lots of error condition checking on both sides.

The popen call avoids that, as a pipe is created to the program, and STDOUT is simple read until EOF from the open FP.

MrC

---

### Post by lloyd_b on 2008-02-27
> **Mr. C. said:**
> Writing the data to a file requires synchronization of the file name between the two programs, cleanup, and lots of error condition checking on both sides.

The popen call avoids that, as a pipe is created to the program, and STDOUT is simple read until EOF from the open FP.

MrC

1. "synchronizing of the file name between the two programs" -
```
system("program > somefile.dat")
```
takes care of that.

2. "cleanup" - How so?  One way you need fclose(), the other pclose().

3. "error condition checking" - Using the example in #1, no extra error checking is required in the called program, and the only error checking required by the caller is on the fopen() (same as error checking on the popen()), and on the actual read, which is the same either way.  

So popen() is equivalent to a merging of system() and fopen(), which *does* simplify things in that it eliminates one line of code.  But in exchange, you lose the ability to check the return value of the system() call.

I wasn't familiar with the popen() call until you mentioned it (P.S. - thanks), but I suspect this'll be a "six of one, half a dozen of the other" situation, and jPotter will have to decide which approach to take based on the particulars of the situation.

Lloyd B.

---

### Post by volanin on 2008-02-27
> **JPotter said:**
> I have a completed C program that is run multiple times by a second C program to compare sorting algorithms. I want to return a float value from my program and capture it in my outer C program.
can I declare my main function as a float?

Yes you can... technically.
Both an INT and a FLOAT are 4 bytes long in a 32-bit environment.
So you can cast between one and the other freely.

Your first program would be:
```
int main( void )
{
  float MyFloat = 3.5;
  return (int)MyFloat;
}
```

And your second program would be:
```
nit main( void )
{
  float MyFloat;
  MyFloat = (float)WEXITSTATUS( system("call_first_program") );
}
```

This sure works for 32-bit architectures.
But I don't know if it's portable to 64-bit cleanly! (Maybe it is, I just don't have how to test it!)
:)

---

### Post by Mr. C. on 2008-02-27
> **lloyd_b said:**
> 1. "synchronizing of the file name between the two programs" -
```
system("program > somefile.dat")
```
takes care of that.

What happens what the system call fails?  What happens when somefile.dat exists, is unwritable, is a directory?  Very poor error checking indeed!

> **lloyd_b said:**
> 
2. "cleanup" - How so?  One way you need fclose(), the other pclose().
What cleans up somefile.dat ?  Or do you just assume you can leave it in /tmp and ignore it.  Poor programming practice!

> **lloyd_b said:**
> 
3. "error condition checking" - Using the example in #1, no extra error checking is required in the called program, and the only error checking required by the caller is on the fopen() (same as error checking on the popen()), and on the actual read, which is the same either way.  
There is no file redirection in example #1.  In your case, you must check that the file actually did get created.  System will return a generic error if the command exec'd fails in anyway - the failure cause must be evaluated. How are you determining if the command failed, or the redirection failed?
> **lloyd_b said:**
> 
So popen() is equivalent to a merging of system() and fopen(), which *does* simplify things in that it eliminates one line of code.  But in exchange, you lose the ability to check the return value of the system() call.
Not quite - with popen, you're dealing with a memory based pipe, instead of a filesystem (which comes with the nasties of permissions, existence, etc.) entity.  Always avoid creating temporary files when they are unnecessary, and programmer laziness does not promote convenience into necessity.
> **lloyd_b said:**
> 
I wasn't familiar with the popen() call until you mentioned it (P.S. - thanks), but I suspect this'll be a "six of one, half a dozen of the other" situation, and jPotter will have to decide which approach to take based on the particulars of the situation.
Lloyd B.
You're welcome.  But I have I've convinced you that they are not equivalent.  The system() library call should generally be avoided- next popen should, all in favor of fork/exec/and pipe.

MrC

---

### Post by Mr. C. on 2008-02-27
> **volanin said:**
> Yes you can... technically.
Both an INT and a FLOAT are 4 bytes long in a 32-bit environment.
So you can cast between one and the other freely.


This is silly.  All you've done is cast the value into float, which then gets slammed back into an int upon returning from main via_exit in the C runtime (via its status parameter).

And look at your declarations!  You have 

```
int main()
```

These are declared and defined to return int.  The exit system call, and any return from main return 4 byte ints.  Any silly casting is pointless.

What is the point of encouraging this tomfoolery ?

MrC

---

### Post by lloyd_b on 2008-02-27
> **Mr. C. said:**
> 
These are declared and defined to return int.  The exit system call, and any return from main return 4 byte ints.  Any silly casting is pointless.

What is the point of encouraging this tomfoolery ?

MrC

Even if you do get that float stuffed into that int, it wouldn't help..  The exit system call ANDs the return value with 0xFF, so the actual value returned only contains the lower 8 bits of that 32bit int.

The rest of those 32bits are used for other purposes by the system.  The WEXITSTATUS macro is guaranteed never to return a value outside of the char range.

(I'm not certain if this is a Linux thing, or if it's something common to other Unix variants)

There are ways to stuff a float into an int (and vice versa) without a conversion.  For instance:
```
intval = *((int *) &floatval);
floatval = *((float *) &intval);
```
but thanks to exit, these can not be passed intact from child to parent with any reliability.  Besides which programming tricks like this are notorious for being non-portable, and should only be used as a last resort...

Lloyd B.

---

### Post by volanin on 2008-02-28
> The exit system call ANDs the return value with 0xFF, so the actual value returned only contains the lower 8 bits of that 32bit int.

Now that's a good argument.
I rest my case.
:)

---

