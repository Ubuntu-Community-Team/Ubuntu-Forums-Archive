---
title: "Selecting a programming language"
date: 2014-05-04
forum: Programming Talk
---

### Post by DisappearingOak on 2014-05-04
I want to create desktop apps with beautiful interfaces, cross-platform, like irc client, music app, wordpad, etc. so I need a good language and an IDE. I already know that the best in class is C++ and Qt, but I feel reluctant to delve into a language that even coding superstars think is highly complicated and difficult. But I do not want to start out with Python or Ruby either, as I did not like the feel of them. Same with Java. I want a solid language that is powerful enough to fit my needs in the future as I do not want to change languages a little while after starting to code, especially since I feel less motivated to even start. So I need a friendly language that is powerful also. 

I looked at Rebol today, and really liked it, the syntax is very easy to the eye, but the open source version is alpha software. I do not even know if it has an IDE and the Rebol apps I saw in Google seem to be very retro in look, which I did not like, but I would compromise on that, but then, it's alpha, and I do not know if there are good guides for a beginner. There don't seem to be alternatives for it which are final quality. I looked at Smalltalk but don't know if it's for desktop apps with beautiful interfaces. I just want a language that is easy, friendly, but powerful as I go along, and is utterly suitable for such things. I do not mind if the language is 'alternative' than mainstream as long as it has friendly syntax, ease of use, and the required resources like a solid IDE, etc. Please advise.

---

### Post by Vaphell on 2014-05-04
you should pick some established language. Aesthetics are somewhat important, but access to a wide collection of libraries and wisdom of the crowds using the language cannot be overestimated. With obscure language you are on your own and that's it. Unfortunately the best candidates with the best supporting tools are all the ones you don't like.

Qt is probably the best gui library there is, which kind of implies c++, but Qt also has bindings to many other languages. It's possible to write qt app in python for example.

---

### Post by King Dude on 2014-05-05
C and Lua would be the languages I'd recommend. There's also a fairly new language called [Julia]("http://julialang.org/"), which is great for mathematics intensive programming.

---

### Post by ofnuts on 2014-05-05
I completely agree with Vaphell. And don' t overestimate C++ complexity. If you are a programmer of sufficient caliber to write a usable IRC client or wordpad, C++ won't be that difficult.

---

### Post by DisappearingOak on 2014-05-05
> **ofnuts said:**
> I completely agree with Vaphell. And don' t overestimate C++ complexity. If you are a programmer of sufficient caliber to write a usable IRC client or wordpad, C++ won't be that difficult.

I'm a beginner, actually, I mentioned those software as the type of gui apps that I'm interested in creating after I learn. But, I decided to learn C++ after I read that it is not required to know all of the language or all of the complex features, and even pros don't, and a novice can use the simpler stuff first and then grow. Anyway, I really like the look of writing cout << "Hello" << strone; I think I'll put in the effort to learn this and Qt.

---

### Post by ian-weisser on 2014-05-05
> **DisappearingOak said:**
> I feel reluctant to delve into a language that even coding superstars think is highly complicated and difficult.

I do not want to change languages a little while after starting to code, especially since I feel less motivated to even start.

If you do not find the idea of writing code motivating, then don't write code. Do something that motivates you.

If you do decide to write code, you will certainly wind up learning more than one language. Since most languages share many concepts, I find this rather less annoying than you seem to expect.

---

### Post by lisati on 2014-05-05
> **ian-weisser said:**
> If you do decide to write code, you will certainly wind up learning more than one language. Since most languages share many concepts, I find this rather less annoying than you seem to expect.

Agreed. Even if you focus on learning one language, you'll probably find that with time, reading code in another language and getting a basic feel for how it works will become easier.

---

### Post by sps828gaming on 2014-05-05
I would recommend C++ since most Os's use it so making an app go cross-platform wouldn't be so hard and it's great for game development.

---

### Post by ofnuts on 2014-05-06
If you want to learn programming, have a look at Python. Rather forgiving, can introduce you to object-oriented and functional programming, and the complex stuff can be avoided at the beginning (it only comes in handy when you want to code more efficiently).

---

### Post by hamiljf on 2014-05-17
Must put in a comment here... I've used around 30 languages at some time or other and my favourite is still Java: clear structure, good documentation, colossal class library, wide platform support, including mobile devices, and an excellent, free, IDE: Eclipse.

---

### Post by ofnuts on 2014-05-18
> **hamiljf said:**
> my favourite is still Java: clear structure

[http://geek-and-poke.com/geekandpoke/2014/1/2/games-for-the-real-geeks-part-2](http://geek-and-poke.com/geekandpoke/2014/1/2/games-for-the-real-geeks-part-2)

---

### Post by veddox on 2014-05-19
> you should pick some established language. Aesthetics are somewhat important, but access to a wide collection of libraries and wisdom of the crowds using the language cannot be overestimated. With obscure language you are on your own and that's it. Unfortunately the best candidates with the best supporting tools are all the ones you don't like.

I definitely agree with that. I taught myself programming two years ago, and without good documentation, you're stumped.

>  just want a language that is easy, friendly, but powerful as I go along, and is utterly suitable for such things. I do not mind if the language is 'alternative' than mainstream as long as it has friendly syntax, ease of use, and the required resources like a solid IDE, etc.

 If you want that in a language as a beginner, I'm afraid you'll just have to go with something mainstream. Python would be one that is very easy to learn and use, yet powerful and portable, as ofnuts suggested. You can also use PyDev (an Eclipse plugin) as an IDE, or Geany if you want something somewhat lighter. Making GUIs isn't quite as straightforward, although there are various extensions, or you could use Jython (a Java implementation of Python) to have access to the Java Swing library.

 I personally would go with Java, just like hamiljf. It's the language I learnt first, it's relatively friendly for beginners, the syntax is a bit more standard than the Python syntax, it has native graphics capabilities and a huge library (an invaluable asset with any language). Plus, you have Eclipse, which is the non-plus-ultra open-source IDE as far as I'm aware. You also don't need to worry about recompiling to achieve portability, as you do with C++. In fact, you have even greater portability than with Python in a sense, because way more people have Java installed than Python.

And yes, you definitely will be learning more than one language during your programming career. So don't worry too much right now about finding the *perfect* language.

---

### Post by slickymaster on 2014-05-19
> **ofnuts said:**
> [http://geek-and-poke.com/geekandpoke/2014/1/2/games-for-the-real-geeks-part-2](http://geek-and-poke.com/geekandpoke/2014/1/2/games-for-the-real-geeks-part-2)

LOL

I've been using Java, professionally for about 17 years, and that comic stripe pretty much sums it all.

---

### Post by ofnuts on 2014-05-19
> **slickymaster said:**
> LOL

I've been using Java, professionally for about 17 years, and that comic stripe pretty much sums it all.

Sometimes I wonder if one of my coworkers isn't moonlighting as the G&P author. [Last week's issue]("http://geek-and-poke.com/geekandpoke/2014/5/13/undead-code") also strikes home. But the best description of my current job is [here]("http://mashable.com/2014/04/30/programming-sucks/"):
> Also, the bridge was designed as a suspension bridge, but nobody  actually knew how to build a suspension bridge, so they got halfway  through it and then just added extra support columns to keep the thing  standing, but they left the suspension cables because they're still sort  of holding up parts of the bridge. Nobody knows which parts, but  everybody's pretty sure they're important parts.

---

### Post by mmstick on 2014-05-26
The Go programming language is actually relatively simple and packs a lot of powerful features as the latest modern programming language that even make programming concurrent programs simple enough that a beginner could do it. It was designed by the creator of UNIX  to take the existing concepts of programming languages like C/C++ which are loaded with a lot of complicated cruft and make it simple with the KISS principle, so now we have a programming language that's simple like Python but stronger than C/C++ while producing code that's easy to read.

I quite like how easy it is to set up an environment with go, since all you need to do is to install the go package. As I use KDE, I can just open up Kate and enable the terminal panel at the bottom, write a go source code file and execute go run sourcecode.go and it compiles/runs the program using gcc.

There is a Qt binding for Go so you can program Go programs with Qt.

---

### Post by ritwikraghav14 on 2014-05-26
As you yourself said:
> [COLOR=#000000]*just want a language that is easy, friendly, but powerful as I go along, and is utterly suitable for such things.*[/COLOR]
Python satisfies them. Also, many flavors of Python are available like Cpython, PyPy, Jython etc. and for gui, you may use libraries like TkInter[FONT=Arial, Verdana, Geneva, Bitstream Vera Sans, Helvetica, sans-serif][COLOR=#000000]...[/COLOR][/FONT]

---

### Post by zircon_34 on 2014-06-03
I agree, just started to use Python, its more fun especially that you get quickly some results. Qt with C++ seems to be an excellent platform to develop desktop apps though, so if I had time, would try to learn that but this language is more extensive to learn.

---

### Post by Erik1984 on 2014-06-03
> **mmstick said:**
> The Go programming language is actually relatively simple and packs a lot of powerful features as the latest modern programming language that even make programming concurrent programs simple enough that a beginner could do it. It was designed by the creator of UNIX  to take the existing concepts of programming languages like C/C++ which are loaded with a lot of complicated cruft and make it simple with the KISS principle, so now we have a programming language that's simple like Python but stronger than C/C++ while producing code that's easy to read.

I quite like how easy it is to set up an environment with go, since all you need to do is to install the go package. As I use KDE, I can just open up Kate and enable the terminal panel at the bottom, write a go source code file and execute go run sourcecode.go and it compiles/runs the program using gcc.

There is a Qt binding for Go so you can program Go programs with Qt.

That sounds attractive, it is similar to my current Python workflow with Kate. Have to give Go a go... :P

---

### Post by xb12x2 on 2014-06-04
> **mmstick said:**
> The Go programming language is ...

Go is owned by Google and so was designed to target ***Google's*** very specific requirements, not to address a generalized set of programming needs. Google must support very ***large*** and ***distributed*** systems AND Google depends on mountains upon mountains of ***existing*** code, and so on. 

So, because of Google's specific requirements, you might have some issues with it. Some examples of possible issues are: Go does not provide conventional exceptions, does not provide assertions, is not object oriented in the conventional sense, does not support generics (last I looked), and so on. 

There's a lot of online documentation about Go and in it Go's designers have made it clear that it is first and foremost a tool sharpened for Google.

---

### Post by loldotdot on 2014-06-04
Plus one for Java. My first language was Java (more Android oriented now) and I like its syntax and form. I started Bruce Tate's Seven languages in Seven Weeks and it's been difficult but fun looking at different paradigms and their own uses.

---

### Post by sam-c on 2014-06-11
Some Years ago I asked Young active Programmers what do they Prefer Java or C++? As Cis Dangerous.
2-Question 2 What do uou know about Java 5?;);)

---

### Post by ofnuts on 2014-06-11
> **sam-c said:**
> Some Years ago I asked Young active Programmers what do they Prefer Java or C++? As Cis Dangerous.
2-Question 2 What do uou know about Java 5?;);)

A programmer telling you which language s/he prefers tells more about him/her than about the language. Languages are indeed like cars, they tell a lot about the personality of their "owners". Even more so, since you can always learn your dream language, while you can't always afford your dream car.

---

### Post by veddox on 2014-06-13
> **ofnuts said:**
> A programmer telling you which language s/he prefers tells more about him/her than about the language. Languages are indeed like cars, they tell a lot about the personality of their "owners". Even more so, since you can always learn your dream language, while you can't always afford your dream car.

Sorry, this is a little off-track, but you've made me curious ;-) What does which language-preference tell you about a programmer, in your opinion?

---

### Post by ofnuts on 2014-06-13
Curiosity, open mindedness, ability to grasp new concepts,  for the more positive traits. Corporate blindness, devotion to the past for some others.

Of course, phase 2 is looking at the code they produce with said language :)

---

### Post by trent.josephsen on 2014-06-14
Well, for instance, when someone I don't know suggests **Java** *to a new programmer*, I assume that Java is the only programming language they know.
If you suggest **Python**, I assume you're just repeating the conventional wisdom.
**Ruby**, you've never done anything but Web development.
**PHP**, you've never done anything but Web development badly.
**Perl**, you're stuck in the '90s.
**Tcl**, you're stuck in the '80s.
**Bash**, you've never heard of Perl.
**Lisp or Scheme**, you've never written a program that does useful work. You may be proud of this.
**Haskell**, you're a functional programming zealot willfully ignorant of the fact that FP is hard for most people.
**Scala**, you jump on every bandwagon that comes along.
**JavaScript**, the only other language you know is HTML.
**C**, you imagine it reveals profound truths about computing. You think the best way to learn to swim is by falling in a lake.
**Verilog**, you actually know profound truths about computing. You think the best way to learn to swim is by falling in the ocean.
**Assembly**, see C.
**C++**, you're probably Stroustrup in disguise.
**C#**, you're on Microsoft's payroll. You're about to angrily reply and tell me that I've never heard of Mono.

I could go on, just give me more languages...

By request:
**APL**, you're stuck in the '70s.
**Smalltalk**, you're an OOP zealot willfully ignorant of the fact that OOP isn't always appropriate.
**COBOL**, you program because it pays money. You are [this guy](http://xkcd.com/621/).
**Fortran**, you learned to program from the physics department.
**MATLAB**, you learned to program from the engineering department.
**Ada**, your favorite thing about programming is copying and pasting.
**Go**, you don't like C and you'll believe anything Google tells you.
**Swift**, see Scala, plus you'll believe anything Apple tells you.
**Lua**, you've never heard of Tcl. You also think 1-based indexing is perfectly reasonable.

*[SIZE=1]Note: The above is intended as humor. Nevertheless, if you wish, you may find a grain of truth in each statement. If I offended you or your favorite language in the list above, please imagine I'm talking about everybody else but you.[/SIZE]*

BTW, before anyone else brings it up, yes, I know Tcl didn't exist in the eighties. I'm going to claim that was an intentional commentary on its backwards design and totally not a mistake.

---

### Post by ofnuts on 2014-06-14
> **trent.josephsen said:**
> 
I could go on, just give me more languages...

*[SIZE=1]Note: The above is intended as humor. Nevertheless, if you wish, you may find a grain of truth in each statement. If I offended you or your favorite language in the list above, please imagine I'm talking about everybody else but you.[/SIZE]*

PL/1, APL,Rexx, SmallTalk, Cobol, Fortran, Ada, Go, Swift, Lua...

Otherwise, I kind of agree with the above(*) : )

But of course the most revealing thing is that one has an "absolute" preferred language, and not preferred languages, depending on task and programmer skill.

(*) With one exception: **JavaScript**, you think you know it, but you only know the DOM.

---

### Post by trent.josephsen on 2014-06-14
Added to my original post. Couldn't think of anything to say about PL/1 or Rexx, though, and some of them are beginning to stretch a bit.

> **ofnuts said:**
> But of course the most revealing thing is that one has an "absolute" preferred language, and not preferred languages, depending on task and programmer skill.
Good point.

It's also important to realize that most open-ended threads on a forum like this one boil down to "What's your favorite language?" after half a dozen posts or so. You tend to see a lot of answers that aren't really about whatever the OP wanted at all, but just there to make one's preferred language look good in the popularity contest.

---

