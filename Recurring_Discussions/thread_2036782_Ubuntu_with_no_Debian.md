---
title: "Ubuntu with no Debian"
date: 2012-08-02
forum: Recurring Discussions
---

### Post by TheMTtakeover on 2012-08-02
Would it be hard for Ubuntu to not be built on top of another distro? Would it be costly to build a distro that is not dependent on another distro? What exactly are the reasons that Ubuntu is built on top of another distro?

I don't want this to come off as "bashing" or anything like that, just trying understand.

---

### Post by QIII on 2012-08-02
Let's not reinvent the wheel...

;)

---

### Post by Mikeb85 on 2012-08-02
> **TheMTtakeover said:**
> Would it be hard for Ubuntu to not be built on top of another distro? Would it be costly to build a distro that is not dependent on another distro? What exactly are the reasons that Ubuntu is built on top of another distro?

I don't want this to come off as "bashing" or anything like that, just trying understand.

To maintain compatibility with an established ecosystem.  There are other reasons too, like not having to create everything from scratch, and in Ubuntu's case part of it is also that Mark Shuttleworth was a contributor to Debian...

---

### Post by TheMTtakeover on 2012-08-02
so essentially the biggest advantage from building over top of Debian is that it saves resources (time and money?) ?

---

### Post by Mikeb85 on 2012-08-02
> **TheMTtakeover said:**
> so essentially the biggest advantage from building over top of Debian is that it saves resources (time and money?) ?

Well, Debian is pretty decent on it's own too, but yes.  Why didn't Red Hat write their own kernel in 1993?

---

### Post by thatguruguy on 2012-08-02
> **TheMTtakeover said:**
> Would it be hard for Ubuntu to not be built on top of another distro? Would it be costly to build a distro that is not dependent on another distro? What exactly are the reasons that Ubuntu is built on top of another distro?

I don't want this to come off as "bashing" or anything like that, just trying understand.

Yes, it would considerably more work, and be more costly, to build Ubuntu from the ground up. Debian is both an OS and all the packages maintained for it, plus its own package management system. It's maintained by nearly a thousand developers. It would take quite a bit to rebuild all of that infrastructure.

---

### Post by QIII on 2012-08-02
Why didn't Red Hat?

Because Deb and Ian weren't in the game yet?

---

### Post by TheMTtakeover on 2012-08-02
Thanks for the response guys.

---

### Post by a2j on 2012-08-03
"The cost of developing all the packages included in Debian 5.0 *lenny* (323 million lines of code), using the [COCOMO]("http://en.wikipedia.org/wiki/COCOMO") model, has been estimated to be about [US$]("http://en.wikipedia.org/wiki/United_States_dollar") 8 billion.[ ]("http://en.wikipedia.org/wiki/Debian#cite_note-15") [Ohloh]("http://en.wikipedia.org/wiki/Ohloh") estimates that the codebase (54 million lines of code), using the COCOMO model, would cost about [US$]("http://en.wikipedia.org/wiki/United_States_dollar") 1 billion to develop.[]("http://en.wikipedia.org/wiki/Debian#cite_note-16")"

---

### Post by vexorian on 2012-08-03
> **TheMTtakeover said:**
> Would it be hard for Ubuntu to not be built on top of another distro? Would it be costly to build a distro that is not dependent on another distro? What exactly are the reasons that Ubuntu is built on top of another distro?

I don't want this to come off as "bashing" or anything like that, just trying understand.
Assume that debian didn't save ubuntu (billions of!) dollars. There would be no reason for things to stay the way they are. But we would still need a good reason to change them. What would a good reason to perform this hypothetical move be?

---

### Post by mips on 2012-08-03
Would be financial suicide to reinvent the wheel. Use what's out there and works. Debian is a very good base to work from.

---

### Post by MadmanRB on 2012-08-03
Indeed Debian is a very solid thing to base your system off of.

---

### Post by Old_Grey_Wolf on 2012-08-03
> **TheMTtakeover said:**
> What exactly are the reasons that Ubuntu is built on top of another distro?

Basically you are asking what [Open Source]("http://en.wikipedia.org/wiki/Open_source") is about. 

Ubuntu uses Debian for a base; because, in the Open Source community you are *free* to use what others have already accomplished. It saves time and money.

Even Debian uses something developed by someone else; such as, the Linux kernel. Then Debian contributes back to the Linux kernel by providing improvements and bug fixes.

---

### Post by snip3r8 on 2012-08-03
Question , why did you ask this question? (break;//to avoid infinite loop)

---

### Post by ugm6hr on 2012-08-03
> **Old_Gray_Wolf said:**
> Basically you are asking what [Open Source]("http://en.wikipedia.org/wiki/Open_source") is about. 

Ubuntu uses Debian for a base; because, in the Open Source community you are *free* to use what others have already accomplished. It saves time and money.

Even Debian uses something developed by someone else; such as, the Linux kernel. Then Debian contributes back to the Linux kernel by providing improvements and bug fixes.

Answered beautifully.

---

### Post by tartalo on 2012-08-03
That's an intelligent question (honest, no sarcasm). 

I encourage you to try Debian, then consider if Debian needs Ubuntu.

(I hope that this doesn't mean my third infraction for "trolling", the mods here are too sensible)

---

### Post by TheMTtakeover on 2012-08-03
> **tartalo said:**
> That's an intelligent question (honest, no sarcasm). 
 
I encourage you to try Debian, then consider if Debian needs Ubuntu.
 
(I hope that this doesn't mean my third infraction for "trolling", the mods here are too sensible)
 
In your personal opinion does Debian not need Ubuntu?

---

### Post by cariboo on 2012-08-03
Debian may not need Ubuntu, but Canonical does support it financially.

---

### Post by Lyfang on 2012-08-03
Yes, Ubuntu could be built on top on any Linux distro, maybe even an UNIX-like operating system. E.g. FreeBSD can provide Adobe Flash Player using nspluginwrapper & linux_base-f10.
> **Lyfang said:**
> Hi, Ubuntu has improve usability for novice users compared to Debian? Difference between Debian and Ubuntu: Ubuntu easy to use but bloated? Debian More resource efficient but for experienced Linux users?

Why Ubuntu is needed: Easy to use & the release cycle. Maybe helping update the Debian repositories would benefit Ubuntu as well?

---

### Post by madjr on 2012-08-04
this might also be helpful, Debian vs Ubuntu:

[http://www.wikivs.com/wiki/Debian_vs_Ubuntu](http://www.wikivs.com/wiki/Debian_vs_Ubuntu)

---

### Post by rjbl on 2012-08-04
> **Mikeb85 said:**
> Well, Debian is pretty decent on it's own too, but yes.  Why didn't Red Hat write their own kernel in 1993?

Duhhh ..........................!

rjbl

---

### Post by tartalo on 2012-08-04
> **cariboo907 said:**
> Debian may not need Ubuntu, but Canonical does support it financially.

Link please?

---

### Post by castrojo on 2012-08-06
> **tartalo said:**
> Link please?

Various DebConfs over the years, at varying levels.

---

### Post by 1clue on 2012-08-06
I reject that "billions of dollars" figure.  There are several distributions out there with no parent distro.  And frankly I doubt it would cost 8 billion of dollars to pay a bunch of commercial developers to rewrite all of open source.

Even so, that is irrelevant to the discussion.

As I mentioned there are several "base" distros out there.  I use Gentoo which is a source-based distro that makes almost no decisions for you in terms of what sort of software to use or how it should be compiled.  It's sort of the Jekyl and Hyde opposite for Ubuntu, but I see a lot of users on Ubuntu who are also on Gentoo, so I'm not alone in liking both.

Any distribution comes together when a group of like-minded individuals decide to build one.  Their reasons could be anything, but IMO if they stand a chance to succeed then they have a specific goal or set of goals to accomplish.  That is their focus, and anything else is either done in pursuit of the main goal or it's window dressing.

My best advice is to go load a few different distros, join their forums and figure out what exactly makes these things different from one another.  You can read it, but that doesn't drive the understanding home like running the product does.

In the case of Debian, their focus is to get a wide range of hardware working smoothly, not so focused on the 'prettiness' of it but on a solid operating system underneath.  It's been that way since I first discovered it years ago.

Ubuntu focuses on an easy-to-use and attractive user environment that doesn't need a lot of knowledge to operate, to help bride the gap between "normal" Linux and what people are used to seeing, which would be Microsoft or Apple operating systems.

IMO it would be a big headache to try to for a distro like Ubuntu to build from scratch.  They started with something that lets them focus more precisely on their core purpose.  They chose the most common likely hardware, grabbed Debian for that set of hardware and then started building on that.

---

### Post by vexorian on 2012-08-06
^ The figures come from the COCOMO model. You'd have to argue against that model.

But I think billions sounds about right. Ubuntu uses few packages by default. But there are tons and tons of packages in the universe repository. That is a lot of man hours. Numbers tend to stack together.

---

### Post by 1clue on 2012-08-06
OK I frankly doubt the model then, but even so building your own distro is not rewriting every piece of open source software.  So the COCOMO model doesn't apply here.

A distro is a group of people who get together and bundle pre-existing Open Source software with a purpose.  You're saying 8 billion dollars to do what Debian does?  No way.

---

### Post by Mikeb85 on 2012-08-06
> **1clue said:**
> OK I frankly doubt the model then, but even so building your own distro is not rewriting every piece of open source software.  So the COCOMO model doesn't apply here.

A distro is a group of people who get together and bundle pre-existing Open Source software with a purpose.  You're saying 8 billion dollars to do what Debian does?  No way.

That figure is a little high, but you have to account all the man hours of development of some of these distros since they were created.  Red Hat, SUSE and Debian have all been around for 20 years, and have put in alot of work since.

---

### Post by 1clue on 2012-08-06
Are we splitting hairs?

Seriously, coming up with a valid traditional Linux distro would NOT take a billion dollars.  Get ten guys who know their way around compiling code from source, develop a strategy and it's useful enough to download in a year.  I know most modern distros have a lot more resources than that, but AFAICT Slackware has been mostly just one guy.  It's a distro, and people have been using it for two decades.  It's one of the first five I used.

RHEL is obviously a completely different distro with an entirely different strategy.  And Ubuntu is somewhere in the middle.

---

### Post by vexorian on 2012-08-06
> Seriously, coming up with a valid traditional Linux distro would NOT take a billion dollars. That's only because of the amount of voluntary work.

And we are not talking about making any traditional Linux distro, but about making Debian. It required a lot of voluntary work . You could try to make your own debian clone, but if you don't have the volunteers you might have to pay some money. Slackware packaging is incredibly easy and simplistic in comparison to debian packaging.

---

### Post by 1clue on 2012-08-06
Dude, you're seriously overestimating what a distro does, and you're drastically overestimating how much money a programmer makes.

Take your salary, and divide a billion by that.  That's "b" not "m".  Regardless of what you might have heard, programmers generally do NOT make a six figure salary.

Debian didn't write Apache Web Server or KDE or any of that.  They take what already exists and compile it to fit their methodology and then make those packages available to others.  These guys don't compile just one thing, the guys building packages build them all day every day.

Debian DOES do a lot of work on drivers and ensuring that odd hardware has a good chance of working, because that's one of their main goals.  But they don't design the software they use, and they PROBABLY don't do much in the way of configuration.   Usually the upstream package maintainer does that.

The lion's share of the work is done upstream of the distro.

---

