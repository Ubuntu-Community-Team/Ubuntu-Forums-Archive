---
title: "how to cleaning the swap and ram ?"
date: 2006-09-05
forum: Programming Talk
---

### Post by arkangel on 2006-09-05
Hi 

I am working with large matrixes (3000x3000 ~ ) programming in fortran

any time  i run my program i see the the ram usage and the swap usage going up ,  i am using valgrind to test my modules , but i am also linking to another library , which is quite big so no hope to edit the code 

after each time  my program  was running  the swap increases and after ending  the swap and ram remains and the next time the computer slows dows,  i saw in valgrin ouput(quite big)  that there are some leaks in several places in this library and in one of my subroutines

how can i clean  my swap and my ram , regraless of how the programs exits?

---

### Post by LordHunter317 on 2006-09-05
You end the program.  Ending the program does not mean however, that memory paged out will automatically be paged back in.

---

### Post by Hendrixski on 2008-02-25
I kind of wonder about this myself, so if It's not too rude to bump this old of a thread, I can't seem to find an answer.

I'm using GDB to step through some code, and this causes my memory usage to jump into the 80% memory usage bracket and SWAP starts to kick in, when I close the gdb the memory usage goes back to normal, but the amount of swap used stays current.  This sucks because the next time I fire up GDB and  run the program the swap usage increases again and never goes down.  Is there a way to wipe it?

---

### Post by darsu on 2008-02-25
How much swap is being used is *per se* irrelevant. As long as there's swap space to spare, there's no need to clean up; letting data just sit in the swap doesn't cost CPU cycles or anything. The memory manager will unswap data if/when the program to which the data belongs wakes up and wants to access it.

---

### Post by Zwack on 2008-02-25
In addition to the comment from darsu...

The amount of swap being used is irrelevant as long as you have spare swap or spare memory...

Presumably what is happening is that you are running a long with some programs running (but not doing much/anything) and you kick off your memory hog program... 

This program is active and uses huge amounts of memory so it asks for all of the physical memory that's available, and then asks for some more.

The kernel then swaps something that is not being used out of memory and into swap space.  This frees up some physical memory for your process.

Eventually your process terminates and frees up some real memory (and any swap space it had)...

Now you have a bunch of free memory, and some used swap space... So what happens...

If your machine is busy because all of this stuff is being actively used then it brings some pages back from swap space into memory when they are needed... If however they are processes that are running but not using that "memory" then it will stay in swap space until it's needed or the program terminates.

For example you are running a specific daemon but nothing ever connects to it.  That can be swapped out and will never swap back in.  Or you might have a program running which is using memory to cache images that it has displayed, but it only displays them once because you never flip back through them... Again it might have them swapped out but never touch the swap space.

If you're constantly swapping then you probably should worry about it, but if you're just "using swap" then let it use swap...

Check the si and so columns in vmstat to see how you are doing swap wise...

Adam

Z.

---

