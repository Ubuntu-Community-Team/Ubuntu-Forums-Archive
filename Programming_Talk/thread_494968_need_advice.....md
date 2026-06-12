---
title: "need advice...."
date: 2007-07-07
forum: Programming Talk
---

### Post by hockey97 on 2007-07-07
Hi I am trying to make a computer cuircuit currently, but I don't know what programming language to use.

I know c++, c, and Python, i also know html and php. 

I have read that for hardware programmers usaly use ASM, I did learn some ASM but haven't mastered it.

I heard that you would for a whole computer system use 1% ASM, and 99% C++, I don't know how true 
this is.

some people said that to find the error's in your OS  you would use ASM becuse it can detect error's and report where the error's occured on a low level, like the hardware program scripts level.

they said tha ASM is used to debug your OS on a low level the main gut's of the computer, while C++
is mostly used to program the overall stuff, the applications ect.

I was woundering if that's true?? and also what would you suggest I do?? 

I hear that ASM is rarely used,  just hear that c++ is mostly used.

I am just trying to play around with computers well I am trying to build one myself, from ground up,  like designing the circuits.

but I don't fully know what's used in the programming industry for hardware, like Windows, I have seen those blue screen's where it will post the memory address where the error occured.

If their is any sites that would guide me and explain me what today's standard is for overall computer's
I would like the links.

I really need some guidance, right now I am just messing around with the chips I have but don't know  on where to start programming it.

I tested the circuit it works just their is no program to give commands to the proccessor .

So I am starting to work on programming it.

I know programming like c++, it's just I never programmed a computer system from ground up.

---

### Post by Wybiral on 2007-07-07
I think there's more then 1% assembly.

Also, I think C is more common in writing hardware communication then C++.

C is also easier to work into assembly (and work assembly into C).

This sounds like an outrageously large project... Maybe a bit too large for one person?

---

### Post by AlexThomson_NZ on 2007-07-07
I applaude your ambitiousness!  if you were serious, just to save you some time: you will not be able to build a x86 compatible computer from the ground up.

---

### Post by finer recliner on 2007-07-08
i agree with the above posts that your project is unfortunately too large. 

instead start with something smaller like this:
[http://www.sparkfun.com/commerce/present.php?p=BEE-1-PowerSupply](http://www.sparkfun.com/commerce/present.php?p=BEE-1-PowerSupply)

that will give you a nice introduction to CPUs and how to program them (he uses C code). depending on your current knowledge, you may be able to skim the first 1 or 2 lectures before getting into new material (links to the next lecture in the series is near the bottom of the page)

---

### Post by nitro_n2o on 2007-07-08
such a good like finer recliner :) thx for that 
I'll lean with C, you can have assembly out of C very easily using GCC .... and you'll never have to kill yourself to write a loop.. 
To debug stuff in your OS you'll certainly need to understand binary and hex. I think assembly is really important you need to know it, but you'll use C most of the time

---

### Post by hockey97 on 2007-07-08
well ya the project is alot of one person, but I am dedicated on finishing my goals, I have a college book on embedded computers, well it takes you from gound up for computer engineering, from ohms law, ect to binary then too anolog, then too digital, and then to the whole system of a computer and teaches a little of ASM, and then talks about using C++ and gives links to study from.

Thanks for the links, I am just playing around just to get a feel one the overall how the stuff works together, havent seen the programming that brings the hardware together, I know the binary system and hex system.

I took a college level class in highschool on computers we mostly played with dos, but it was mostly lectures on the overall computers how ever it never went in main details of the programming part. the class was more on hardware debugging and how the hardware is made, and also networking teaches how to debug the network and how to monitor the network, and protect computers from viruses.

I got 9 college credits from that paid only 5 bucks for it.

Thanks for the replies.

If anyone has anything new tips or advice on this subject, 

feel free to reply.

---

### Post by Wybiral on 2007-07-08
What kind of computer are you thinking about and how "ground up" do you plan?

It's not hard to collect a bunch of computer components and assemble a computer... But if you mean working on the circuitry yourself... You're out of your mind, lol (unless you plan on a VERY simple computer... Like, basically a calculator. Which is entirely possible for a one-man project)

Anyway, can you be a bit more specific on your goals?

---

### Post by AlexThomson_NZ on 2007-07-08
You might be able to hack together a calculator using a FPGA, but forget about anything that can remotely run linux unless you have a fabrication plant.  This isn't a matter of how smart you are, but physical limitations (ie. the power required to power all the NAND gates on a breadboard that implements the whole x86 instruction set, let alone the size!- let alone ram controllers, video controllers, etc.)

If you want to give it a go, go for it- just promise you'll come back and tell us how it worked

---

### Post by Wybiral on 2007-07-08
This site has some really cool circuit simulator applets that lets you assemble really complex binary logic circuits (it's neat because you can build a circuit, then compact it into a chip and use it in another circuit... Very cool and lots of fun if nothing)
[http://math.hws.edu/TMCM/java/index.html](http://math.hws.edu/TMCM/java/index.html)

This site also has some basic info on how computers work (and links to another awesome binary logic simulator)
[http://courses.cs.vt.edu/~csonline/MachineArchitecture/Lessons/index.html](http://courses.cs.vt.edu/~csonline/MachineArchitecture/Lessons/index.html)

Here's another cool circuit simulator (I know... I'm an addict) that has some really good examples which might be of use to you. This one is also an electronic circuit simulator, not just binary logic gates.
[http://www.falstad.com/circuit/](http://www.falstad.com/circuit/)

Anyway, I'm hoping you have a thorough understanding of electronics and binary logic.

I will also say this... To be worrying about C or C++ or even conventional assembly at this point is getting ahead of yourself. You need to start designing an ALU and figuring out how you want to (and are capable of) structuring your machine language.

My suggestion if you are serious about a ground-up computer: make a calculator. If you can pull that off, make an extremely simple programmable graphing calculator.

If you can do that, then you can start working on more complex systems.

But if I were you, I'd just go to a computer store and buy pre-made parts :)

---

