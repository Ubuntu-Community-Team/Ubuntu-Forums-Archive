---
title: "Cpu.....asm"
date: 2007-08-02
forum: Programming Talk
---

### Post by hockey97 on 2007-08-02
Hi, I am making a project for myself, I want to create a computer just using a huge breadboard, so not dealing with pcb's ect.

I want to use a quad core, but I don't know where I could learn the ASM or I mean get the asm compiler so that the ASM code would be able to be runned by the cpu.

I want to make a computer that are today's standards, this way I can get experience on the new type of cpu's be able to make a system of today'.

mainly just messing around, I need a tutorial or a place to explain today's computer tech, like quad-core how to use the cpu and also programm it , in order to create an embedded system.

I know a little ASM, I know c++ and c-script and also python.

---

### Post by Wybiral on 2007-08-02
What are you doing? Building a computer?

Why do you need assembly?

---

### Post by ev5unleash1 on 2007-08-02
I think me may be talking about something about the motherbord idk. Please explain more.

---

### Post by hockey97 on 2007-08-02
sorry for being unclear.

ok,  well  I got a bread board , so I can test designed circuit's.

my plan is to build a motherboad, like I want to just build it on my breadboard and just have fun, with it.

I want to have an experience on making a motherboard, basicly a computer system.

I am going to make the cuircuitry and use lan chips and cpu's and gpu's.

well what my question is I want to use top noch stuff, like quad-core,

so when I finish it I will have up to date eperience.

what I am asking is I need to program using ASM for the board and all , and make my own OS.

well I can't find anything on a quad-core on how to program it with using a ASM compiler, it's a amd proccessor the new one phantom.

my question is mainly on how could I find info on the cpu so I can programm it, or run my code using it.

I need help with the programming, I plan to do some programming in ASM to get the system going, like booting ect.

then I plan to program in C++ which I am more familiar.

how do people go about's learning how to program of the cpu, opcode..


if this is still not clear please let me know.

---

### Post by AlexThomson_NZ on 2007-08-03
Do you know how many pins on a quad core CPU?  Not really breadboard friendly, I'm afraid.  I'd suggest a simpler project.

---

### Post by xzero1 on 2007-08-03
This should give you a start:
[http://en.wikipedia.org/wiki/X86_assembly_language]("http://en.wikipedia.org/wiki/X86_assembly_language")
but you should also know something about the hardware itself. You are basically designing a system and there are many critical parameters such as timing,temperature,capacitance,current and voltage that must be met -- or it will not work, not to mention, the rf that will be produced if it does!  Learning asm will be the least of your problems if you really decide to proceed. Good luck.

---

### Post by LaRoza on 2007-08-03
My wiki has links to Assembly programming, but I don't know how helpful it will be. See my sig "Learn to Program", and look in the library.

---

### Post by Wybiral on 2007-08-03
Unfortunately, boards these days are printed for a reason... There's no way you can squeeze that much crap on a normal bread board.

And if you could... It would be so tedious and time consuming... Then you want to write an OS for it? Wow...

Why not try writing a simple OS for an old computer first. Go pick up an old 386 based computer with the most generic parts you can find and try to get a simple OS running on it.

I can understand wanting to do something like this from the ground up for the learning experience... But it's just not possible these days. Certainly not with a quad core processor.

Why don't you start be designing a simple half-adder circuit... Then design a full-adder circuit. Learn a LOT about binary and boolean logic... Then try to build your own calculator.

But don't start with interfacing a quad core AND writing your own OS at the same time.

---

### Post by b1g4L on 2007-08-03
Wait, are you serious? Sorry to rain on your parade, but you may want to start with simple circuits. Look for projects to build adders, FM radio, timers, etc. It's simply unfeasible to "Build your own computer" of today's standards. Try to find  circuit diagrams of the current Intel / AMD CPU's and you'll see why. Just trying to follow the process of adding on a current CPU architecture is very complicated.

---

### Post by hockey97 on 2007-08-03
wow,  ok here's my backround, I took lot's of classes in computers at school one was a college course in eletronics, we built our own radio's ect and done simple projects but we never used a cpu, like computer terms we were supposed to play with micro controllers but never had the time.

so I am trying to learn how programming the board ect, I have a big bread board, and   4 regular ones so I could add on to it.

I have done sodering in that class and also done dos ect, I could now go for a A+ certification if I wanted to that's the eletrcial level I have. I never had a class for programming , but had a web-design class teaching html, I learn that in 6th grade.

I learned c++ and c-script , I  mostly do c++ , I also learned python.

I might put a heat sink on the cpu.

I am not going to make a OS like xp or somthing, I plan on making simple OS, but at least making the system boot and able to use keyboard and mouse and the internet.

I have time to spend and I really learn good when I first read the principals and then try them out, becuse if I didn't understand some areas I will find out when tinkering with the example.

what I want to do is to read tutorials or stuff that would teach me they whole system from ground up, 

and then do an example.

also in that class we used logic gates in 3 projects  , and played with a 555 timer chip.

I know the hardware, just don't know how to blend it in with programming.

I know some ASM I have a book on it,  I just don't know what compiler and  does ASM not change for new cpu's,  I want to use a quad core or at least a duo core so that what I learn is currnet stuff.

so start small??

I know ohm's law and  basic circuit building, we used tronics lab's a company that provided the kit's, and we had for our final  we had to design something eletronic, using all we learned, and had to use bread boards.

I am taking a class in college right now to futher my education in eletronics, but I plan just to take one class, and that will be it, becuse I am thinking to go into accounting.

would you give mea link to any intel or amd cpu that you were saying if I look at it I will know why it's so difficult.

Thanks for the replies

---

### Post by aks44 on 2007-08-03
Just a question... how are you gonna handle the high clock frequency required by modern processors, and the associated timing and interferences problems on a breadboard? :shock:

At work, seasonned engineers occasionnaly ran into such problems using a 68HC microcontroller running at 16MHz on a breadboard (although they were expecting it I guess), so I really wonder how you're going to handle GHz frequencies...


I would rather advise you to start with some microcontroller (the 68HC family is quite "simple" to integrate on a board, but there are others).

Anyway I guess that we can't change your mind if you already decided to waste your time & money for no result...

Good luck then, keep us in touch...

---

### Post by hockey97 on 2007-08-03
I just downloaded freeware program, that I can build a system and then program it  and test run it , all on screen, so I might first go through that.

well I am going to ask a guy that is a engineer for microsoft, he know's alot about hardware and software interfacing he also wrote couple of books and has lot's of experience. He designed direct x 8 

He mostly play's with arm procceors on his free time.

Well I will throw some question's at him, I love computers and would love to get into it, as a business if possible.
I don't really want to work for companies for computer programming or hardware wise since I heard alot of  people saying that they will keep you 3 year's then toss you if you don't keep up with the new tech.
so they said it'sa bad feild since you alway's have to learn new tech to keep up with the job.

I will inform you guy's if I ever get such a project done, or got somthing going.

Key word,  IF

---

### Post by Wybiral on 2007-08-03
> **hockey97 said:**
> so they said it'sa bad feild since you alway's have to learn new tech to keep up with the job.

That's just how technology is... Anyone interested in technology will have to keep up.

Personally, I enjoy it... Who doesn't like to learn?

---

### Post by Steveway on 2007-08-03
You know that a modern Cpu has millions and millions of switches?
Recreating this on a bread-board would be a time-consuming procedur.
In my Opinion you should first learn to properly write and speak english, this is more helpful in the computer-world and less time-consuming.

---

### Post by aks44 on 2007-08-03
> **Steveway said:**
> 
In my Opinion you should first learn to properly write and speak english, this is more helpful in the computer-world and less time-consuming.

I just love it when you're being sarcastic :p (see my sig ;))

---

### Post by Steveway on 2007-08-03
Whooo, I'm in a Signature. Thanks! No really, thank you! :)
Yeah, sarcasm is a great thing, but it's hard not to cross the line and beeing mean.
But I really meant it serious. With his level of knowledge of the english language, he won't come far in this world.
Look at his posts, he can't even explain properly what he wants, if he wants to work in this industry he would fail miserably.
There are more important things than building a big version of a CPU that allready exists and that would need months or years of work.
My English isn't perfect, too.
But that's not the point.
EDIT: Ah yes, forgot to say this I'm German so we are almost neighbours. Strangely people don't really correct my grammar, maybe they are not brave enough to tell me or I really don't make that much errors, what I doubt cause I often sit on a sentence several minutes and can't get it right. ^^

---

### Post by aks44 on 2007-08-03
More off topic following, please disregard this post if you're part of the OT police...

> **Steveway said:**
> Yeah, sarcasm is a great thing, but it's hard not to cross the line and beeing mean.
Well, as far as I understand it, sarcasm is meant to cross the line... IMHO the problem is only on the reader's part if (s)he is not bright enough to get it. 


> **Steveway said:**
> But I really meant it serious. With his level of knowledge of the english language, he won't come far in this world.
Look at his posts, he can't even explain properly what he wants, if he wants to work in this industry he would fail miserably.
There are more important things than building a big version of a CPU that allready exists and that would need months or years of work.
My English isn't perfect, too.
But that's not the point.

Not being a native english speaker myself (I'm french if you didn't notice it yet) I know what you mean...
I really struggled hard to get a "decent" level of english, yet I often find myself corrected by other people regarding my grammar / spelling. Not that I mind... that's the only way we can learn ;)


EDIT: sh** I've been sig-quoted too... w00t ;)

---

### Post by aks44 on 2007-08-03
> **Steveway said:**
> EDIT: Ah yes, forgot to say this I'm German so we are almost neighbours. Strangely people don't really correct my grammar, maybe they are not brave enough to tell me or I really don't make that much errors, what I doubt cause I often sit on a sentence several minutes and can't get it right. ^^

As far as I know, we ARE neighbours ;)

Anyway FWIW most of the "english purists" I found are hanging on Usenet... not much are on web forums...

(Shall we give that thread back to the OP? PM me if you wanna chat more ;))

---

### Post by hockey97 on 2007-08-03
[QUOTE=Steveway;3128625]You know that a modern Cpu has millions and millions of switches?
QUOTE]

What do you mean??  I am not going to make my own cpu.

or are you talking about the transistor's??

I know their are switches, I also know boolean logic, and binary.

if it's not ever possible to do such thing's on a bread board, then what does microsoft do??
and how does AMD test their sutff??

most design's are first thought out then tested on a bread board or a proto- board, the wire wrapping which is not used anymore, according to latest eletronic books, that talk about sodering.

---

### Post by Steveway on 2007-08-03
Microsoft makes no PCs or CPUs.
Well, then you want to make a motherboard or what?
You should have followed my advice, then we would know what you want and could maybe help you better.
Have you tried mailing on of those companys and asking them how they do this?
They know it the best and maybe they point you out on how you can start. But they propably won't help you if you write like that to them.
EDIT: I don't really have anymore time to chat. I'm downloading Gentoo at the moment and I'm gonna try it again.

---

### Post by aks44 on 2007-08-03
> **hockey97 said:**
> if it's not ever possible to do such thing's on a bread board, then what does microsoft do??
and how does AMD test their sutff??

Both have tools you've never dreamed of. Nothing even remotely close to a breadboard. ;)

---

### Post by ablegreen on 2007-08-03
> **hockey97 said:**
> I just downloaded freeware program, that I can build a system and then program it  and test run it , all on screen, so I might first go through that.

well I am going to ask a guy that is a engineer for microsoft, he know's alot about hardware and software interfacing he also wrote couple of books and has lot's of experience. He designed direct x 8 

He mostly play's with arm procceors on his free time.

Well I will throw some question's at him, I love computers and would love to get into it, as a business if possible.
I don't really want to work for companies for computer programming or hardware wise since I heard alot of  people saying that they will keep you 3 year's then toss you if you don't keep up with the new tech.
so they said it'sa bad feild since you alway's have to learn new tech to keep up with the job.

I will inform you guy's if I ever get such a project done, or got somthing going.

Key word,  IF

Are you doing all this to keep up with latest 'tech'?
If you're trying to be the next Bill Gates, he didn't build his own computer hardware, so maybe you don't need to?

---

### Post by Wybiral on 2007-08-03
> **hockey97 said:**
> [QUOTE=Steveway;3128625]You know that a modern Cpu has millions and millions of switches?
QUOTE]

What do you mean??  I am not going to make my own cpu.

or are you talking about the transistor's??

I know their are switches, I also know boolean logic, and binary.

if it's not ever possible to do such thing's on a bread board, then what does microsoft do??
and how does AMD test their sutff??

most design's are first thought out then tested on a bread board or a proto- board, the wire wrapping which is not used anymore, according to latest eletronic books, that talk about sodering.

They have crazy stuff like simulated circuits and do more testing theoretically then anything.

With as many components there are in modern CPU's and even motherboards... Physically breadboarding it out would not only be physically impossible (components of that size are limited in a number of ways compared to micro components, you should already know this), but it would be terribly inefficient time and money-wise for a company to do this.

---

### Post by hockey97 on 2007-08-03
ya I know that it's mirco peices the componenets.

but  their are software out their that would  simulate the circuit,

of your design, then a pcb layout show's up and you can print it or send it through e-mail to a company where they shrink the layout and then do the pcb proccess.

So bread boarding is noting but for using it to test home products, like custom made low level stuff for your home, like hobbies?

So today's stuff is micro  to a point you can't really do by hand .

has to be with machines.

---

### Post by seamless on 2007-08-03
[QUOTE="hockey97"]wow, ok here's my backround,[/QUOTE]
You have just described introduction to electronics 101 at a university. The project you have described is at the level of about a masters student. You have a long way to go before you will be able to hook a modern processor to a bread board, write and OS and be able to use the internet.

---

### Post by jpkotta on 2007-08-04
> **hockey97 said:**
> ya I know that it's mirco peices the componenets.

but  their are software out their that would  simulate the circuit,

of your design, then a pcb layout show's up and you can print it or send it through e-mail to a company where they shrink the layout and then do the pcb proccess.

So bread boarding is noting but for using it to test home products, like custom made low level stuff for your home, like hobbies?

So today's stuff is micro  to a point you can't really do by hand .

has to be with machines.

You can do what you want, just on a smaller scale.  You cannot build a modern PC via breadboarding, but you can build a system with something like a PIC microcontroller.  PIC assembly is dead easy (32 instructions), and there are free C compilers (no gcc, though, IIRC).  

The place where I work does this kind of stuff.  I'm working on a board with an ARM9 and an ARM7 on it.  We're small and time is tight, so we only get one spin on the hardware.  There is no breadboarding, at least not for the whole board.  We just do simulations, look at the manufacturers recommodations (which is biting us in the *** right now...), use examples like dev boards, and of course use experience and general good practices.  My senior project in college was the same way.  All you can do is triple check and be prepared to put bandaids on afterwards.

---

### Post by HerrWu on 2007-08-04
Unfortunately, your computer system build with bread boards may work incorrectly even if you have correctly connected all of the component. The working frequency of the computer today is so high that reaches the radio frequency. So you can imagine that your computer build with bread boards will have serious EMI problems that prevent it from working correctly.

A computer today is too complex to study as a start like that. Maybe you can start with a 8086. Or you can start with a MCU of other series such as ARM or MIPS etc.. OS like Linux and eCos and WinCE can also run in such systems.

---

### Post by hockey97 on 2007-08-04
I see .

Well then I will start with the arms lol ,  I just wanted to make  some project that I could learn well experience how a computer boot's and run's.

so Do you guy's think if I go with the arm microcontroller and build a small system on my breadboard.

and then use linux type OS, or make a small OS by myself using ASM.

??

---

### Post by jpkotta on 2007-08-04
If you don't have much experience, I would really recommend PICs or something like that over ARMs.  They are very simple and can be breadboarded with no problems.  You can do lots of interesting things with PICs too, though you will not be able to do anything comparable to a PC.

The system I'm working on uses an Atmel at91sam9260.  There is support for it in the vanilla Linux kernel.  There is a tool called buildroot that will compile a cross-toolchain, bootloaders, kernel, and userspace.  If you want to see how a simple yet fairly complete system works, have a look at that.

[http://atmel.com/dyn/products/product_card.asp?part_id=3870](http://atmel.com/dyn/products/product_card.asp?part_id=3870)
[http://atmel.com/dyn/products/tools_card.asp?family_id=605&family_name=AT91SAM+32%2Dbit+ARM%2Dbased+Microcontrollers&tool_id=3933](http://atmel.com/dyn/products/tools_card.asp?family_id=605&family_name=AT91SAM+32%2Dbit+ARM%2Dbased+Microcontrollers&tool_id=3933)

[http://buildroot.uclibc.org/](http://buildroot.uclibc.org/)
[http://www.at91.com/phpbb/viewtopic.php?t=3193](http://www.at91.com/phpbb/viewtopic.php?t=3193)

---

### Post by HerrWu on 2007-08-05
> **hockey97 said:**
> I see .

Well then I will start with the arms lol ,  I just wanted to make  some project that I could learn well experience how a computer boot's and run's.

so Do you guy's think if I go with the arm microcontroller and build a small system on my breadboard.

and then use linux type OS, or make a small OS by myself using ASM.

??

If you want Linux run on your Computer system, ARM9 is a must. If you choose the ARM7 series, only ucLinux, ucOS or eCos could be installed. I think that the PIC's MCU is also a good choice, if you want to build your own controll system and write software by yourself. The principles of such MCU is the same as the 80x86 series.

---

### Post by chewearn on 2007-08-05
The last time I used breadboard was in school, making blinking lights.  No body use breadboard anymore in their practical work; even wire wraps are pretty much out.

Up to say 10MHz, you might conceivably get away with bread boarding; wirewrap possible up to 50MHz; as long as the IC packages are thru-holes.

A standard ARM CPU runs in a few hundreds MHz range; bread boards and even wirewraps will destroy signal integrity of the buses.  At this clock speed, even double-sided etched PCB will be problematic; so that rule out manual hand-made stuffs.

If you are really really interested in embedded design field, do yourself a favor and buy your CPU hardware ready assembled.  90% of the technical / fun / challenging stuff starts at software.  The hardware production is a tedious thing you need to get out of the way asap.

EDIT: By the way, there is no big money to be made in this area; just looks of grief and stresses, and occasional great moment when your finished product goes into millions of homes.

---

### Post by sarang on 2009-05-21
None of the processor packages these days are breadboard friendly. Why don't you consider building a motherboard for the 8085/6 or the 8051?

---

### Post by samjh on 2009-05-21
You really should read the date of the last post. ;)

Is it the Dark Art of Thread Necromancy, I feel?

---

### Post by sarang on 2009-07-12
> **samjh said:**
> You really should read the date of the last post. ;)

Is it the Dark Art of Thread Necromancy, I feel?


Why does being old make this thread irrelevant? In this case it clearly does not.

---

### Post by hockey97 on 2009-09-20
thanks for the replies. It's been a while when I posted this. 

I am interested in making my own embedded devices or my own eletronic device. 

I understand about motherboard making get someone to do it for you and assemble it.  I really have fun doing it all bymyself so when I finish it I can say hey I made that.  I mean if I pay a manufactor to build the hardware and I just program it I don't see why program it when you can just pay high end phd guys that can do a better job at programming the device for you or pay a small firm to do the software for you. 

Like I said I enjoy building stuff from ground up as much as possible. 

I do have a guy that has contact lists of manufactors in china that will create the motherboards.

---

### Post by lisati on 2009-09-20
Others might be able to provide some more up-to-date suggestions, but reading through this thread made me think of two books. I'm not sure if they're still in print.

[From chips to systems (Rodney Zaks)]("http://www.amazon.com/Chips-Systems-Introduction-Microprocessors/dp/0895880636")
[The soul of a new machine]("http://en.wikipedia.org/wiki/The_Soul_of_a_New_Machine")

---

### Post by hockey97 on 2009-12-09
So then how does todays computer chip computer systems get tested before they mass produce the boards? if they can't use wirewrap or a breadboard.

---

### Post by chewearn on 2009-12-10
> **hockey97 said:**
> So then how does todays computer chip computer systems get tested before they mass produce the boards? if they can't use wirewrap or a breadboard.

Lot's of computer simulations, then building prototypes on actual printed circuit boards.

---

### Post by Simian Man on 2009-12-10
> **hockey97 said:**
> So then how does todays computer chip computer systems get tested before they mass produce the boards? if they can't use wirewrap or a breadboard.

They are described in a hardware description language such as Verilog or VHDL and then extensively verified and tested using electronic design automation tools which simulate the design at the transistor level.

---

### Post by grayrainbow on 2009-12-10
[http://en.wikipedia.org/wiki/Programmable_logic_device]("http://en.wikipedia.org/wiki/Programmable_logic_device")

---

