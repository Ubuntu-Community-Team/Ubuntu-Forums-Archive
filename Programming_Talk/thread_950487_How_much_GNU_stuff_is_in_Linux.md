---
title: "How much GNU stuff is in Linux?"
date: 2008-10-17
forum: Programming Talk
---

### Post by randysparks on 2008-10-17
Hi 

I'm not a programmer, and this will perhaps be obvious, but how much GNU stuff is actually in Linux? 

I know about BASH and GNU C Lib, and how GCC is used to compile Ubuntu. But what else is there that an average user might find on his/her system after installing Ubuntu that comes directly from the GNU project (not including stuff that's allied to GNU, like GNOME)?

---

### Post by LaRoza on 2008-10-17
[http://en.wikipedia.org/wiki/List_of_GNU_packages](http://en.wikipedia.org/wiki/List_of_GNU_packages)

**Base system** (minus Hurd)

Some of **Development**

Most of **Graphical Desktop**

Some of **Applications and utilities** (although it is all in the repos)

None of **Scientific software** that I know of.

GNU Chess in **Other**

---

### Post by randysparks on 2008-10-17
> **LaRoza said:**
> [http://en.wikipedia.org/wiki/List_of_GNU_packages](http://en.wikipedia.org/wiki/List_of_GNU_packages)

**Base system** (minus Hurd)

Some of **Development**

Most of **Graphical Desktop**

Some of **Applications and utilities** (although it is all in the repos)

None of **Scientific software** that I know of.

GNU Chess in **Other**

Hi -- great link, thanks. I'm primarily interested in how much GNU stuff is in Ubuntu, in terms of a recreation of Unix, and not so much allied projects like GNOME, which are really independent projects that fall loosely under the GNU umbrella and don't really form a definition of Unix.

---

### Post by LaRoza on 2008-10-17
> **randysparks said:**
> Hi -- great link, thanks. I'm primarily interested in how much GNU stuff is in Ubuntu, in terms of a recreation of Unix
GNU forms the base system, except for Hurd.

---

### Post by tribaal on 2008-10-17
Linux is only the Kernel.

The most obvious GNU is, like LaRoza said, the base system (most utilities on the command line), some of the development packages (GCC, GDB...), anything GNOME.

I would consider your question the other way around - "how much linux is there in GNU" instead :) 
There is (much) more GNU code in Ubuntu than linux code :)

Cheers,

- Trib'

---

### Post by iponeverything on 2008-10-17
Which is why RMS will never let a "Linux" slip by without correcting the speaker "it's GNU/Linux"  :)

RMS, My hero -- He saw this train wreak of propitiatory software coming and went on the offensive a long time ago.. He has never wavered in his commitment to freedom.

A tiny bit about the history of Linux.  RMS and his tiny band of brothers had been working on a clean-room implementation of a UNIX "system" replacement for about 10 years before a bright young Finn came in with the final piece of the puzzle.

---

### Post by LaRoza on 2008-10-17
> **iponeverything said:**
> 
RMS, My hero -- He saw this train wreak of propitiatory software coming and went on the offensive a long time ago.. He has never wavered in his commitment to freedom.

+1 He may be weird at times, but aren't we all?

> 
A tiny bit about the history of Linux.  RMS and his tiny band of brothers had been working on a clean-room implementation of a UNIX "system" replacement for about 10 years before a bright young Fin came in with the final piece of the puzzle.

As I am corrected by Finns, I correct you. Two "n"'s in "Finn".

---

### Post by nvteighen on 2008-10-17
**In** Linux, exactly 0, as it is the kernel and is not part of the GNU project :)

Actually, the OS is GNU... as a user, you never interact with the kernel (but developers do). You instead use something (a program) that in turn ends up (sometimes after some intermediate steps) using the kernel.

So, if you happen to install Debian GNU/Hurd (when it ever gets finished), you wouldn't notice any change when using the computer... but developers would have had a real big headache porting the Linux kernel-compatible applications to that new kernel.

---

### Post by pmasiar on 2008-10-17
> **iponeverything said:**
> a bright young Finn came in with the final piece of the puzzle.

1) [http://en.wikipedia.org/wiki/Linus_Torvalds](http://en.wikipedia.org/wiki/Linus_Torvalds) belongs to the Swedish-speaking minority (5.5%) of Finland's population. 

2) GNU prophet, [Richard Stallman St. IGNUcius](http://www.stallman.org/saintignucius.jpg) says:

"There is no system but GNU, and Linux is one of its kernels."

;-)

---

### Post by LaRoza on 2008-10-17
> **pmasiar said:**
> 1) [http://en.wikipedia.org/wiki/Linus_Torvalds](http://en.wikipedia.org/wiki/Linus_Torvalds) belongs to the Swedish-speaking minority (5.5%) of Finland's population. 


Native speaker, I would say. I believe Swedish is taught to everyone, to the dismay of some people.

---

### Post by estyles on 2008-10-17
I feel like the main reason that more people think of the OS as Linux instead of GNU or GNU/Linux is just because Stallman is so abrasive.  I don't know that much about him (though I've read a number of articles he's written), but I feel like I don't like him (just an impression).  Despite that, I certainly am grateful for all the work he has done for Open Source and Free Software, and so I try to remember to write "GNU/Linux" at least half the time I mention the OS.  Linux, the kernel, is an important part of "Linux", the OS, but GNU stuff is definitely a bigger portion of the whole.

---

### Post by snova on 2008-10-17
I could do with a few less acronyms myself. *Never* forget what GNU is and what the project has done for us, but seriously- "G-N-U slash Linux" is too big of a mouthful. No wonder we have less than %1 market share, who wants to pronounce that? :)

Or just call it "Ubuntu" and ignore the whole problem. (By creating another. Now everybody wonders what the difference between Linux and Ubuntu is, and we have to explain distributions...)

He does seem like somebody I wouldn't like a lot. He certainly deserves respect for starting all this, but sometimes I think he's a little crazy about it. What was that thread in the Cafe about? "Cloud computing"- It's obviously a problem if the cloud doesn't come with source, but by the sound of it, he doesn't even want to consider it. Besides, what's to stop us from being our own cloud? (Note that I haven't actually read that thread...)

But for the original purpose of the thread... Are GTK and Gnome part of the GNU project? Then quite a lot.

And, by the way, I'm fairly certain there *is* a Debian GNU/HURD (more acronyms...).

Most of the headaches are those of glibc hackers, anyway. Only software that actually interfaces with the Linux proper would have problems. Oh, that and possibly every program dealing with device files... not sure about that.

---

### Post by pmasiar on 2008-10-17
> **snova said:**
> No wonder we have less than %1 market share, who wants to pronounce that? :)

But Linux has less that 1% of marketing budget, so even if it has only 1% market share (and I do not believe your stats: servers are **much** more than that, and even desktops). With 1%, Linux punches above it's weight, abd possibly way above.

> sometimes I think he's a little crazy about it. 

That's the difference, and the reason why RSM won "Genius" grant, and you (and many others, like me) did not. He has guts to follow his conscience, even if it is not convenient.

As they say, wise people adjust themselves to the world, fool tries to adjust the world. As consequence, all progress depends on fools 8-)

> (Note that I haven't actually read that thread...)

But you have strong opinion why one of the luminaries of FOSS is wrong and crazy? 

I did read the discussion a while ago, and agree with RMS's point, even if I am not ready to follow his example, because I value my convenience - and rely on others (like RMS) to fight and win the battle :-/

---

### Post by nvteighen on 2008-10-18
> **pmasiar said:**
> 
That's the difference, and the reason why RSM won "Genius" grant, and you (and many others, like me) did not. He has guts to follow his conscience, even if it is not convenient.

As they say, wise people adjust themselves to the world, fool tries to adjust the world. As consequence, all progress depends on fools 8-)


Like it happened with so many people, RMS will be unanimously be considered the genius he really is only after death...

Think about this: he started an OS to be follow his principles, which are good in any sense... he didn't just left the GNU project as some pretty utopic good intention, but he made it true by sacrificing a fairly good position at the MIT AI Labs and, of course, having to deal with difficulties. You may call him a fool philanthropist in a world reigned by money... yeah, he's a sort of "fool", but a pretty nice "fool" that wants us all be able to participate in technological progress.

He's challenging a whole world-view; that's why many people judge him not trying to understand what he means, but applying their prejudices. Always, when facing an argument of someone you have to understand what his/her logic reasoning was like to then be able to criticize him/her constructively... And not just face the argument using your own logic; that's absurd as trying to judge the Assirian Empire using the UNO's Human Rights Declaration...

Sometimes his articles are a bit fanatical, yeah, but progress comes from people with strong beliefs and personality.

---

### Post by LaRoza on 2008-10-18
> **nvteighen said:**
> 
Sometimes his articles are a bit fanatical, yeah, but progress comes from people with strong beliefs and personality.

Actually, I think his articles are very logical. They are "extreme" because of the current state of "progress", which we can hopefully undo someday...

---

### Post by snova on 2008-10-18
> **pmasiar said:**
> But Linux has less that 1% of marketing budget, so even if it has only 1% market share (and I do not believe your stats: servers are **much** more than that, and even desktops). With 1%, Linux punches above it's weight, abd possibly way above.

Well, speaking desktop-wise, I'd be glad to be shown percentages larger than one or two percent, but then how can you tell? Microsoft knows how many copies have been registered, but Linux doesn't do that. (I'm not trying to imply that it's a good thing...)

I keep finding different stats for server usage, though. Everywhere from 13% to 50%... It's obviously good, though. Apache might be even higher.

> **pmasiar said:**
> > sometimes I think he's a little crazy about it. 

That's the difference, and the reason why RSM won "Genius" grant, and you (and many others, like me) did not. He has guts to follow his conscience, even if it is not convenient.

As they say, wise people adjust themselves to the world, fool tries to adjust the world. As consequence, all progress depends on fools 8-)

I can't come up with an response for that...

> **pmasiar said:**
> > (Note that I haven't actually read that thread...)

But you have strong opinion why one of the luminaries of FOSS is wrong and crazy?

Eh, who doesn't have strong opinions? I don't see him as wrong, but I'm not nearly as picky (using the word as a replacement for "crazy", which was a bad choice, apparently) about proprietary software. I use Opera, Fglrx, and Sun's Java. I also installed Google Earth yesterday just to try it. I've tried Aptana recently out of curiousity, and something called Jira that didn't work... A little reminder of what a pain software registration is, I guess.

> **pmasiar said:**
> I did read the discussion a while ago, and agree with RMS's point, even if I am not ready to follow his example, because I value my convenience - and rely on others (like RMS) to fight and win the battle :-/

Hmph. Now I feel guilty for not helping. :(

(How do I get into these discussions???)

---

### Post by LaRoza on 2008-10-18
> **snova said:**
> Hmph. Now I feel guilty for not helping. :(


You should. You probably further the oppression by buying DVD's.

---

### Post by snova on 2008-10-18
> **LaRoza said:**
> You should. You probably further the oppression by buying DVD's.

Nope...

---

