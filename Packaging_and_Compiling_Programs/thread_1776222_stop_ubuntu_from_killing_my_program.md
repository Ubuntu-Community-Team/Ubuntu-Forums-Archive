---
title: "stop ubuntu from killing my program"
date: 2011-06-05
forum: Packaging and Compiling Programs
---

### Post by MysticMetal on 2011-06-05
Hi,

I'm trying to run an application I wrote that uses lots of large numbers, but Ubuntu keeps killing it.  Can someone please tell me how to stop this from happening?

Thanks in advance:confused:

---

### Post by scott-ian on 2011-06-05
What language is it programmed in?

---

### Post by MysticMetal on 2011-06-05
c++, although it's all ansi c except for some file i/o

---

### Post by lavinog on 2011-06-05
can you post the source?

What error message do you get when you run it from the terminal?

it could be that you are allocating too much memory, or there is a segfault somewhere.

---

### Post by MysticMetal on 2011-06-07
I'd rather not post the code yet (I am doing research).  However, there are no errors or seg faults, it just runs and then says [killed].  I'm certain my code is correct becuse I get output that I want up until the program gets killed.

I've heard about a command 'nice' that I'm going to try to use and will get back.

---

### Post by lavinog on 2011-06-07
I don't think nice is going to help.  That just reduces the priority of your program.
add some debug statements in your program and see how far it gets before it is killed.

did you look at dmesg?

How are you initializing your array?  Are you using malloc or allocating it in one big array?

---

### Post by MysticMetal on 2011-06-08
The progam reads some numbers (if I can stop this killing thing then it will be 50 million unsigned longs), then outputs files as it does it's thing.

At first (when the input file was 50 million unsigned longs) the program would get killed before it wrote any files.  However, by only inputing a part of these numbers I was able to get some output before it got killed.

I'm using the gmp library, in it's standard way;  I'm convined that there are no segmentaion faults (I do admit that my conviction is not infallible), and I think my code is solid.

  I just installed ubuntu on a different drive and made the swap partition 5GB, which seems to have helped.  That is, I read all 50 million unsigned longs.  I think that it will go to completion, but that will probably be tommorrow sometime so I'll let you know.

Thanks for all the advice;  If this doesn't work I'm going to designate 20GB of swap space.:guitar:

---

### Post by MysticMetal on 2011-06-08
Well that didn't work.... completely.  I've come to the conclusion that I just need more memory, although I don't like it.  Maybe if I could get a super light-weight OS or something, but I'll try more memory.

thanks again.

---

### Post by MadCow108 on 2011-06-08
before you buy more ram you should find out it really is the problem. There can be various reasons for the kernel killing your program,  the most common being segmentation faults, bus errors or memory exhaustion.
Use gdb to get a stacktrace, use valgrind to hunt for memory corruption, use massif to do heap profiling, etc.

if your code is as good as you say it should error out with an helpful error messages that tells you your out of ram.
```
void * a = malloc(1000);
if (a = NULL) {
  printf("allocation failed");
  exit(1);
}
```

---

### Post by lavinog on 2011-06-08
Are you using a linked list to store it or are you just using an array?

---

### Post by MysticMetal on 2011-06-13
enter humility, stage center:


Well it turns out that I was not using mpz_clear on a variable that got used a bajillion times, so it was all my fault.

This is when you either rub it in my face or just say 'I told you so'.

Thanks for insisting that it was my code (even though it wasn't seg faults)

---

### Post by lavinog on 2011-06-13
Just curious...did you ever look at dmesg or /var/log/messages to see if the oom killer was what killed it?

---

### Post by MysticMetal on 2011-06-17
No I didn't, sorry.  But I when I have time I'll unfix it, check those, and post the results.  It will probably be next week sometime.

---

