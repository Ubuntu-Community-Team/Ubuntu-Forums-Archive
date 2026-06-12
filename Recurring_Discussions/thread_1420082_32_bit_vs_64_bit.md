---
title: "32 bit vs 64 bit"
date: 2010-03-02
forum: Recurring Discussions
---

### Post by 007casper on 2010-03-02
Can a computer has to be 64bit to handle 64bit version of ubuntu?

What is the easiest way to find out if a computer can handle 64 bit? especially if you dont have any of the specs

Is it possible to load 64bit then revert it to 32bit?

I am sorry if these questions are really retarded.  Extremely newbie.  Thank you. :)

---

### Post by sandyd on 2010-03-02
> **007casper said:**
> Can a computer has to be 64bit to handle 64bit version of ubuntu?

What is the easiest way to find out if a computer can handle 64 bit? especially if you dont have any of the specs

Is it possible to load 64bit then revert it to 32bit?

I am sorry if these questions are really retarded.  Extremely newbie.  Thank you. :)
1. processor does.
2. uname - m
3. no

---

### Post by oldos2er on 2010-03-02
```
cat /proc/cpuinfo
``` , check for the lm flag, as in "flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall [COLOR="Red"]lm[/COLOR] constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx1"

---

### Post by 007casper on 2010-03-02
I thank both of you.

on a 64bit
Is it possible to load 64bit then revert it to 32bit?

---

### Post by Ghost|BTFH on 2010-03-02
> **007casper said:**
> I thank both of you.

on a 64bit
Is it possible to load 64bit then revert it to 32bit?

No.  However, there's also no reason to want to revert to 32bit.

Cheers,
Ghost|BTFH

---

### Post by Tahakki on 2010-03-02
If you have a 64-bit CPU, go ahead and run 64-bit. There's little difference besides the max RAM and software availablilty - these days, though, most stuff can run on 64-bit.

---

### Post by eriktheblu on 2010-03-02
If you want 32 bit, just install 32 bit from the start. If your CPU is 64 bit however, I can't see why you would want a 32 bit OS.

---

### Post by uRock on 2010-03-02
32bit is faster than 64bit, but 64bit can handle more RAM. The only reason I reinstalled the 64bit is to run Windows 7 in a VBox.

---

### Post by 007casper on 2010-03-02
great thank you so much everyone.

I know 64bit is ram hungry, but how is it possible that 32bit faster than 64bit?  

I am just curious.  Majority of the servers are 64bit, desktops 32bit. I would think the servers will have superior setup.

---

### Post by audiomick on 2010-03-02
Firstly, I am running 64 bit, and don't have a problem with it, although it is a good thing to make sure you have a 64bit flash installed.
There are some useful instructions on that subject here
[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

As far as finding out about your system goes, bodi.zazhen posted a useful script here
[http://ubuntuforums.org/showpost.php?p=8851089&postcount=27](http://ubuntuforums.org/showpost.php?p=8851089&postcount=27)

copy and paste it into gedit and save it as "yourchoiceofname" in your home folder, then do
```
bash ./yourchoiceofname
```
in a terminal.
it should produce a result like this (I saved it as "anewdumb" for reasons best known to myself...)
```
mick@ubuntu-desktop:~$ bash ./anewdumb
Your computer is running 64 bit Linux

Your CPU is 64 bit capable

```

---

### Post by audiomick on 2010-03-02
> **007casper said:**
> but how is it possible that 32bit faster than 64bit? 
according to what I have read, but unfortunately didn't save a link to, it isn't. I saw some benchmark figures that indicate that a 64 bit system is faster in a lot of cases, however the difference is also not necessarily very great. If you really want to find out more, do a forum search using " 32bit 64bit" as a search criterion. There have been a lot of threads on the topic.

---

### Post by hobo14 on 2010-03-02
> **iRock said:**
> **32bit is faster** than 64bit, but 64bit can handle more RAM. The only reason I reinstalled the 64bit is to run Windows 7 in a VBox.

This is simply incorrect.  In fact the opposite is true; [64 bit is faster]("http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks").

I can't imagine even a reason someone could think would justify this statement.

---

### Post by NightwishFan on 2010-03-02
More correct is 64-bit *can* be faster. It allows for larger files to be mapped in memory. Processes also use more memory, but on any modern computer that should be no problem. I would suggest you go with 64-bit, I have been running it for years with no problem. Also 64-bit Ubuntu has all the available optimisations such as SSE.

---

### Post by Ghost|BTFH on 2010-03-02
> **iRock said:**
> 32bit is faster than 64bit, but 64bit can handle more RAM. The only reason I reinstalled the 64bit is to run Windows 7 in a VBox.

You have that backwards. 64bit is faster than 32bit on a 64bit system.

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

Cheers,
Ghost|BTFH

---

### Post by uRock on 2010-03-02
I know what tests I ran on my own system. When I ran my tests, there were no reps from AMD, Intel or any other CPU maker putting money in my pocket to change my results.

---

### Post by bodhi.zazen on 2010-03-02
> **Ghost|BTFH said:**
> You have that backwards. 64bit is faster than 32bit on a 64bit system.

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

Cheers,
Ghost|BTFH

Honestly, it depends on the application. There are some tasks where 32 bit is faster, even in those benchmarks you linked.

32 bit systems tend to be smaller in size and use less RAM, although these differences are often trivial (well trivial IMO).

Also, depending on the task, without running benchmarks, for many desktop users with typical tasks, you may not notice a difference. The differences are seen with CPU intense tasks, such as compiling.

With this said, IMO, if you have a 64 bit processor I advise you install 64 bit Ubuntu. You can run 32 bit applications if you wish.

---

### Post by NightwishFan on 2010-03-02
Benchmarks are unreliable at **best**. It is hard for them to be subjective. Perhaps cron ran at the exact time you did something that lowered your results. Also the Ubuntu generic kernel is configured differently on 64-bit. It uses a timer of 100hz instead of 250, which may affect some tasks.

---

### Post by uRock on 2010-03-02
I guess that could be why I get better numbers with 32bit. The only consuming software I run is VBox. Everything else is super simple software.

---

### Post by Shibblet on 2010-03-02
I think there isn't a "true" 64 Bit OS yet.  Windows, Ubuntu, and most other OS's use x86_64, which uses both instruction sets.

However the 64-Bit processors are the same, backwards x86 compatible.

And off Subject... Carlee?  Are you back and feeling better?

---

### Post by hobo14 on 2010-03-02
> **bodhi.zazen said:**
> Honestly, it depends on the application. There are some tasks where 32 bit is faster, even in those benchmarks you linked.
There are some apps that's won't benefit from 64 bit, but their performance won't suffer because of it.

As for those benchmarks, the only test which you could possibly be referring to is 32 bit flash on 64 bit Ubuntu, where the need for an extra compatibility layer gives a slight edge to 32 bit, but 64 bit flash sees an increase between 5 and 10% over 32 bit.
Hardly evidence to justify saying "32 bit is faster", more of a condemnation of Adobe's code.

---

### Post by bodhi.zazen on 2010-03-02
> **hobo14 said:**
> There are some apps that's won't benefit from 64 bit, but their performance won't suffer because of it.

As for those benchmarks, the only test which you could possibly be referring to is 32 bit flash on 64 bit Ubuntu, where the need for an extra compatibility layer gives a slight edge to 32 bit, but 64 bit flash sees an increase between 5 and 10% over 32 bit.
Hardly evidence to justify saying "32 bit is faster", more of a condemnation of Adobe's code.

There are benchmarks that show 32 bit is superior to 64 bit :

[http://www.osnews.com/story/5768/Are_64-bit_Binaries_Really_Slower_than_32-bit_Binaries_](http://www.osnews.com/story/5768/Are_64-bit_Binaries_Really_Slower_than_32-bit_Binaries_)

As with Statistics, benchmarks are somewhat artificial.

You can debate the issue all you like or write off any differences any way you wish.

Benchmarks are not the only consideration and all have flaws of one kind or another.

In the Ultimate benchmark, day to day use, most desktop users will not notice a difference in speed or performance for the vast majority of applications they run as the vast majority of applications / tasks re not all that CPU intense (posting on the Ubuntu forms for example is no faster on a 64 bit machine, nor is word processing, or email ... ).

So while you can claim all the benchmarks you wish, if you make the claim that 64 bit is faster then 32 bit most desktop users are going to be disappointed that their systems are not "snappier".

As I indicated earlier, the times you will notice a difference are with CPU intense tasks, compiling for example, but these tasks are generally not typical day-to-day tasks for the majority of desktop users.

---

### Post by hobo14 on 2010-03-02
> **bodhi.zazen said:**
> There are benchmarks that show 32 bit is superior to 64 bit :

[http://www.osnews.com/story/5768/Are_64-bit_Binaries_Really_Slower_than_32-bit_Binaries_](http://www.osnews.com/story/5768/Are_64-bit_Binaries_Really_Slower_than_32-bit_Binaries_)
That was 2004, on a Sparc Ultra 5 with 256 MB of RAM running Solaris! ;)
Not really relevant to this discussion at all.

> As with Statistics, benchmarks are somewhat artificial.

You can debate the issue all you like or write off any differences any way you wish.

Benchmarks are not the only consideration and all have flaws of one kind or another.
No, benchmarks are not perfect, but they are the best method we have of measuring performance.

> In the Ultimate benchmark, day to day use, most desktop users will not notice a difference in speed or performance for the vast majority of applications they run as the vast majority of applications / tasks re not all that CPU intense (posting on the Ubuntu forms for example is no faster on a 64 bit machine, nor is word processing, or email ... ).
Agreed.
However, the same can be said of transition periods from 8 bit to 16, and 16 to 32 bit.  I'm quite sure no-one here would be willing to go back to 16 bit though.

> So while you can claim all the benchmarks you wish, if you make the claim that 64 bit is faster then 32 bit most desktop users are going to be disappointed that their systems are not "snappier".
User satisfaction is not guaranteed by correctness.

> As I indicated earlier, the times you will notice a difference are with CPU intense tasks, compiling for example, but these tasks are generally not typical day-to-day tasks for the majority of desktop users.
Again, agreed, but this is not what you claimed in your earlier post; you said "*There are some tasks where 32 bit is faster...*".

---

### Post by NightwishFan on 2010-03-02
Ubuntu uses a 64-bit build of Firefox, which apparently is rare in the Windows world. There would be improvements in javascript performance I assume?

---

### Post by 007casper on 2010-03-03
it is not that I am confused, but it started to sound like american cars handle better than japanese cars.

so if you are going to make a cluster - what is the prefered choice for optimium performance?  I would've said 64bit ~ now, I am a bit questioning... would you get more bang for the buck with 32bit

---

### Post by NightwishFan on 2010-03-03
I seriously think that 64-bit should give you more performance in any case. You can still run 32-bit software on it.

---

### Post by uRock on 2010-03-03
I had one program that wouldn't run on 64bit Ubuntu, which forced me to install Windows 7 and still I got tired of dual booting and installed 32bit Ubuntu on here. The 32bit is snappier and boots faster on my machine.

---

### Post by NightwishFan on 2010-03-03
> **iRock said:**
> I had one program that wouldn't run on 64bit Ubuntu, which forced me to install Windows 7 and still I got tired of dual booting and installed 32bit Ubuntu on here. The 32bit is snappier and boots faster on my machine.

I believe you. It does indeed go both ways. I am willing to bet my system would feel snappier if I used 32-bit, though I also do a lot of server-like tasks that improve due to 64 bit.

---

### Post by uRock on 2010-03-03
I must say I am glad we have the option to do whichever easily in Ubuntu/Linux.

---

### Post by LewRockwellFAN on 2010-03-03
> **007casper said:**
>  ... but how is it possible that 32bit faster than 64bit? ... .
Depending on the ap. If it was written for 32 bit systems I believe it would be faster on the 32 bit OS.  

But more to the point, I think, is that some aps are available ONLY for one version or the other. Not surprising considering that most of this stuff is written for fun, fame, and glory, not profit. If you want to use one of these that may determine which you install. Of course there is no reaqson not to install both and dual or multiboot if you have harddrive space. Then if you find that one version does everything better you can scrap the other one when you need the room. That's what I do. Currently running 2 diferent Ubuntus, Sabayon, and W7.

---

### Post by NightwishFan on 2010-03-03
x86_64 has full support for 32-bit apps. They may actually be faster due to the 64-bit kernel and memory mapping.

---

### Post by hobo14 on 2010-03-03
> **NightwishFan said:**
> I believe you. It does indeed go both ways. I am willing to bet my system would feel snappier if I used 32-bit, though I also do a lot of server-like tasks that improve due to 64 bit.
It doesn't "go both ways". There are no advantages to 32 bit over 64 bit, provided you have enough RAM that the larger pointers don't fill it up, and assuming those same larger pointers don't lower the hit rate of the cache (but 64 bit processors are designed with this in mind, AND they have more registers), and assuming you aren't running 32 bit apps on 64 bit and feeling lag from the compatibility layer.
If there's more to it that I'm not considering I'd really like to hear about it, but to put it simply, 64 bit is just superior.

> **LewRockwellFAN said:**
> Depending on the ap. If it was written for 32 bit systems I believe it would be faster on the 32 bit OS. 
Not how it works.

---

### Post by NightwishFan on 2010-03-03
The extra pointers cause my system to desire to swap more which lowers responsiveness on the desktop as the kernel balances the virtual memory.

---

### Post by hobo14 on 2010-03-03
> **NightwishFan said:**
> The extra pointers cause my system to desire to swap more which lowers responsiveness on the desktop as the kernel balances the virtual memory.
Swapping pages to disk?  Just make sure you have enough physical memory, and that problem evaporates.

---

### Post by uRock on 2010-03-03
> **hobo14 said:**
>  but to put it simply, 64 bit is just superior.

I guess my system lied to me when I changed from 64bit to 32bit Ubuntu. Until you have tested them both on the same machine, I guess you will have to go by what the CPU testers are paid to tell you. Personally, I think you had read too many MaximumPC adds.

---

### Post by del_diablo on 2010-03-03
Can't we just let ye old x86 die?
And get a new architecture that is just 64-bit?
x86 is a 16-bit CISC architecture, that currently got 32-bit extension and 64-bit extensions. Th 16-bit are dropped and dead, the architecture runs CISC over an RISC........... Its bugged over with random weird extensions, it deserves to die.

So please, stop this discussion and dedicate your enegy on the death of ye old x86.

---

### Post by NightwishFan on 2010-03-03
I understand the concept of virtual memory, trust me. This machine cannot have more RAM than it has at 1gb. Swapping may make my machine "feel" unresponsive, but in the end I have more throughput. If I desire responsiveness I will turn vm.swappiness to 20. 32-bit I am sure will lower RAM usage at the cost of less multimedia performance.

---

### Post by hobo14 on 2010-03-03
> **NightwishFan said:**
> I understand the concept of virtual memory, trust me. This machine cannot have more RAM than it has at 1gb.
[s]This sentence has no meaning...[/s] Sorry, I don't understand this sentence, please clarify it...

>  Swapping may make my machine "feel" unresponsive, but in the end I have more throughput. If I desire responsiveness I will turn vm.swappiness to 20. 32-bit I am sure will lower RAM usage at the cost of less multimedia performance.
You can set swapiness to 50, and with enough memory to keep the distress level at zero, never swap until your memory is full...
But seriously, this argument is just a red herring.  If you make sure you have sufficient physical memory this becomes irrelevant.


> **iRock said:**
> I guess my system lied to me when I changed from 64bit to 32bit Ubuntu. Until you have tested them both on the same machine, I guess you will have to go by what the CPU testers are paid to tell you. Personally, I think you had read too many MaximumPC adds.
I don't need a benchmark to tell me which architecture is superior (and I don't know what MaximumPC is), I linked to benchmarks for people who don't understand the architecture.
Do you think your single experience (which doesn't sound like it was particularly rigorous) gives an answer to any question?

Providing hardware capacities all increase at the same rate that "bitness"(?) does, a larger bit architecture has performance advantages over, and no performance disadvantages compared to a lower bit architecture.
Always.

64 bit hardware is superior to 32 bit, so to use a 32 bit OS on it seems a waste.

---

### Post by NightwishFan on 2010-03-03
Perhaps then just ask me to clarify. My machine only has the capacity for 1gb of RAM. I have 1gb of RAM. Thus adding more ram will not help.

---

### Post by hobo14 on 2010-03-04
> **NightwishFan said:**
> Perhaps then just ask me to clarify. My machine only has the capacity for 1gb of RAM. I have 1gb of RAM. Thus adding more ram will not help.

Understood, thanks.

---

### Post by uRock on 2010-03-04
> **hobo14 said:**
> [s]64 bit hardware is superior to 32 bit, so to use a 32 bit OS on it seems a waste.

Do whatever makes you happy. If the local gov doubled the lanes on the road, does that mean the traffic moves faster when the speed limit is the same? 

The buses on both sides of the CPU are no faster than they were before. Yeah. if you have a large program running that can actually utilize a 64bit wide thread, then maybe the processor will get more done. 

I don't play games, I don't edit movies and I don't use my system as a server, so running 64bit is like filling a bird bath with a fire hose, it is overkill for what I need.

I won't be replying to anymore of your posts, good-bye.

---

### Post by hobo14 on 2010-03-04
> **iRock said:**
> Do whatever makes you happy. If the local gov doubled the lanes on the road, does that mean the traffic moves faster when the speed limit is the same? 

The buses on both sides of the CPU are no faster than they were before. Yeah. if you have a large program running that can actually utilize a 64bit wide thread, then maybe the processor will get more done. 

I don't play games, I don't edit movies and I don't use my system as a server, so running 64bit is like filling a bird bath with a fire hose, it is overkill for what I need.

I won't be replying to anymore of your posts, good-bye.

I'm sorry iRock, but you really don't understand what you are talking about.

Doubling the width of a road whilst leaving the speed limit the same is a good analogy for a bus, and doubling the width will deliver double the number of cars (or data) in the same amount of time.

Re. the buses, by "faster" you are referring to the transfer rate, in Mhz?
It may not have changed, but the front and back side buses are 64 bit buses, which are not fully utilised by a 32 bit OS.
64 bit OSes can fully utilize the buses, and so potentially increase the data transferred per unit of time by up to double.(Not that this in itself is necessarily an advantage, as addresses are now 64 bits, but it means no disadvantage to the 64 bit cpu)

I didn't say _you_ need 64 bit.

I agree; not replying is an excellent way to avoid definitively losing an argument.

I repeat: 64 bit architecture has advantages over, and no disadvantages compared to, 32 bit as far as performance is concerned. (assuming the hardware capacities I mentioned last post, of course)

You are free to not buy 64 bit hardware (although you will find that very difficult), and you are free to run 32 bit software on 64 bit hardware, but that is a waste, IMHO.
You may be comfortable with 32 bit, but the home pc industry is moving to 64 bit regardless (and 128 bit is already in the pipeline).

---

### Post by uRock on 2010-03-05
> **hobo14 said:**
>  as addresses are now 64 bits

Do your homework before claiming to be winner. Name and prove that any 64bit processor on the market for desktop computers has a 64bit physical address.

---

### Post by matthew on 2010-03-05
Since the discussion has degraded into a flame war, it is being closed.

---

