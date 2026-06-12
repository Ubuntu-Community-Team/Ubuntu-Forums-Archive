---
title: "Ubuntu Scripting for beginners advice?"
date: 2010-05-18
forum: Programming Talk
---

### Post by pr0t3g3 on 2010-05-18
Is there a tool or tutorial specifically for ubuntu to edit scripts and programs that work here?  Maybe I'm asking the wrong question; forgive me but I like ubuntu and the sooner I start with something within the system the happier I'll be.  I'd like to edit some programs... but it's just not that easy... again: is there a smart-tool or something like that, that is available; could someone make one :P?

---

### Post by GregBrannon on 2010-05-18
Perhaps if you could be more specific in what you'd like to do.  Bash is the typical scripting language used in a terminal window.  You can find many sources online for bash tutorials.  Ubuntu application programs are written in almost as many languages as currently exist in the mainstream.  You could pick an application you'd like to improve, find the source code, then focus on learning the language it was written in, if you don't already know it.

That's a start.  If you can be more specific about what your interests are, you could get a better answer.

---

### Post by Sub101 on 2010-05-18
I agree with GregBrannon. 

If you are talking about changing scripts then ok, if you mean to change actual programs then it is more difficult and programming knowledge would normally be required.

---

### Post by pr0t3g3 on 2010-05-18
I see ... Let's say, I wanted to edit.... um... forgive me for my weakness... if I wanted to edit halo with custom edition or diablo 2 lod or any type of game in general; you mentioned finding the script source how do i find that? for ANY application?  do i load it as a .text? and once i have it what do i do with it?

---

### Post by pr0t3g3 on 2010-05-18
let me be a bit more specific; if I wanted to edit an operating system ( the way it load's or just its functions)  where would I even start... I understand that this is big stuff but where would I even begin how do i pull the os up to edit it... >.< what do i do?? what are the first things i need to know when i want to edit a program or system in general?

---

### Post by Sub101 on 2010-05-18
> **pr0t3g3 said:**
> I see ... Let's say, I wanted to edit.... um... forgive me for my weakness... if I wanted to edit halo with custom edition or diablo 2 lod or any type of game in general; you mentioned finding the script source how do i find that? for ANY application?  do i load it as a .text? and once i have it what do i do with it?

If by this you mean you want to actually edit the source of a program like Halo then it would be quite impossible as Halo is not open source.

If we are again talking about editing open source programs then it would be a task that requires programming ability. 

If you want to take a look at the source of an open source application then you can normally download it from their website. And you can open it in gedit, or most other text editors.

---

### Post by proggy on 2010-05-18
I think the poor kids wants to learn how to hack games/operating systems.

I might be wrong.

---

### Post by pr0t3g3 on 2010-05-18
> **Sub101 said:**
> If by this you mean you want to actually edit the source of a program like Halo then it would be quite impossible as Halo is not open source.

If we are again talking about editing open source programs then it would be a task that requires programming ability. 

If you want to take a look at the source of an open source application then you can normally download it from theebsite. And you can open it in gedit, or most other text editors.
what if i just wanted to edit the functions inside of halo custom editions like the weapons and their functions their power how they load how fast they load.... or in diablo if i wanted to add a new custom character created by me in the game.. so that the character can interact in the environment with the scripts edited so that any custom attacks do what i want them to do with out mimicking he effects of another move... and edit the way the ai talk to them how would i do all of that... is that not possible? would it be more work then it's worth?

---

### Post by pr0t3g3 on 2010-05-18
> **proggy said:**
> I think the poor kids wants to learn how to hack games/operating systems.

I might be wrong.
No. lol... but if i can get ubuntu to run microsoft programs and other  programs that run on those unique operating system without using another  program inside of linux then my life ... shoot ANYONES life would be  much easier.  I can have what i want without changing operating  systems... i dont care if i have to edit it for a few years if i get the  results i want i'm good ^_^

---

### Post by Sub101 on 2010-05-18
> **pr0t3g3 said:**
> what if i just wanted to edit the functions inside of halo custom editions like the weapons and their functions their power how they load how fast they load.... or in diablo if i wanted to add a new custom character created by me in the game.. so that the character can interact in the environment with the scripts edited so that any custom attacks do what i want them to do with out mimicking he effects of another move... and edit the way the ai talk to them how would i do all of that... is that not possible? would it be more work then it's worth?

Id go with not possible, and not supported on these forums even if it was.

A general note - you can only really edit programs if they are open source.

I think thats it for my help on this slippery slope topic.

---

### Post by pr0t3g3 on 2010-05-18
i'm a novice but that's why i want to learn and i'm asking you how to find source codes and once i find one how do i edit it... you said there are different types what resources can i use to find out what they are and edit them with?

---

### Post by pr0t3g3 on 2010-05-18
> **Sub101 said:**
> Id go with not possible, and not supported on these forums even if it was.

A general note - you can only really edit programs if they are open source.

I think thats it for my help on this slippery slope topic.
are you telling me it's not worth pursuing this topic.. ok then how about editing any application.... once i have the source code how do i identify what type it is and what resource to use to edit it?

---

### Post by Sub101 on 2010-05-18
> **pr0t3g3 said:**
> are you telling me it's not worth pursuing this topic.. ok then how about editing any application.... once i have the source code how do i identify what type it is and what resource to use to edit it?

As long as we arent talking about editing the source on copyrighted programs I will continue.

If you take a look at the source code of the Ubuntu text editor "[gedit]("http://ftp.gnome.org/pub/GNOME/sources/gedit/2.30/gedit-2.30.2.tar.gz")" you can open up in a text editor the program.

For simplicity sake we will say that most programs are written in C or C++ with some exceptions.

To understand what is going on in the source you need to have some knowledge in the programs language, as I said that is generally C.

---

### Post by pr0t3g3 on 2010-05-18
> **Sub101 said:**
> As long as we arent talking about editing the source on copyrighted programs I will continue.

If you take a look at the source code of the Ubuntu text editor "[gedit]("http://ftp.gnome.org/pub/GNOME/sources/gedit/2.30/gedit-2.30.2.tar.gz")" you can open up in a text editor the program.

For simplicity sake we will say that most programs are written in C or C++ with some exceptions.

To understand what is going on in the source you need to have some knowledge in the programs language, as I said that is generally C.
hmm... so the only way to know is to have knowlege of the language... so basically to compare what i've been asking;  i asked you how do i know what language chinese or russian or (language of choice here)  ... but it's the wrong way to go about it right? i need to just study the basics and then branch out to different languages before i go randomly editing things correct?

---

### Post by Sub101 on 2010-05-18
> **pr0t3g3 said:**
> hmm... so the only way to know is to have knowlege of the language... so basically to compare what i've been asking;  i asked you how do i know what language chinese or russian or (language of choice here)  ... but it's the wrong way to go about it right? i need to just study the basics and then branch out to different languages before i go randomly editing things correct?


Yes, learn the basics of programming and work your way up. 

The spoken language is not all that important in programming, with the exception that comments tend to be written in English.

---

### Post by pr0t3g3 on 2010-05-18
For anyone with the same questions I had; this is a great place to start:

[http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867)


I get the feeling that thread will be invaluable to me for the next few months ^_^

---

### Post by DaymItzJack on 2010-05-18
Seriously, not trying to be mean, but give up with editing other programs. You will _never_ get the source code (the code that makes up the whole program) to something as big as Diablo or Halo. Most open source programs are ones that make no money, or very little.

You also have this false perception that you think programming is something easy. It's not. Halo and Diablo took years to make by _professional_ programmers, you are not going to "pick up" programming and then rewrite it to support it on Linux, it's not going to happen.

---

### Post by pr0t3g3 on 2010-05-18
[QUOTE=

You also have this false perception that you think programming is something easy. It's not. [/QUOTE]



I never stated or let on it was easy.  If you interpreted my thread as such then your sorely mistaken.   I have another thread:


  [http://ubuntuforums.org/showthread.php?t=1487328](http://ubuntuforums.org/showthread.php?t=1487328)

asking what to even do with the most basic of programming tools.

---

### Post by lunaz on 2010-05-19
Diablo2 single player modding community, been around for years...
[http://phrozenkeep.hugelaser.com/index.php](http://phrozenkeep.hugelaser.com/index.php)

---

### Post by pr0t3g3 on 2010-05-19
> **lunaz said:**
> Diablo2 single player modding community, been around for years...
[http://phrozenkeep.hugelaser.com/index.php](http://phrozenkeep.hugelaser.com/index.php)


Thanks but I'm in the middle of trying to figure out what to do with a basic programming package ^_^ 


 [http://ubuntuforums.org/showthread.php?t=1487328](http://ubuntuforums.org/showthread.php?t=1487328)



and I don't think that will help me much as my version of the game was converted into a single portable 1.70 gigs exe (everything is packed) by a guy pseudo-named romzon something or other on [http://www.warez-bb.org/](http://www.warez-bb.org/) he's also on megauploadforum.net 

So that link you gave me is useless to me, as I can't really reach the files to mod.

---

### Post by sky.programming on 2010-05-19
when you look into Ubuntu, and is used to do every thing within system , you would learn and master a lot from it.
Then you can find the tools that you can use it smoothly.
good luck.

---

