---
title: "Memory Leak"
date: 2006-05-08
forum: Programming Talk
---

### Post by krypto_wizard on 2006-05-08
I have a python code which is running on a huge data set. After starting the program the computer becomes unstable and gets very diffucult to even open konsole to kill that process. What I am assuming is that I am running out of memory.

What should I do to make sure that my code runs fine without becoming unstable. How should I address the memory leak problem if any ? I have a gig of RAM.

Every help is appreciated.

---

### Post by LordHunter317 on 2006-05-08
[QUOTE=krypto_wizard]What I am assuming is that I am running out of memory.[/quote]That's possible.  Another possibility is the CPU load + VM load is high enough to be painful.

> What should I do to make sure that my code runs fine without becoming unstable.Limit how much data you load.

>  How should I address the memory leak problem if any ? I have a gig of RAM.The only easy way to get a memory "leak" in python is to have objects that refer to each other you then discard.  Avoid cyclic references and you'll be ok.  Even then, the GC can catch most cases, just later.

---

### Post by thumper on 2006-05-09
One thing that I have come across at work now (I'm doing python full time now :) ) is that some of the other python developers don't seem to even consider the amount of memory that things take up, or the efficiency of their algorithms.

Coming from a C++ background perhaps I am a bit anal about it all.

For example - in one place I create a generator instead of a large list - however this means that I miss out on some functionality of the framework that is using it (percentage complete).  One guy said just return a list.  I then pointed out that the list would contain about half a million items, "so..." he said, and each item is a string that is around 50 to 100 characters long.  He didn't see this as a problem at all.

I prefer not to prematurley pessimise :)

---

### Post by shawnhcorey on 2006-05-09
[QUOTE=thumper]For example - in one place I create a generator instead of a large list - however this means that I miss out on some functionality of the framework that is using it (percentage complete).  One guy said just return a list.  I then pointed out that the list would contain about half a million items, "so..." he said, and each item is a string that is around 50 to 100 characters long.  He didn't see this as a problem at all.[/QUOTE]

He would be correct. C and C++ were developed in days when RAM was measured in kilobytes. Today's RAM is measured in gigabytes. Unless you're working on audio or video, most data will fit into RAM these days. Even JPEGs, which at once time were too large to process all at once, can be completely loaded and processed in one pass.

Efficiency is a relative term. Is is more efficient to load all the data so you can access it at high speed or is it more efficient to load only part of it and have many disk accesses?

shc

---

### Post by thumper on 2006-05-09
It wasn't actually the data itself, but a pointer to data stored in the zodb.

Part of it comes down to personal style: monolithic list or generator...

BTW, we can't load all the data into memory as we are working on a box with 2 gig ram, but working on 18 gig of data.

---

### Post by shawnhcorey on 2006-05-09
[QUOTE=thumper]BTW, we can't load all the data into memory as we are working on a box with 2 gig ram, but working on 18 gig of data.[/QUOTE]

In other words, you changed the rules.

Before you said the data was half a million items of up to 100 characters, or 50MB. Now, it's up to 18 GB.

But the question of efficiency remains. Is it better to load everything and let swap(1) handle the exchanging of data to and from the disk, or to write your own code? Personally, if I have a choice, I would choose to use someone else's, bug-free code than to write my own.

shc

---

### Post by thumper on 2006-05-09
No I didn't change the rules. I just didn't give all the information up front.

The list of 500000 items were references into the zodb.  The size of the list would have been 50MB, the size of the production zodb is 18GB.

If you try and let the machine handle it, you end up in swap death with most of the cpu time swapping pages in and out of memory.  The machine grinds to a halt when even just dealing with 3GB memory let alone 18.

---

### Post by shawnhcorey on 2006-05-09
[QUOTE=thumper]If you try and let the machine handle it, you end up in swap death with most of the cpu time swapping pages in and out of memory.  The machine grinds to a halt when even just dealing with 3GB memory let alone 18.[/QUOTE]

Swap doesn't die, it thrashes. (Yes, that's the technical term for it.) I have always found that when someone decides that there is too much thrashing, they not only write their own disk handler but also significantly refactor the program. In other words, if they had just refactored it but still let swap handle the disk, they would still have the same improvement. And they wouldn't be writing new disk handling code with all the potential new code has for bugs.

shc

---

### Post by thumper on 2006-05-09
And this is the reason that we don't just let swap handle the memory.

Yes it thrashes.  So the program was refactored to not use so much memory.

Sometimes even python programmers need to consider how much memory their programs are using.  That was my initial point.

---

### Post by LordHunter317 on 2006-05-09
[QUOTE=thumper]For example - in one place I create a generator instead of a large list - however this means that I miss out on some functionality of the framework that is using it (percentage complete).[/quote]If you know how many items ahead of time, just return the "index" of the item you're on in addition to the object to process.  You can then determine % complete manually.

[quote=shawnhcorey]He would be correct.[/quote]He *might* be correct.  That's about 47 MiB, which may or may not be acceptable.  We don't know without more details.  It's certainly questionable in certain situations.

>  C and C++ were developed in days when RAM was measured in kilobytes.C++ was not, no.

> Unless you're working on audio or video, most data will fit into RAM these days.No, you're wrong.  Audio and video don't even pull RAM requirements for most people.  The fact you'd mention them strongly implies you've never worked in large memory situations before.  Hint: it's called a RDBMS, and it's called Oracle or DB2.

> Even JPEGs, which at once time were too large to process all at once, can be completely loaded and processed in one pass.No, you're again, wrong.

> Efficiency is a relative term. Is is more efficient to load all the data so you can access it at high speed or is it more efficient to load only part of it and have many disk accesses?Non-sequitur.  That's not even remotely relevant.

> In other words, you changed the rules.No, he did not.  You incorrectly assumed, multiple times.

> But the question of efficiency remains. Is it better to load everything and let swap(1) handle the exchanging of data to and from the disk, or to write your own code? Personally, if I have a choice, I would choose to use someone else's, bug-free code than to write my own.In a language where you don't manage the memory like python, relying on swap is always a bad idea.  Because you can't control how the pages are allocated or what is in them.  You very well may not be able to drop any pages in the pathalogical case.  In any case, you won't be able to drop as many pages as you would in a language that requires manual-memory management.

Far better for performance to never hit that case anyway.  Swapping is painfully slow and doesn't habe any domain-specific data.  Presumably, you do.

> I have always found that when someone decides that there is too much thrashing, they not only write their own disk handler but also significantly refactor the program. In other words, if they had just refactored it but still let swap handle the disk, they would still have the same improvement.Non-sequitur.  Did you ever consider this refactoring was because they changed the way they handled I/O and no other reason?  IOW, it's purely an implementation change.  You may not be able to refactor if you don't make the disk handling change, whatever that means.

And no, that's not what most programs do when they have paging problems.  They really change their memory handling scheme: switch to memory-mapped files, only load parts of files, etc.  This may require changes in I/O but that's not the part that significantly changes code structure.

>  And they wouldn't be writing new disk handling code with all the potential new code has for bugs.No, you're wrong.  You don't have the fantiest ideas about memory managment and it shows.

---

### Post by shawnhcorey on 2006-05-09
[QUOTE=LordHunter317]No, you're wrong.  You don't have the fantiest ideas about memory managment and it shows.[/QUOTE]

Actually, I know more than you.

Swap is tuned to your specific hardware. It knows your page size and sector size. It is only rarely that you can write a better handler. And it is throughly debugged.

Most programs thrash because they make multiple passes thru large data, each doing a different job. By limited the amount of data in memory at once, you make it glaring obvious that as many of these jobs should be done in a single pass. But by applying the same philosophy without forcing the issue, will achieve the same results, less thrashing.

Swap does not thrash on large data, it only thrashes when you access more data than your RAM can hold and then goes back and re-accesses it. If you don't re-access the data, it does not thrash.

shc

---

### Post by LordHunter317 on 2006-05-09
[QUOTE=shawnhcorey]Swap is tuned to your specific hardware.[/quote]No, it rarely is.

> It knows your page size and sector size. Actually, if you look a the Linux swap handling code, you'll see it makes no optimizations based on knowing either.  Why?  because the size of a page on most modern architectures is not constant (not all page sizes can be swapped, that's another concern).  Block size to disk certainly isn't constant and hasn't been for years.

> It is only rarely that you can write a better handler.You can always write a better handler, because you can do a better job of picking what pages to throw away.  More importantly, swap will impinge on other applications you may have no control over but who's performance you still care about, like your database.  Meaning it's clearly not an option when you have code that's not under your control.

>  And it is throughly debugged.Writing code to release memory you're not using isn't hard in a language like python.  If you're following proper scoping rules you shouldn't have to do a thing, most of the time.

> Most programs thrash because they make multiple passes thru large data, each doing a different job.No, that makes no sense.  Your O() space usage is constant.

> By limited the amount of data in memory at once, you make it glaring obvious that as many of these jobs should be done in a single pass. But by applying the same philosophy without forcing the issue, will achieve the same results, less thrashing.I can't parse this as English but I'm pretty sure it's wrong because your premise was incorrect.

> Swap does not thrash on large data, it only thrashes when you access more data than your RAM can hold and then goes back and re-accesses it. No, wrong.  If the pages in question are anonymous data, they must be written out for other pages to be paged back in.  That means when the page is taken away, you occur one I/O out and I/O in. 

> If you don't re-access the data, it does not thrash.If there is no page replacement going on at all, then there is no paging to disk occuring, so this is also a non-sequitur.  The Linux kernel doesn't page to disk at all unless it needs to replace physical pages.  If it does, then you have the potential for two disk I/Os: one out and one in.

---

### Post by shawnhcorey on 2006-05-09
You're missing my point.

If you write your own data-disk handler, it becomes obvious that your program should be refactored to use each chunk of data only once, if possible. What I'm saying is that if the program can be refactored in this manner, you can skip creating the data-disk handler; just refactor your program to access the data one chunk at a time.

Swap will not reload a page unless your program accesses the chunk of data more than once.

shc

---

### Post by LordHunter317 on 2006-05-09
> **shawnhcorey]You're missing my point.[/quote]No, I'm not.  You don't apparently have one.  I have yet to see a single fact posted by you.

[quote]If you write your own data-disk handler, it becomes obvious that your program should be refactored to use each chunk of data only once, if possible. What I'm saying is that if the program can be refactored in this manner, you can skip creating the data-disk handler said:**
> No, that's not necessarily true in the least.  That may not be what the refactoring entails. More importantly, the only way to do what you describe may be through doing what you say is unnecessary.  

More importantly, what you claim becomes obvious doesn't necessarily become so.  Memory-mapped I/O tricks allow for holding only a part of a file in memory while giving the appearance of having the whole thing in memory.  

Also, sometimes chunked access to the data isn't possible, nor is possible to force all the access to happen at once.  Sometimes the requirements placed on the data make that impossible: it's possible to create SQL queries where you just won't be able to what you describe on large datasets.

[quote]Swap will not reload a page unless your program accesses the chunk of data more than once.But swap won't evict the page to disk in the first place unless the physical memory is needed for something else.  That's the problem: you haven't addressed how the page was sent out of RAM in the first place.  Incidentially, that's something you have no control over.  The absolute most that will happen is the PTE is unmapped, which while a non-free operation, is comperatively free compared to the cost of pushing something to/from disk.

---

### Post by shawnhcorey on 2006-05-09
[QUOTE=LordHunter317]No, I'm not.  You don't apparently have one.[/QUOTE]

Obstinancy is not appreciated.

shc

---

### Post by LordHunter317 on 2006-05-09
My apologies.  But it's difficult to find your point admist all the errors.

---

### Post by shawnhcorey on 2006-05-09
[QUOTE=LordHunter317]My apologies.  But it's difficult to find your point admist all the errors.[/QUOTE]

And, somehow, you think this is an apology?

shc

---

### Post by LordHunter317 on 2006-05-09
I don't know what else you expect me to say? 

 The truth of the matter is your posts have been riddled with errors, some very fundamental, so even if you had a valid premise or solution somewhere in there, it's rather difficult to devine admist the stuff that's incorrect.

---

### Post by shawnhcorey on 2006-05-09
[QUOTE=LordHunter317]I don't know what else you expect me to say?[/QUOTE]

I except you to say: "I disagree with you!"

I do not like false apologies.

We have a total disagreement on opinion. But saying things like, "You are wrong..." or "That is 'non-sequitur' ..." is totally disrespectable.

I have been writing programs since 1974 (and UNIX came out in 1979), so yes, in my totally self-centered opinion, I know a little something about computers. And programming. 

All I ask of you is to say "I think you are wrong ..." or "I think you have miss the point ..."

Your posts are arrogant. And no, in my opinion there are no errors in my posts. If you think otherwise, that's your opinion.

All I ask of you is to step outside of your cubie and smell the free air.

shc

---

### Post by LordHunter317 on 2006-05-09
[QUOTE=shawnhcorey]I except you to say: "I disagree with you!"[/quote]This isn't an disagreement on matters of opinion.   It's on matters of **fact**.

> I do not like false apologies.It was quite sincere.  

> We have a total disagreement on opinion. But saying things like, "You are wrong..." or "That is 'non-sequitur' ..." is totally disrespectable.No, it isn't.  If it were, teachers would be forbidden from correcting students.  This entire view is absolutely silly in any environment where learning is to occur.  At some point, you must get to objective facts and whether you're correct about such things is rather binary.

> I have been writing programs since 1974 (and UNIX came out in 1979), so yes, in my totally self-centered opinion, I know a little something about computers.Your statements are contradictory with that world view.

> All I ask of you is to say "I think you are wrong ..." or "I think you have miss the point ..."There's no *think* about it though.  I *know* you are wrong.  Show me where in the Linux mm code the page swapping code does any optimizations based on page size and or block size.  It doesn't.  The most it tries to do is ensure contigously swapped out pages are clustered together, on the basic assumption they will be faulted for together.  But no where does it assume, "because the page size is 4 KiB and the disk block is 512 bytes, I can do..." because neither of those things are constant across all the architectures Linux runs on.  Page size on some architectures may not even be the same for all pages at runtime: PPC supports pages of different size while the system is running, so IA-32 lets you pick your page size when you turn paging on.  

> And no, in my opinion there are no errors in my posts.I'm sorry you cannot accept the Linux kernel source proves you wrong.

> All I ask of you is to step outside of your cubie and smell the free air.I ask you to go to lxr.linux.no and support your statements.  

You were also wrong about timeframes too.  JPEG wasn't formally ratified until 1992, though early implementations existed as early as 1987 or so.  Same with C++, thereabouts.  Neither of which were devloped on or for the era of kilobyte computers; the 80386 was already out by this point.  Most people had a megabyte of RAM or thereabouts.  Which is more than enough to process most JPEGs.  And high-end systems that were actually used for image processing then had considerably more memory.

Again, these aren't arguable matters because they are facts.  The day the JPEG standard was ratified isn't a matter of debate.  What systems were being sold at that time isn't, either.

Your swap statements are non-sequiturs because they make no sense.  I ask you again, how is the kernel reading a page back into memory from disk if it didn't evict in the first place?  And if the page isn't backed by a file (i.e., not code or mmaped) how can it evict it from physical memory without writing it to disk?

There's definitely an I/O penalty for paging anonymous data out.  There has to be, it makes no sense if there isn't.

---

### Post by shawnhcorey on 2006-05-09
[QUOTE=LordHunter317]Your swap statements are non-sequiturs because they make no sense.  I ask you again, how is the kernel reading a page back into memory from disk if it didn't evict in the first place?  And if the page isn't backed by a file (i.e., not code or mmaped) how can it evict it from physical memory without writing it to disk?[/QUOTE]

THE KERNAL IS NOT READING THE PAGE BACK BECAUSE YOU HAVE REFACTORED THE PROGRAM SO IT READS IT ONLY ONCE.

shc

---

### Post by LordHunter317 on 2006-05-09
[QUOTE=shawnhcorey]THE KERNAL IS NOT READING THE PAGE BACK BECAUSE YOU HAVE REFACTORED THE PROGRAM SO IT READS IT ONLY ONCE.[/quote]How is that relevant in the least?

Your original statement:> In other words, if they had just refactored it but still let swap handle the disk, they would still have the same improvement. And they wouldn't be writing new disk handling code with all the potential new code has for bugs.is contradictory with that, BTW.

But, the statement I've drawn issue with:> Swap does not thrash on large data, it only thrashes when you access more data than your RAM can hold and then goes back and re-accesses it. **If you don't re-access the data, it does not thrash.**(emphasis mine) stands alone.  How can this be, given that the page must be evicted and that inccurs a disk I/O?

How can this be, given that the only reason a page will be evicted to disk is to bring another page in (essentially)?

That statement stands alone and makes no sense.  No modern virtual-memory system randomly swaps data to disk.  There's some pesmissim vs. optimism there, but generally data isn't placed on disk unless the physical memory is needed for something else.  You're trying to imply that the eviction to bring something else in to memory is free and that's hardly the case.  It's *nearly* free if you're evicting code or memory-mapped data, because the PTEs can simply be unmapped and the page overwritten; when the data is needed again, it can be read back from the file in question.  But for data without a file to call home (or anonymous memory-maps) the physical page must go somewhere.  And that is a cost that is almost equal to the cost of bringing in the physical page that is replacing it (PTE map and disk I/O).

So like I said, your statement makes no sense.  Eviction isn't remotely free. Anyone who understands the concept of "anonymous data" immediately understands why it cannot be free.

---

### Post by krypto_wizard on 2006-05-09
[QUOTE=LordHunter317]That's possible.  Another possibility is the CPU load + VM load is high enough to be painful.[/QUOTE]
I checked that in the Performance monitor graphs that my memory is getting full and it is also using Virtual memory around half a gig.

> 
Limit how much data you load.

How to do this ? I am a newbie and really not sure how to do these manipulations.

> 
The only easy way to get a memory "leak" in python is to have objects that refer to each other you then discard.  Avoid cyclic references and you'll be ok.  Even then, the GC can catch most cases, just later.
My program is a simulation program with four classes and it mimics BitTorrent file sharing systems on 2000 nodes(and higher). Now, each node has lot of attributes and my program kinds of tries to keep tab of everything. As I mentioned its a simulation program, it starts at time T=0 and goes on untill all nodes have recieved all parts of the file(BitTorrent concept). The ending time goes to thousands of seconds. In each sec I process all the 2000 nodes. 
Higher level Psuedo Code is as follows::

Time = 0
while (True){
       For all nodes in the system{
             Do (Process + computation+saving new data)
        }
       Time++
       If (DownloadFinished == True) 
             exit;
}

I will really appreciate If you could give me some headstart to get rid of above mentioned problems.

---

### Post by LordHunter317 on 2006-05-09
Seeing the entier source code would be most likely the most helpful way.  I'm not a python optimization expert though.  If you're not willing to post it here, I'd be willing to discuss it in private.  Email is in the profile and I can sign a NDA or whatever if needed.

---

### Post by shawnhcorey on 2006-05-09
[QUOTE=LordHunter317]How is that relevant in the least?[/QUOTE]

I have found a link that explains it better: [http://www.ubuntuforums.org/showthread.php?t=172521](http://www.ubuntuforums.org/showthread.php?t=172521)

I realize that English is not your native tongue but try your best to understand it.

shc

---

### Post by KiwiNZ on 2006-05-10
lordhunter317 and shawnhcory please cool it or take it elsewhere

Thankyou

---

