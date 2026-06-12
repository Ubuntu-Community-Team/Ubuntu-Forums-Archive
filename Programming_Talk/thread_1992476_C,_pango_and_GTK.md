---
title: "C, pango and GTK"
date: 2012-05-31
forum: Programming Talk
---

### Post by anewguy on 2012-05-31
I'm getting help on the programming forum for my actual code, but I have a question that I hope I'm posting to the correct place:

I have a 64-bit system, using 64-bit Ubuntu 12.04.  My program has pointers to char types in it, and it uses GTK and Pango.  When I use the memory checker valgrind, it shows repeated invalid read of 4 bytes errors.  Does anyone know if all the functions used by GTK, Pango and their calls (like libcairo) are all 64-bit or if by chance one of those along the way was compiled as 32-bit, so such things as pointer sizes are incorrect?

I don't know where else to post this for now - the programming forum would probably be incorrect as I think this is more of an ubuntu "internals" question.

Thanks in advance!
Dave ;)

---

### Post by PeterP24 on 2012-05-31
you really should have posted this in the programming forum. I've watched your thread on that programming subforum - and most likely you are doing something wrong - it is not the fault of the libraries or of the way they were compiled.

---

### Post by anewguy on 2012-05-31
> **PeterP24 said:**
> you really should have posted this in the programming forum. I've watched your thread on that programming subforum - and most likely you are doing something wrong - it is not the fault of the libraries or of the way they were compiled.

See the last post before mine - they say that the errors showing in the valgrind output now do not trace back to my program - note that "gscedit" doesn't appear in the trace backs.  That's why it's got to be in something I'm calling instead of my code, as best I can tell.

If not - any suggestions on actually finding the problem?

---

### Post by anewguy on 2012-05-31
It's probably worth noting that even when valgrind is running my process, memcheck (valgrind) never goes above 2% of my total memory (16gb).  When I run my program stand-alone I have yet to see it go above .1%.  If I was actually leaking memory like the valgrind log shows, my memory usage should keep climbing - it doesn't.

However, if you, or anyone else for that matter, wants to look at the valgrind log and explain to me how to ever trace that back to my code it would be greatly appreciated.

I know valgrind shows the various libs as 64-bit by name, but if someone compiled one on a 32-bit system the results would be bad.  Take my errors of the reads with 4 bytes.  If I understand correctly, on a 32-bit sys04%tem the length of a pointer to type char is 4 bytes.  On a 64-bit system the length is 8 bytes.  So, if I'm understanding correctly, and if one of the libs was compiled on a 32-bit system (even though the name says 64), then pointer passing would be off by 4 bytes.  I believe it still uses the least signifacant bytes, so if the value is being truncated by the size difference, the value would remain the same as long as I don't exceed the maximum memory 32-bits can address.  I would think this would result in the messages with the reads with the 4-byte messages.

Dave

---

### Post by PeterP24 on 2012-05-31
Ok, I am going to check that subforum more carefully and try to reproduce your problem. I already have all the libs in place.

---

### Post by anewguy on 2012-05-31
Thanks so very much - I'm not saying my code isn't wrong, it just looks suspicious.  Maybe somewhere I have something declared as an int when it should be a long or something like that.  You know from following the other thread I just don't know what the heck I'm doing anymore!

I did download the ISO for 32-bit 12.04 as well, so I'm going to make another VM using it and see what happens in 32-bit mode.

BTW - I don't think my most recent code was loaded to the other thread - I've made many changes since then to get rid of the compiler warnings.  Some things I really don't understand, like why I can declare a string as 

char *somestring;

but I get a compiler warning when I reference it in things like an sprintf - it says it expects a pointer to type char * when it got char ** or some such thing.  All I know is that if I cast it in the sprintf as

sprintf((char *)somestring......);

then I get no warnings.  At this point I don't understand why.

Maybe something like that is causing it = I really don't know.  I'll find out soon enough when I try it in 32-bit with valgrind and see what happens (hopefully where valgrind hooks in won't be so low as to go past the 32-bit virtual and end up with 64-bit.  I'll know in a little while.

When it does fail (somehow I'm just guessing it will) then obviously there is something in my code, but I can't figure out how to trace it back.

I appreciate the help - I *hope* it's what I'm thinking, but I suppose chances are pretty high it's still something I'm doing ;)

Attaching the latest code and the log file from valgrind.

Thanks again!

Dave ;)

---

### Post by Bachstelze on 2012-05-31
To be brutally honest with you, I don't think anyone is going to look at your program in detail and tell you what's wrong. It's just too big. Also, the purpose of a tool like Valgrind is not to tell you everything that you did wrong, but to spot minor mistakes in an otherwise correct program. With a program that big, and given your shaky knowledge, there are probably just too many errors, and it makes Valgrind close to useless. When you want to write a program like that, you have to really know your stuff, there's just no way around it, and it doesn't matter what you *used* to know.

If you want to program in C, you have to learn it from the beginning before you can write programs like that. If you want to write graphical programs easily, look into Python.

---

### Post by anewguy on 2012-05-31
Well, I guess that takes care of that.  I was *hoping* I could find out how to trace back from valgrind to my program.  Apparently not.  Seems like there should be an equivalent in linux/unix to what I was used to - let the program abort, look at a memory map from your program and look in the dump to see what the program counter, the registers, variable values, etc., are.  Apparently not.

---

### Post by Bachstelze on 2012-05-31
> **anewguy said:**
> Well, I guess that takes care of that.  I was *hoping* I could find out how to trace back from valgrind to my program.  Apparently not.  Seems like there should be an equivalent in linux/unix to what I was used to - let the program abort, look at a memory map from your program and look in the dump to see what the program counter, the registers, variable values, etc., are.  Apparently not.

Another problem is that you don't listen to what you are told. Any kind of debugging tool is not a substitute for knowing your stuff.

---

### Post by anewguy on 2012-05-31
I too much beyond replying the bad way to that.  Please see the post I am creating requesting somebody take on writing the tool for the users who need it.  I'm out of it.

It's not like I don't appreciate your help - but I completely fail to see where I DIDN'T listen to what you said.  All I've been doing is trying my best to create a tool to fit a need.  If I can't do it, I can't do it.  If I'm too d**m dumb then I'm too d**m dumb.  Either way it's not worth wasting any more time by anyone.  You guys have better things to do.  I've got other electronics projects I have put on the back burner to try to work on this, so it will be nice to be rid of a headache of nothing but frustration and to things I do know yet and enjoy.

I don't know if you know what an Ubuntu Member is, but I have just requested on the beginner's forum to be removed also.  If I'm such an idiot I don't want to give out bad advice to anyone.

Thanks for the help you did give me, and for all the patience you did show.

Have a wonderful life.

---

### Post by Bachstelze on 2012-06-01
I said:

> **Bachstelze said:**
> When you want to write a program like that, you have to really know your stuff, there's just no way around it, and it doesn't matter what you *used* to know.


But all you asked for is another debugging tool.

And please don't put words in my mouth. I never called you dumb, I said that if you want to program, you have to learn (or relearn) it, like everyone else does.

---

### Post by lisati on 2012-06-01
Closed by request of OP

---

