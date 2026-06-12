---
title: "Stack smashing"
date: 2008-10-31
forum: Programming Talk
---

### Post by whoelse on 2008-10-31
Hi, I am writing a program in C and I have the following problem:

If I have large input data the program is aborted because of stack smashing. 


The program is one large loop which overwrites its values all the time, but all variables are defined before the loop, so everything should be overwritten. If the lopp is repeated 10000 times everything works fine, but with 100000 repeats it crashes.
My question is now, if that error can occurr if I overwrite an array too often (I am not an expert in memory allocation, does it always use the same memory, or is new memory allocated if I overwrite the data). Or do I have to look for an array-out-of-bound error. Or are there any other things I should look for.

Thanks for any suggestions.

---

### Post by Zugzwang on 2008-10-31
You should consider using "valgrind". That tool looks for illegal memory access. 

In general, if you create a variable on the stack, the memory location remains constant until the variable goes out-of-scope. So all pointers to this variable should then also have been gone out of scope.

Look [here]("http://http://ubuntuforums.org/showthread.php?t=828018") for an example on the usage of valgrind. Use google for details.

---

### Post by whoelse on 2008-10-31
Thanks for the tip.

I habe tried that now, but I am still not quite sure what to make of it.

> ==17515== Syscall param socketcall.sendto(msg) points to uninitialised byte(s)
==17515==    at 0x40007D2: (within /lib/ld-2.8.90.so)
==17515==    by 0x804BBA9: udp_send (in /home/xxx/source/receiver)
==17515==    by 0x804A477: main (receiver.c:558 )
==17515==  Address 0xbea0c3c5 is on thread 1's stack
==17515== 
==17515== Conditional jump or move depends on uninitialised value(s)
==17515==    at 0x4026447: strlen (mc_replace_strmem.c:242)
==17515==    by 0x40C6E07: fputs (in /lib/tls/i686/cmov/libc-2.8.90.so)
==17515==    by 0x804A25E: main (receiver.c:525)
==17515== 
==17515== Syscall param write(buf) points to uninitialised byte(s)
==17515==    at 0x40007D2: (within /lib/ld-2.8.90.so)
==17515==    by 0x40D2CB6: _IO_do_write (in /lib/tls/i686/cmov/libc-2.8.90.so)
==17515==    by 0x40D268F: _IO_file_overflow (in /lib/tls/i686/cmov/libc-2.8.90.so)
==17515==    by 0x40D17A4: _IO_file_xsputn (in /lib/tls/i686/cmov/libc-2.8.90.so)
==17515==    by 0x40C6E73: fputs (in /lib/tls/i686/cmov/libc-2.8.90.so)
==17515==    by 0x804A25E: main (receiver.c:525)
==17515==  Address 0x402c02f is not stack'd, malloc'd or (recently) free'd


1. It seems that on line 558 in receiver.c udp_send tries to send something which is not there.

2. and 3. On line 525 seems to be an error with "fprintf(file_pointer, "%s", received_data)". Received_data is a char array of size 20 and in every turn new values are written into the array.

But now I am back with my original questions. These functions work in first 5000 repeats without a problem.

@Zugzwang: Are you German? (Because of your name)

---

### Post by snova on 2008-10-31
Showing us the code would help. How can we determine the problem if we don't know anything about the program?

(I always thought Zugzwang was named after the chess term.)

---

### Post by whoelse on 2008-10-31
But just copying small portions of the code is also quite useless.

Therefore I wanted to know what generally causes these crashes. The problem with uploading is that there are a number of files all having necessary functions.
Still I would really appreciate if anyone looks at my file and can tell me why the error is happening.




Is Zugzwang an English term in chess?

---

### Post by rnodal on 2008-10-31
Could you please run the program under gdb? It seems logical that as soon as the program crashes it would give some info. At least where it happens. 

-r

---

### Post by whoelse on 2008-11-01
> **rnodal said:**
> Could you please run the program under gdb? It seems logical that as soon as the program crashes it would give some info. At least where it happens. 

-r
Hi, thanks for all the tips.
As I have seen that some of you are really willing and able to help me, I will shortly describe my program and the problems with it.

I have two PCs sending data to each other. PC 1 reads it from a file, sends it over the network via UDP and PC 2 writes it in a file and sends acknowledgements.
PC 2 runs one infinte loop until it gets a kill signal. This loop runs for about 5000 received packets and for packet 5001 it crashes because of stack smashing.

The problem it is hard to set break points for a loop where the only condition is that there was no kill signal.

---

### Post by Delever on 2008-11-01
> **whoelse said:**
> Hi, thanks for all the tips.
As I have seen that some of you are really willing and able to help me, I will shortly describe my program and the problems with it.

I have two PCs sending data to each other. PC 1 reads it from a file, sends it over the network via UDP and PC 2 writes it in a file and sends acknowledgements.
PC 2 runs one infinte loop until it gets a kill signal. This loop runs for about 5000 received packets and for packet 5001 it crashes because of stack smashing.

The problem it is hard to set break points for a loop where the only condition is that there was no kill signal.

Some thoughts:
You would not need to send acknowledgements if you change your protocol to tcp. When you use tcp, and there is problem with connection, you get error when reading or writing. That means connection is lost, and there is not much you can do about it. However, when connection is established, packets arrive reliably and in right order.

---

### Post by whoelse on 2008-11-01
I know that TCP would be the right choice for reliable communication but I have to use UDP. One major point of the program is that it does everything step by step.

Otherwise you are right and I would not have to bother about reliability. But like most of the times the easy solutions are not the ones suitable for the problem.

Nevertheless thanks for the input.

---

### Post by rnodal on 2008-11-01
Thanks for describing the intended behavior. Now, you do not need to set break points. Instead start the program under PC2 and let it run under gdb once it crashes gdb will point out the line where the problem occurs and doing a trace back will help. When you can't your find the problem by looking at the source code then gdb seems logical to me. Learning how to use gdb will benefit you in the long run anyways. 

-r

---

### Post by whoelse on 2008-11-01
With GDB I do not get more information than with valgrind. I have identified the lines of error (third post), but I have not found the reason why this happens.

I have now started to deactivate one functionality after another, to see waht triggers the error. But that is quite some work to keep the whole program working but to disable certain elements.

---

### Post by rnodal on 2008-11-01
Sorry for missing that post.

> fprintf(h_file, " %li %li", ppl_start, ppl_end);
			for (i = 0; i <= weights; ++i)
				fprintf(h_file, " %i", ppl[(ppl_cur - i + weights + 1) % (weights + 1)]);

Are you sure that you are not going past the limit of your "ppl" array? One more time using gdb you can check what the value of the caculation inside the brackets does not go out or range. Give that a try and see what happens.

-r

---

### Post by whoelse on 2008-11-01
Don't be sorry, I am really grateful that you are taking your time and are looking at my code.

ppl is defined as ppl[MAX_WEIGHTS+1], MAX_WEIGHTS has to be larger than weights and so if I have a modulo at the end, it cannot exceed the array.

BTW, the program is executed with MAX_WEIGHTS set to 32, but weights only to 8. This means I have defined ppl[33] and execute ppl[x%9]. That cannot be a problem.

---

### Post by whoelse on 2008-11-02
I have found a way to prevent the stack smashing by deleting the following code: 
> 
if ((nready = udp_select(&max_wait)) <= 0) {
                        if (nready == 0)
				printf("Timeout\n");
                                break;
                        if (errno == EINTR)
                                continue;
                        else
                                perror("select_error");
}
So I have to find an alternative for program termination.

I have found a new problem in my program:
[Interprocess Communication]("http://ubuntuforums.org/showthread.php?t=967844")

---

