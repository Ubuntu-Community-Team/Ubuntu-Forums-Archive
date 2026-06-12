---
title: "hardware programming."
date: 2008-07-24
forum: Programming Talk
---

### Post by hockey97 on 2008-07-24
Hi I asked on another website about hardware programming.

I was told before that ASM is the way to go until I ask this other website.

They told me ASM has no value in todays market. Perl is the way to go  and perl was used to create windows xp.

they said c and perl are mostly used in hardware programming.

I have a hard time finding computer chips that would be programmed by c script, so far I have seen only ASM.

Is this true??

is ASM not really used anymore???

Should I learn perl, I already know c script. I would like to know what perl is used for and what can it be used in.

thanks for your time.

---

### Post by tamoneya on 2008-07-24
ASM is rather outdated.  almost all hardware programming is C (not C++), not perl.  I am very suproised that you cant find chips that are programmed in anything but ASM.  I typically use either microchip PICs: [http://www.microchip.com/stellent/idcplg?IdcService=SS_GET_PAGE&nodeId=64](http://www.microchip.com/stellent/idcplg?IdcService=SS_GET_PAGE&nodeId=64) or Atmel AVRs:[http://www.atmel.com/](http://www.atmel.com/)

---

### Post by LaRoza on 2008-07-24
> **hockey97 said:**
> 
I was told before that ASM is the way to go until I ask this other website.
Lots of languages are used. Java, Forth, C etc.

> 
They told me ASM has no value in todays market. Perl is the way to go  and perl was used to create windows xp.
Sounds like someone is pulling your leg...

> 
Is this true??

is ASM not really used anymore???

Of course it is used.

> 
Should I learn perl, I already know c script. I would like to know what perl is used for and what can it be used in.

Perl is like Python in many ways, but it is focused on text processing (re's and such are built into the language)

For programming on hardware, you should try Forth.

---

### Post by mike_g on 2008-07-24
> They told me ASM has no value in todays market. Perl is the way to go and perl was used to create windows xp.
AFAIK you need to use ASM to access many hardware features (such as the MMX registers on an intel processor), this can't be done in C alone, and certainly not in Perl. Athough you can add inline asm to C code.

---

### Post by clash on 2008-07-25
> **hockey97 said:**
> Hi I asked on another website about hardware programming.

............

is ASM not really used anymore???


ASM is of course used. But unless your planning on coding for a very niche part of the market then you don't need it and its far too much trouble to learn then its worth unless you absolutely know you will be using it. 

Unless you actually know you will need assembley or something else for a very specific job then 99% chance all you need is C. 

And anyone who says anything different is wrong.

---

### Post by slavik on 2008-07-25
Perl for hardware programming is a first to me. Although you can use Perl to write device drivers.

The following has probably been pointed out:
C is used a lot for embedded programming since it is easier to manage and read than ASM code. ASM code is very processor dependent, change the model a bit and there might be a different instruction (or a change and so on).

---

### Post by DavidBell on 2008-07-25
@ OP. You are probably looking at C as others have stated, maybe a small amount of ASM. Other langauages may be an option depending on the hardware you are interested in.

@ tomaneya. FYI you can use C++ on atmels, it might cost you 0-10% overhead but I accept that because I find the code easier to read. My record for a _useful_ C++ program is 1063 bytes small (compiled), targeted at atmel Tiny2313 :-). You can also use a version of basic on atmels. Don't know about PICs.

DB

---

### Post by Lster on 2008-07-25
Assembly and C work well together. They're what I used for OS development a while ago - I don't think you can really get away without a little assembly here and there - if you can, tell me! ;)

---

### Post by LaRoza on 2008-07-25
> **Lster said:**
> Assembly and C work well together. They're what I used for OS development a while ago - I don't think you can really get away without a little assembly here and there - if you can, tell me! ;)

Forth on hardware? More control, higher level.

---

### Post by Lster on 2008-07-25
[QUOTE=LaRoza]Forth on hardware? More control, higher level.[/QUOTE]

I've never seen it done (in fact, I've never seen the language used at all!). You've got to remember that there is a lot of tutorials and docs for assembly and C development, though. And, as I hinted at, I think assembly is required for at least some of it. That makes C ideal as the two languages are easy to mix...

---

### Post by MaindotC on 2008-07-25
The following is from the Oreilly book "Understanding the Linux Kernel":

> Linux source code for all supported architectures is contained in more than 14,000 C and assembly language files...

I took an assembly language class and my professor told me that typically no one nowadays should have to write huge programs in assembly because of the amount of coding you would have to write, but there are times when you need to use that low-level access to the hardware and can't rely on the decisions that a high-level language makes when accessing memory or ports.

---

### Post by LaRoza on 2008-07-25
> **Lster said:**
> I've never seen it done (in fact, I've never seen the language used at all!). You've got to remember that there is a lot of tutorials and docs for assembly and C development, though. And, as I hinted at, I think assembly is required for at least some of it. That makes C ideal as the two languages are easy to mix...

[http://en.wikipedia.org/wiki/Open_Firmware](http://en.wikipedia.org/wiki/Open_Firmware)

---

### Post by Lster on 2008-07-25
Interesting link - thanks! :)

---

### Post by DavidBell on 2008-07-25
> **LaRoza said:**
> Forth on hardware? More control, higher level.

How more control?

Never used Forth, but I get the feeling it's a nice language that's gradually drifting into obscurity. I think at one point in the 90s there was even hardware being specifically designed to take advantage of it, but that's no longer happening. 

Before you used it you would have to check language/tool support for the hardware you are targeting. eg AFAIK it doesn't work on most of the atmels mentioned above.

DB

---

### Post by hockey97 on 2008-07-25
wow I started a debate lol.

well The reason I asked, is that I currently just bought a learners kit where it has a development kit, this kit is to introduce cplds ect and also teaches some ASM since I will be coding in 2 different language ASM and the special language that was made for the chip, well in this kit it has a eletronic board with a cpld chip, a tv chip, audio chip, and video chip, it then has a onboard programming chip, and how this board is made it ha a breadboard where I can include my circuit.

now I never done any hardcore programming I done small projects ect to atleast allow me to learn while doing ect.

I was going to start this kit next week. I also did try looking for chips that I can program in c but never found them.

after I finish my learners kit I plan to build a eletronic board maybe might try doing pci or somthing not sure right now but I do plan to start a small prodject that won't take years but would like to gain some experience so I can do a big prodject to gain my knowledge.

I asked on here because I was on a board forum talking about this kit and the people lol. then told me (the stuff I already said in my first post) So I wanted to make sure this was not in some way to misinform me.

they told me xp was made using perl. they said only the start menu was made in c.

and they did told me that perl and c are commonly used for hardware programming.

they also did tell me that perl is mostly used for device drivers.

If you know of a good website that can teach perl making device drivers please do tell.


I am computer hungry lol. I been so far programming in web programming langos and haven't gain much on applications and hardware programming.

I am also currently in college going for a major in accounting.

very boring stuff and teachers don't really help much they would only refer you to pages in the book to read which when you read it the book assumes  you have some basic knowledge in this area.

I really wanted to go for computerscience but my dad told me that
programmers are treated badly and their skills are no valueable since their is alot of people in that area they can easily replace you.

So I listened to my dad and went for accounting which the college requires us to take business courses, I will be taking the same courses as business admins but then in my bach years I will drift towards accounting in depth.
I am currently in a class that teaches federal tax. I also hope you know by law we are not reqired to file a 1040 form.
IRS tells you that you need to but in reality their is no law currently that states that we have too.

well I want suggestions where I should focus in learn for hardware.

I have a xbox gamepad and have a device driver. I can also get the source code for the gamepad should I start their.

I don't know what programming language it is in.

I also now just saved that website you guys provided of the chips that can be programmed in c.

I also would like to learn how the xbox chips was programmed.

---

### Post by rlc on 2008-07-25
[I]'they told me xp was made using perl. they said only the start menu was made in c.'
[/I]
hilarious

[I]'I really wanted to go for computerscience but my dad told me that
programmers are treated badly and their skills are no valueable since their is alot of people in that area they can easily replace you.

So I listened to my dad and went for accounting which the college requires us to take business courses' [/I]

well this is a mistake

It doesn't sound like your dad knows much about computer programming no offense. This honestly just sounds like mindless reaction from conventional talking points about 'outsourcing' and 'globalization'...both good things I would argue.  

For someone in university now, who isn't invested in one specific area, computer science is an excellent field.  Its the older programmers who refuse to retrain and whose high paychecks make them easy targets who should be worried anyway.  

Computing is a dynamic constantly changing field and the ones who can remain on their feet and are willing to be continuing learners can expect great rewards.  

besides, I couldn't think of anything more dreadful and mindnumbing than being an accountant :)

---

### Post by pmasiar on 2008-07-28
> **DavidBell said:**
> Never used Forth, but I get the feeling it's a nice language that's gradually drifting into obscurity. I think at one point in the 90s there was even hardware being specifically designed to take advantage of it, but that's no longer happening. 

Forth is productivity-multiplicator language which has no patience with fools. Good programmer can be 20 times more productive, but below-average programmer will be 20 times **less** productive in Forth, because Forth does not even pretend to shield programmer from any kind of error or mistake - you have full raw power to do anything you can imagine.

And because really good programmers are rare, most popular language in enterprise world is Java which accommodates replaceable cogs average programmers with average training over the experts.

---

### Post by pmasiar on 2008-07-28
> **hockey97 said:**
> and they did told me that perl and c are commonly used for hardware programming.

they also did tell me that perl is mostly used for device drivers.

They were making fun of you. Some forums are less friendly to beginners - ubuntu has Code of Conduct which will not allow for such misinformation.

> my dad told me that
programmers are treated badly and their skills are no valueable since their is alot of people in that area they can easily replace you....So I listened to my dad and went for accounting

you seems to be a magnet for bad advice :-)

You will be bored out of your mind, try to switch to MIS or something computer related. It's pityfull life to hate/be bored going to work.

---

### Post by KingTermite on 2008-07-28
Are you trying to access hardware on a computer with an OS or directly controlling hardware without OS in between? Its different.

Either way, C is by far the most used way to go. If you are using an OS (like a piece of hardware plugged in to your computer) then you have to either modify driver in the OS (Linux) or go through the OS APIs (Windows).

If you are directly controlling hardware, you will typically have a compiler set up and have to download the code to the device. Going this route you can directly access hardware parts such as registers, memory, etc....

Either way, C is the most used. ASM is kind of outdated, though I'm sure its still used in places. Perl seems a very unlikely choice (though not impossible if in a OS and accessing the APIs via Perl - I've done this once). I think people who told you this info were likely yanking your chain.

---

### Post by DavidBell on 2008-07-29
> **pmasiar said:**
> Forth is productivity-multiplicator language which has no patience with fools. Good programmer can be 20 times more productive, but below-average programmer will be 20 times **less** productive ...

Ha ha, now I know *why* it's fading away. Doubt I'll be learninging it as I'm more likely to be in the second group :-)

---

### Post by pmasiar on 2008-07-29
> **DavidBell said:**
> Ha ha, now I know *why* it's fading away.

Well, if good programmers were not restricted by their PHBs, they would solve most problems already and put average and below programmers to early retirement. If 5% of programmers is 20 times as productive, they solve same amount of problems, right? So it is "conspiracy of the morons" (or "programmer full employment act") to prefer Java over the Forth, but it's a sad fact.

---

### Post by slavik on 2008-07-29
> **pmasiar said:**
> Well, if good programmers were not restricted by their PHBs, they would solve most problems already and put average and below programmers to early retirement. If 5% of programmers is 20 times as productive, they solve same amount of problems, right? So it is "conspiracy of the morons" (or "programmer full employment act") to prefer Java over the Forth, but it's a sad fact.
yes, but try to write a website authentiction module in Forth, not so simple. :(

edit: hockey97, does your father work with programmers in any way? if he doesn't, then I can't see why he would give such a life altering advice.

---

### Post by pmasiar on 2008-07-30
> **slavik said:**
> yes, but try to write a website authentiction module in Forth, not so simple. :(

Forth approach is to implement (in Forth) customized mini-language (DSL, domain-specific language) to write authentications, then use that DSL to implement the module.

---

### Post by Mr.Macdonald on 2008-07-30
I have a good idea, if you become an accountant, you could spend a year or so programming a few computers to do the work for you!! you could then go on vacation or to the beach while customers do everything online. And every 2 weeks you just collect the paycheck and go on another vacation!! Good life, huh?

---

### Post by pmasiar on 2008-07-30
> **Mr.Macdonald said:**
> I have a good idea, ... Good life, huh?

You don't have any real-world experience in making living as a programmer, fixing bugs, etc, do you?

There are **hundreds** of accounting packages, all trying to do what you suggest. Think for 5 minutes what might be the reason why none succeeded so far? Any ideas?

---

### Post by slavik on 2008-07-30
> **pmasiar said:**
> Forth approach is to implement (in Forth) customized mini-language (DSL, domain-specific language) to write authentications, then use that DSL to implement the module.

you also need to write a module for the http server or your own http server ...

---

### Post by winch on 2008-07-30
> **pmasiar said:**
> Forth is productivity-multiplicator language which has no patience with fools. Good programmer can be 20 times more productive, but below-average programmer will be 20 times **less** productive in Forth, because Forth does not even pretend to shield programmer from any kind of error or mistake - you have full raw power to do anything you can imagine.

While c/asm are well known for shielding the programmer from their mistakes and holding back the hardware.

---

### Post by pmasiar on 2008-07-31
> **winch said:**
> While c/asm are well known for shielding the programmer from their mistakes and holding back the hardware.

Do you know Forth at all?

C and ASM are low-level languages. Forth is as high-level as you want (and also allows defining some functions in ASM if you need to). All other high-level languages (except Forth) protect programmer and hide hardware.

---

### Post by MaindotC on 2008-08-01
> **winch said:**
> While c/asm are well known for shielding the programmer from their mistakes and holding back the hardware.

I disagree with you regarding ASM.  I take computer science classes that started with instruction in C and ASM, but just for kicks I took some electronics classes.  I learned that assembly is the bridge between the high-level language and manually applying electrical charges to be held in registers in the CPU for processing.  I can use assembly to do plenty w/ the hardware like placing specific contents in memory directly accessed by the video card (probably easy for all of you) and especially nasty things like make the wiper go off the disk and smack against the wall of the hd repeatedly.

I don't feel that assembly really shields anything.  Could you explain why you feel this way?

---

### Post by pmasiar on 2008-08-01
> **strAlan said:**
> I don't feel that assembly really shields anything. 

It was a sarcasm. Of course ASM does not. But Forth is high-level language, which lets programmer to do anything, including direct manipulation of call stack.

---

### Post by MaindotC on 2008-08-01
Oh lol how foolish of me :) Ok pmasair - I'm wit you now :)  When you say the stack, you mean the stack of commands pointed to by the stack pointer, which I think are located in the ds register, correct?

---

### Post by pmasiar on 2008-08-01
> **strAlan said:**
> Oh lol how foolish of me :) Ok pmasair - I'm wit you now :)  When you say the stack, you mean the stack of commands pointed to by the stack pointer, which I think are located in the ds register, correct?

Either callstack of Forth calls, or even DS register: any Forth word (~= "function") can be defined in ASM, and do whatever programmer wants (and break whatever s/he forgot to care about). 100% full control (and responsibility).

---

### Post by DavidBell on 2008-08-01
Well I think I'll wait for Fifth. 

Don't really see why anyone would use a HLL language that seems to revel in making your life difficult and has 400x variation in productivity (yes that was a slight exageration wasn't it?). And I can imagine enterprise would just love a bunch of 1337 hakkors making up their own mini languages that only they can understand. 

I would need a really compelling reason to even consider it. DB

---

### Post by lisati on 2008-08-01
> **winch said:**
> While c/asm are well known for shielding the programmer from their mistakes and holding back the hardware.
ASM shield you from your mistakes? Please forgive me if I disagree. 
The biggest foul-up I've ever made was making an assumption with ASM which  resulted in a non-profit group's client database getting scrambled. (Program tested on a '286, target machine had an NEC chip v20 or something of that kind which could run programs written for 8086/8088, and which interpreted some '286 instructions a bit differently to the x86 family)

---

### Post by slavik on 2008-08-01
forth is supposed to be implemented in hardware (there were lisp machines that had every lisp basic function in hardware, but they were slower than a general pupose ibm pc), and you can modify the return address in C and assembly (buffer overflow anyone?) but why would you want to do that?

---

### Post by DavidBell on 2008-08-02
> **lisati said:**
> ASM shield you from your mistakes? Please forgive me if I disagree. Don't worry it was a joke.

---

### Post by pmasiar on 2008-08-02
> **DavidBell said:**
> Don't really see why anyone would use a HLL language that seems to revel in making your life difficult and has 400x variation in productivity (yes that was a slight exageration wasn't it?). And I can imagine enterprise would just love a bunch of 1337 hakkors making up their own mini languages that only they can understand. 

I think that every hacker should be tempted to try such language (I know I was :-) ), just to see if I can handle it. 

Forth does not make your life difficult (it is not brainfuck) intentionally: it just allows you to  do tricks (if you want to) not possible in other languages, because they (other languages) trust programmer less.

I agree that Forth is not for enterprisey programming ("mongolian hordes" of average code monkeys, if you read [http://en.wikipedia.org/wiki/Mythical_man-month](http://en.wikipedia.org/wiki/Mythical_man-month) ), but for superprogrammers of old school, but that is not a bug: it is a **feature**.

And 400-times variation is not exaggeration: bottom 20% of code monkeys would have **zero** productivity in Forth :-)

---

### Post by pmasiar on 2008-08-02
> **slavik said:**
> forth is supposed to be implemented in hardware 

Because Forth is extremely simple, it is easy to implement both in software and in hardware. Forth chips were available since 80ties - but they were drowned in flood of unwashed PC masses... :-(

Complete Forth system (OS, BIOS, compiler, editor, shell) [was](http://www.ultratechnology.com/) 6K object code and 30K source code - in mid-80ties. I still do not understand why people prefer Java for embedded apps. :-(

---

