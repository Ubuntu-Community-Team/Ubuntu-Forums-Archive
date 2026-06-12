---
title: "Is it possible to make a LGPL like project for the creation of a true modular PC?"
date: 2007-09-12
forum: Programming Talk
---

### Post by jingo811 on 2007-09-12
I'm having trouble formulating my thoughts concise enough  :-k so the title and whatever content that follows might sound weird and confusing.


*[FONT="Century Gothic"]But I have a dream to one day have a true modular (laptop) PC in my hand where one can replace vital components with ease like playing and building with LEGO pieces.[/FONT]*


In order to realize that dream it seems like you need to bring together all the big companies like Intel, AMD, Nvidia, ATI, +mobo companies, etc. etc.
Bringing them together and co-operate on creating such product.

**1.** What's the probability to make them all implement the GPL / LGPL mindset in such an open source project?
**2.** How can one proceed in order to set all this in motion?
**3.** Where can one begin to take that first step?

---

### Post by CptPicard on 2007-09-12
It just needs proper industry standards, which are hard to come by, but not impossible. The whole commodification of the IBM PC architecture is proof of this... as long as manufacturers have more to gain by expanding the overall market through adherence to standards, they will.

In many ways, we already are there... so I don't really see your point :)

---

### Post by jingo811 on 2007-09-12
I want a laptop PC where you can just take out and put in any brand of GPU, CPU units as my will desires.  Lets say you have a laptop PC from the year 2007 ten years later 2017 I want to upgrade my GPU and CPU units without having to replace 80% of the hardware inside the laptop case.

To do that you need to make the Motherboard manufacturers think in a new way compared to how it's done today.  A way that can make the motherboards modular.  To do that you need Mobo companies work together with CPU and GPU manufacturers.  Preferably in an opensource manner where the public can participate in some way or another.....

How can one set that in motion, where can one begin?

PS.
I'm spinning off from an Digg article I read some months ago
[http://digg.com/hardware/NVIDIA_and_ATI_Talk_About_MXM](http://digg.com/hardware/NVIDIA_and_ATI_Talk_About_MXM)
since it seems like they have trouble to get it right.  I want to find all possible ways in which a true modular laptop PC can be realized.  I hoped that I could uncover the formula for that by asking ppl who's been working with GPL projects in the programming industry.  And see how that can be as succefully implemented in the electronics industry.

---

### Post by pmasiar on 2007-09-12
Look at this from the future: would you want in 2027 your motherboard be $50 more expensive **and slower** so just some caveman can add his 20 years old thingie? Like now, if someone wanted to use tape recorder as external memory? tape recorders were standard with first generation of 8bit home computers, and is **good** we don't have to support them anymore. At least I hope nobody uses them now :-)

You want **some** standards, but you also want sometime to forget about baceward compatibility, so you can look forward instead.

---

### Post by aks44 on 2007-09-12
I believe Amiga did it quite right way back then.

Full plug and play before anyone coined the term (not today's plug and pray, mind you), full memory mapping. All drivers were provided onboard (in a ROM / EEPROM).

Granted, this were not thought with evolution in mind but with little effort IMHO the issue could be addressed.

The biggest problem would be the manufacturers agreeing on some standard hardware protocols.

---

### Post by jingo811 on 2007-09-12
Yeah that's a good point without the use and toss mentality during these past 50-100 years much of the hardware we have today wouldn't be as cheap, efficient, light, and all the good stuff that comes with technological evolution.

**But from the electronic newspapers that I read it seems like you can't push the speed much further on CPUs**.  And it doesn't seem to be sound to push the speed even further even if we could do that.  
Because we have already reached a *critical mass*.  Doing so is environmentally bad higher speeds consumes more electricity which means burning more coal and establishing more Nuclear power plants that might pose as dangerous time bombs from mismanagement.

Now we have Dual Core or Multi Core processors.  But still it seems like we are re-using old technologies.  Much of what we have in computers nowadays seems to have reached their *critical mass*.
The next leap would involve spintronics in the hardwares.  By then our PCs might just be a blob of flesh lump or something :)  Like Wraith technology from Stargate Atlantis.  So inserting our old tape recorders might be out of the question anyways by the next tech leap.

**Long story short:**
It seems like this is the right time to bring together all those companies for a GPL / LGPL like project.  Because the evolution has peaked with our current hardwares.  Worrying about our 2007 hardwares not being compatible with 2027 hardware won't matter since the tech leap will have been too great by then.

---

### Post by pmasiar on 2007-09-12
> **jingo811 said:**
> seems like you can't push the [CPU] speed much further ...Now we have Dual Core or Multi Core processors. ... the evolution has peaked with our current hardwares. 

Why peaked? [Moore's Law](http://en.wikipedia.org/wiki/Moore%27s_Law) is still valid, it just applies not on CPU speed, but on number of CPU cores, caches etc. So get ready for doubling number of cores every 2-3-4 years. It means, btw, around 100 cores in 20 years from now.

Better start learning parallel programming :-)

Moore's law has also interesting consequences for disks. Disk capacity increases **much** faster than access speed (positioning of the head + rotation speed) and throughput. So file storage architectures needs to change too. Now space is cheap and throughput is not.

---

### Post by Awalton on 2007-09-12
Something to think about would be Chumby ([http://chumby.com](http://chumby.com)), the Bug Labs hardware ([http://www.buglabs.net/](http://www.buglabs.net/)), or the GumStix computers ([http://gumstix.com/](http://gumstix.com/)). Depending on what level of "Lego-ness" you're looking to obtain.

Chumby is interesting because they readily encourage the hacking of an otherwise simple bedside computer and have a neat connector that breaks out a lot of options for a hardware maker to play with. It's also probably one of the more open computers currently out there, with both its entire schematics, board layouts and operating system all open source and under a rather liberal license.

Bug Lab's prototype will be really interesting, but is a little bit closer to "OEM"-style hardware, where the platform is just what you'd use to build your own product (like if you were a toy manufacturer or something I guess). It's kinda like Chumby, only with a more powerful computer and designed from the ground up to be portable and "mashable" (like web mashups).

And at the extreme end we have the GumStix computers which are self-contained ARM modules that are intended for hackers and educators, and possibly for integration clients like you'd see with Bug Labs. They're great for hobby-builders because every pin you'd want to use is broken out for you, no hacking necessary.

Keep in mind that all of these are using the ARM architecture (of which Ubuntu currently doesn't support), and are rather low-powered devices compared to more recent PCs. You could look at something like the OLPC if you wanted to get something with a bit more oomph, but designing that kind of project takes significantly more money and time. Hope that helps get you on the path to Free Hardware.

---

### Post by jingo811 on 2007-09-13
So I'm guessing that I just have to email Intel, AMD, Nvidia, ATI, Asus then :) and see what will happen.  Because trying to run an Open source hardware project to satisfactory degree from scratch with public resources would just take too long am I right?  Thus those leading companies will have to stand for the money & resources.
Or maybe I should involve the low profile electronics manufacturers out there with not much PC market shares as of this time.  Tnx!


> Better start learning parallel programming 
**4.** How much time do you estimate that a single core programmer will need in order to shift to Dual core programming?
**5.** Will it be easier for programmers to adopt multi core programming once they get used to Dual core programming? 
**6.** Or will each core addition require as much time it takes to go from single to Dual core?
**7.** I don't know much OO programming but for a programmer to handle 10-50 cores at once that must be really messy to work with right?

---

### Post by Soybean on 2007-09-13
> **jingo811 said:**
> Lets say you have a laptop PC from the year 2007 ten years later 2017 I want to upgrade my GPU and CPU units without having to replace 80% of the hardware inside the laptop case.

The trouble with this is that, as the technology for CPUs and GPUs advances, so does the technology for the pathways between them. When new motherboard chipsets and expansion slot formats are introduced, it's not just because the hardware manufacturers are trying to be jerks... they've improved the technology, and you need the entire set of improvements to realize the benefits of the new CPU/GPU. For example, if you were to adapt a GeForce 8800 to fit in a standard PCI slot, you'd still have a fancy new GPU, but it wouldn't be able to get data fast enough to be worth it.

It's like... say there was a stretch of highway that was very busy, and it was always a terrible traffic jam because it only had two lanes. So the government upgrades the highway, making it 18 lanes wide at one end, 16 lanes wide at the other, but still only 2 lanes wide for a bit in the middle. It's not going to help the traffic situation at all, right? They'll still all get bottlenecked at that middle segment. The CPU is one end, the GPU is the other end, and the bit in the middle is the 80% of your computer that you don't want to replace. ;)

It might be possible to standardize things a bit more than they are now... but take it too far, and you'd just kill off any sort of progress.

> **jingo811 said:**
> **4.** How much time do you estimate that a single core programmer will need in order to shift to Dual core programming?
**5.** Will it be easier for programmers to adopt multi core programming once they get used to Dual core programming? 
**6.** Or will each core addition require as much time it takes to go from single to Dual core?
**7.** I don't know much OO programming but for a programmer to handle 10-50 cores at once that must be really messy to work with right?

If you learn the basics of multi-threaded design, designing for 50 cores would be about the same as designing for 2. It might be difficult to effectively use all 50 cores with a single program, but that's just because few tasks can be broken into that many independent sub-tasks.

---

### Post by pmasiar on 2007-09-13
> **jingo811 said:**
> So I'm guessing that I just have to email Intel, AMD, Nvidia, ATI, Asus then :) and see what will happen. 

let me guess: nothing? We need to aggregate tens of thousands of users to get st least some tractions with them.

> those leading companies will have to stand for the money & resources.

Why: where is the profit in it for them?


> How much time do you estimate that a single core programmer will need in order to shift to Dual core programming?

If I apply [Sturgeon's law](http://en.wikipedia.org/wiki/Sturgeons_law), 90% of developers will never be able to learn it :-)

Now seriously: it depends on what language/framework you will use. C++ is hard even without threads, and Java's solutions are famous to be brute force OO approach, usable only by Java API gurus. 

Compared to that, [Parallel Python](http://www.parallelpython.com/content/view/17/31/) are simplicity itself. Dynamically typed  language shines again :-)

Edit: I found [http://www.pledgebank.com/open3d](http://www.pledgebank.com/open3d) - to leverage influence of a group

---

### Post by jingo811 on 2007-09-13
I'll answer all the questions tomorrow more seriously, I have a test to prepare for until tomorrow only 1 hour left for study....

I just couldn't resist doing this :)
> Edit: I found [http://www.pledgebank.com/open3d](http://www.pledgebank.com/open3d) - to leverage influence of a group
**I Robert the Bruce solemnly pledge loyalty to William Wallace.**


[COLOR="Red"][SIZE="4"]This is.... SPARTAAAAAA!!!!![/SIZE][/COLOR]

[IMG]http://i6.tinypic.com/4oue06w.jpg[/IMG]

---

### Post by jingo811 on 2007-09-14
[SIZE="4"]**8.**[/SIZE]
> **Soybean said:**
> The trouble with this is that, as the technology for CPUs and GPUs advances, so does the technology for the pathways between them. When new motherboard chipsets and expansion slot formats are introduced, it's not just because the hardware manufacturers are trying to be jerks... they've improved the technology, and you need the entire set of improvements to realize the benefits of the new CPU/GPU. For example, if you were to adapt a GeForce 8800 to fit in a standard PCI slot, you'd still have a fancy new GPU, but it wouldn't be able to get data fast enough to be worth it.

It's like... say there was a stretch of highway that was very busy, and it was always a terrible traffic jam because it only had two lanes. So the government upgrades the highway, making it 18 lanes wide at one end, 16 lanes wide at the other, but still only 2 lanes wide for a bit in the middle. It's not going to help the traffic situation at all, right? They'll still all get bottlenecked at that middle segment. The CPU is one end, the GPU is the other end, and the bit in the middle is the 80% of your computer that you don't want to replace. ;)

It might be possible to standardize things a bit more than they are now... but take it too far, and you'd just kill off any sort of progress.

Ironically I understood your tech talk more clearly than your analogy story :)  But just to make sure that we are on the same frequency I want to make sure I understand your analogy right.

[IMG]http://i14.tinypic.com/6gn671v.png[/IMG]

---

### Post by jingo811 on 2007-09-14
**[SIZE="4"]9.[/SIZE]**
> **pmasiar said:**
> 
> those leading companies will have to stand for the money & resources.

Why: where is the profit in it for them?


The profit and advantage for them to participate and sponsor such a public open source GPL / LGPL project.  Would be in TIME something they lack at this hour and have been for some years.  TIME is what they'll need to fight off the

**Self-fulfilling prophecy: industry struggles to keep up with Moore's Law**
[http://en.wikipedia.org/wiki/Moore%27s_Law#A_self-fulfilling_prophecy:_industry_struggles_to_keep_up_with_Moore.27s_Law](http://en.wikipedia.org/wiki/Moore%27s_Law#A_self-fulfilling_prophecy:_industry_struggles_to_keep_up_with_Moore.27s_Law)

By taking on such a project they might benefit from a different kind of income source other than the kind of business they've been relying on since the Pentium I series processor era and forward.

The semiconductor ppl are pushing their Warp drives so hard to fullfill that prophecy that they're starting to bleed to death.
As my little Top Gun illustration shows.  Just because you push your engines to the max velocity doesn't mean that you'll get to the goal quicker.  By traveling through the hot zones they unnecessary take too much damage and thus slows down uncontrollably and for an undetermined period of time.

**Slow down and get there faster**, is a saying they use at the make pretend Top Gun academy 8)
[IMG]http://i6.tinypic.com/5zgg3tt.png[/IMG]



**[SIZE="4"]10.[/SIZE]**
> Why peaked? Moore's Law is still valid, it just applies not on CPU speed, but on number of CPU cores, caches etc. So get ready for doubling number of cores every 2-3-4 years. It means, btw, around 100 cores in 20 years from now.

If I'm not mistaken somewhere in the 70's the engineers had trouble profiting from the semiconductor business until they unlocked the secrets of the Pentium era and thus could play the processor speed game with the market.

Before that they already had ideas for the Dual/Multi core architecture designs.  At that time around 80-90's that idea wasn't as profitable as the MHz speed game that Pentium processors presented.

Now we have hit the *critical mass* with that MHz/GHz speed game and are re-visiting an old architecture idea that isn't much of a Tech leap.
According to Moore's Law it still counts as technological progress but....
The real tech leap will be something else.....(I just dunno what :) but Multi core isn't it )

---

### Post by pmasiar on 2007-09-14
> **jingo811 said:**
> 
The profit and advantage for them to participate and sponsor such a public open source GPL / LGPL project.  Would be in TIME something they lack at this hour and have been for some years. 

If CEO of a public stock company will miss profit estimates for 2-3 **quarters**, stock holders will not wait **years** until she can make it profitable again, but she will be promptly replaced with another CEO. And making profit from GPL code is not obvious, and not as easy as squeezing profits from proprietary locked-in users. I think this part is obvious?

> industry struggles to keep up with Moore's Law

Not so. Programmers struggle to keep up with possibilities of hardware. And marketoids struggle to persuade users to upgrade, when old hardware is good enough. Hardware is chugging forward with no problems (omly preparing it to productions becomes more expensive) the only problem is to find out how the new transistors can be beneficially put to useful work, and how to cool them.

> By taking on such a project they might benefit from a different kind of income source 

Like what?

> The semiconductor ppl are pushing their Warp drives so hard to fullfill that prophecy that they're starting to bleed to death.

They have no problem to put more transistors to a chip. Problems is, we programmers don't have any good way to use those additional transistors.

> If I'm not mistaken somewhere in the 70's the engineers had trouble profiting from the semiconductor business until they unlocked the secrets of the Pentium era and thus could play the processor speed game with the market.

... until market consolidated, and Intel started raking monopoly profits? :-) 

> Now we have hit the *critical mass* with that MHz/GHz speed game and are re-visiting an old architecture idea that isn't much of a Tech leap.

So for expert like you, parallel programming for multicore systems is something you do before breakfast, blindfolded? I am not that smart, for me it is quite of a challenge to do it right. Which language do you use?

> According to Moore's Law it still counts as technological progress but....

One of us don't understand the Moore's law. It says, **number of transistors** doubles. It says nothing about progress, whatever your definition of progress is. As long as it doubles, law holds. **Side effect** was increasing speed of CPU, until 2003 or so. In '70ties, even one complete core on a chip was challenge, multicore non-RISC CPUs became possible only in last couple of years.

> The real tech leap will be something else.....(I just dunno what :) but Multi core isn't it )

here we have another kind of visionary: the "anti-visionary" :-)

---

### Post by aks44 on 2007-09-14
> **pmasiar said:**
> parallel programming for multicore systems is something you do before breakfast, blindfolded? I am not that smart, for me it is quite of a challenge to do it right.

I'll pop in just to quote (again) Herb Sutter (from the top of my head, so this may not be his *exact* words) :

"*lock-based concurrency* [note: today's vision of concurrency] *is very hard for expert programmers to get right... lock-free concurrency* [note: tomorrow's concurrency?? NOT] *is almost impossible for anyone to get right...*"


Software Transactional Memory anyone? Seamlessly introducing ACID properties into mainstream multithreaded OO design would really be a definitive shift in programming paradigms... I'm just waiting for someone smarter than me to get such a framework up and running. :D

---

### Post by CptPicard on 2007-09-14
On the other hand, things like continuation-based coroutines are very convenient once you get the hang of call/cc :) Of course it's not real multithreading and you need to design your code co-operatively, but the more I look at it, the more convinced I become that this is the way to do multithreading within a single application... as long as you're able to isolate side-effects or even code in purely functional style (like Google does), you remove a lot of complications.

---

### Post by jingo811 on 2007-09-15
**[SIZE="4"]10.[/SIZE]**
> **pmasiar said:**
> 
> Now we have hit the *critical mass* with that MHz/GHz speed game and are re-visiting an old architecture idea that isn't much of a Tech leap.
[B]
So for expert like you[/B], parallel programming for multicore systems is something you do before breakfast, blindfolded? I am not that smart, for me it is quite of a challenge to do it right. Which language do you use?


Just to make things clear I'm probably the least experty in this forum section.  When it comes to computer/ hardware/ programming/ and IT/ understandings.

I'm just an anti-visionary :KS who wants to be able to take apart their PC with ease without triggering Murphy's Law and accidentally mess up the hardware with static charges from my polyester pants for instance. :)
Also I'm probably not competent enough to discuss hardware manufacturing :)  I just happen to be a curious monkey who has a knack for stumbling upon certain information from time to time.


**Regarding the language breakfast comment.**  It seems like whoever that's running the Multi-core industry today isn't doing a good enough job teaching programmers how to shift to Dual Core thinking efficiently enough.

As Soybean put it once programmers get past the Dual Core obstacle the rest will be history.  I think we should send some Ubuntu guys to the Multi-core leaders in order to help them write **Dual Core tutorials** that normal ppl can read and understand.
> **Soybean said:**
> 
If you learn the basics of multi-threaded design, designing for 50 cores would be about the same as designing for 2. It might be difficult to effectively use all 50 cores with a single program, but that's just because few tasks can be broken into that many independent sub-tasks.


---

### Post by Awalton on 2007-09-15
> It seems like whoever that's running the Multi-core industry today isn't doing a good enough job teaching programmers how to shift to Dual Core thinking efficiently enough.

If you ask me, they're doing a fine job.

Keep in mind that most of your day-to-day operations will stand to gain nothing from running on dual cores. Where we should be thinking about multicore technology is in kernel space, not user space.

Think about it this way: when we designed computer operating systems in the past, we designed them to allow us to use a lot of applications on one processor. This meant that we needed a way of scheduling out when what applications could get to use the processor. Now, with multicore technology, all that needs to happen is reducing the granularity of the scheduler to meet the new ability to fill the hardware.

Our OS says "I have one processor, I have 20 applications that want to use it, I need to come as close as possible to giving each application 1/20th of a second on the processor, minus whatever time it takes me to switch between them". When we give it two cores, it needs to say "I have two processors, I have 20 applications that want to use them. I need to come as close as possible to giving each application 1/10th of a second on one core."  As the number of cores increases, we get closer and closer to returning to realtime interactivity ala DOS.

For some applications, this is unacceptable of course, and for those applications, we've already got working mechanisms in place, threading, coroutines, the whole shebang. The biggest problem with the model above becomes resource contention, which is why we need to spend less time worrying about how to deal with multiple cores, and more time worrying about how we're going to deal with getting data in and out of our hardware. 

The slowest component in a modern computer is the hard drive, it's just about the last component in which we can talk about read times taking **milliseconds** as most RAMs can do microsecond or tens of nanoseconds random accesses or better, and most buses can push gigabytes of data per second. We should be asking hard drive companies to build us a hard drive with a bunch of individual platters and read heads rather than asking them to build us one enormous hard disk. A 200GB hard disk implemented as 4 50GB hard disks stacked one on top of the next would basically quadruple sustained read and writes, and would help to salve the pain of random seeks by allowing a lot of them to happen at the same time. 

Of course, we can also start thinking about pushing hard drives to a cold-storage role and letting Flash take on the role of being our everyday storage medium, but even Flash isn't much faster (though one of the huge advantages is being able to buy a lot of smaller Flash devices and chain them together for massively increased bandwidth). Things like Phase-Change RAM will bring us closer to RAM-like speeds but it's going to be incredibly expensive like Flash was at the turn of the last decade until they start building up fabrication. Apple's already moving in this general direction (pushing hard drives to only the top models of their iPod as an example).

It's interesting to think about all of the changes, but it's really deviating from the original topic :-/.

---

### Post by pmasiar on 2007-09-15
> **jingo811 said:**
> Just to make things clear I'm probably the least experty in this forum section. ... I just happen to be a curious monkey who has a knack for stumbling upon certain information from time to time.

I did noticed it - but you present the random bits you stumbled upon with such authority so it forced me to respond, to avoid indoctrination of random passerbys by that misinformation. :-)


>  It seems like whoever that's running the Multi-core industry today isn't doing a good enough job teaching programmers how to shift to Dual Core thinking efficiently enough.

As Soybean put it once programmers get past the Dual Core obstacle the rest will be history.  I think we should send some Ubuntu guys to the Multi-core leaders in order to help them write **Dual Core tutorials** that normal ppl can read and understand.

You might be surprised to learn it, but [http://en.wikipedia.org/wiki/Parallel_algorithm](http://en.wikipedia.org/wiki/Parallel_algorithm) research started in '60 and [http://en.wikipedia.org/wiki/ILLIAC_IV](http://en.wikipedia.org/wiki/ILLIAC_IV) in 1976 was first parallel multi-CPU supercomputer. So if they did not invented easier way to do it yet, chances are  it is really hard, and they will **not** find silver bullet  for another 40 years, and we all will have to learn it the hard way :-)  

Another bad news is, step from singe to dual core is about as hard as from dual to many (10 and more - massively multiparallel) CPU.

---

### Post by pmasiar on 2007-09-15
> **Awalton said:**
> Keep in mind that most of your day-to-day operations will stand to gain nothing from running on dual cores. Where we should be thinking about multicore technology is in kernel space, not user space.

I disagree. Of course kernel can, and should, use more processes. But apps can do it to: when you write email and download and listen to music and compile in background (and run webserver), could those tasks use multiple CPUs?

> When we give it two cores, it needs to say "I have two processors, I have 20 applications that want to use them. I need to come as close as possible to giving each application 1/10th of a second on one core." 

I wish it was **that** easy. What about synchronization of input and placing it into process at right CPU? What if initial guess of task spreading was wrong, one CPU works on 150% and other on 10%, and you need to move some task between CPUs? And many more interesting problems.

> As the number of cores increases, we get closer and closer to returning to realtime interactivity ala DOS.

DOS (if you mean MS-DOS) was **never** real-time. [http://en.wikipedia.org/wiki/Real_time](http://en.wikipedia.org/wiki/Real_time) is about guaranteeing response time for certain processes. MS-DOS was single-task, with build-in [http://en.wikipedia.org/wiki/Cooperative_multitasking](http://en.wikipedia.org/wiki/Cooperative_multitasking) later (when task voluntarily yields CPU control - but scheduler cannot force it).

> We should be asking hard drive companies to build us a hard drive with a bunch of individual platters 

You might be surprised, but most hard disks are multi-platter [since forever](http://en.wikipedia.org/wiki/Image:IBM_old_hdd_corrected.jpg)

> A 200GB hard disk implemented as 4 50GB hard disks stacked one on top of the next would basically quadruple sustained read and writes, 

You mean [http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID) ? It is so  ''80! 30 years old technology!

> buy a lot of smaller Flash devices and chain them together for massively increased bandwidth). 

You are still limited by bus transfer bandwidth.

Summary: all those promised future technologies are here for 30 years, and we **still** cannot solve the problem in  a simple way. Maybe it is a hard problem after all, and there is [no silver bullet](http://en.wikipedia.org/wiki/No_silver_bullet)

---

### Post by Awalton on 2007-09-16
> But apps can do it to: when you write email and download and listen to music and compile in background (and run webserver), could those tasks use multiple CPUs?

Sure they can, but why should they? For certain things, one core is more than enough; web browsing isn't magically going to jump in performance if you add two cores, it's better do to your music playing on one core and save the other for the browser, etc. There are a ton of things that /can/ but /shouldn't/ use multiple cores, and we've already solved problems for those. 

> I wish it was **that** easy. What about synchronization of input and placing it into process at right CPU? What if initial guess of task spreading was wrong, one CPU works on 150% and other on 10%, and you need to move some task between CPUs? And many more interesting problems.

We already have everything needed in place to deal with input and output processes and memory transactions. Why don't we use them instead of throwing away everything we've done to this point? Your question about the "initial guess" junk is completely bunk as well; the kernel already does task switching, the new CF scheduler does almost exactly what I said (thought with a very interesting implementation), and new scheduler just needs to take than and apply it across multiple cores. 

> OS (if you mean MS-DOS) was **never** real-time. [http://en.wikipedia.org/wiki/Real_time](http://en.wikipedia.org/wiki/Real_time) is about guaranteeing response time for certain processes. MS-DOS was single-task, with build-in [http://en.wikipedia.org/wiki/Cooperative_multitasking](http://en.wikipedia.org/wiki/Cooperative_multitasking) later (when task voluntarily yields CPU control - but scheduler cannot force it).

Hmph. My Apple II's DOS was always real-time (aka no scheduling). I don't know about Microsoft's software because they've always gotten everything they've done wrong since day one and I've refused to use them for at least as long. But like I said, we shouldn't skirt scheduling, we're just getting closer to where we'll be able to do everything in real time, so why not gracefully fall back towards that? Back off the granularity until we've got fewer processes than we have tasks, then we can start asking applications if they would rather run on two or three cores. Some things I can easily see moving out to multiple cores would be any kind of data processing,  User interfaces will probably be core-bound for eternity (not saying they should be; BeOS back in the day could do amazing things with threaded UIs and pervasive multithreading, but hardware's solving the problem faster than the software guys can).

One should ask if the software engineers ever will be able to as well; our software is almost never designed or engineered as a system anymore, it's always just a bunch of individual projects loosely knitted together by a bunch of barely-sane guys hoping the next patch doesn't run amok. **Nowadays, we've got so many individual parts, some faster and some pathetically slower than others, that the connections between them are what we need to be looking at as problems.** The over-riding theme of this entire post.

> 
You might be surprised, but most hard disks are multi-platter since forever
You mean [http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID) ? It is so ''80! 30 years old technology!

Open any disk today. You'll see this very common formula in use everywhere: one platter, one read/write head, one I/O unit. When you see a disk that has two platters, it's two platters, two read/write heads (one per platter), one I/O unit. When you see a disk with four platters, it's four platters, four read/write heads, one I/O unit.

What I said in my post is (roughly) one platter, 4 read/write heads, one I/O unit. Two platters, 8 read/write heads, two I/O units. This isn't a problem we can solve in the long term by throwing more hard drives at the situation, we need one hard drive that's four times smarter. In the short term, go nuts as long as you make it a requirement and can find drives light enough for portable use.

> You are still limited by bus transfer bandwidth.
And you still haven't read a word I said. Our buses are hugely wide these days. Our device speeds are not. What's the use of having SATA2 that can do 3Gbps if your hard disk is piddling around with <1Gbps? I'd much rather be bus bound than being device bound any day of the week; engineering new buses is a lot easier than engineering new devices. And in these days, the solution is "why not just use two buses?"; motherboards have so much bandwidth going to waste the manufacturers have no incentive not to build boards with a dozen USB2 (480Mbps x 12) ports, or quad-RAID-able SATA ports.

All-in-all, I'd say take the tongue out of your cheek and re-read what I said.

---

### Post by jingo811 on 2007-09-19
**[SIZE="4"]11.[/SIZE]**
> **Awalton said:**
> 
One should ask if the software engineers ever will be able to as well; our software is almost never designed or engineered as a system anymore, it's always just a bunch of individual projects loosely knitted together by a bunch of barely-sane guys hoping the next patch doesn't run amok. **Nowadays, we've got so many individual parts, some faster and some pathetically slower than others, that the connections between them are what we need to be looking at as problems.** The over-riding theme of this entire post.


Some interesting info you've posted.  Regarding that specific quote above.  Do you have any plans or suggestions for making things better?
What could one do who's not in the circles?
What kind of ppl / competences can change the things you've discussed?


> **Awalton said:**
> 
...Our buses are hugely wide these days. Our device speeds are not. What's the use of having SATA2 that can do 3Gbps if your hard disk is piddling around with <1Gbps? I'd much rather be bus bound than being device bound any day of the week; engineering new buses is a lot easier than engineering new devices. And in these days, the solution is "why not just use two buses?"; motherboards have so much bandwidth going to waste the manufacturers have no incentive not to build boards with a dozen USB2 (480Mbps x 12) ports, or quad-RAID-able SATA ports.
....

That's great news, for me at least (for now) =P~ I have an idea I want to show you guys.
Same questions as above what can one who's not in the proper circles do to change things?

---

### Post by jingo811 on 2007-09-29
OK I'm starting to have trouble keeping track of everything in here.  There's so much questions I want re-ask but that will only make this thread more messy so I'm going to try and not to.

[COLOR="Red"]This is no longer a GPL or LGPL idea since it only seems to apply to programming related works.  The license used will have to be something custom made that works for existing companies.
Formulated so that it won't scare them off and make them uncertain of the rules involved.[/COLOR]

[SIZE="4"]**12.**[/SIZE]
> Why: where is the profit in it for them?

[LIST]
[*]To be able to tap into the cumulative thoughts of creative minds and ideas from all over the Internet.
[/LIST]
[LIST]
[*]To better meet up with the waves of the market.  The market= consumers who says what they want in future PC products and what they dislike.
[/LIST]
[LIST]
[*]Having a direct dialog will help those companies participating in such an open source project focus their developments and sales on products that matters to the market.
[/LIST]


[SIZE="4"]**13.**[/SIZE]
These are some of the ideas I had for a modular PC.  You basically break up the Motherboard and make the Mobo manufacturing more modular in order to better adapt to upgrades.
Where you have flexible connection of some sort to tie each segment to each other.  Either with some cable solution or with some printed circuitry technique.  
Hopefully by doing this a consumer can adapt the motherboard bus "pathways" so that it won't be bottlenecked in the middle because you have some new module like GPU and an old Mobo with less pathways.  By adapting the motherboard pathways old and new hardware can be used longer for the consumer.  Environmental benefits.
**Do you know if this will work or if there's some major obstacle and flaw in the ideas?**

Oh yeah I wanted to use a water tank cooling core in order to get rid of all the noisy fans.  By placing the CPU and GPU surfaces directly inwards the water core.  Will that work you think?
I also prefer not to use Wraith technology it's to messy and sticky it would make things less modular than a regular PC setup. ;-)
[http://youtube.com/watch?v=mo5eZ9VljOk](http://youtube.com/watch?v=mo5eZ9VljOk)
[http://youtube.com/watch?v=t8shVDvMdo4](http://youtube.com/watch?v=t8shVDvMdo4)

[IMG]http://i24.tinypic.com/bgckxz.png[/IMG]
.......
[IMG]http://i21.tinypic.com/wbfe6r.png[/IMG]
.......
[IMG]http://i20.tinypic.com/161eqfp.png[/IMG]

---

### Post by pmasiar on 2007-09-29
> **jingo811 said:**
> 
[LIST]
[*]To be able to tap into the cumulative thoughts of creative minds and ideas from all over the Internet.
[/LIST]
[LIST]
[*]To better meet up with the waves of the market.  
[/LIST]


This has nothing to do with profit. Profit is if you sell  for more than you bought or build.

> break up the Motherboard and make the Mobo manufacturing more modular in order to better adapt to upgrades.


You either are genius smarter than Dell and whole bunch of PC manufacturers, or it will fail. I guess that your chances being smarter than Dell is pretty slim :-) but I cannot tell you more, last time I tried to be honest with a "visionary" like you, it earned me some permanent infraction points, so I will stop now.

---

### Post by jingo811 on 2007-10-05
> **pmasiar said:**
> 
You either are genius smarter than Dell and whole bunch of PC manufacturers, or it will fail. I guess that your chances being smarter than Dell is pretty slim :-) but I cannot tell you more, last time I tried to be honest with a "visionary" like you, it earned me some permanent infraction points, so I will stop now.

I wouldn't think of things as being smart or not, right or wrong.  It's like programming only by using your head, pen and paper.  You will never know for sure if your codes will be 100% water proof until you've put it into a machine to test things.
It's the same here I have some ideas that I now need to put into an electronical "saw machine" to see what tangible obstacles needs to be overcome.

Anyways the i386 motherboard architecture is it only permitted to be produced by Intel, AMD, Asus and such big names.  Or can anyone with the right machines manufacture that architecture.  If not where or from who do you get license and permissions to do it?

---

### Post by jingo811 on 2007-11-11
Nothing to see here move along 	:-$ I'm just taking notes for future references in case I go Memento.
[http://en.wikipedia.org/wiki/Open_architecture](http://en.wikipedia.org/wiki/Open_architecture)

_Open architecture_
[LIST]
[*]IBM PC
[/LIST]

_Closed architecture_
[LIST]
[*]Apple Mac
[*]Amiga
[/LIST]

---

### Post by slavik on 2007-11-11
One of the problems in creating a truly modular system like Lego but with computers is that as time goes on, computers become faster and the parts needs better/wider busses to talk to each other through.

Look at the Socket A ... It went from Athlon Thunderbird (max speed was 1.3GHz) with 133MHz SDRAM to CPUs capable of 3GHz (overclocked) with 400MHz DDR SD-RAM.

between those 2 models are 3 more revisions of the CPU.

Then AMD decided to put the memory controller on the CPU, but the problem arises of needing more pins on the socket,

The only way to do what you want is to come up with a standard that has way more pins than anyone will need currently and hope that you won't run out in near future.

---

### Post by jingo811 on 2007-11-11
That's what I want to find out.  Since how things are today doesn't really make regular PC's modular and upgradeable like you would expect from the word upgradeable.  
I want to find out if you can modularize the motherboard where the Sockets are located.  And make some kind of adaptable bridge between 2 generations of components with different buses.

By slicing up the motherboard.  If that will never work then someone plz explain as soon as possible so I can stop this wild goose chase.  And go back to my life in front of the TV :)

---

### Post by tyoc on 2007-11-11
The point of upgrade is that is about upgrade it with compatible things, in fact in whole, the architectures are compatible, they are not upgradable.

Computers today are modular, you see, you not buy a whole (except if you buy some big company with a "mark" in them... even the OS is plug by default), you can "make" your own computer with different components.


Things today are upgradable to certain extend, but they have limits and those limits are defined by compatibility.


> like you would expect from the word upgradeable.  The problem is the perception... and the word upgradable used in sales but without say the restriction thus the whole thing "upgradable to compatible devices", yea shame in sales and promotion ;)... they don't say all the truth, they only don't say part of it.



That is all about that point I will say.

As a side note, there are places for open the designs of electronic components... opencores IIRC and others, they are some processors open and perhaps other "little" projects for electronics.


-----------------------------------------
I will continue with my point about "upgradable to compatible devices" because re reading my post don't show my point.
[LIST=1]
[*]There exist components (you don't buy a whole)
[*]When some 1 say it is upgradable, it doesn't say it is upgradable to compatible devices.
[*]When you take the computer like a whole, a upgrade is from a CPU of 1.2 to an 2.3. But, the component like entity is not upgradable, is replaceable.
[*]When you have something modular, it can mean that it is separate in pieces, but they don't work alone. Or they can work alone without any other component and can be plugged for make interaction with the other. In fact the case of the modular designs today is the first case (even to some of the examples show in some links, a mother base, etc).
[*]A example. Something that is upgradable in software would not require you download the whole 128Mb for patch a error corrected in few lines of code aka < 1Mb of difference of the program. But still some programs mark an "upgrade" doing you download the whole thing again... in fact you are not upgrading your software you are replacing it.[/LIST]You see, is about perception and usage of words, upgradable to "upgradable to compatible devices", upgradable watching the whole or replaceable watching the parts (parts are not upgradable, if not you will be able to plug parts of it in and out, but they are replaceable in certain context, you need to buy the whole thing, like download the whole program ;)). In other words is a questions of contexts (see 1 thing, see the whole?).

In other words, you are searching/asking that components are more easy replaceable (components will still not be upgradable), but because they can only be replaceable with compatible devices, you are searching to do a "wide compatible device" that has usage for say the next 10 generations of computers, not only revisions of architecture (for replaceable ones) in short time context.

Modularity is another thing... for example if I'm not wrong AMD with ATI wil try to glue CPU and GPU, from my point of view is a nice move for mobile things (now)... but this will not work from my point of view in the market of PCs. Modularity not only mean separate things, but if that is the case, also glue things (like the case of pass memory controller to CPU?).

----------------------

As a side note I don't think is bad to think in not possible things by instance (and I mean that even that you reach a good or bad conclusion probably you will not be able to get it ready to tomorrow), is always a good exercise to mind "debrayar" a little, but if you can get there, thus do it. Perhaps we will not get to some like that (components and architecture upgradable... not only replaceable, and I mean architecture upgradable is that you choice what the computer will focus in compute) in the next?? 10, 40, 100 or more years, but hell yea, that doesn't mean that we cant think of it (probably lost of time... but write post is also pass the time), at the end if not possible in say 70 years we will not be here most probably, and thus only chance now to see it is trough mind.

---

### Post by pmasiar on 2007-11-11
I just seen on [http://programming.reddit.com/](http://programming.reddit.com/) just such a lego-like computer system building kit. I don't remember link, but it is within first 1000 submission, last month only.

---

### Post by jingo811 on 2007-11-11
> **tyoc said:**
> 
..............
..............
..............

As a side note, there are places for open the designs of electronic components... opencores IIRC and others, they are some processors open and perhaps other "little" projects for electronics.

..............
..............
..............


You speak like** V1nt th3 Architect **my brain not compute your words.  But I'm getting the big picture I guess.

[IMG]http://i16.tinypic.com/6y1ydkn.png[/IMG]


You mean this site?
[http://www.opencores.org/browse.cgi/by_category](http://www.opencores.org/browse.cgi/by_category)

By saying IIRC you mean this right?
IIRC = If I Remember Correctly -or- If I Recall Correctly


> **pmasiar said:**
> I just seen on [http://programming.reddit.com/](http://programming.reddit.com/) just such a lego-like computer system building kit. I don't remember link, but it is within first 1000 submission, last month only.
I'm not that desperate yet :) maybe after 3 months.

---

### Post by aks44 on 2007-11-11
> **jingo811 said:**
> I have never heard of this acronym IIRC explain plz!

**I**f **I** **R**ecall  (or **R**emember, YMMV) **C**orrectly

---

### Post by jingo811 on 2007-11-11
[SIZE="4"][COLOR="YellowGreen"]Jackpot!!![/COLOR][/SIZE] 	\\:D/
[http://www.lampret.com/](http://www.lampret.com/)

All I need to do now, is learn how to use a mailing list :-( :confused:

---

### Post by tyoc on 2007-11-11
> my brain not compute your wordshaha, dont worry, is not the first time I heard that in this language or my natal language, hehe.

yea, IIRC is an acronym I use a lot, because my memory is about 512Kb or less.

With my words I mean that upgrade can be possible taking the computer like a whole not piecesT taking the parts or pieces alone thus they are only replaceable by compatible devices (even your motherboard support Intel or AMD, even that both arch are x86 or IA64), there no exist such a device alone that is upgradable (ie, you can't add another 512Mb directly to the graphic card or add a module to support the set of isntructions of DX10, or upgrade from OpenGL 1.5 to 2.0, etc, is *extensible* to use RAM from 256 to 512 if some technology is built-in, but you cant plug to the vidcard another module of 512Mb). This is a point appart of openhw, you need lots of skills to get something real there.


I also found this links about openhw: [http://www.makezine.com/blog/archive/2007/04/open_source_hardware_what.html](http://www.makezine.com/blog/archive/2007/04/open_source_hardware_what.html) I mean, there are already open cores, there are other places that I don't remember that are not tied to opencores for example (like the links in that article). 

There exist LEON 1, 2 and now that Im rereading after some time there is v. 3 (dual core) [http://www.gaisler.com/](http://www.gaisler.com/) . I mean there already exist open hardware, perhaps the big companies or other related are not going to it right now, but also MS isnt going enter to open source with all of what they do, they will only release what they want, even that is has more time than open hardware like concept. If you really want to see some progress there, perhaps you should try your concepts in "little" scale but aiming to "port them" to large scale, thus you will get the facts if what you think is possible.

I barely remember words like "if you really care about computation, you will not only see the software languages, process, etc. but you will also care about where it is run, the desing and such", some like that, I barely remember it. Those "words" was in a context that is possible to write a computer that doesnt follow the von newman architecture (dont remember... but perhaps the author is the same von newman, or a contemporary of he), and was related to this things related in a part to the Bottleneck that communication has, hehe, shame on me that I dont remember the name of the article or the original author. But IIRC if it was the same von newman, he say that was not something good follow that architecture, because is tied to things like that... sorry dont remember Im getting out of space. (Extending this, also IIRC he say that the von newman arch was more like a concept for exemplify computations than a model for implement it, lol... IIRC).


----------------
Searching the reedit I found only this 1 [http://linuxdevices.com/news/NS3871478989.html](http://linuxdevices.com/news/NS3871478989.html) ?? for the ref that pmasiar suguest?

---

### Post by jingo811 on 2007-11-12
........................ :) I'm speechless.
[http://buglabs.net/](http://buglabs.net/)
I liked their youtube video!  From what I've seen about the buglabs team it's like they've already paved the way.  Me don't have to do anything big anymore just small improvements.

---

### Post by hollymcr on 2007-11-12
Just to add another view / set of opinions to this thread...

A modular PC is a great idea; the problem is that we already have it. The idea of having a common infrastructure that can take a wide range of upgradeable components is what we currently call a motherboard; splitting the motherboard up wouldn't gain us much. At the lowest levels little things like cable lengths can make a big difference, so splitting things up to join them together again isn't something to do lightly. In any case the motherboard is one of the lowest cost components of a typical PC.

If you don't think PCs are upgradeable, look at comparable technologies. See if you can upgrade your DVD player to play Blue-Ray disks (you could with your PC), Can you upgrade your TV to HDTV? You could with your PC. Make your car go faster by dropping in a replacement engine? Much easier to swap your PC's CPU.

The problem is that after a few years, it isn't just the CPU or graphics that are outdated; everything is. You'll find some new technology designed to fit old hardware, eg you can get reasonable - not good, but reasonable - graphics cards that support PCI, but the bus simply cannot support faster cards where even AGP has been surpassed. With an open source model it's conceivable that someone would still provide drivers for older hardware, but the Linux kernel frequently drops support for older hardware where the code is no longer maintained and a volunteer to keep it alive can't be found. 

The only things I can see changing this would be to slow the rate of progress or maintain high prices (to encourage people to keep older kit). I don't see either happening, so in the face of that you would need to be prepared to pay a lot extra for your modular PC.

---

### Post by pmasiar on 2007-11-12
Just nitpicking
> **hollymcr said:**
> If you don't think PCs are upgradeable, ... Much easier to swap your PC's CPU.

I have an old IBM XT, very slow. Which current CPU can make it faster?

> the Linux kernel frequently drops support for older hardware where the code is no longer maintained and a volunteer to keep it alive can't be found. 

I would say "it is forced to drop - if noone else cares, why should kernel developers".

> I don't see either happening, so in the face of that you would need to be prepared to pay a lot extra for your modular PC.

There IS one organization ready (and doing it often)  to pay premium price for obsolete hardware: US federal government, Dept. of Defense :-)

---

### Post by jingo811 on 2007-11-13
Hollymcr glad to see you in here ):P your expertise and experiences with PLC's and embedded programming will come in handy in here.
> **hollymcr said:**
> Just to add another view / set of opinions to this thread...

The problem is that after a few years, it isn't just the CPU or graphics that are outdated; everything is. You'll find some new technology designed to fit old hardware, 

eg you can get reasonable - not good, but reasonable - graphics cards that support PCI, but the bus simply cannot support faster cards where even AGP has been surpassed. 

What you said about newer generations of CPU's and GPU's outgrowing the motherboard capacity I understand.  New CPU's/GPU's with better "relayed" circuits (for lack of better words) with more, bigger and better bus "pipes"?! I sort of understand also.
New device with more "bus pipes" can't communicate efficiently and stable enough with Mobo with less "bus pipes".


But what if the buses could be converted so that New device with new buses can talk to old Mobo with less buses?
Isn't it also possible to replace some of the electrical paths on the Mobo with optical paths instead?  Like how optic cables for Internet work?  In order to boost the converter process and maybe also boost the communication between old and new technology in comparison to how it performed between Mobo and Device built specifically for each other.



> The only things I can see changing this would be to slow the rate of progress or maintain high prices (to encourage people to keep older kit). I don't see either happening, so in the face of that you would need to be prepared to pay a lot extra for your modular PC.
or Global warming.  The life cycles of electronic devices especially those for the PC isn't the most environmentally friendly thing in this world.  Some day Arnold the Governator will flex his muscles on this industry. :) like he did with the fossil fueled cars in Caaliphonia.

---

### Post by pmasiar on 2007-11-13
> **jingo811 said:**
>  like he did with the fossil fueled cars in Caaliphonia.

Ridiculous comparison. In last 100 years, cars had one major  innovation: oil pump, at the beginning of the last century. Electric cars are as old as gas-powered, in fact electric car was the first one to break 100 km/h speed record 100 years ago.

In last 40 years, the only "innovation" in cars was SUV, as more "manly" version of station wagon and minivan. Only recently we finally got new combination on age-old ideas: hybrids. It was about time, after 100 years. So comparing innovation cars and PCs hardly makes any sense. Phonia indeed.

---

### Post by jingo811 on 2007-11-14
Either way the production and recycling of PC electronics is bad today.  I haven't read the RoHs directive from top to bottom but from what I get from electronic newspapers.  EU (European Union), the politicians have started to force the electronic manufacturing industry towards a greener way.

That started to get more enforced in the year 2006 when press started to write more about it.
[http://www.rohs.gov.uk/](http://www.rohs.gov.uk/)
[http://en.wikipedia.org/wiki/Restriction_of_Hazardous_Substances_Directive](http://en.wikipedia.org/wiki/Restriction_of_Hazardous_Substances_Directive)

> The only things I can see changing this would be to slow the rate of progress or maintain high prices (to encourage people to keep older kit). I don't see either happening, so in the face of that you would need to be prepared to pay a lot extra for your modular PC.

If it isn't slow rate of progress or higher prices to encourage ppl to keep older kits then the environmental regulations such as RoHs directive will force the industry to make PC's with longer life span ( so that you can upgrade properly during 10-20 years without having to throw away your Mobos ).

That's why celebrities like Arnold Schwarzenegger with little real influence in this Global warming train will make some sort of difference just because they are famous.  If you're famous you could even be a Governor, that's how I think when bringing up the Governator.

[SIZE="3"]My point is RoHs is just the beginning the regulations will get more stringent.  Reducing or completely removing the lead %-age in electronics is just one little step in many steps to come.  That's why the Global Warming train should be accounted for in the qouted reasoning above.[/SIZE]

---

### Post by jingo811 on 2007-11-16
Ah this is what I've been searching for this whole time.  What to make of it is another question though.
[IMG]http://i1.tinypic.com/8amkobm.png[/IMG]

**hollymcr>>>**
What's the proper english term for the above components?
In swedish they call it "flexibla mönsterkort".
Badly translated it would be something like "flexible structure cards" but I suspect that's not the word the industry uses.

**All>>>**
In retrospect all this endless searching, all the energy and work put into this wild goose chase seems to lead to no-mans-land.
It would be much simpler and elegant to find some mathematician and calculate an equation like this from scratch.  (the example is simplified :-) )  
```
(a + b) = (c + d + e)
```
Then apply the theories directly into some nano-tech self-healing components instead.
But if it has to come to that then there won't be any open source modular PC any more. :(

---

