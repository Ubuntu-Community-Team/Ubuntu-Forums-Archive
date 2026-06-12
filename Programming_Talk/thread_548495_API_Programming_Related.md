---
title: "API Programming Related"
date: 2007-09-11
forum: Programming Talk
---

### Post by jenson on 2007-09-11
Hi Guys,

Recently I head something about API programming is the way to get better in programming and I have long wanted to know how can I get started.

I wish to know where can start from, which language to start off with, and what are the resources available for my learning?

Is there any requirement to be good at it? How can I improve from there? And how can I contribute back?

I think my questions are not deep in depth enough, but well, at least will get me started and fire off better questions from there :)

Thanks guys!

Regards,
Jenson

---

### Post by CptPicard on 2007-09-11
Umm.. you do understand that the API is a fairly general concept that you can apply to anything that presents an *Application Programming Interface* to the outside world? Like, a library?

Actually, you have to make sort of API design-related decisions in all software design, when you design the way you lay out your code even inside your own project.

You just pick any language you like and implement some functionality for other people's code to call. That's all there is to it. Try to make your library's interface as clean, logical and convenient as possible, and you get a good API...

Generally, you become a good API designer by being a good programmer, so you know what works and what doesn't, and also know your language well enough that you're able to make most of the language's features...

EDIT: for advancing your API design skills, the specific language really is sort of irrelevant, but you do want to evolve your software design skills in general -- those that are not linked to any language in particular. Learn [software design patterns]("http://en.wikipedia.org/wiki/Design_pattern_%28computer_science%29"), for example, so you know solutions to common problems, and your users who are hopefully aware of these patterns too, get the hang of the way you solved these problems much faster...

---

### Post by pmasiar on 2007-09-11
When you design a module you call from other module, you designed API. So it is not rocket science to do it - IIUC your question is how to do it **right**.

Gurus say that [http://en.wikipedia.org/wiki/Test-driven_development](http://en.wikipedia.org/wiki/Test-driven_development) is excellent way to design your code so it is: 
- callable and usable in small snippets
- testable

Of course TTD is big change, and it will be not easy to make the switch, but everyone who made it, does not want to come back, I heard. 

As i remember your question from another thread, you are interesting in learning  better skills. You can do it in any language of course, most obvious choices would be:
- the language you use right now in work/study :-)
- the language you want to learn for the open-source project you are passionate about, and has enough code to learn from

---

### Post by jenson on 2007-09-11
So does it means as long as I'm writing a module or block of codes that is reusable across the program, it is considered as API programming? Or I have to create a library?

How do I go about writing a customized API library which can be made available to any future project that would make use of it?

Regards,
Jenson

---

### Post by CptPicard on 2007-09-11
> **jenson said:**
> So does it means as long as I'm writing a module or block of codes that is reusable across the program, it is considered as API programming? Or I have to create a library?

Essentially all programmatic objects can be, in some sense, considered to present an API to whatever code calls that object or entity. You have this somewhat strange notion that there is some separate realm of "API programming" out there. You do not "program an API", your programming "has" an API when it is used somehow from outside :)

Most of the time when you use the term you do talk about a library's "public face", though, as that's where the concept becomes significant... if the ways your library is used are really weird and cause programmers grief, then you certainly have failed in your API design, and should consider refactoring something in your library.

> How do I go about writing a customized API library which can be made available to any future project that would make use of it?

By writing it. Again, your terminology is strange. There is no such thing as an "API library". Your library has an API, which you hopefully design in a smart way and document sufficiently. The "API" is not the library, it's the architectural choices you choose and impose on your programmers... I mean... your Java SDK classes are not "the API", [this is the API]("http://java.sun.com/j2se/1.5.0/docs/api/") (of those SDK classes).

EDIT: Wikipedia has it put quite well... [http://en.wikipedia.org/wiki/API](http://en.wikipedia.org/wiki/API)

---

### Post by jenson on 2007-09-11
Ok, I think I "somehow" get what you are trying to say. Btw, for example, is writing my own class in Java considered API programming?Since I create my own variables, methods, and etc that is reusable and callable from other class.

Regards,
Jenson

---

### Post by pmasiar on 2007-09-12
Java calls those 'package' and packs them into jar.
> **jenson said:**
> How do I go about writing a customized API library which can be made available to any future project that would make use of it?


I cannot guarantee you will be able to reuse it later: "it is hard to predict, especially the future" :-)

But in the future you will try to reuse it, and you will find it is not exactly what you needed, and you refactor, and edit previous usage too. 

Read about good practices in programming, "Code Complete" and "Pragmatic Programmer", design patterns (Head Firts Design patterns" is good - and all other head-first books too, etc.

---

### Post by jenson on 2007-09-12
> **pmasiar said:**
> Java calls those 'package' and packs them into jar.


I cannot guarantee you will be able to reuse it later: "it is hard to predict, especially the future" :-)

But in the future you will try to reuse it, and you will find it is not exactly what you needed, and you refactor, and edit previous usage too. 

Read about good practices in programming, "Code Complete" and "Pragmatic Programmer", design patterns (Head Firts Design patterns" is good - and all other head-first books too, etc.

Alright, so Code Complet and Pragmatic Programmer are those books that are not inside Head First series?

And yeah, I heard about good comments and reviews on Head First series, which make me feel like want to get one or two Head First series that fit into my interest of Java programming. I've long forgotten how to code in Java properly now. I used to learn Java 1.1.3 before during college time, but now I can't, I think I really need some books to keep me going and learning bit by bit from there.

I find that involve in some projects is the best approach to master a language, like what you guys have mentioned earlier. I learned .NET programming by doing real life projects, but no choice, even though I don't really like, but my background make me have to survive with the dark side, which is M$. I've been a long-time .NET programmer as well as VB programmer for years and until recently just involved heavily in large scale projects and keep me busy. I'm now trying my very best to squeeze out some of my time to learn my own language as well as some language that would become a norm in the near future and sounds/seems interesting to me too.

I can't stop coding as my life has been so wonderful that I learned quite a lot of things from coding. But until recently I don't even know what a real API programming means, I think most likely due to the dark side training. But I seems to like open source programming better. Though it's relatively easier to code on Windows platform and with M$ IDE for their languages and all the software and technology available.

It's easy to achieve stuff but not so easy to stay competitive as there are simply too many companies doing windows, .NET programming and too many programmers doing it too. I want to try something new and different, and can keep myself entertained and my time well-spent =) And I like to contribute, open source seems like a way that I can contribute the most and most of the time ;)

I like Ubuntu, and I like open source!

Regards,
Jenson

---

### Post by CptPicard on 2007-09-12
> **jenson said:**
> Ok, I think I "somehow" get what you are trying to say. Btw, for example, is writing my own class in Java considered API programming?

Drop the whole idea of "API programming" -- it's not some special case of "programming"... it's more of a software design concept :) API is just the conventions and ways with which an outside user is expected to interact with a piece of code (if we stick to the more conventional idea of a "public" API which is directed at the outside user)

Think of the meaning of the word "interface". You design and define the API... and coding the library is the implementation of that API. Then, when documented, someone can *use* the knowledge of the API by using your code by interfacing to it according to the specifications of the API.

Sometimes the API doesn't contain all there is to what can be used from outside... there are often undocumented features, which you can think of as the private API if you like...

---

### Post by jenson on 2007-09-13
> **CptPicard said:**
> Drop the whole idea of "API programming" -- it's not some special case of "programming"... it's more of a software design concept :) API is just the conventions and ways with which an outside user is expected to interact with a piece of code (if we stick to the more conventional idea of a "public" API which is directed at the outside user)

Think of the meaning of the word "interface". You design and define the API... and coding the library is the implementation of that API. Then, when documented, someone can *use* the knowledge of the API by using your code by interfacing to it according to the specifications of the API.

Sometimes the API doesn't contain all there is to what can be used from outside... there are often undocumented features, which you can think of as the private API if you like...

Hmm, so it's a concept rather than a field of programming or ways to program? So it is actually learning how to design and write good reusable codes?

Regards,
Jenson

---

### Post by CptPicard on 2007-09-13
> **jenson said:**
> Hmm, so it's a concept rather than a field of programming or ways to program? So it is actually learning how to design and write good reusable codes?


First part is spot on, the latter... well... you can of course make godawful APIs if you're a bad designer... :)

The API is very much an abstract concept... think of it in terms of protocols and standards, which are close. APIs define similar contracts between two pieces of code, so that their interaction -- the "interface" -- is specified.

For example, if I were writing this humongous application I wanted outsiders to be able to extend, I would have to define the extension points ... to come up with some kind of a plugin architecture, for example. At this point I would have to start thinking of the API I am going to present to the plugin programmer... I am not going to give them access to the entire source and let them call whatever pieces they feel like... I am going to think hard about what kind of a sandbox the plugin is going to live in, and what kind of an official plugin interface I am going to publish for the other programmers' use. The contents of that plugin interface are the plugin API.

---

### Post by jenson on 2007-09-13
> **CptPicard said:**
> First part is spot on, the latter... well... you can of course make godawful APIs if you're a bad designer... :)

The API is very much an abstract concept... think of it in terms of protocols and standards, which are close. APIs define similar contracts between two pieces of code, so that their interaction -- the "interface" -- is specified.

For example, if I were writing this humongous application I wanted outsiders to be able to extend, I would have to define the extension points ... to come up with some kind of a plugin architecture, for example. At this point I would have to start thinking of the API I am going to present to the plugin programmer... I am not going to give them access to the entire source and let them call whatever pieces they feel like... I am going to think hard about what kind of a sandbox the plugin is going to live in, and what kind of an official plugin interface I am going to publish for the other programmers' use. The contents of that plugin interface are the plugin API.

Hmm..it is, indeed, quite abstract and not easy to understand, especially for a noob like me. Hmm, I think I would really need a source to read up and more and have some practice on hands to get myself more familiar, I think I have to grasp the concept well before I can come out with anything.

But I roughly get the idea, just to clarify, if I wrote a plugin API, I wrote the methods and functions, etc, like maybe to draw a circle, so i have drawCircle(int x, int y), and maybe getX () and geyY(), etc, and I only make this 3 available for people to use, but I kept my other methods/functions from being accessible from outside the "sandbox", maybe the getX() and getY() are internal procedures, but drawCircle() would be the one they can use to display the circle of their specified X and Y figures. Is this idea similar to what you are tying to say? Then I make this available as a plugin that allow people put draw a circle as if this is a complicated process which I made it into a plugin to implement it much easier in their program without the needs for them to code out with such "API"?

Btw, I have just added you in case I do need some helps in the future, if you don't mind? Would get a faster reply instead of waiting here for the reply. Except for some other discussions, that might be beneficial to allow other members to get involved ;)

Thanks.

Regards,
Jenson

---

### Post by CptPicard on 2007-09-13
> **jenson said:**
> Hmm..it is, indeed, quite abstract and not easy to understand, especially for a noob like me. Hmm, I think I would really need a source to read up and more and have some practice on hands to get myself more familiar, I think I have to grasp the concept well before I can come out with anything.

Seriously, you're just making it more difficult for yourself than it needs to be. :) My view would be that you just keep on coding instead of holding back until you feel like you've "got it"... you're creating API conventions as you go anyway as you design and modularize your code, and whether you feel you understand the concept 100% is not really relevant at this point. At some point it will just click, if it hasn't already :)


> But I roughly get the idea, just to clarify, if I wrote a plugin API, I wrote the methods and functions, etc, like maybe to draw a circle, so i have drawCircle(int x, int y), and maybe getX () and geyY(), etc, and I only make this 3 available for people to use, but I kept my other methods/functions from being accessible from outside the "sandbox", maybe the getX() and getY() are internal procedures, but drawCircle() would be the one they can use to display the circle of their specified X and Y figures. Is this idea similar to what you are tying to say?

Yeah, that's it. Let's assume for the sake of stupid argument that you're writing a library that draws graphics on a display device, and that for some reason you don't want your users to draw whatever stuff on the screen. We can also assume that drawing individual pixels is somewhat really esoteric and all that.. you just design your API so that it exposes higher-level graphics primitive drawing functions for your users to make use of. The set of the definitions of those functions and their parameters, return types etc comprise the public API of your library. You also need to add to this the semantic knowledge that is not part of syntax; for example, if some of your function calls have side-effects on their parameters, for example, or if there is internal state the user of your library needs to be aware of (like, again for stupid argument, you can't draw a circle after a polygon for some internal implementation reason..)

For a real world example, check out the data structure framework of Java's API, or for something even more "over-engineered", the classes that abstract multithreading concepts. They are pretty good examples of API design. I like the former, the latter feels contrived and some of the conventions used are just simply wrong in a lot of everyday scenarios and force me, as a programmer, to actually work around them to get Java's multithreading work the way I would intuitively expect it to, but hey, I didn't design the API... got to live with what they give me.

> Btw, I have just added you in case I do need some helps in the future, if you don't mind?

Sure, no problem...

EDIT: Hmm... let's describe this in really simple terms without all the hand-waving. Suppose we're coding the same application. I want you to provide some piece of the application for me. Therefore, so that my code is able to make use of your code, we need to agree what your code is going to look like and how it behaves when I'm using it. We need to agree upon an API, and whenever you start explaining to me how you expect your code to be used by me, you're explaining the API to me. Capiche? ;)

---

### Post by jenson on 2007-09-14
> **CptPicard said:**
> Seriously, you're just making it more difficult for yourself than it needs to be. :) My view would be that you just keep on coding instead of holding back until you feel like you've "got it"... you're creating API conventions as you go anyway as you design and modularize your code, and whether you feel you understand the concept 100% is not really relevant at this point. At some point it will just click, if it hasn't already :)




Yeah, that's it. Let's assume for the sake of stupid argument that you're writing a library that draws graphics on a display device, and that for some reason you don't want your users to draw whatever stuff on the screen. We can also assume that drawing individual pixels is somewhat really esoteric and all that.. you just design your API so that it exposes higher-level graphics primitive drawing functions for your users to make use of. The set of the definitions of those functions and their parameters, return types etc comprise the public API of your library. You also need to add to this the semantic knowledge that is not part of syntax; for example, if some of your function calls have side-effects on their parameters, for example, or if there is internal state the user of your library needs to be aware of (like, again for stupid argument, you can't draw a circle after a polygon for some internal implementation reason..)

For a real world example, check out the data structure framework of Java's API, or for something even more "over-engineered", the classes that abstract multithreading concepts. They are pretty good examples of API design. I like the former, the latter feels contrived and some of the conventions used are just simply wrong in a lot of everyday scenarios and force me, as a programmer, to actually work around them to get Java's multithreading work the way I would intuitively expect it to, but hey, I didn't design the API... got to live with what they give me.



Sure, no problem...

EDIT: Hmm... let's describe this in really simple terms without all the hand-waving. Suppose we're coding the same application. I want you to provide some piece of the application for me. Therefore, so that my code is able to make use of your code, we need to agree what your code is going to look like and how it behaves when I'm using it. We need to agree upon an API, and whenever you start explaining to me how you expect your code to be used by me, you're explaining the API to me. Capiche? ;)

Alright, seems like everything is getting clearer after each round of discussion. Hmm, well, I think I better concentrate on my on Java journey too, maybe from there, I would be exposed more on that and hence get a better idea. But at least now I know what you are trying to explain to me and what is the API and how we make use of it or even thinking of creating one to use etc.

Btw, I can't send you any message, that's quite strange, something is just not right with my messenger I think. I will have to get it fixed.

I'll be outstation for two days, so might not be able to do anything until I returned to my house.

Thanks for getting so patient with me, CptPicard =)

You have been a great helps to me.

Though it still seems to be quite abstract at least the idea is there now, haha... that is quite complicated, as all the while I thought API is a separate entity from high level programming >.<" :lolflag:

Regards,
Jenson

---

