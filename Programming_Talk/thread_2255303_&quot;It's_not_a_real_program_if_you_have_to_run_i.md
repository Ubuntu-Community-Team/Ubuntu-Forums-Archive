---
title: "&quot;It's not a real program if you have to run it from the command line.&quot;"
date: 2014-12-04
forum: Programming Talk
---

### Post by SagaciousKJB on 2014-12-04
So yeah, I sinned and showed some foolish pride in a program I've been working on as of late, and showed it to my friend David.  He was just giving me a hard time but he joked, "Why don't you make a real program instead of something I have to run from the command line!"

You know, the thing is, as horribly misguided and inaccurate as that statement is...  I do kind of feel like I'm not a real "programmer" since the only thing I've ever wrote are command-line driven apps.  Frankly I just don't really think I have thought of or needed anything that even required a GUI and in some regards I've become more comfortable with the command line and I don't develop applications for anyone but myself so that makes sense.

But I supose it's kind of like, the least next step...  In my mind at least.  So with that in mind I think I'm ready to tackle making something with a GUI, but that kind of brings up the obvious questions...  Which library, and what to do?

Are there any tutorials or exercises people could recommend specifically for this purpose?  I suppose for now the general things like taking user input, opening files, etc. would be good to have and then I could think about what to actually "drive" in the background?

---

### Post by Lars Noodén on 2014-12-04
Having looked at the beginner side of these things, I found Qt easier to start with.  There are a lot of good tutorials, if you search.  

However, I still use and prefer the shell though I will sometimes write a web interface for things.

---

### Post by jhay2 on 2014-12-04
qt librarys or gtk can help you

---

### Post by ofnuts on 2014-12-04
You can wrote a script that uses TCL or else to show a dialog and call your "program" with a bunch of parameters.... 

Otherwise a typical push-button UI isn't very hard to write, you just have to understand that you don't control the order in which things happen and you have to take special steps when something will run for over 200ms. What is more difficult is writing something with interactive graphics.

---

### Post by sudodus on 2014-12-04
If you made the program for yourself, it is enough that it does what you want it to do. No need at all to make a GUI. By the way, a typical linux server uses no graphical desktop environment, so many advanced programs are command line programs.

But if you want many unqualified users to use your program, your friend David is probably right, they will not use it unless it has a GUI. In my experience making the GUI can take longer time than making the original program. I recently went through that process with [mkusb]("https://help.ubuntu.com/community/mkusb"). It is programmed in bash (yes, only the standard command line interface) and it uses ***zenity*** to provide a GUI.

What language were you using to create the program? Some flavour of C, python, ... , or bash?

---

### Post by Matthew_Harrop on 2014-12-04
The irony with GUI's is that they actually slow productivity.
At a company I used to work for we trialed a GUI based inventory system to replace the old CLI system (It was IBM i think) and everything ran much much more slowly, because it took that much longer for the staff using it to click the buttons, rather than tap out the commands. CLI is king!

---

### Post by QIII on 2014-12-04
Years ago, when that silly Windows thing appeared, we all said "Pshaw!  Those aren't *real *programs!"

---

### Post by SagaciousKJB on 2014-12-04
> **sudodus said:**
> If you made the program for yourself, it is enough that it does what you want it to do. No need at all to make a GUI. By the way, a typical linux server uses no graphical desktop environment, so many advanced programs are command line programs.

But if you want many unqualified users to use your program, your friend David is probably right, they will not use it unless it has a GUI. In my experience making the GUI can take longer time than making the original program. I recently went through that process with [mkusb]("https://help.ubuntu.com/community/mkusb"). It is programmed in bash (yes, only the standard command line interface) and it uses ***zenity*** to provide a GUI.

What language were you using to create the program? Some flavour of C, python, ... , or bash?

That looks nice, I've been wondering if such things were available.  I used C

Yeah I tend to prefer CLI as well, especially when talking about things being "slowed down".

---

### Post by buzzingrobot on 2014-12-04
Pfft! ;)

The command line and a GUI are both shells, i.e., programs that accept input from a user and displays results to a user. Whatever language a user speaks, the computer can't understand it.  So, we need shells to interpet our input and translate the computer's results.

Command line shells, like Bash, trace their lineage to years ago when hardware could not support a GUI.  You can't have a GUI when a display can only display characters on green phosphor and doesn't know a mouse from a moose.

The actual substance of programs is distinct from the interface they use. Using a command line interface is simpler than crafting an attractive GUI, which is a design skill that a developer may or may not possess.

---

### Post by Matthew_Harrop on 2014-12-04
> **buzzingrobot said:**
> Pfft! ;)
The actual substance of programs is distinct from the interface they use. Using a command line interface is simpler than crafting an attractive GUI, which is a design skill that a developer may or may not possess.

Ohh, so thats why nobody buys my software ;)

---

### Post by sudodus on 2014-12-04
I browsed the internet for ***C++ tutorials*** and found several links. Maybe you will find a good starting point that way.

Who can suggest a suitable tool and tutorial to create a GUI to a C program?

---

### Post by lisati on 2014-12-04
> **QIII said:**
> Years ago, when that silly Windows thing appeared, we all said "Pshaw!  Those aren't *real *programs!"

Indeed. I recall having such a reaction (or a variant of it) when Windows and the early Macs first appeared.

---

### Post by SagaciousKJB on 2014-12-04
> **sudodus said:**
> I browsed the internet for ***C++ tutorials*** and found several links. Maybe you will find a good starting point that way.

Who can suggest a suitable tool and tutorial to create a GUI to a C program?

Indeed I have found some QT tutorials before, but was wondering if anyone had opinions on which was the easiest for a beginner to GUI programming to pickup.

It would be cool to have something that's Windows portable too.  Isn't GTK ported to Windows?

---

### Post by pauls2 on 2014-12-04
My reasoning for using C99 is that you have the ability to easily port the program to any (almost any) other system as long as there is a compiler for it. When you begin to use GUI you lose the portability.

Back in the early 1980s I wrote some software with popup windows and pull down menus but it only worked in DOS. You remember Turbo C? Then Windows crashed onto the scene but the programs would still opperate with full functionality. Then Windows decided to control the hardware and the programs couldn't print. I quit writing software until just recently. I am now using C99 with Ubuntu and Lubuntu and while the software ir run in the terminal it provides the output I need. When I am done I will release them under the GNU-GPL and if someone wants to port it to operate with Windows or any other GUI then they can. The number crunching remains the same - only the dressing changes.

---

### Post by sudodus on 2014-12-05
> **SagaciousKJB said:**
> Indeed I have found some QT tutorials before, but was wondering if anyone had opinions on which was the easiest for a beginner to GUI programming to pickup.

It would be cool to have something that's Windows portable too.  Isn't GTK ported to Windows?

Portability might be a problem for the GUI. One option is to have a separate external GUI like zenity in linux and something else (but corresponding) for Windows and Mac.

The alternative would be to keep the 'computing' part of the program the same, and link separate GUI program parts for the different platforms in order to get the same look and feel 'everywhere'. This alternative might give the best result, but I think you have to spend a lot of time to find suitable tools and to learn how to use them.

---

### Post by eight.coffee.beans on 2014-12-05
I'd say that a real program is the one that works as it should ;)
I don't know why, but I really prefer those 'old-school' programs. :)

---

### Post by lisati on 2014-12-05
> **eight.coffee.beans said:**
> I'd say that a real program is the one that works as it should ;)
I don't know why, but I really prefer those 'old-school' programs. :)

+1.

On the very rare occasions I've done any programming in recent years, I haven't bothered too much with a GUI, on the assumption that getting the program to do what it's meant to do is more important than aesthetics.

---

### Post by ofnuts on 2014-12-06
> **lisati said:**
> +1.

On the very rare occasions I've done any programming in recent years, I haven't bothered too much with a GUI, on the assumption that getting the program to do what it's meant to do is more important than aesthetics.

Normally a GUI is not just aesthetics. It is also, when done properly, an efficient way to have the user and the program agree on what is asked and what is feasible.

---

### Post by lisati on 2014-12-06
> **ofnuts said:**
> Normally a GUI is not just aesthetics. It is also, when done properly, an efficient way to have the user and the program agree on what is asked and what is feasible.

Good call about a good GUI being a useful part of interaction between program and user. Perhaps I'm finding that old habits die hard - with my early coding efforts 30+ years ago, having a GUI wasn't an option.

---

### Post by vasa1 on 2014-12-06
What about "quickly"? Or has progress overtaken it? [Here's a video]("https://www.youtube.com/watch?v=sO8hiPreNBg") made by Canonical's former Community Manager.

---

### Post by buzzingrobot on 2014-12-06
> **ofnuts said:**
> Normally a GUI is not just aesthetics. It is also, when done properly, an efficient way to have the user and the program agree on what is asked and what is feasible.

Yes.  That was part of the point I was trying, poorly, to make earlier.

Neither approach is better or more valid than the other.  A GUI interface and a character-based interface are both shells that serve the same purpose:  Collect input from a user, interpret it into machine-readable form, pass it along to the operating system, get the results, interpret them back into human-readable form, and display them.

E.g., "ls -l" is as unintelligible to the OS as a click on a file manager. Something -- a program -- needs to be in the middle.

Character-based interfaces are often touted as faster and more efficient.  That can be true when the user already knows the correct sequence of commands to feed to the shell (Bash, usually, in Linux). If they don't already know that, though, speed and efficiency vanish because they have to stop and look things up.

User don't need to memorize or look things up to use a well-designed GUI. And a GUI gives the designer a chance to optimize the display of data returned by the system.

On the other hand, GUI's aren't very amenable to scripting.

---

### Post by matt_symes on 2014-12-06
Hi

on my servers, all the programs are run from the command line and they are real programs ;)

you may want to mention that to your friend next time he browses to a webpage hosted on a non windows server :)

kind regards

---

