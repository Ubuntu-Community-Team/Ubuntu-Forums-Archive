---
title: "my list of questions"
date: 2006-01-09
forum: Programming Talk
---

### Post by iand675@gmail.com on 2006-01-09
I'm gonna make this a a thread about programming related questions that I'll post as i think of them.

For starters, what was the first OS and how was it programmed?
Binary and Hex are what I understand to be the only languages that a computer can interpret by itself, so how does it do that through hardware and how did we know how to "speak"/program in binary?

---

### Post by iand675@gmail.com on 2006-01-09
Another question is: how do memory addresses work?
How about motherboards? What makes them tick, and how do you write a bios for one?
How do you write a hardware driver?
What is a "stack"?
Is there any way to install dmg files on linux since mac is unix-based?
What kind of power do this isp guys have that makes it that they have control of who gets to use the internet?

---

### Post by toojays on 2006-01-10
These are not simple questions. Some of require years of study for a proper understanding. You would get better answers if you did one question a week, with a thread per question. Your thread should include what you have already found out about the topic from google, wikipedia, howstuffworks, etc.

---

### Post by gord on 2006-01-10
computers only technically understand binary, and we knew howto "speek" to them bceause they wern't created by some strange magical force, we as humans designed them.

most of the rest of the questions require a basic understanding of computing that is beyond the musings of an internet forum, im sure if you look up the questions in [wikipedia](http://www.wikipedia.org) you'll find your answers though.

---

### Post by iand675@gmail.com on 2006-01-10
well could you give me a better phrasing of what I need to ask then? because I don't know what terms to put my questions in to finde the answers on a search engine. I did try before I asked.

---

### Post by LordHunter317 on 2006-01-10
[QUOTE=iand675@gmail.com]For starters, what was the first OS and how was it programmed?[/quote]I don't know, but the first computers didn't have operating systems at all.  You programmed each address by flipping physical switches, then ran the application.

> Binary and Hex are what I understand to be the only languages that a computer can interpret by itself, so how does it do that through hardware and how did we know how to "speak"/program in binary?Computers don't speak either.  They deal solely with electrical voltages: one voltage (range) means '0', and one voltage (range) means '1'.   Transistors provide the ability to do this quite trivally.

A CPU (or any other progrmmable digital device) applies special meaning to certain sequences of inputs that it interprets as code. 

Much like your other hardware questions, you'd be better off by taking a digital design course at a college then asking here.

---

### Post by earobinson on 2006-01-10
[QUOTE=iand675@gmail.com]Another question is: how do memory addresses work?[/QUOTE]
[http://en.wikipedia.org/wiki/Memory_address](http://en.wikipedia.org/wiki/Memory_address)

[QUOTE=iand675@gmail.com]What is a "stack"?[/QUOTE]
[http://en.wikipedia.org/wiki/Stack_%28computing%29](http://en.wikipedia.org/wiki/Stack_%28computing%29)

[QUOTE=iand675@gmail.com]Is there any way to install dmg files on linux since mac is unix-based?[/QUOTE]
I dont think so but if you find one let me know!

[QUOTE=iand675@gmail.com]What kind of power do this isp guys have that makes it that they have control of who gets to use the internet?[/QUOTE]
Hard to answer, really they dont.

EDIT: for longer better answers look at toojays's post, we need more information on what you know and dont to better help you

---

### Post by iand675@gmail.com on 2006-01-10
[QUOTE=earobinson]

Hard to answer, really they dont.

[/QUOTE]
So theoretically would that mean that I could set up my own free dsl or something?

EDIT: I realize that these are pretty complex questions and as lord hunter says that this should be a college class question thing, but I'm a sophomore in high school, so I don't really have that option available to me. I am hoping to become a computer engineer though, so I'm just trying to learn about how they tick in my spare time. Unfortunately, the questions that I tend to ask are the ones that are hard to answer.

---

### Post by bigdufstuff on 2006-01-10
[http://en.wikipedia.org/wiki/Digital_logic](http://en.wikipedia.org/wiki/Digital_logic)

[http://en.wikipedia.org/wiki/Logic_gates](http://en.wikipedia.org/wiki/Logic_gates)

[http://en.wikipedia.org/wiki/Inverter_%28logic_gate%29](http://en.wikipedia.org/wiki/Inverter_%28logic_gate%29)

might get you started. if you don't have a degree in EE, CE, ECE, or CS it is hard to explain this to you.

---

### Post by iand675@gmail.com on 2006-01-10
[QUOTE=bigdufstuff][http://en.wikipedia.org/wiki/Digital_logic](http://en.wikipedia.org/wiki/Digital_logic)

[http://en.wikipedia.org/wiki/Logic_gates](http://en.wikipedia.org/wiki/Logic_gates)

[http://en.wikipedia.org/wiki/Inverter_%28logic_gate%29](http://en.wikipedia.org/wiki/Inverter_%28logic_gate%29)

might get you started. if you don't have a degree in EE, CE, ECE, or CS it is hard to explain this to you.[/QUOTE]

So to try and put this into metaphor- The train is the electronic signal, and the circuitry is kind of the different routes it can go on the rails due to switches and things. And the route the train goes decides what the output is.

Am I getting the idea? Or is that a really screwed up interpretation of those articles?

---

### Post by LordHunter317 on 2006-01-10
[QUOTE=iand675@gmail.com]So theoretically would that mean that I could set up my own free dsl or something?[/quote]No.  Internet providing is actually very structured, into essentially 3 teirs of providers.

Getting the ability to resell service from another ISP or the telco (or both, depending on what you offer) is a hugely expensive and difficult operation.  Which is why very few mom&pop ISPs still exist.

> EDIT: I realize that these are pretty complex questions and as lord hunter says that this should be a college class question thing, but I'm a sophomore in high school, so I don't really have that option available to me.A good digital circuits text can help a lot with the basics of digital logic, which is the core foundation you'd need for understanding how computer hardware works.

I, unfortunately, can't recommend one, as the text I was given in school was intentionally selected to be more of a reference than a tutorial.  I'll ask my professors upon my return if they can recommend some introductory texts.

If you want to play with electronics, get one of hte Radio Shack (100|200|300|x) in 1 electronics kits.  Seriously.  They teach you the basics of reading schematics, and include some basic digital circuit stuff without overwhelming you in theory.  They're also handy for building your own circuits later.

After that, a good bench power supply  that supplies +5V, +12V, some resistors, some logic gates, switches, some LEDs and a breadboard are you need to build your own circuits.  Enough gear to play for a long time with could probably be had for $50 or so, minus the cost of a good power supply.  You can probably find one used very cheaply.

> Unfortunately, the questions that I tend to ask are the ones that are hard to answer.Well, some of it's trivia and some of it has nothing to do with hardware.

How an application addresses memory is totally different from how hardware addresses it (virtual vs. physical in the linked article, nevermind paging considerations).  And computers address memory very differently from most devices, due to all sorts of I/O considerations.

Essentially however, a memory chip has two sets of inputs: address inputs and the data input/outputs.  You put a number on the address and then read/write the data pins.

> 
So to try and put this into metaphor- The train is the electronic signal, and the circuitry is kind of the different routes it can go on the rails due to switches and things. And the route the train goes decides what the output is.

Am I getting the idea? Or is that a really screwed up interpretation of those articles?It's not excessively screwed up, but I'm not sure I'd look at a train in metaphor.

A better way to look at it as is a table.  In fact, CEs use tables called "truth tables" all the time to determine the given output for a value.  For example, here's the truth table for a basic AND gate:```

IN | OUT
00     0
01     0
10     0
11     1
```In essence, *basic* digital design is just this: lookups.   In a slightly more formal sense, a digital circuit is the implementation of a discrete function f(x).  Which is just mapping a fixed set of inputs to a fixed set of outputs.

You are correct in that the circuity "traveled" changes based on the input, sometimes.

The reality of the matter is however is that in basic digital logic circuits, the path doesn't change based on the input.   If for example, I have 3 AND gates cascaded together, I know a value of '0' from the first gate will mean both sucessive gates will yield a value of '0', no matter what the other gate inputs are.  However, instead of trying to short-circuit those gates, I just let the value propogate through.  Far simpler to design.  Certainly anything of the level you should concern yourself with for now will be of this nature.

Obviously, items like busses don't behave like this: only one device on a bus can talk at a time (generally) and so the physical path traveled would be different.  But those are a touch advanced ;)

Most of this also applies to basic combinational logic.  Sequential logic adds another step: basically you have the input of one stage advance to the output of another on a clock.  Obviously, CPUs are of this nature.  They're also synchronous devices, meaning all the stages advance data at the same time.

All of this would be covered in a basic digital design course.  If you can, see if you can't get your HS to let you take college credit at your local community college, they ought to have one class that covers this stuff (though perhaps for technicans and with more of a implementation than design focus).

---

### Post by iand675@gmail.com on 2006-01-10
I also realize that some of my questions are somewhat trivial, but i'm ocd, so I really had to ask them. In any event, thanks for the answer. It helped clear up some things for me. On a less on-topic note, what do you need to know before you go to university for a computer engineering degree? I sort of have a fear that since I'm not  very proficient at coding or circuitry as a high-schooler that I might fail miserably. So since you have first hand experience, it would really be nice to hear your thoughts on that.

---

### Post by LordHunter317 on 2006-01-10
[QUOTE=iand675@gmail.com]On a less on-topic note, what do you need to know before you go to university for a computer engineering degree?[/quote]Nothing if the school is good.  My school (WNEC) is very good, and the Computer Engineers professors are awesome.  Introductory Digital Design is open to almost all students (mandatory for CE and CS) and doesn't require any former experience, even circuitry experience.  You spend maybe one week where knowing Ohm's Law (V=IR) and the power equation (P=IV and derived) is necessary, and that's the limit of the electrical part, really.

> I sort of have a fear that since I'm not  very proficient at coding or circuitry as a high-schooler that I might fail miserably.Not especially, if you're willing to learn and pay attention.  Understanding some stuff before hand helps, but I'd never really done much digital logic before college.  I did however, know how to wire circuits and stuff, the general concept of "ground", and a few other things.  But you'd learn those anyway.

---

### Post by LordHunter317 on 2006-01-10
I should say however, it's good you want to learn now, but don't think of it as a mandatory requirement to study this stuff in college.  Worry more about having strong math, logic, and critical analysis skills.  Engineering is about designing things, and the most important two questions to be able to answer are, "Do these results make any sense?" and, "Will this solution solve the problem I'm given?"

Largely, those two are less about the tools or branch you're working in, but more about your ability to reason, analyze, and think.

Also, I can't stress the importance of having strong writing and speaking skills.  Communication is paramount for a good engineer.

---

### Post by iand675@gmail.com on 2006-01-10
Well, I'm shooting for MIT provided I keep my grades up and continue doing well on the SAT, so I figured that an exceptional technical knowledge would be required to do well there. If so, it would be a necessity to begin learning now.

---

