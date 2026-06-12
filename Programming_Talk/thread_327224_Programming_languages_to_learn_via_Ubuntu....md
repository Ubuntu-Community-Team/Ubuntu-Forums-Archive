---
title: "Programming languages to learn via Ubuntu..."
date: 2006-12-28
forum: Programming Talk
---

### Post by some_random_noob on 2006-12-28
Anything really, come on and broaden my interests :D 

Web design/scripting? A C# compiler? I don't mean nooby drag and drop things when I say that. I'm a 1337 wannabe :cool: Drop me a few links please.

---

### Post by Tomosaur on 2006-12-28
[An awesome resource](http://www.ubuntuforums.org/search.php)

Jesus...

---

### Post by Paul41 on 2006-12-28
For web design/scripting I use php. They have good documentation on their website. [http://php.net/](http://php.net/)

---

### Post by Wybiral on 2006-12-28
To Tomosaur: lol...

To "some_random_noob": that's a broad question... Maybe you should start by asking yourself what you want to do, and then read around on the other post's in this forum.

---

### Post by some_random_noob on 2006-12-28
> 
To "some_random_noob": that's a broad question... Maybe you should start by asking yourself what you want to do, and then read around on the other post's in this forum.
I'm just looking for resources, I might choose to do lots of different stuff. Its not unusual to do some web design and some programming.

---

### Post by Paul41 on 2006-12-28
What I think Wybiral is getting at is the best language to use frequently depend on what you are trying to accomplish. For example, when you say you want to do some programming, C/C++ could be the best option or it may be something like Python.

---

### Post by Tomosaur on 2006-12-28
What I was getting at is this same question has been asked a billion times. Please use common sense - this same question gets asked a few times every week.

---

### Post by Wybiral on 2006-12-28
This might help: [http://www.ubuntuforums.org/showthread.php?t=327239](http://www.ubuntuforums.org/showthread.php?t=327239)

---

### Post by some_random_noob on 2006-12-28
> **Tomosaur said:**
> What I was getting at is this same question has been asked a billion times. Please use common sense - this same question gets asked a few times every week.
I looked through and there isn't actually that much of interest to me. Not that I'm asking you to challenge me on that... this isn't a gaming forum :D

Anyway cheers for the info on various stuff everyone. Php looks cheesy, comes with a free introductory tutorial :D ... has a link to mysql stuff too.

Edit: interesting stuff there wybiral, random question: are there any exclusive linux programming languages that are worth checking out as a matter of interest?

> I think we should compile a list of resources for various languages and then sticky and lock the topic.
Yep, someone should push for that to happen...

---

### Post by FuriousLettuce on 2006-12-28
What do you mean, php looks 'cheesy'? Have you ever actually programmed before? Any idea what you want to achieve? You can't just write off languages because they come with helpful documentation and have strong links to one of the major databases in the web-serving world :|. There are many different mainstream languages out there, and all are aimed at / excel at different things. Decide what you'd like to be able to do, then search it, it's not hard.

EDIT: This can be a useful resource: [http://www.ubuntuforums.org/showthread.php?t=255970&page=1](http://www.ubuntuforums.org/showthread.php?t=255970&page=1)

---

### Post by Wybiral on 2006-12-28
As a matter of interest... Assembly is fun to play with. It isn't really efficient for writing stuff in because it's so meticulous... But it will definitely expand your knowledge of the processor and what a lot of programming languages are compiled into.

I'm not advocating this as a good beginner languages or anything, just saying that as a "matter of interest" it is something that gives me a sense of accomplishment to program in. If you have GNU Gcc installed (and you should), you can program things in assembly using it's assembler...

The default first program (hello world) in GAS (the GNU assembler) looks like this...

```

.data
 msg: .string "Hello world!\n"
 len= .-msg
 
.globl _start
_start:
 movl $4, %eax
 movl $msg, %ecx
 movl $len, %edx
 int $0x80
 
 movl $1, %eax
 int $0x80

```

Save that as something like "MY_PROGAM.s" and compile it from the command line with this...
```
as MY_PROGRAM.s -o MY_OBJECT.o
```
Then link it to create an executable with this...
```
ld MY_OBJECT.o
```

Then you should have an output file, probably "a.out" that you can execute from the command line for a small "Hello world!" program.

But, I am in no way saying that ASM should be your first language, just adding an option.

---

### Post by some_random_noob on 2006-12-28
> **FuriousLettuce said:**
> What do you mean, php looks 'cheesy'? Have you ever actually programmed before? Any idea what you want to achieve? You can't just write off languages because they come with helpful documentation and have strong links to one of the major databases in the web-serving world :|. There are many different mainstream languages out there, and all are aimed at / excel at different things. Decide what you'd like to be able to do, then search it, it's not hard.

EDIT: This can be a useful resource: [http://www.ubuntuforums.org/showthread.php?t=255970&page=1](http://www.ubuntuforums.org/showthread.php?t=255970&page=1)
Yes I have programmed before, like I said I'm looking for all kinds of stuff. I currently don't do webdesign, but it looks like a good skill. Which leads to php & mysql, along with my current interests of application programming. Also just a matter of interest. This thread is probably just a waste of space. Someone get in contact with a mod for some stickies... anyway I think I know what I'm doing now :D

---

### Post by maddog39 on 2006-12-28
This cant be hard...

I will compile a list of stuff when I go away tomorrow on vacation. I will make a list of languages, toolkits, and the likes, with descriptions and links. Will that work?

---

### Post by &lt;mawe&gt; on 2006-12-29
A bit offtopic:
@Wybiral: Do you have any links to good Assembly tutorials?

---

### Post by Wybiral on 2006-12-29
To <mawe>:

This is a really good (free) book to read, very informative:
[http://download.savannah.nongnu.org/releases/pgubook/ProgrammingGroundUp-1-0-booksize.pdf](http://download.savannah.nongnu.org/releases/pgubook/ProgrammingGroundUp-1-0-booksize.pdf)

The GAS manual (a must):
[http://www.gnu.org/software/binutils/manual/gas-2.9.1/html_mono/as.html](http://www.gnu.org/software/binutils/manual/gas-2.9.1/html_mono/as.html)

A linux system call lookup table:
[http://asm.sourceforge.net/syscall.html](http://asm.sourceforge.net/syscall.html)

A great i383 manual (A MUST):
[http://pdos.csail.mit.edu/6.828/2005/readings/i386/c01.htm](http://pdos.csail.mit.edu/6.828/2005/readings/i386/c01.htm)

Misc:
[http://cosmos.raunvis.hi.is/~johannos/mips/mips-howto.html](http://cosmos.raunvis.hi.is/~johannos/mips/mips-howto.html)
[http://www.janw.dommel.be/eng.html](http://www.janw.dommel.be/eng.html)
[http://www.lxhp.in-berlin.de/lhpk6opt.html](http://www.lxhp.in-berlin.de/lhpk6opt.html)
[http://www.cs.virginia.edu/~evans/cs216/guides/x86.html](http://www.cs.virginia.edu/~evans/cs216/guides/x86.html)
[http://ares.x25zine.org/ES/txt/0x4553-Asm_tutor.htm](http://ares.x25zine.org/ES/txt/0x4553-Asm_tutor.htm)

This is just the collection I have found that isn't the usual "this is hello world, see how it's different from dos assembly..." stuff (like every linux assembly tutorial). Hope this helps.

---

### Post by amo-ej1 on 2006-12-29
I agree on Programming from the ground up, I once started reading it and had great fun working through it. When I have some more free time I'm gonna try to pick it back up again.

Edit: also mind there are two assembly words, you have the Intel x86 syntax, using nasm to compile and the GNU syntax using gas. Tutorial above (including programming from the ground up) cover the GNU syntax. 
[http://asm.sourceforge.net/](http://asm.sourceforge.net/) contains a more generic list of tutorials

---

### Post by gh0st on 2006-12-29
> **Tomosaur said:**
> What I was getting at is this same question has been asked a billion times. Please use common sense - this same question gets asked a few times every week.

I'd have to agree, you see this question all the time on here. Usually worded almost exactly the same :)

---

### Post by PriceChild on 2006-12-29
> **Tomosaur said:**
> What I was getting at is this same question has been asked a billion times. Please use common sense - this same question gets asked a few times every week.> **gh0st said:**
> I'd have to agree, you see this question all the time on here. Usually worded almost exactly the same :)Then please take the time to post a link to one of these topics instead of rude responses such as "search for it" etc.

---

### Post by &lt;mawe&gt; on 2006-12-29
Thank you for the links amo-ej1 and Wybiral. I had a quick look at *Programming from the Ground Up* and it seems to be great.

---

### Post by some_random_noob on 2006-12-29
> **maddog39 said:**
> This cant be hard...

I will compile a list of stuff when I go away tomorrow on vacation. I will make a list of languages, toolkits, and the likes, with descriptions and links. Will that work?
Yeah... make some recommendations, list the difficulty and what the language is used for. A lot of people just want to know where to start. And people like me want to know what the best language for a specific task is. Get some good links to resources and it should work nicely :D

---

### Post by gh0st on 2006-12-30
If you are interested in Python then this is a good place to start - [http://wiki.python.org/moin/BeginnersGuide](http://wiki.python.org/moin/BeginnersGuide)

Python is a very user friendly language and can be a good place to start for beginners.

---

### Post by pmasiar on 2006-12-30
> **some_random_noob said:**
> Anything really, come on and broaden my interests :D 

Web design/scripting? A C# compiler? I don't mean nooby drag and drop things when I say that. I'm a 1337 wannabe :cool: Drop me a few links please.

Ok, maybe I am feedeing a troll :-/ But looks as you genuinely like challenge. Here are couple of links to 1337 languages to broaden your horizon:

From [list of hello world programs]("http://en.wikibooks.org/wiki/List_of_hello_world_programs"), take a look at [Befunge]("http://en.wikipedia.org/wiki/Befunge") [Brainfuck,]("http://en.wikipedia.org/wiki/Brainfuck") [Piet,]("http://en.wikipedia.org/wiki/Piet") [Whitespace]("http://en.wikipedia.org/wiki/Whitespace_%28programming_language%29")

Having fun yet?

If you want links more related to your interests, it might help to tell us what interests you have. :twisted:

---

### Post by Engnome on 2006-12-30
> This cant be hard...

I will compile a list of stuff when I go away tomorrow on vacation. I will make a list of languages, toolkits, and the likes, with descriptions and links. Will that work?

> **some_random_noob said:**
> Yeah... make some recommendations, list the difficulty and what the language is used for. A lot of people just want to know where to start. And people like me want to know what the best language for a specific task is. Get some good links to resources and it should work nicely :D

I got the feeling he was being sarcastic, dunno could be wrong.

---

### Post by coder_ on 2006-12-30
Note: To anyone wanting to start assembler, while looking around on the links already provided in this thread, I found another nice resource:  [http://www.lxhp.in-berlin.de/lhpsysc0a.html](http://www.lxhp.in-berlin.de/lhpsysc0a.html)

It is a list of Linux system calls and has the parameters, returns, descriptions, and such for a good bit of Linux system calls for asm.  It has the registers and what should be in them for the system call. It is quite handy for a new user like me.

I've just started beginning asm using GAS, and found this reference very handy.

---

