---
title: "linux vs dos"
date: 2007-12-24
forum: Programming Talk
---

### Post by speckman on 2007-12-24
I'm going to start a project and am itching to do it in assembly (maybe w/ some C), perhaps using freedos.  perhaps linux.  It's sort of a neural network matrix.  Not using pointers, just hardcoded offsets (for speed).  think n-dimensional matrix brain.

Does anybody know for certain what sort of performance gains I would get by not doing this in linux?  

I can think of a lot of major obstacles (like portability), but I sort of want absolute control of the processor, memory, and even hard drive partition.  I plan on using all of the memory, and do not want to have to go through any intermediate memory address lookup stage.  i want direct offsets from every other location in ram.  (could I do that in linux with just a very humongous array, say 512M?)

So I'm thinking that by getting rid of the OS and memory segmentation (protection?), and all of that stuff, I can gain quite a bit of speed.  Does anyone know if I'm right about that?

I know that there's a zillion tools I'll need that are in linux, like multi-threading, drivers, other people :), etc.

I think I'll have to do it in both eventually.

Thanks for whatever help you've got!

---

### Post by LaRoza on 2007-12-24
This would only work with a bootable disk.

You have  to access devices through the Linux kernel for everything, and it seems you want total control. 

Basically, you'd have to write an operating system for this. [http://www.osdev.org/](http://www.osdev.org/)

(Unless I misunderstood your intent)

---

### Post by speckman on 2007-12-25
yeah, i was thinking that too.  i guess i should ask on those forums.  
do you know how much overhead linux adds?

---

### Post by tyoc on 2007-12-25
No, but there is [http://www.menuetos.net/](http://www.menuetos.net/) , a complete OS writed in asm, like I remember is one of the more stable (and large) OS writed in asm. Thought I can be wrong, havent been there from some time, there is also some RTOS kernels, and I also think that 1 task process OS will add you less overhead for sure, perhaps running a Linux kernel in single user mode, and with the less auto&#314;oaded apps and drivers would be enought too.


[http://www.freedos.org/](http://www.freedos.org/) IIRC has more extension/support for large memory segments (ie, it is the model flat, not like the old DOS segmented days), and if is like DOS, then it should be almost 1 task at a time (thought perhaps it support more).


Also for advice, it will be nice, if those things that "depend" on the interface with the OS, can be wrote in an "abstract" way, I mean, change a flag ehre and there, and perhaps if done carefully, you will end with version for DOS and linux.

---

### Post by Kadrus on 2007-12-25
> **LaRoza said:**
> This would only work with a bootable disk.

You have  to access devices through the Linux kernel for everything, and it seems you want total control. 

Basically, you'd have to write an operating system for this. [http://www.osdev.org/](http://www.osdev.org/)

(Unless I misunderstood your intent)
That's a nice link...been wanting to read about OS development for a while...not intending to build anything...just curious..thanks for the Link :)

---

### Post by LaRoza on 2007-12-25
> **Kadrus said:**
> That's a nice link...been wanting to read about OS development for a while...not intending to build anything...just curious..thanks for the Link :)

No problem. It is an interesting site and very informative.

---

### Post by speckman on 2007-12-25
i found [dexos]("http://www.dex4u.com/"), which is more of what i want--full access to everything with single-tasking.  (i have been looking at menuetos for a while but am not sure about developing on that)

yeah i read through some of that os dev stuff and got a sick feeling inside.  i think i'll start with an OS, rather than write one.  :)

freedos and dexos, and maybe solaros (but the site is down)
(you're right tyoc, keep it abstract for portability)

still though, is it worth it?  

Well I guess in my mind I'm going to write it in C eventually anyway, for linux (and everything else).

I think I'll have to ask on an OS dev forum about the speed gains

---

### Post by Kadrus on 2007-12-25
> **LaRoza said:**
> No problem. It is an interesting site and very informative.

I have a question and maybe you could answer it..
I was just wondering if functional languages were used in Operating system development...like Haskell for example...there is an operating system developed with  Haskell.. [http://programatica.cs.pdx.edu/House/I/screendump-oct2005.png](http://programatica.cs.pdx.edu/House/I/screendump-oct2005.png)
and there is another one developed also called Kinetic..
[http://www.ninj4.net/kinetic/](http://www.ninj4.net/kinetic/)
I was wondering if it can be a good language to write an OS with..
Once again not intending to build an OS :p...just a bit curious...

---

### Post by tyoc on 2007-12-25
Indeed, there are lots of others OS wrote in different langs, the major part of all OS in history have "died" because there are somewhat research ie not a product, the fun with research is that is research ;), then you can code like you want it and for research what you want.

Indeed, Haskell should abstract lot of things inside and provide the good things that write in that lang give you, that should be fun, still they should wrote the interface for the hardware, that was a part of his research.

> and maybe solaros[http://www.oby.ro/os/](http://www.oby.ro/os/) it work OK for me, IIRC that was an RTOS multitasking (in asm) OS.


>  (you're right tyoc, keep it abstract for portability)

still though, is it worth it?  If you can work without tie yourself much, thus it will be worth, and also you will be able to profile if there is overhead in other environment, and have a point of comparation for your system.

---

### Post by CptPicard on 2007-12-25
Are you sure your algorithm works in the first place before you're considering such extreme optimization? Or are you just wondering about the possibility of running something on top of the iron? You have to realize that this isn't done for performance reasons in general even in really demanding applications... 

Also remember that while the process is running, the OS is not acting as some kind of a "middleman". Your code sits straight on the CPU for as long as the clock interrupt or something else arrives, and if there is no other load on the machine, time spent in scheduler is completely negligible. Same for other kernel-space syscalls, which you pay for if you use them, and would have to code for yourself if you needed them and didn't use an OS.

There is no need to hardcore your memory references as they are resolved by the loader, and stay as they are after that.

I'm not even sure if modern processors even have single-process modes with some kind of flat address space... 

And about writing OS in Haskell... the problem is the hardware interface which you will still need to be writing in something pretty low-level, and I'm not sure if you'll actually be gaining anything in writing stuff like process management in a high-level language... and does Haskell even compile to native? Most dynamic high-level languages have some fundamental issues why it's either really hard to do that or you have to essentially "cheat" by implementing a tiny VM plus bytecode -style binary.

---

### Post by LaRoza on 2007-12-25
> **Kadrus said:**
> 
I was wondering if it can be a good language to write an OS with..
Once again not intending to build an OS :p...just a bit curious...

C, that is why it was made.

---

### Post by monkeyking on 2007-12-25
> **speckman said:**
> I'm going to start a project and am itching to do it in assembly (maybe w/ some C), perhaps using freedos.  perhaps linux.  It's sort of a neural network matrix.  Not using pointers, just hardcoded offsets (for speed).  think n-dimensional matrix brain.

Does anybody know for certain what sort of performance gains I would get by not doing this in linux?  

I can think of a lot of major obstacles (like portability), but I sort of want absolute control of the processor, memory, and even hard drive partition.  I plan on using all of the memory, and do not want to have to go through any intermediate memory address lookup stage.  i want direct offsets from every other location in ram.  (could I do that in linux with just a very humongous array, say 512M?)

So I'm thinking that by getting rid of the OS and memory segmentation (protection?), and all of that stuff, I can gain quite a bit of speed.  Does anyone know if I'm right about that?

I know that there's a zillion tools I'll need that are in linux, like multi-threading, drivers, other people :), etc.

I think I'll have to do it in both eventually.

Thanks for whatever help you've got!

:o

What kind of neural network are you doing?
Have you ever done something like this before,
just writing a driver that actually works, is close to real life hell, and will most likely end in many endless nights.

I would highly recommnd prototyping the problem in some very highlevel language like R. Where a lot of out-of-the-box neural net algorithms has allready been created. Just for checking if you're idea is reallly worth the trouble.

And if you want performance gains, I would rarther looking into threading the problem. Or using some message passing like mpi, if you have access to multiple computers.
Or even csp if youre planning to do a beowolf cluster.

good luck

[http://www.r-project.org/](http://www.r-project.org/)
[http://en.wikipedia.org/wiki/Message_Passing_Interface](http://en.wikipedia.org/wiki/Message_Passing_Interface)
[http://vl.fmnet.info/csp/](http://vl.fmnet.info/csp/)

---

### Post by speckman on 2007-12-26
yeah, i've done assembly programming before and loved it, although it was hell.  :)    I wrote a 4k intro.  I knew what every operand did, had watched it all go through the debugger, etc.  

I guess I'm being nooby about this.  I have the algorithm in my head, and it makes sense to me doing it in assembly, but not so much in high-level stuff.  I last really programmed (and had fun doing it) in assembly, in dos, where I had control over everything.

What I should really do is write it in C, compile with -O3 or so, and then write it in assembly in freedos or an asmos, and see the difference.


The idea is a neural net matrix.  All of the connections between nodes are functionally determined, not pointers.  Like add 0001  0010  0100 1000 etc (and then sub) to get offsets, plus the xor of the address.

Actually what I thought about doing was trying to use genetic programming to figure out optimum configurations.  (like which functions, how many connections)  I'm not even certain it should be a neural net, I just keep thinking about RAM in terms of high-dimensional arrays.  like 256^4 == 4^16.

That's the first part of the program.  The second is to use a random number generator as an oracle.  Treat the random number as it if were a tarot card, an I Ching hexagram, etc.  

In my experience, oracles work, even when done on a computer.  quantum random number generators are easily available (even on-chip on the VIAs), so that would give a "true" random number.

So I want to get oracles constantly and treat that as input.  And then have some sort of associative learning matrix.  

I think this is really good "AI".  Even without a computer, I can use three coins to get an I Ching reading that is pretty right on.  I know most people say that's ********, but that's my experience.

So I figure if a random card or some coin flips can tell me about my life and the state of the world, even of the future, then why not do that a few billion times a second and give it a memory?


Hey, that's exactly the kind of information I was looking for, CptPicard and monkeyking.  Thanks!

I used to spend a lot of time watching the dos assembly scene demos in the 90s.  I don't know how much they actually did in assembly, but that stuff was always cutting edge fast.

> Also remember that while the process is running, the OS is not acting as some kind of a "middleman". Your code sits straight on the CPU for as long as the clock interrupt or something else arrives, and if there is no other load on the machine, time spent in scheduler is completely negligible. Same for other kernel-space syscalls, which you pay for if you use them, and would have to code for yourself if you needed them and didn't use an OS.

What about memory allocation?  I guess, now that I think about it, I can just allocate very large arrays and manage the memory myself.

I know that with Moore's law and dumpster-diving, I can pretty much get as much computational power as I want.

Well thanks again for the feedback.  There's basically just two parts of me.  The part that wants to do it from scratch, in an original way, and the part that is writing this email inside ubuntu, thinking about all of those C libraries that would be awfully useful (and drivers, and process control, and nvidia's CUDA, etc.)

---

### Post by CptPicard on 2007-12-26
If I were you I would be much more concerned about whether this idea even works in any meaningful way. To me it just seems like you are essentially running random code and hoping something comes out of it, regardless of you calling it a  "neural net" ;)

You should be mindful of the fact that there's no way of even telling whether your random arrangement of code will halt, and most of it will probably not, or will fail in some other ways. No amount of genetic algorithms is going to let you optimize out of that if your fitness measure starts running infinitely long on most occasions.

Normal NNs which express their connection strengths as real numbers are not that much weaker than you seem to think... after all, they're connected to all of their neighbours (let's ignore the complication you're introducing by not keeping it feed-forward) to varying degrees, and their training even is quite well understood. The training of yours isn't, and GAs are probably not the answer for reasons given above. They would be awfully slow too.

And what's with all the mysticism? What next, Astrology? :) At least computational oracles are a bit different concept from just tossing coins.. :)

---

### Post by speckman on 2007-12-26
CptPicard:  :) :) haha

Yeah it's something like that.  The evolution will be very much within defined bounds.  Stuff like what and how many connections, which activation functions.  I plan to write a nice display program so I can watch their behavior in realtime.  The GAs will be a tool to find a good NN setup.

Yeah it's all mystical.  It totally breaks with what I was taught in compsci.  :)  But it jives with the experience I have with oracles, magic, and other weird 'psychic' stuff.  My logic goes, if oracles work, then they should work running at N times the speed.

I am going to try a normal neural net, just in more of a low-level way.  

I know the idea is nuts, and it's a doozy.  I also know that about a jillion people have been researching NNs and other AI techniques and really have a lot of good info that I should tap into.

Mostly, the NN is an interface between the "pure-wisdom" of the oracle, and I/O.  I don't know what a byte-based oracle means (0-255).  Even if I just did tarot cards or the I Ching, I don't know how to apply that to a computer's world.

One interesting tidbit is that African shamans have been using a 256-symbol oracle for a few thousand years, and a few tribes were even using xor.  (I read that in a scholarly book about oracles a while ago, which I don't know the info for).

You've read Gibson, right?  How the Voodoo gods are living in the net?  Voodoo uses that 256-oracle.


About the speed increase, I asked on the DexOS forum, and Dex says 400%.  :)

[http://jas2o.forthworks.com/dexforum/index.php?topic=311.0](http://jas2o.forthworks.com/dexforum/index.php?topic=311.0)
> ...from my working out all things being equal, i would say again of 400% .
Now this may shock alot of coders, But its based on the old Xbox, Now the spec of the old Xbox is the same as DexOS...


And yes, Astrology will definitely be incorporated as an input for the NN.  I don't know why everybody hates on Astrology.  It's better at predicting psychology and relationships than anything else I know of in western psych.

Well, I know why.  :)  It's the same reason that everybody hates on magic and psychic powers.  And no, that reason is not because it's a fake.  :)  It's because somehow, in our culture, we have systematically and collectively ignored all evidence that proves the existence of all of those magical things.

My favorite example of scientific proof of 'magic' is Karl von Reichenbach.
[http://www.hbci.com/~wenonah/history/odenergy.htm](http://www.hbci.com/~wenonah/history/odenergy.htm)

My other favorite example is my own experience.

---

### Post by Lster on 2007-12-26
Oh my! Some one else considering OS development! I have got to say that is very tricky - it took me about a year to get an OS running in PMode, with memory management, graphics and almost no hardware drivers (except the screen, keyboard, mouse etc...). It is probably the most frustrating programming I have done - but I did find it very satisfying. :)

---

### Post by CptPicard on 2007-12-26
Not that I buy into your magical thinking -- and I still think there is no reason not to prototype this first in a higher-level way if you want to prove a point -- but there is an interesting idea about consciousness I once heard... neural nets are interestingly powerful machines considering how crude a copy they are of real neurons, but their problem from the cognitive science point of view is their behaviourism. It's pretty clear that there is more to consciousness than mere stimulus-response. Thus we have the computational model of the mind.

However, we haven't yet really figured out how the whole seems to be greater than the sum of its parts, and how the fundamentally rather passive neural net ends up being the active agent we find inside our skulls.

Someone once suggested that it seems like the very low-level brain stem sort of functions of the brain seem to be somewhat chaotic in nature. What if there is some kind of a natural random number generator down there that works based on the random energy it gets from the evironment, which our organized, trained cortex then organizes into consciousness? The impulses have to come from somewhere you know. Otherwise the brain would just sit there, doing nothing.

Are *we* essentially just noise of the universe that the brain tries to make sense of in some way that evolution has found beneficial? I've always been very, very interested in the philosophy of AI, and still, that doesn't quite answer the ultimate metaphysical question of as to why exactly there is consciousness. It doesn't seem to be an necessity even in this picture.

---

### Post by LaRoza on 2007-12-26
> **CptPicard said:**
> but there is an interesting idea about consciousness I once heard... neural nets are interestingly powerful machines considering how crude a copy they are of real neurons, but their problem from the cognitive science point of view is their behaviourism. It's pretty clear that there is more to consciousness than mere stimulus-response. Thus we have the computational model of the mind.


Isn't that what powered the Terminator? A "neural net processor". I am a big fan of that movie (T1 and T2) and highly recommend abondoning this project and building a nuclear shelter.

</weirdness>

Somethings just have to be said, no matter how crazy it seems.

---

### Post by Kadrus on 2007-12-26
> **LaRoza said:**
> C, that is why it was made.
Euuh...what about ADA?As powerful as C in that domain?

---

### Post by LaRoza on 2007-12-26
> **Kadrus said:**
> Euuh...what about ADA?As powerful as C in that domain?

ADA was made by the DoD for critical applications like aviation software, C was made in the 70's for programming Unix.

---

### Post by speckman on 2007-12-28
i guess i'm hoping that there's something more mathematical and fundamental, contained within the basic operations, that would do the job of a neural net.  Just store information and learn.  I know it's there.

I mean, cause that's what computers do well, is calculate and store.  Just some way to utilize it's full capability and have that be a brain!  That's it!  :)  that's all.  

well, I think I just jumped into an ocean with my snorkel and flip-flops.  
i think i should follow everyone's advice, thank you.

> **LaRoza said:**
> Isn't that what powered the Terminator? A "neural net processor". I am a big fan of that movie (T1 and T2) and highly recommend abondoning this project and building a nuclear shelter.

</weirdness>

Somethings just have to be said, no matter how crazy it seems.

I think it's inevitable, that if we find AI, it'll be put in robots that will fight our wars and us.  Oops, that happened 5 years ago!  :)

That's basically life on planet Earth.  Countless generations of eating each other. 

But I sure would like to just sit and hang out with my computer, the wisest thing around.  Make a Robo-one robot sentient pet.  
[http://www.robots-dreams.com/roboone/](http://www.robots-dreams.com/roboone/)

btw, let the randomness be creativity.  if it were an oracle, it would be the one symbol that best corresponds to the present or asked-about situation.  (ie. a digital input focused on a god)

I can't get over how fast computers are developing.  If I live to be an old man, that'll be the equivalent of the beginning of PCs --> modern age.  And older still will be another one of those leaps.  AI's got to be on the way.  Maybe it's here and we just haven't grasped our condition yet!  (slavery to the computers!  or symbiosis)

---

