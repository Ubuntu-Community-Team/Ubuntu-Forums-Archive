---
title: "PLC Programming"
date: 2009-03-07
forum: Programming Talk
---

### Post by tobias_84 on 2009-03-07
Hi All!

I'm looking for some software that can me help me program PLC-units.
Have an Hitachi device whit serial connection to play whit.

Found a nice application to design a program and can be found here:
Classic Ladder: [http://sourceforge.net/projects/classicladder]("http://sourceforge.net/projects/classicladder")

But How do I transmit my program to my PLC-device?

Got any ideas?

---

### Post by stevescripts on 2009-03-07
hmm ... a quick google search for "linux PLC programming software" brings 
over 230,000 hits...

That said, in my work expierence here, my customers have insisted upon PLC brands that (as far as I knew at the time) have no linux programming software available, as it all is written with a COM interface for windows
computers.

I have some folks I might be able to contact next work week, as far as I 
know, they use PLC's from Automation Direct, but I dont know what software  they have been using.

Steve

---

### Post by mmix on 2009-03-07
Have you check hitachi plc manual?

[http://www.hitachi-ds.com/en/download/plcmanuals/](http://www.hitachi-ds.com/en/download/plcmanuals/)

---

### Post by U-P-S on 2009-10-03
same thing, excempt i am having mitsubishi melsec's PLC. dont wanna hang on windows xp any longer, and i found out tons of hits but noone mentioned about programming melsec PLC over COM from linux. currently on windows but i think this will change not matter what, it would just be good if i'd have ability to program PLC from linux.

so: any ideas how to program mitsubishi melsec plc via com port?

---

### Post by stoobers on 2010-08-20
Hi, hopefully this posting isn't considered too old to reply to.

Two things are being brought up.
1.  programming in ladder logic.
2.  transmitting the code to a plc.

I think #2 is the part in question.

If you want to transmit to a PLC (or anything else) over a serial port, and you don't have the software to "transmit" the code too the serial port, you can just write the code.  It is much easier than one would think.  You stick a character on the serial buffer, and the buffer chip on the motherboard will transmit the character.  Then, you can read the buffer and see what was sent back, and get to use all those previously useless bit shift operators that c has.

The easy way:
Write a useless ladder logic program on the windows pc and transmit the useless program to the PLC with the windos PLC specific transmitting software.  Then get a program that will let you view what the com port is saying (hacker style - snoop on the serial port!)  When you transmit the useless program for the plc, you can view what the PC says, and how the PLC responds.  This give you enough info to phreak the language.  Then you write a linux script to emulate the phreaked language.

The hard but educational way:
Plug the windows pc into the linux pc with a serial cable that has the transmit and receive pins crossed.  Then, use linux to capture what the windows pc says during a transmission to the plc, (note that the linux computer is hooked to the windows computer, and the plc is not doing anything yet.)  The windows pc will likely say something like "xq#7" or some other gibberish, which probably means "wake up!" or something similar.

So then, you hook the linux pc up to the plc with a conventional serial cable and write a script that says to the plc "wake up!" and the PLC will say something back, like "ok, i'm awake".  You capture this response and write it down.

Slowly, you repeat this process until you have phreaked enough of the protocol language to "trick" the plc into thinking you are legit.

Usually, there are 10 bazillion things transmitted for every simple action, because engineers like to do inane things the hard way.  But don't despair!  Usually, you can find some tiny subset of the communication protocol that gets the job done without all the monkey business.  It leaves one wondering why the engineer didn't use the easier subset of the protocol in the first place.

Thanks,
Christopher Stubban

---

### Post by singizitp on 2011-02-22
am new and currently working with PLCs and would very much appreciate it if I get some tips from you guys who have the exp and don't mind sharing with me. For the past few week I have been working with horizontal steam sterilizers(autoclave) and have seen quiet a lot of different PLCs. For starts can anyone help me with a ladder logic diagram of an autoclave for the Mitsibussgi FX seriies or the Toshiba T1S series. I would be very grateful as this will make my work easier.

Stay blessed

---

### Post by LoopTown on 2013-04-30
I've solved the problem by using windows for my work laptop. If you're into PLC's then sooner or later your going to be in a industrial environment or at a building site and when that happens - laptops tend to pass away in these conditions - so let it be windows. : )

For overall PLC tips - learn logic! Really - saves you a lot of time and then - start with box diagrams like Siemens Function Box Diagram (or anything similar) and move over to ladder - when you've got those then start on Structured Text Languages. Don't try to learn them all - there are as many different PLCs today as there are factories and for competitive market, they all have to have a slightly different programming languages. Once you know the basics you can pick up any PLC language in a few days. 

BTW: Siemens Logo was mentioned because the software LogoSoft is free on their website and also can run simulation and I/O states without the expensive controller attached to it.

---

### Post by tgalati4 on 2013-04-30
Sometimes you can simply *cat* the file to the serial port:

```
cat textfilewithyourlogic.txt > /dev/ttyS1
```

Try some simple commands that light up the display and see what happens.

You can install *microcom* and send strings of characters to your device to verify the function of commands.  There are a lot of tools to work with serial devices, you just need to spend some time with them and search the repositories for *serial*. 

```
apt-cache search serial
```

After a while you won't miss the fancy Windows programming interface.  You are only uploading a file with special commands to the device.  How fancy does the interface need to be?

---

