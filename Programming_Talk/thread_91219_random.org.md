---
title: "random.org"
date: 2005-11-16
forum: Programming Talk
---

### Post by jeffjanzen on 2005-11-16
it is my understanding that whenever a user requests a *random* sequence of events, linux generates *pseudo*-random numbers using an algorithm.  (please correct me if i'm wrong.)
i'm not a programmer, but my guess is that it should be fairly simple and worthwhile to throw out the algorithm that's deceiving us and program linux to download *true* random numbers from random.org instead, so that users get true random sequences when they ask for them.
please read some of the literature on random.org to prevent the embarrassment of posting an ignorant reply.

---

### Post by SSTwinrova on 2005-11-16
Just to clarify, are you talking about the pregenerated files? If not, then you're assuming the computer has an active internet connection (while, even though probably more than half the time this would be true, could never be guaranteed to reach the 100% penetration mark that the offline "psuedo" generator provides).

---

### Post by UbuWu on 2005-11-16
In almost all cases, those pseudo random numbers are good enough for the goal that needs to be achieved.

---

### Post by jeffjanzen on 2005-11-16
"good enough"?  the computer's hardware clock is "good enough" without daily ntp synchronization, but daily syncing is really the best way to go.  i think random.org is the best way to go for random functions.  it's just a little thing that could make linux better, the way i see it.
i should just learn the programming literature and rig it up myself, but i know nearly nothing of programming, and i'm afraid to break linux, because i like it so much and it's working pretty nicely for me now and i think some of you people that are reading this thread know enough to make this type of idea really fly in under an hour. (is that realistic at all?)
consider it an extra credit homework assignment.  i don't want you guys to get bored...

---

### Post by gord on 2005-11-17
the hardware clock is just a seed as well, using a number from random.org to seed it would make the generated random numbers no more pseudo or valid than the regular numbers generated.

---

### Post by jeffjanzen on 2005-11-18
i'm not just talking about generating random numbers using a seed from a website, i'm talking about *using* true random numbers from random.org, in all forms (integers, sequences, other numbers, etc.) in linux applications, like randomly selecting which picture to use for a screensaver, or randomly assigning test subjects to groups for a scientific experiment.
fyi: "pseudo" means false.
i'm suggesting a movement *away* from pseudo-random numbers, *toward* using **true random numbers**.  in most cases, our pseudo-random numbers are "valid" or "good enough," but the truth is that they're not actually random, and there are tasks (e.g. scientific experiments) that require true random values in order to be "valid" experiments.  the numbers provided by random.org *are* truly random.  please read:
[http://www.random.org/essay.html]("http://www.random.org/essay.html")
i suppose no one with the skills to implement such a function believes that true random numbers are necessary, or users should all go visit random.org themselves every time they want true random values.  that kind of sucks, but i should have seen it coming...

---

### Post by jeffjanzen on 2005-11-18
i just discovered a wealth of linux software using random.org as a source for true random numbers.  it feels good to know *somebody* shares my understanding of the occasional imperativeness of **true random numbers**.

EDIT: i was mistaken.  a quick "random.org" query on unix.freshmeat.net yielded a few hundred applications that i hastily assumed used random.org in some way or another.  truth: *none* of them do.  (so often i'm addled by search engines....) i maintain that there are some situations which require true random numbers, and there are plenty who agree with me.  there just aren't many who believe that these situations arise in linux, for linux users, and i'm starting to agree with them...

---

### Post by kperkins on 2005-11-18
[QUOTE=jeffjanzen]i have just discovered a wealth of linux software using random.org as a source for true random numbers.  it feels good to know *somebody* shares my understanding of the occasional imperativeness of **true random numbers**.[/QUOTE]
Care to share?

---

### Post by Burke on 2005-11-19
While the random number generator could definitely use some work (I don't know *how* to fix it, I just know it needs fixing), I think talking to random.org every single time you want a random number would bring your system to a grinding halt.  rand(); in C++ takes a lot less time than I can determine, and grabbing data from some remote system, over even a fast connection still has relatively huge latency issues. Good idea in theory, but it would never work.

---

### Post by kahping on 2005-11-19
[QUOTE=Burke]While the random number generator could definitely use some work (I don't know *how* to fix it, I just know it needs fixing), I think talking to random.org every single time you want a random number would bring your system to a grinding halt.  rand(); in C++ takes a lot less time than I can determine, and grabbing data from some remote system, over even a fast connection still has relatively huge latency issues. Good idea in theory, but it would never work.[/QUOTE]

i think jeffjanzen is trying to say something like "replace the current pseudo-random number generator in Linux with the true random number generator algorithm used by random.org" or something to that effect.

i'd like to see that happen too, but i think the Linux developers have more important things to work on right now, so replacing something that's already "good enough" may not be a very high priority thing right now ;) 

kahping

---

### Post by Burke on 2005-11-19
That was what I thought originally, but after reading about how the numbers are generated, I realized he actually did mean to pull a number from the global interweb each time rand() was called (or however it was implemented) 

random.org generates numbers with a microphone in front of a radio tuned to static. The program takes part of that data, then processes it with some skew-correcting algorithm.  This would obviously be infeasible for a desktop, as the radio and the mic. would be more than a little awkward.

---

### Post by gord on 2005-11-19
true random numbers arn't needed in day to day applications anyway, applications for scientific experiments are generally custom made and will incorporate there own way of getting random data. 

for every day stuff are true random numbers better than pseudo random numbers, yes. does it matter? not in the least. it only matters in a very small ammount of situations and the costs are many many many times greater than the benifits. if you need it, code it. if you don't, don't.

maybe one day there will be a quantum chip (or som't...) on every computer that has a constant stream of random numbers by using the random nature of quantum mechanics, it'd be a good thing. but maybe it just wouldn't matter.

---

### Post by Seq on 2005-11-19
Does a user care that their photo screensaver (to use an existing example) isn't "truely" random? As long as the sequence is jumbled, the user will never even consider it. I think a key point is that a special application requiring "true" randomness is exactly that -- a special application. Any such application would have taken the random requirement into consideration at design time.

**Edit**: removed quote from gord as I was not really replying to him

---

### Post by jeffjanzen on 2005-11-20
i think you guys are right.  it's not worth the delay, considering its relative unimportance.  the user's hardware and isp, and the random.org server would all have to be blazingly fast, and even then, i'd probably experience a delay, and i would want to revert back to the old, quick algorithm.

---

### Post by Endolith on 2009-08-20
For people who search "random.org Ubuntu":

No, you don't need true random numbers for the vast majority of things.

Yes, Ubuntu supports true random numbers already.

Read all about it:

[http://en.wikipedia.org/wiki//dev/random](http://en.wikipedia.org/wiki//dev/random)

use /dev/random for true random numbers (entropy is gathered from mouse movements, network activity, etc), and /dev/urandom for everything else.

And yes, you can seed from random.org if you want:

[http://manpages.ubuntu.com/manpages/karmic/man8/reseed.8.html](http://manpages.ubuntu.com/manpages/karmic/man8/reseed.8.html)

---

### Post by pepperphd on 2009-08-21
I thought classical physics specifically prohibits the existence of anything truly random.  Can I play with your quantum computer OP?

---

### Post by TheStatsMan on 2009-08-21
The mersenne twister has a period of 2^19937 and there are very fast implementations of it that you can download.

---

### Post by lisati on 2009-08-21
Would a definition of "random" be useful? 

A simple definition which doesn't involve too much in the way of abstraction might be this: "A random number or event is one that you can not easily predict."

Yes, I am aware that there's more to the subject of randomness than this.....

---

### Post by ArmenianLeader4 on 2009-08-21
Does it really make a difference? I'm sure it would be useful in certain applications, but definetly not ones that would be of the utmost importance to most of today's Linux users. And, (in fear of being "ignorant") why can't you generate random numbers elsewhere? Like, say, a calculator? Or, maybe, YOUR MIND. *gasp* what a novel concept. I got this 'variable' from MY MIND. Everyone's become so dependant on computers figuring crap out for them.. and I know you're going say "well, your MIND doesn't generate PERFECT random numbers." Well, honestly, if its "RANDOM" can't you just put down whatever the hell you feel like putting down? the "RANDOM" results could end the same way, you know.

Oh, and by the way, I like endolith's post up there ^^. Thats the answer.

---

### Post by Mirge on 2009-08-21
Hurray for almost 4 year old threads...

---

### Post by Mickeysofine1972 on 2009-08-21
There are no true random numbers.

Only Random enough.

Mike

---

### Post by Can+~ on 2009-08-21
There are things we can see and process, and things that fall from the scope of our understanding, those are the ones we call random.

Say that a plane falls right on your back yard. You'll probably say "what are the odds?, that's totally random". Go back 6 months ago, the plane had it's regular maintenance, they forgot to put a cable back somewhere, the error went unnoticed. Fast forward to the present, the plane was flying with a certain trajectory, speed, altitude, etc now suffers the problem, gravity takes care of the rest, wind resistance, viscosity, weight, everything counts.

If you could get ALL the data involved on this accident, and not only things like weight and amount of passengers, but what was the temperature that day, what was the speed of the wind, etc; you could've predicted the incident. But we would be stretching our data-collection skills to an impossible length.

So you are part of a infinite stream of interconnected events, that you most of the time will go unnoticed, due to, not only it's sheer magnitude but because it also depends on time (events occurred long time ago) and things that you can't even quantify (how well was the pilot trained, what was he thinking). So the idea of "random" goes more like "I can't understand everything" rather than "It's unpredictable".

And I can't believe I just wrote all that out of a forum post.

---

### Post by ad_267 on 2009-08-21
Isn't /dev/random just as much a true random number generator as this?

---

### Post by jeffathehutt on 2009-08-21
> **ArmenianLeader4 said:**
> Does it really make a difference? I'm sure it would be useful in certain applications, but definetly not ones that would be of the utmost importance to most of today's Linux users. And, (in fear of being "ignorant") why can't you generate random numbers elsewhere? Like, say, a calculator? Or, maybe, YOUR MIND. *gasp* what a novel concept. I got this 'variable' from MY MIND. Everyone's become so dependant on computers figuring crap out for them.. and I know you're going say "well, your MIND doesn't generate PERFECT random numbers." Well, honestly, if its "RANDOM" can't you just put down whatever the hell you feel like putting down? the "RANDOM" results could end the same way, you know.

Oh, and by the way, I like endolith's post up there ^^. Thats the answer.

Most cryptography relies on the "randomness" of numbers.  If I can determine the sequence of random numbers your computer uses, I can eavesdrop on your activities.  Things like SSL wouldn't work without "real" random numbers, so there would be no more secured connections over the internet.

As for generating numbers with your brain... Well, my brain isn't fast enough for that. :P  A computer can generate hundreds of numbers in the same time I can generate one.

[QUOTE=ad_267]Isn't /dev/random just as much a true random number generator as this? [/QUOTE]

Basically.  When this thread was started years ago I don't think /dev/random was the same as it is today.

---

### Post by ad_267 on 2009-08-21
Whoops, didn't see that this thread was ancient. It should probably die again now...

---

