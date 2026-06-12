---
title: "[SOLVED] C/c++"
date: 2008-01-30
forum: Programming Talk
---

### Post by RadiationHazard on 2008-01-30
I'm pretty sure you can do it on ubuntu? what's a good program for righting and compiling c and c++?

---

### Post by emarkd on 2008-01-30
Try anjuta.  It's in the repositories.

---

### Post by vishzilla on 2008-01-30
I use **Geany**, its in the repos!!! Geany can compile most of the programming languages!!!

---

### Post by LaRoza on 2008-01-30
> **emarkd said:**
> Try anjuta.  It's in the repositories.

> **vishzilla said:**
> I use **Geany**, its in the repos!!! Geany can compile most of the programming languages!!!

Both wrong, those are IDE's and not compilers. When learning, learn how to use the tools that are needed, not IDE's.

See [http://ubuntuprogramming.wikidot.com/C](http://ubuntuprogramming.wikidot.com/C)

And my wikis (link is in my sig)

---

### Post by emarkd on 2008-01-30
Why wrong?  Linux is all about choice, after all...

---

### Post by LaRoza on 2008-01-30
> **emarkd said:**
> Why wrong?  Linux is all about choice, after all...

Because neither of those are compilers.

---

### Post by emarkd on 2008-01-30
No, they're IDE's (at least Anjuta is, never tried the other) that rely on the compiler in the background.  But they still get the job done.

You can't write code in gcc, after all ;)  It's not an editor.

---

### Post by LaRoza on 2008-01-30
> **emarkd said:**
> No, they're IDE's (at least Anjuta is, never tried the other) that rely on the compiler in the background.  But they still get the job done.

You can't write code in gcc, after all ;)  It's not an editor.

And you can't compile with an editor.

I don't get your point.

This forum (this thread was moved) has stickies that address the IDE preferences, and has great resources for beginners.

Read my first post where I state they are IDE's, then come back to this.

---

### Post by mattismyname on 2008-01-30
compiler: g++
editor: vim
"IDE": cscope

---

### Post by LaRoza on 2008-01-30
> **mattismyname said:**
> compiler: g++
editor: vim
"IDE": cscope

As long as we are discussing it, g++ isn't actually a compiler. gcc is used.

---

### Post by jcwmoore on 2008-01-30
to write ANY programming language I use vim/gvim, and to compile c/c++ i use gcc and g++

---

### Post by emarkd on 2008-01-30
The OP asked for advice on good software for writing and compiling c/c++ in Ubuntu.  A correct answer could be and IDE like Anjuta or an editor/compiler pairing like vim+gcc.  What's right or wrong is different for different users.

---

### Post by Wybiral on 2008-01-30
Actually, you can't [COLOR="Red"]right[/COLOR] code at all. :)

But, you're [COLOR="Red"]write[/COLOR], the editor IS a personal choice, the compiler however is much different. GCC is almost exclusively used in Linux (and a number of other platforms as well). It doesn't matter how you edit your code... Use what you like.

To the OP:

C or C++, you have to pick one. They aren't the same.

---

### Post by RadiationHazard on 2008-01-30
thanks for all the help. and fighting entertainment.
:lolflag: can i get some links to some of these? or can i get them in synaptic or add/remove programs?
but yeah i'm just going to sit back and get some popcorn and continue to watch you guys fight this out til we get a winner. xD 
:popcorn:

---

### Post by LaRoza on 2008-01-30
> **emarkd said:**
> The OP asked for advice on good software for writing and compiling c/c++ in Ubuntu.  A correct answer could be and IDE like Anjuta or an editor/compiler pairing like vim+gcc.  What's right or wrong is different for different users.

I could have also said "Ubuntu" and be correct, as it does answer the question.

However, if someone with no experience in programming in Ubuntu asks for advice on C and C++ programming, the best answer isn't a glorified editor.

The wiki page I linked to has all the information that is need, and that wiki has pages for various editors and IDE's.

Also, this forum has stickies that address this issue, but since this post was in the ABT, I didn't immediately refer to them until after this thread was moved.

The sticky for New Programmers in Linux specificaly address the IDE preferences and the compiler question. 

There is not much more to say that hasn't been said many times.

---

### Post by RadiationHazard on 2008-01-30
and i know they aren't the same.
haha i'm going to learn both. i tried starting with java. only understood alittle of it. so i'm going to start with c then go to c++ then java

---

### Post by LaRoza on 2008-01-30
> **RadiationHazard said:**
> thanks for all the help. and fighting entertainment.
can i get some links to some of these? or can i get them in synaptic or add/remove programs?
but yeah i'm just going to sit back and get some popcorn and continue to watch you guys fight this out til we get a winner. xD 
:popcorn:

If it weren't for the misinformation, it wouldn't have happened :)

See the stickies (as I stated) and see the wiki for programming in Ubuntu. That wiki isn't very complete yet though, but has enough to get you started.

You can add them in Synaptic and Add/Remove, however, don't restrict yourself to an IDE.

Personally, I use Gedit and the terminal plugin for C programs.

(As for winners, it would most likely be me, but that would be an abuse of my responsibility)

---

### Post by igknighted on 2008-01-30
If you are just learning, I would VERY strongly recommend starting with a simple editor (gedit or scite on gnome/xfce, or kate if you use KDE) and compiling via gcc/g++ in the terminal.  If you've been programming for a while, feel free to check out the IDE's like anjuta and others.  I think Eclipse also can handle c/c++ and would be an excellent choice as well.

If you really want to get into the text editors, try to learn vi.  It's counter intuitive at first and you will despise it, and probably not even be able to type "hello, world" in it... but once you learn it, it's awesome and has features that you had never dreamed of that you will wonder how you lived without.

> **RadiationHazard said:**
> and i know they aren't the same.
haha i'm going to learn both. i tried starting with java. only understood alittle of it. so i'm going to start with c then go to c++ then java

Just so you know, high level languages like Java, C# and Python are usually much easier to learn.  Then once you understand the concepts you can move on to a language like C or C++ that requires a much higher attention to detail.

---

### Post by Wybiral on 2008-01-30
> **LaRoza said:**
> (As for winners, it would most likely be me, but that would be an abuse of my responsibility)

You love rubbing that in, don't you :)

---

### Post by emarkd on 2008-01-30
What wouldn't have happened?  Anjuta is in the repos and you can install it with Synaptic.

I just felt that a newbie to Linux would be more comfortable with an IDE.  Most progammer who come from Windows are used to Visual Studio, after all.

And I noticed you changed your original post to make it sound less elitist ... Thanks, I guess)

---

### Post by jcwmoore on 2008-01-30
> i'm just going to sit back and get some popcorn and continue to watch you guys fight this out til we get a winner. xD

:lolflag: That's right... so for kicks and grins i'm going to put it out there....


Visual Studio is the BEST IDE/Compiler out there.... after all I use it at work, it must be....


:popcorn:

---

### Post by LaRoza on 2008-01-30
> **Wybiral said:**
> You love rubbing that in, don't you :)

Love it? No. I find responsibility to be a most serious thing.

However, I might as well have a laugh now and then, but that doesn't mean I *enjoy* it.

---

### Post by Erikina on 2008-01-30
> **LaRoza said:**
> If it weren't for the misinformation, it wouldn't have happened :)

Don't be too harsh. Yeah, they did make a mistake. Yet their information would still be useful (a new programmer, wouldn't be ill advised to try a nice editor like Geany or w/e was recommended).

Oh yeah, before you critise people get your facts straight.

[QUOTE=LaRoza]As long as we are discussing it, g++ isn't actually a compiler. gcc is used.[/QUOTE]

G++ is in the "GNU Compiler Collection", however it's a compiler (in a collection). Saying it's not a compiler is patently wrong.

Try be a bit more forgiving, and assume good faith.

:)

---

### Post by Sockerdrickan on 2008-01-30
I'd recommend Gedit and G++ for this guy.

---

### Post by RadiationHazard on 2008-01-30
> **Erikina said:**
> 
Try be a bit more forgiving, and assume good faith.

:)

i agree!
can't we all just get along?? :)

---

### Post by LaRoza on 2008-01-30
> **Erikina said:**
> Don't be too harsh. Yeah, they did make a mistake. Yet their information would still be useful (a new programmer, wouldn't be ill advised to try a nice editor like Geany or w/e was recommended).

Oh yeah, before you critise people get your facts straight.

G++ is in the "GNU Compiler Collection", however it's a compiler (in a collection). Saying it's not a compiler is patently wrong.

Try be a bit more forgiving, and assume good faith.

:)

If something is not right, it is misinformation. I have never gotten a sensitive error message during programming.

> 
Error on line 17: Missing ;, but don't feel bad, everyone misses a semicolon.


Well, perhaps I should have said the command wasn't a compiler, as you can use the command "gcc" to compile C++ programs with the appropriate options.

---

### Post by vishzilla on 2008-01-30
> **Tux0r said:**
> I'd recommend Gedit and G++ for this guy.

hmm...yes for beginners this is recommended....but an IDE is always better and faster.

---

### Post by LaRoza on 2008-01-30
> **vishzilla said:**
> hmm...yes for beginners this is recommended....but an IDE is always better and faster.

I never heard any of the programmers on this forum recommend this before for anyone.

---

### Post by Sockerdrickan on 2008-01-30
> **vishzilla said:**
> hmm...yes for beginners this is recommended....but an IDE is always better and faster.

If you mean better as in faster I hope you mean code input, right? I happen to like Gedit, it's clean and simple and it works great even for larger projects. :KS

---

### Post by amingv on 2008-01-30
Why break your head guessing what language to learn when you can break your head thinking what IDE/editor to use...:)

I do reccomend gcc/g++ + text editor suited for programming because you will learn the stuff your IDE does in the background.

---

### Post by RadiationHazard on 2008-01-30
omg!!
as entertaining as this is can we all come together on the programs i need for writing and compiling c i'll figure out one for c++ later. or maybe we could just get some that do both? that'd be nice? :)

---

### Post by LaRoza on 2008-01-30
> **RadiationHazard said:**
> omg!!
as entertaining as this is can we all come together on the programs i need for writing and compiling c i'll figure out one for c++ later. or maybe we could just get some that do both? that'd be nice? :)

Read the stickies and make up your own mind.

---

### Post by emarkd on 2008-01-30
Honestly, that's probably the best advice you've gotten yet.  There are lots of choices and ways to go about this.  You've got to experiment and find what works for you.

---

### Post by LaRoza on 2008-01-30
> **emarkd said:**
> Honestly, that's probably the best advice you've gotten yet.  There are lots of choices ways to go about this.  You've got to experiment and find what works for you.

I said it on the first page...

(This thread is weird because it started in the ABT and was moved. I also happen to be distracted with a few things, so no offense was meant at any time)

---

### Post by Erikina on 2008-01-30
RadiationHazard. I'll try clear this up for you.

A compiler is a program, that turns your source file (i.e. human readable computer commands) into computer readable commands (binary).

However typing statements, is a bit boring to most programmers:

if(variable == 3)
{
   dothis();
}

verse:

[PHP]
if(variable == 3)
{
   dothis();
}[/PHP]

Looks nicer, eh?


It starts to look boring. And often the computer can give you "hints" on what to type (and tell you about your mistakes). For this advanced functionality. People use editors. (such as all the ones recommended.)

They just make your job nicer (i.e. pretty colors) and stuff. But in the end, it makes the same source (commands) as all other editors. So it's just personal preference.

To be honest, I wouldn't really worry about it much. Just get something that has syntax highlight (pretty colors) and indenting. Then worry about it later when you're a programmer. :D

(BTW, after you learn some C++ take a look at the Qt toolkit. It'll make programming fun! As you'll be able to do stuff other than console windows!)

---

### Post by LaRoza on 2008-01-30
If you are new to programming in general, most people on this forum recommend another language.

I suggest you browse the Learn to Program link in my sig.

---

### Post by RadiationHazard on 2008-01-30
i think i'm going to go with gedit and g++ first. alot of people seem to be recomending those. sorry if that's not what you recomended. know i still love all you guys equally :D haha and i'll no doubt be needing al you guys help again so i'm going to close this post.

thanks for everyone on this sites help. haha and i'm usually not one to get serious but really. thanks for you guys help. you are one of the few sites that actually helps. and helps fast. i would recommend this site to anyone!!


much love from your little n00b! :KS

ps. i'm not new to programing. i'm not good at it yet. but i'm not to bad. i'm just new to ubuntu and all it's glory. hahaha

---

### Post by Sockerdrickan on 2008-01-30
> **RadiationHazard said:**
> i think i'm going to go with gedit and g++ first. alot of people seem to be recomending those. sorry if that's not what you recomended. know i still love all you guys equally :D haha and i'll no doubt be needing al you guys help again so i'm going to close this post.

thanks for everyone on this sites help. haha and i'm usually not one to get serious but really. thanks for you guys help. you are one of the few sites that actually helps. and helps fast. i would recommend this site to anyone!!


much love from your little n00b! :KS

ps. i'm not new to programing. i'm not good at it yet. but i'm not to bad. i'm just new to ubuntu and all it's glory. hahaha

:guitar: See you around!

---

### Post by Erikina on 2008-01-30
Good choice! I think you're going in a really good direction.

Also, I recommend you get a good book on the subject. Learning from the internet is too tedious, and disjointed. The library is a good place.

Oh, and yes. C++ is more complicated than other languages. But it's a real language. You can do everything in it. I say it'll take about 3 weeks to get a grip on it. (and when you think about it. It's not that bad).

So yeah, it is complex. But you can do it. In the period of a month, I taught my 13 year old (half) sister how to program. She has an intuitive grasp of pointers (even pointers to pointers). And has no problems with classes. (I'm just now teaching her STL and Qt toolkit). So it's not too hard. Just takes perseverance. But you're going in the right direction!

Good luck. I hope you don't give up.

---

