---
title: "converting windows codes to linux"
date: 2008-06-09
forum: Programming Talk
---

### Post by x88a on 2008-06-09
i have the source code for a program for windows XP.
it is a GUI. Written in C#.
Does anyone know how or any guide to convert the codes to operate in Linux Ubuntu 7.10?

tq

---

### Post by LoneWolfJack on 2008-06-09
Sure. Reprogram it from scratch.

Microsoft .NET is platform dependent, especially when it comes to GUIs.

Mono can compile C# under Linux but I don't think that will get you very far with a GUI.

However, you may htry to compile it for windows and tweak it until it runs with WINE.

---

### Post by x88a on 2008-06-09
LOOOOL
no way i am going to program that huge complicating program from scratch.

> However, you may htry to compile it for windows and tweak it until it runs with WINE.

could you please state the procedure?
tq

---

### Post by Frak on 2008-06-09
Let's get this MinGW bus on the road!

By that I mean you'll need to install MinGW cross-developing compiler/libs to be able to compile for a Windows system.

If your up to it, just say and I'll help, but it'll be a pretty long procedure.

---

### Post by LoneWolfJack on 2008-06-09
> could you please state the procedure?

Compile the code under windows.
Move the exe to linux and run it with WINE.
Check the WINE error messages.
Change the code to avoid the problem.
Compile it under windows.
Move the exe to linux and run it with WINE.
Check the WINE error messages...

---

### Post by x88a on 2008-06-09
> **Frak said:**
> Let's get this MinGW bus on the road!

By that I mean you'll need to install MinGW cross-developing compiler/libs to be able to compile for a Windows system.

If your up to it, just say and I'll help, but it'll be a pretty long procedure.

if it will work, then i am up to it
where should i start?

---

### Post by Vadi on 2008-06-09
Wouldn't adapting it to work in Mono be a lot more easier?

---

### Post by LaRoza on 2008-06-09
[http://ubuntuforums.org/showthread.php?t=818192](http://ubuntuforums.org/showthread.php?t=818192)

With no knowledge of C# and programming, you will not be able to do this.

I see so many of your threads about mono, and posting errors. You will not be able to do anything this way. 

If you can't run the Windows app in Wine, try to find a Linux alternative or use Windows for this app (in a VM even)

You aren't going to be able to get this working by posting errors on this forum, please don't try.

---

### Post by Vadi on 2008-06-09
> **LaRoza said:**
> You aren't going to be able to get this working by posting errors on this forum, please don't try.

Thank you for your encouragement, but I think that if you simply ignored this thread, it would have been a lot more productive.

---

### Post by Frak on 2008-06-09
> **LaRoza said:**
> [http://ubuntuforums.org/showthread.php?t=818192](http://ubuntuforums.org/showthread.php?t=818192)

With no knowledge of C# and programming, you will not be able to do this.

I see so many of your threads about mono, and posting errors. You will not be able to do anything this way. 

If you can't run the Windows app in Wine, try to find a Linux alternative or use Windows for this app (in a VM even)

You aren't going to be able to get this working by posting errors on this forum, please don't try.
Sure beats "Something went wrong"
"What"
"This"
"Whats this"
"I don't know, you tell me"

---

### Post by x88a on 2008-06-09
i do have knowledge in programming.
i did C++ and a bit of javascript and Ruby before.
it is just that i am new to C#.
i am confident i can do it.
So pls teach me

---

### Post by Vadi on 2008-06-09
While I'd recommend that you use C++ on Linux, or anything else but C#, C# is still a very viable choice on Linux. Look here ([click]("http://www.monodevelop.com/Main_Page")) to get started on it.

---

### Post by x88a on 2008-06-09
> **Vadi said:**
> While I'd recommend that you use C++ on Linux, or anything else but C#, C# is still a very viable choice on Linux. Look here ([click]("http://www.monodevelop.com/Main_Page")) to get started on it.

i am using C# because the available Windows source code i have is C#

---

### Post by KingTermite on 2008-06-09
> **LaRoza said:**
> You aren't going to be able to get this working by posting errors on this forum, please don't try.
Then what is the point of this forum existing at all? Might was well chuck it.

---

### Post by LaRoza on 2008-06-09
> **Vadi said:**
> Thank you for your encouragement, but I think that if you simply ignored this thread, it would have been a lot more productive.

I noticed that all the other threads on this same issue (a Windows program in C# not working in Linux) have no responses and the ones that do, have no fixes posted. Productivity isn't shown in the other threads also on this same issue.

> **x88a said:**
> i do have knowledge in programming.
i did C++ and a bit of javascript and Ruby before.
it is just that i am new to C#.
i am confident i can do it.
So pls teach me

There is more to it than the language, C#. The program you are using is apparently using non standardized libraries, probably highly specific to Windows. C# itself is easy to learn, the rules are very similar to C++ and Java. 

So, to get this project working on Linux, I would recommend contacting the original developer of this open source project. You will also need to study how it works.

> **KingTermite said:**
> Then what is the point of this forum existing at all? Might was well chuck it.

Look at the other threads started (all the ones about mono or C#). Do you see a pattern?

The OP doesn't know C# or anything about mono, doesn't know how the application works, and doesn't know (or didn't) how to use the repositories to install needed libraries. The reason I made the post was to help end the pointlessness.

---

### Post by Vadi on 2008-06-09
Canonical is paying for the forum storage, so don't worry about some extra posts for help. Someone might come by and answer.

---

### Post by KingTermite on 2008-06-09
> **vadi said:**
> canonical Is Paying For The Forum Storage, So Don't Worry About Some Extra Posts For Help. Someone Might Come By And Answer.

Lol +1

---

### Post by Can+~ on 2008-06-09
If you made your own C# project on windows and then port it to windows, is likely that it will run, since, you know how it works.

Trying to understand someone else's project (the bigger, the worse) when not knowing the language, and trying to fix it via trial and error it's the highway to [voodoo programming]("http://en.wikipedia.org/wiki/Voodoo_programming").

Try to run it in wine (wine is in the repository), or in virtual box. If you want to learn C#, start from the bottom, build your own application, and try to port it then.

---

### Post by LaRoza on 2008-06-09
> **Vadi said:**
> Canonical is paying for the forum storage, so don't worry about some extra posts for help. Someone might come by and answer.

It has nothing to do with storage. Doesn't anyone else see the futility of this? An unknown project of unknown scope written in C# for Windows, being ported by someone who doesn't know C# and doesn't understand the code and starts many threads without giving context to the problem?

@OP Instead of making a thread every error, you'll be better off providing the project's name, homepage (with source code), and keeping everything together. There is a reason you aren't getting anywhere with this.

> **LaRoza said:**
> 
With no knowledge of C# and programming, you will not be able to do this.

If you can't run the Windows app in Wine, try to find a Linux alternative or use Windows for this app (in a VM even)


> **Can+~ said:**
> 
Try to run it in wine (wine is in the repository), or in virtual box. If you want to learn C#, start from the bottom, build your own application, and try to port it then.

In otherwords...

---

### Post by Phenax on 2008-06-09
How do you port an application from one operating system to another?

You learn the programming language and make sure it is intended for the platform you are porting it to.
You find the platform-specific libraries that are used in the project, and then find the code that relies on this.
You find libraries that work on your platform and then begin converting the platform-specific code to use this library.

---

### Post by LaRoza on 2008-06-09
> **Vadi said:**
> Canonical is paying for the forum storage, so don't worry about some extra posts for help. Someone might come by and answer.

[http://ubuntuforums.org/showpost.php?p=5148786&postcount=5](http://ubuntuforums.org/showpost.php?p=5148786&postcount=5)

et tu, Vadi?

---

### Post by Vadi on 2008-06-09
Yeah, I didn't tell him to give up and go away, I provided him a resource on more help.

---

### Post by KingTermite on 2008-06-09
> **Vadi said:**
> Yeah, I didn't tell him to give up and go away, I provided him a resource on more help.
Exactly!

I think people should ask all the questions they want. If its too much in scope or there are better resources to help OP discover their answers, then those can be posted.

Sometimes a link to a good reference can be just as helpful as "knowing" the answer.

---

### Post by x88a on 2008-06-09
wow....it is nice to see this thread so active now.
i will try what you all suggested.
stay tuned  :)

---

### Post by LaRoza on 2008-06-09
> **Vadi said:**
> Yeah, I didn't tell him to give up and go away, I provided him a resource on more help.

I didn't say that, I just gave things he can do, instead of trying to do things he can't do.

Trying it on Wine, running it in Windows, and running Windows in a VM are all things to consider to get this working, instead of not getting it work...

---

### Post by lisati on 2008-06-09
> **Phenax said:**
> How do you port an application from one operating system to another?

You learn the programming language and make sure it is intended for the platform you are porting it to.
You find the platform-specific libraries that are used in the project, and then find the code that relies on this.
You find libraries that work on your platform and then begin converting the platform-specific code to use this library.

Hopefully the original progam is sufficiently well-structured so that the GUI-related  and OS-specific stuff is sufficiently separated from the "meat and bonens number crunching" parts of the code

> **LaRoza said:**
> I didn't say that, I just gave things he can do, instead of trying to do things he can't do.

Trying it on Wine, running it in Windows, and running Windows in a VM are all things to consider to get this working, instead of not getting it work...

This option might be a better place to get started for the novice programmer trying to adapt software.

---

### Post by Vadi on 2008-06-09
> **LaRoza said:**
> I didn't say that, I just gave things he can do, instead of trying to do things he can't do.

Oh? Well I think you did, and here's what I'm referring to:

> **LaRoza said:**
> You aren't going to be able to get this working by posting errors on this forum, please don't try.

I understand your pessimism, and I don't think it's doing any help at all, even if you claiming that it's for the better.

---

### Post by x88a on 2008-06-10
> So, to get this project working on Linux, I would recommend contacting the original developer of this open source project. 

i have contacted the original developer and they gave me the source code.
They dont offer Linux support.

> Try to run it in wine
unfortunately, Wine doesnt support it.

> @OP Instead of making a thread every error, you'll be better off providing the project's name, homepage (with source code), and keeping everything together. There is a reason you aren't getting anywhere with this.

i am trying to create a viewer in Linux for an ethernet camera.
[http://www.smartnd.com/sites/products/smart_cams/](http://www.smartnd.com/sites/products/smart_cams/)
i have the source code for the viewer in windows XP

---

### Post by x88a on 2008-06-10
> **Frak said:**
> 
By that I mean you'll need to install MinGW cross-developing compiler/libs to be able to compile for a Windows system.


for cross-developing compiler, do i need a the windows OS in my comp?
my comp only has Linux.

> If your up to it, just say and I'll help, but it'll be a pretty long procedure.
awaiting orders from you :)
i am now reading up on WinGW

---

### Post by scourge on 2008-06-10
> **x88a said:**
> for cross-developing compiler, do i need a the windows OS in my comp?

No, you don't need Windows. That's whole point of using a cross-compiler. But I don't see any need for MinGW here.

---

### Post by x88a on 2008-06-10
> **scourge said:**
> No, you don't need Windows. That's whole point of using a cross-compiler. But I don't see any need for MinGW here.

what would you suggest me to do then?

---

### Post by scourge on 2008-06-10
> **x88a said:**
> what would you suggest me to do then?

What others have already suggested: learn some C#, bring the code to Monodevelop, and make the changes that you need to compile a Linux binary. MinGW is only for compiling Windows binaries, which you don't need.

---

### Post by x88a on 2008-06-10
ok
could you pls go to [www.monodevelop.com](www.monodevelop.com) ?
can you access it?
i dont seem to be able to access the website
tq

---

### Post by LaRoza on 2008-06-10
> **x88a said:**
> ok
could you pls go to [www.monodevelop.com](www.monodevelop.com) ?
can you access it?
i dont seem to be able to access the website
tq

[http://lwn.net/2000/features/Axis/](http://lwn.net/2000/features/Axis/)

It may be possible to get this working without a special application (note, above article is for a specific camera, but the concepts are likely the same)

---

### Post by x88a on 2008-06-10
> **LaRoza said:**
> [http://lwn.net/2000/features/Axis/](http://lwn.net/2000/features/Axis/)

It may be possible to get this working without a special application (note, above article is for a specific camera, but the concepts are likely the same)

reading it now :)

---

### Post by x88a on 2008-06-10
> Instead, you have to configure your system to give an IP address to the camera via either ARP or BOOTP. ARP is the simpler solution

does anyone know of any manual which can teach me how to do this?
tq

---

### Post by pmasiar on 2008-06-10
> **LaRoza said:**
> With no knowledge of C# and programming, you will not be able to do this.

Recently, we have flooding of posting where people want to move app from Win to Linux without  any clue about what obstacles they have to overcome. MSFT created whole industry based on platform lock, with many decisions made for deliberate incompatibilities with older, and more mature, Unix/Linux platform. Starting with picking \ as path delimited, which was used for decades in Unix as escape char (\t is tab, etc.). So of course you will have problems with porting - it was the whole point in developing Windows/.NET platform! Vendor lock!

We here use Linux because we want to use linux, and want to use tools native to linux. Java is the cross-platform C# you are looking for.

> You aren't going to be able to get this working by posting errors on this forum, please don't try.

While I understand the spirit (yet another C# post going nowhere), "please don't try" feels wrong. Anyone should have opportunity try, and strive, maybe fail, but has chance to learn and win. I would not hold my breath, but maybe you can win. But:

> **x88a said:**
> does anyone know of any manual which can teach me how to do this?
tq

this approach shows that OP is just a wannabe, furiously thanking anyone supporting his quixotic quest, but without basic Google-fu skills. A leech, possibly. Let him live, maybe s/he is up to something. Maybe new influx of C#/VS lovers can help him to get off the ground.

---

### Post by LaRoza on 2008-06-10
> **pmasiar said:**
> 
While I understand the spirit (yet another C# post going nowhere), "please don't try" feels wrong. Anyone should have opportunity try, and strive, maybe fail, but has chance to learn and win. I would not hold my breath, but maybe you can win. But:


I think I was the only one to see that all the threads started in this forum by the OP were all related.

See: [http://ubuntuforums.org/showthread.php?t=823365&page=2](http://ubuntuforums.org/showthread.php?t=823365&page=2)

This is a larger program, with many threads that do not give the context. It isn't just an "error" it is part of a bigger picture.

I don't think the OP is going to get this working, especially by making lots of threads on it. Making lots of threads on one topic is against the Code of Conduct anyway, and it is just wasting people's time.

---

### Post by pmasiar on 2008-06-10
> **LaRoza said:**
>  especially by making lots of threads on it. Making lots of threads on one topic is against the Code of Conduct anyway, and it is just wasting people's time.

That's completely different issue then. Leech, breaking CoC!

---

### Post by x88a on 2008-06-10
> I don't think the OP is going to get this working, especially by making lots of threads on it. Making lots of threads on one topic is against the Code of Conduct anyway, and it is just wasting people's time.

but those 2 threads arent the same, correct?
if it aint allowed, i wont do it again
sorry

---

### Post by pmasiar on 2008-06-10
It always helps to at least link to other thread, so ppl can get relevant background - humans rarely have perfect memory like LaRoza, and may not link your two posts together as relevant.

Make no mistake: we want to help people, but we want to help people who want to help themselves. We can show the way, but you have to do the learning - and show certain drive. Nobody has time and passion to teach you page by page - you go to school for that, and pay.

[How to become a hacker](http://www.catb.org/~esr/faqs/hacker-howto.html). And hacker is not cracker. :-)

---

### Post by x88a on 2008-06-11
OK, i will keep that in mind next time :D

Yes, so pls show me guidelines on how to convert the codes.
i m giving my best.

TQ

---

### Post by thornmastr on 2008-06-11
> **x88a said:**
> OK, i will keep that in mind next time :D

Yes, so pls show me guidelines on how to convert the codes.
i m giving my best.

TQ

I think you misunderstood. Pimsy will help you as will almost anybody provided you show some work of your own that attempts to solve your stated problem. So, please show us what code you have converted and what about that code is not working properly.

---

### Post by slavik on 2008-06-11
> **pmasiar said:**
> Recently, we have flooding of posting where people want to move app from Win to Linux without  any clue about what obstacles they have to overcome. MSFT created whole industry based on platform lock, with many decisions made for deliberate incompatibilities with older, and more mature, Unix/Linux platform. Starting with picking \ as path delimited, which was used for decades in Unix as escape char (\t is tab, etc.). So of course you will have problems with porting - it was the whole point in developing Windows/.NET platform! Vendor lock!

MSFT copied CPM's path delimeter (which is \). At the time, CPM was the big single user OS (a separate instance of it would run on an IBM 370 mainframe for every user).

---

### Post by LaRoza on 2008-06-11
> **slavik said:**
> MSFT copied CPM's path delimeter (which is \). At the time, CPM was the big single user OS (a separate instance of it would run on an IBM 370 mainframe for every user).

Wrong. QDOS copied CP/M and Microsoft bought QDOS and renamed it. (basically, you forgot the guys in the middle)

---

### Post by pmasiar on 2008-06-11
I do not recall original CP/M (for i8080) having directory structure, and [http://en.wikipedia.org/wiki/CP/M](http://en.wikipedia.org/wiki/CP/M) supports my hunch. Looks like directories were added only to CP/M-86, which has to compete with MS-DOS, but that was too late. When MS-DOS appeared on market, Unix was 12 years old -- all clues support my version of timeline. Do you have better resources?

---

