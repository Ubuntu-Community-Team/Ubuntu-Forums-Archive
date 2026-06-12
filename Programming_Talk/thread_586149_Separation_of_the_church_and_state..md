---
title: "Separation of the church and state."
date: 2007-10-22
forum: Programming Talk
---

### Post by slavik on 2007-10-22
This is intented to be sort of the Cathedral and the Bazaar type post.

State - The core program/utility
Church - The interface (GUI, curses, etc.)

Have you wondered why just about every project aims to create a library and a program based on that library? (Pidgin and GNOME come to mind) The reason is simple. You don't need the Church to make use of the State, but you need the State for the Church to be of any use.

This also allows you to have code that can be surrounded not by your fancy OpenGL interface (like Compiz for example) but also by something simple like Fluxbox.

If anyone can create an interface for your program, then your program becomes useful in another way ... the batch way.

Please make sure to have sane defaults for just about every option you ask for. you don't need to tell gcc where the libraries are, or where to save the output, or even how to compile for a simple fact of having the defaults for things you can assume. If you look at the make utility, it doesn't even ask for an input makefile (which defaults to Makefile).

There are some people guilty of having a rule by church and I am sure they know who they are (I have told you this already).

---

### Post by Lux Perpetua on 2007-10-22
I agree strongly with your main points, at least what I understood of them: 

- functionality should not be tied to a particular visual interface
- options should have intuitive and sane defaults

However, I do not understand your use of the church/state metaphor.

---

### Post by hecato on 2007-10-22
hehe, with this you can argue lot, but in fact you need to change lot of things. Church state? I can say that they are good apart from each other... and in most the best.

"it doesn't even ask for an input makefile (which defaults to Makefile)", but you need to know that you need to write a Makefile, and you need to know how to write rules and "all that". Like you see the interface, what make the program more usefull or behaves diferent is interaction... even if this interaction come from mouse, kb, internet, a flow of instructions inside a file (like the Makefile, or a *.cpp file... yes it ask to #include, #define #if and modify at run the behaviour).


It is something like the MVC you are talking (or at less I), but it is more far than that "simple thing", Im saying that controllers can be human or other or a combination



some.cpp

```
int main(){
#ifdef ALGO
 return 0;
#else
 return 1:
#endif
}
```
```
gcc some.cpp
```
```
gcc -DSOME some.cpp
```


Even the environment is part of that interaction, you know always is a env variable that hasd some extra info for the programm, the presence of run the a programm in a terminal can cause it output some extra info there.


**Interaction** is not only about "presentation", but with who you can interact ;) ;). I have think long for this, but all that are not complete that, and for the momment I only share that.

---

### Post by pmasiar on 2007-10-22
> **Lux Perpetua said:**
>  I do not understand your use of the church/state metaphor.

In some countries, separation between church and state is guaranteed by constitution. IIUC slavik would like us always to remember they ARE separate.

---

### Post by LaRoza on 2007-10-22
> **pmasiar said:**
> In some countries, separation between church and state is guaranteed by constitution. IIUC slavik would like us always to remember they ARE separate.

Not is the U.S.A.

Read the Constitution and you'll find no such statement, only the "Establishment Clause" and the "Free Exercise Clause".

The Separation of Church and State is a result of the Strict Separation Interpretation, others are the Neutrality Interpretation and the Accomodation Interpretation.

---

### Post by pmasiar on 2007-10-22
I stay corrected. Not that I care, or it could change anything :-)

Because in fact, in politics they are pretty much inseparably joined, for better or, more probaly, worse. :-/

---

### Post by LaRoza on 2007-10-22
> **pmasiar said:**
> I stay corrected. Not that I care, or it could change anything :-)


I took a class on Constitutional Law, for my degree in Criminal Justice, I had to do several case briefs on such issues.

You don't really stand corrected, because you didn't say it was the USA, just many countries. China, for one, has a pretty strong separation of church and state, or, perhaps a complete fusion, the state is the church.

---

### Post by Wybiral on 2007-10-22
> **LaRoza said:**
> Not is the U.S.A.

Read the Constitution and you'll find no such statement, only the "Establishment Clause" and the "Free Exercise Clause".

The Separation of Church and State is a result of the Strict Separation Interpretation, others are the Neutrality Interpretation and the Accomodation Interpretation.

I'm confused. The very first amendment says:

> 
12/15/1791:
Congress shall make no law respecting an establishment of religion, or prohibiting the free exercise thereof; or abridging the freedom of speech, or of the press; or the right of the people peaceably to assemble, and to petition the Government for a redress of grievances.


Which sounds to me like government isn't allowed to encourage or discourage any religious establishment. Even if it doesn't state a definite separation, it at least states that there be no governmental bias (which sounds close enough to me).

Then again, history suggests to me that the laws in the US don't really matter (whatever the court says goes).

---

### Post by LaRoza on 2007-10-22
> **Wybiral said:**
> 
> 
Congress [color=Red]shall make no law respecting an establishment of religion[/color], or [color=Purple]prohibiting the free exercise thereof[/color]; or abridging the freedom of speech, or of the press; or the right of the people peaceably to assemble, and to petition the Government for a redress of grievances.

Which sounds to me like government isn't allowed to encourage or discourage any religious establishment. Even if it doesn't state a definite separation, it at least states that there be no governmental bias (which sounds close enough to me).


[color=Red]That is the Establishment Clause. It prohibits the state from enacting a state religion. So the governement can not have an "official" religion, like England (at the time).[/color]

[color=Purple]That is the Free Exercise Clause. It prohibits the state from interfering with the free exercise of religion. The government can restrict activities though, if there is a compelling governmental interest.[/color]

The three theories:

_Strict Separation_: This holds that the state and religion can **never** mix. This is a very unrealistic standard, as it would in theory, ban the use of moral values in decision making. In strict separation, a judge following this view, would take issue with the slightest display of religion on state property.

_Neutrality_: This view desires to keep the goverment neutral on religious issues. It acknowledges religion, but will frown on a clear religious preference, so a Christmas display with secular, Jewish, and Christian is allowed on state property.

_Accomodation_: This theory acknowledges the importance of religion in the citizen's lives, and will accomodate the display of religious symbols for a group, if they want it, as long as it doesn't discriminate.

The two clauses, highlighted above, can conflict. The government can't "fund" religion, but can't impede it either, so how is a Muslim, et al, going to get religious services on an aircraft carrier if the carrier is in the middle of the ocean for nine months?

All of my facts and examples are from real US Supreme Court cases, but I doubt you want the citations.

-EDIT Is this thread of topic? Discussing Constitutional Law in a Programming Forum? Only here...

---

### Post by slavik on 2007-10-22
> **hecato said:**
> hehe, with this you can argue lot, but in fact you need to change lot of things. Church state? I can say that they are good apart from each other... and in most the best.

"it doesn't even ask for an input makefile (which defaults to Makefile)", but you need to know that you need to write a Makefile, and you need to know how to write rules and "all that". Like you see the interface, what make the program more usefull or behaves diferent is interaction... even if this interaction come from mouse, kb, internet, a flow of instructions inside a file (like the Makefile, or a *.cpp file... yes it ask to #include, #define #if and modify at run the behaviour).


It is something like the MVC you are talking (or at less I), but it is more far than that "simple thing", Im saying that controllers can be human or other or a combination



some.cpp

```
int main(){
#ifdef ALGO
 return 0;
#else
 return 1:
#endif
}
```
```
gcc some.cpp
```
```
gcc -DSOME some.cpp
```


Even the environment is part of that interaction, you know always is a env variable that hasd some extra info for the programm, the presence of run the a programm in a terminal can cause it output some extra info there.


**Interaction** is not only about "presentation", but with who you can interact ;) ;). I have think long for this, but all that are not complete that, and for the momment I only share that.
but are you required to set that define flag in a single way? Is setting the define flag tied to the user interface of gcc or to the core of gcc?

think about an IDE that is build that uses gcc. Now think if the gcc code and the IDE code were in the same source files.

Compare how you would make a game on top of the Unreal engine or the Quake3 engine.

---

### Post by aks44 on 2007-10-23
> **LaRoza said:**
> _Strict Separation_: This holds that the state and religion can **never** mix. This is a very unrealistic standard, as it would in theory, ban the use of moral values in decision making.

Yeah, of course, it's well a known fact that morality is exclusive to religion... </sarcasm>



Anyway the whole metaphor is interesting... the state doesn't need the church to work correctly (and it indeed is less messy that way) ; the church often tends to be a state of its own (which leads to crappy, unmaintenable code) ; any sane design should enforce strict separation.

At least the software world understood it (even if it's not strictly applied)...
Now let's wait for the real world to catch up... :p

---

### Post by LaRoza on 2007-10-23
> **aks44 said:**
> Yeah, of course, it's well a known fact that morality is exclusive to religion... </sarcasm>


I am having a PM discussion with a poster here in furtherance of this topic.

I defined religion as the beliefs which actually guide a persons actions, not a traditional definition of an organized system.

That is in line with your, seemingly, view, that morality is what counts, not the professed (if any) religious affiliations.

---

### Post by hecato on 2007-10-23
> **slavik said:**
> but are you required to set that define flag in a single way? Is setting the define flag tied to the user interface of gcc or to the core of gcc?

think about an IDE that is build that uses gcc. Now think if the gcc code and the IDE code were in the same source files.

Compare how you would make a game on top of the Unreal engine or the Quake3 engine.


It is tied to bot, to the user interface (controlled in this case by command line and the source itself), and the core. Also sometimes can be external like in the environment.

What you are talking is more specialized than general (like C is so general not only for write something only for x or y thing).


Thought yes, will be enough for you like programmer to say what you wana (like specialize the environment for your actual work, even that the environment is generic, but you fail again that you need first specialize or say what you want), and the environment and language take care of other things when necessary (like the DEF).

The point is that if you have a "black box", you need some way to interact with it, a perfect design of a black box, will hide all inside, but if you have no way to interact, you will see that it doesnt work.

Is somewhat difficult to really separate that, or there is no way if you only have a 2 blackboxes that no communicate each other, 1 for the core the other for user or source interaction. The best, is to find the proper way.

Returning to your unreal script example (don't know if continue calling itself that way), thought yes, you don't need to say wich libraries or compiler flags, etc. But that part of interaction is glued with the core doing it now more specialized. Like you see, the "thing" is present there, doesnt matter that itself present to you like a:[LIST]
[*]option button
[*]Define flag in command invocation or inside a .c file
[*]in a more specialized environment[/LIST]The point is that is necessary.

---

### Post by Wybiral on 2007-10-23
> **hecato said:**
>  ... 

Obviously the "blackbox" has to have sufficient accessibility, but as a general design rule this kind of abstraction and encapsulation is a good thing. For purposes of testing, freedom (later it's easier to change the GUI or make it a command line program if you design the "state" first), and general organization... Why would GUI related objects be anywhere near the core of the program in the first place?

---

### Post by hecato on 2007-10-23
Im not talking of "black box" in the sense of OO... Im talking of interaction (and necessity of presence and can be present in different forms: buttons, comand line or inside the source code, inside the source of any interaction, or in more specialization of the app)... I don't see where I refer to OO concepts. And also Im not talking only of GUI, Im talking of interfaces.


> Why would GUI related objects be anywhere near the core of the program in the first place?But, answering your question. They all are relate... the mean that you write them separately, doesnt mean that they are not related in some way. For example, you have 2 different apps for database access in MVC, and assume that you can compile/run each one apart of the others, some like M1V1C1 and M2V2C2, obviously if you mix them: M1C2V1, or M1C1V2, your app will not work even tha each "module" not depend on the others (and like the assumption compiled and runed), because the system relate to itself. Separation of concepts or code doesn't mean separation of the self semantics ;) that are widespread all the self.

---

### Post by Wybiral on 2007-10-23
> **hecato said:**
> Im not talking of "black box" in the sense of OO

I'm not necessarily talking about OO either, I'm talking about modularity.

> **hecato said:**
> Im talking of interaction (and necessity of presence and can be present in different forms: buttons, comand line or inside the source code, inside the source of any interaction, or in more specialization of the app)

The interface AND the source code can and should remain as modular as possible. You write the necessary means of communication into them, but each object is responsible for its own interface with its neighboring objects.


> **hecato said:**
> Separation of concepts or code doesn't mean separation of the self semantics ;) that are widespread all the self.

I don't get what you're saying here. There is no reason two objects communicating and using each-other should have to be connected in any way. They just need an adequate means of communicating.

Are you suggesting that code should just be one big blob because all the parts depend on each other? Why bother writing functions if they're just going to be called and returned from? Why bother with classes since the data needs shared with other parts of the code? In fact, why not write your entire application in one file since it's all going to be compiled anyway?

Trust me, modularity is a good thing.

---

### Post by hecato on 2007-10-23
You seem to don't understand what I express or why I express it.

You say that you don't express OO, but I see the term "object".

MVC is like a divide and conquer _strategy_ or a patter if you want, you can divide things, work in them separately, you know, but at the end all of them relate. Like I have explained, you can have 2 different MVC, but you can't mix them, even that each app is perfect about the implementation of the MVC, because at the end they are all relate to itself, each ***subunit*** M, V or C have no real usage if they are not used in the whole they are about.

>  
[quote]Separation of concepts or code doesn't mean separation of the self semantics :wink: that are widespread all the self.I don't get what you're saying here. There is no reason two objects communicating and using each-other should have to be connected in any way. They just need an adequate means of communicating.
[/quote]There is certain contradiction there... if we (the ones writing this posts) where not connected (in some "estrange way" aka web), thus we can't communicate each other our points of views, even that you and I have our own arguments about this subject ;).

Yes, for communicate you need some type of connection. Personally I have never seen in nature or other place a way of communication that doesn't have a connection somewhere. "adequate means of communicating" and that adequate means of communicating is where coupling enter.

About my statement that you don't get "Separation of concepts or code doesn't mean separation of the self semantics :wink: that are widespread all the self.", mean that you can have a divide and conquer strategy (like the quoted MVC) or others, but the fact is that it is a whole or a unit (that you divide for have best handling of  certain things and promote others like coupling, modularization, etc), and yes the whole can be in parts, but parts have no sense without the whole.

> 
Are you suggesting that code should just be one big blob because all the parts depend on each other? Why bother writing functions if they're just going to be called and returned from? Why bother with classes since the data needs shared with other parts of the code? In fact, why not write your entire application in one file since it's all going to be compiled anyway?
No, you are thinking that. I not. I also see again OO terms there (thougth now Im using them because you introduce them). In some way compilers do that "write your entire application in one file since it's all going to be compiled" and also the executable or the memory containing the app runtime do that.

>  Trust me, modularity is a good thing.I don't need to trust you in that respect. I know it before hand. But like I see not the starter of this thread, not me are talking about modularity ;).

You need to read and skip all the religious post about religion and state (and late morality) in not programming way and read the other post.

Then of what we are talking you will arguee?? some hints???[LIST]
[*] Have you wondered why just about every project aims to create a library and a program based on that library?
[*]you don't need to tell gcc where the libraries are, or where to save the output, or even how to compile for a simple fact of having the defaults for things you can assume.
[*]"it doesn't even ask for an input makefile (which defaults to Makefile)", but you need to know that you need to write a Makefile, and you need to know how to write rules and "all that". Like you see the interface, what make the program more usefull or behaves different is interaction... even if this interaction come from mouse, kb, internet, a flow of instructions inside a file (like the Makefile, or a *.cpp file... yes it ask to #include, #define #if and modify at run the behaviour).
[*] **Interaction** is not only about "presentation", but with who you can interact :wink: :wink:. I have think long for this, but all that are not complete that, and for the momment I only share that.
[*]but are you required to set that define flag in a single way? Is setting the define flag tied to the user interface of gcc or to the core of gcc?
[*] think about an IDE that is build that uses gcc. Now think if the gcc code and the IDE code were in the same source files. [COLOR=Red][perhaps the expression of the "same source files" is incorrect from the point of view of Wybiral about " Are you suggesting that code should just be one big blob"[/COLOR][COLOR=Red], thus I must say how I read it, "why if the IDE and GCC where a unit and not separate projects", I only remember [http://fresh.flatassembler.net/](http://fresh.flatassembler.net/) trying to do some like that][/COLOR]
[*]Compare how you would make a game on top of the Unreal engine or the Quake3 engine.[/LIST]Blame me for introduce the example of the MVC, but like I wrote when I introduced it, I guess what we are talking is more far than "that simple concept".


I will also like to answer second time "Is setting the define flag tied to the user interface of gcc or to the core of gcc?", Is tied to the whole, it has different representations at different levels, an option in command line, a #ifdef or #define in code, a token in the syntax tree when processing (thus in the core of GCC), thougt there is separation (I have readed some of that code, and know it has modularization in it) with 1. command line, 2. user code (source code), 3 internal manipulations of sintaxis trees (AST, etc) they all have or "know" the define (in some way or the other), because what drive GCC is the concept of programming language C (this is the whole semantic for this programm to be implemented and used). And thus you can see more clearly what I call "self semantics :wink: that are widespread all the self". If you specialize something (like the UT3 editor that let you write some wepons mods, new characters, AI and related things IIRC), thus you have 2 options, or provide specialized tools, or the general thing have specialization options (in any case, you only move the button, define, or more generally interaction to other place,  there is no way to get right of it, it will be present in some way or other at different levels in different presentations ;)).

---

### Post by slavik on 2007-10-23
I implement a list.

You use the list library.

You decide that it can be better suited for you if you manage the pointers within my list on your own.

I make a new version of the list.

Your code breaks when the new list is being used.

You should not rely on the internal behavior of whatever you are using. So when you are creating a graphical interface for ls and cd, you should not do the system calls that ls and cd do. Instead, you want to separate ls and cd into a separate piece of code (shared object) and use calls provided by that shared object.


EDIT:
For example. In the C library, we have fopen. fopen, depending on the system (Linux vs. Windows) puts different things in different registers and calls a different interrupt. You should have that code (register/interrupt stuff) in your code that opens a file. that is why fopen is a part of the standard library, because it is predictable on any system (fopen returns errors the same way on Linux and Windows, whereas the specific system call that is done in assembly might not). fopen parses "Error 10: permission denied" and "Error 234: Insufficient Permision" into the same error code.

---

### Post by hecato on 2007-10-23
But I still think you are talking of 1 thing, we about another.

We have not write about depend of not in internal behaviour of other things. And that is what the first 5 lines (or paragraphs are about).

The next paragraph is a little more related with the subject, but it also rely (or has its base) on dependence of internal behaviours.

---

### Post by Wybiral on 2007-10-24
> **hecato said:**
> You seem to don't understand what I express or why I express it.

You say that you don't express OO, but I see the term "object".

I mean object as an entity/module/"blackbox". Not strictly as an OO object (though that would certainly fall into the category). Unfortunately I am having trouble grasping what you're saying, I'm guessing you don't natively speak English (in which case I will try a bit harder to fully understand before responding).

> **hecato said:**
> There is certain contradiction there... if we (the ones writing this posts) where not connected (in some "estrange way" aka web), thus we can't communicate each other our points of views, even that you and I have our own arguments about this subject ;).

Yes, for communicate you need some type of connection. Personally I have never seen in nature or other place a way of communication that doesn't have a connection somewhere. "adequate means of communicating" and that adequate means of communicating is where coupling enter.


No, we can communicate because we have adequate interfaces for communication. I have fingers which can communicate with my computer, which can communicate with the internet, which sends the signal to you. Notice how I wasn't born with a hard-coded interface with you? I have a generic interface that allows me to communicate with a variety of objects (once again, I don't just mean OO). Likewise the makers of my computer didn't put a hard-wired connection to the internet, they just put an Ethernet port (an adequate interface for my computer to communicate with the web).

> **hecato said:**
> I see not the starter of this thread, not me are talking about modularity ;).

You need to read and skip all the religious post about religion and state (and late morality) in not programming way and read the other post.


I've read, but it looks to me like you are arguing against separating implementation from interface. A modular design pattern would do the exact opposite.

> **hecato said:**
> We have not write about depend of not in internal behaviour of other things. And that is what the first 5 lines (or paragraphs are about).

The next paragraph is a little more related with the subject, but it also rely (or has its base) on dependence of internal behaviours.

That's the reason you separate implementation from interface and modularize your code. Because it abstracts away the implementation so that the user doesn't have to deal with it (and hopefully encapsulates it enough so that the user can use it properly). And no, I don't strictly use those words to describe OO, it applies to any modularized design.

---

### Post by hecato on 2007-10-24
> 
I mean object as an entity/module/"blackbox". Not strictly as an OO object (though that would certainly fall into the category). Unfortunately I am having trouble grasping what you're saying, I'm guessing you don't natively speak English (in which case I will try a bit harder to fully understand before responding).
ya, Im natal from other place, my real learning and practice of this lang as been on the web not at school (I was bad there). Also for some little knowledge perhaps I write to much to say to little. And sometimes even in my natal language take more time to translate my thoughts to others, so don't surprise that is hard to understand me.

Also I think the concepts that we are trying to get, are not "standard" ones, in other words, we have no source code for show our points (at less like I get it and Im triying to write). I mean they look like interfaces, MVC, etc, but from what I see is not exactly that.

> 
No, we can communicate because we have adequate interfaces for communication. I have fingers which can communicate with my computer, which can communicate with the internet, which sends the signal to you. Notice how I wasn't born with a hard-coded interface with you? I have a generic interface that allows me to communicate with a variety of objects (once again, I don't just mean OO). Likewise the makers of my computer didn't put a hard-wired connection to the internet, they just put an Ethernet port (an adequate interface for my computer to communicate with the web).
 I still see the connection ;) not only the interfaces ;). See this part "we have adequate interfaces for communication" thought I'm sure you used "for" implicating the direct usage of the interface for communicate, I think that the "for" implicate the purpose of communication using interfaces. I mean "I have fingers which can communicate with my computer", in fact your kb is the interface to the computer and your fingers are adequate for that interface (if you use you leg it will be hard), but for this 2 interfaces to do something, in some moment need to connect (communicate), is that moment where you hit a key and is pressed that exist the connection and thus the communication ;). Yes they are adequate to each other, only because the kb was designed for be a human interface to the computer. By fact monkeys have also... fingers, but that interface doesn't have real usage because they don't have our brain, thus matching of similar interfaces doesn't mean have real usage. Monkeys at some extend can also use the kb  (also perhaps programs will not be able to do something of significance with the input... example a GIMP program where you need to open a new page and start using the "tools" and then hit save, but for the computer and kb it will not be difference between hits of a monkey and I).

> 
but it looks to me like you are arguing against separating implementation from interface. A modular design pattern would do the exact opposite.

..
That's the reason you separate implementation from interface and modularize your code. Because it abstracts away the implementation so that the user doesn't have to deal with it
Sure I think we are arguing (not exactly about what you write), if you see carefully what I have wrote and the other guy (the starter of the thread), you will see clearly that we have not named the "thing" ;) because or at less for me have no name (for the momment),  because like I understand the first post, was about something that has no name, we to the momment have used examples. Yes, in some sense it can be confused with modularity, blackboxes, but personally I think this is not the case of the first post, and my post (except those related to answer about the misconception over our arguing without name ;)).

---

