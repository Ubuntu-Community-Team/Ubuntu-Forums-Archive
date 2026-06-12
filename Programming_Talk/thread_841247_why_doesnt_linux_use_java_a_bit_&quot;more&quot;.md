---
title: "why doesnt linux use java a bit &quot;more&quot; ?"
date: 2008-06-26
forum: Programming Talk
---

### Post by dexter.deepak on 2008-06-26
is it related to some poor language feature or the "closed-source" nature of java (which was made open-source some time back) ?

the only java application i seem to use on ubuntu today is azureus..why is it so ? there ought to be more..
what are you people's thoughts over java's failure on linux..and what changes should be made to have  a better compatibility between the two?

---

### Post by henchman on 2008-06-26
Well, have a look at this article: 

[http://www.ferg.org/projects/python_java_side-by-side.html](http://www.ferg.org/projects/python_java_side-by-side.html)

python is just easier and better and (was?) faster to be interpreted. today many ubuntu projects use python and very few java.. so what should you lern when you want to contribute to ubuntu? of course python, so you will write your programs in python and the next generation of programmers will, too :)

There was also a long time when there was no 'good' open source java runtime environment... now openjdk has catched up, but it's still somewhat slow and one reads here frequently about users using it and complaining about its speed

---

### Post by CptPicard on 2008-06-26
I wouldn't say Java is in any serious sense "failing". Java on top of Linux is a very popular *server* platform, plus an embedded device platform.

Java is "failing" on the desktop etc. on Linux for the same reasons it's "failing" on other OSes... virtual machine doesn't allow tight integration with the host OS for the obvious reasons that you must play for the lowest common denominator, plus the fact that the VM memory management is not integrated with the OS, which means a separate JVM oversized heap for each process. You just simply can't run many Java apps on the same box.

Plus the fact that the language is a bit unwieldy for more rapid development where Python et al are fast gaining ground... but trust me, Java has a nice future in large distributed heterogenous systems (where it can enforce some homogeneity).

---

### Post by kknd on 2008-06-26
> **CptPicard said:**
> 
...


+1.

A simple example of why you don't see much Java desktop apps: even a "Hello World" with Swing uses up to 20mb of memory (to compare, transmission, running for some hours consumes less than 8mb).

---

### Post by xlinuks on 2008-06-26
Java was closed source and not under a Linux-friendly license. For that reason it wasn't included by default in the Linux distros (the GNU version of Java was and is a much worse implementation than Sun's one) and you cannot run Java apps, first you - the user - have to install Java.
OpenJDK "finished" these days getting completely open source - but - it is, once again, about the pour quality of the open sourced version (people experience freezing, the graphics libraries are not as fast as Sun's JDK and, buggy graphics) and perhaps for that reason - OpenJDK was not integrated into Ubuntu. (Now compare the state of Python on Ubuntu).
That was and is the main reason(s) for me and (all) the other Java developers I know to not create apps in Java (targeting Linux).
For me - only after that come the other reasons, particularly those that CptPicard noticed, of which the main one would be that each app starts in a new JVM (which seems to be "fixed" in the Java 6 update 10, not sure if for Linux as well).
I don't know the state of Python on Linux compared to other platform, but Sun's Java for Linux is worse than that for Windows (for instance - rendering performance).
There are lots of other issues, but if they do the update 10 version for Linux the _right_ way - I see a lot of (additional) reasons for using Java.

---

### Post by xlinuks on 2008-06-26
> **kknd said:**
> +1.

A simple example of why you don't see much Java desktop apps: even a "Hello World" with Swing uses up to 20mb of memory (to compare, transmission, running for some hours consumes less than 8mb).

For me a Swing Hello World app on Linux takes 11.5MB but that doesn't change much.
The 11.5MB are in fact the JVM (like 95%) + your app (like 5%).

---

### Post by pmasiar on 2008-06-26
Java reimplemented every tool Unix/Linux has, to be "platform-independent". So now, if you know your way around Linux, you need to learn another incompatible and huge Java API and many tools to do same things you already know. Why anyone would want to do that?

People who want to promote Java on Linux mostly came from Java on Windows. We just need to show them how much simpler and faster is developing in Python or Ruby, and they will not miss Java anymore :-)

---

### Post by dexter.deepak on 2008-06-26
i havent tried python, but on going through the link given by henchman..i realized the differences...though the author of that page seems to be quiet biased in his approach...he doesnt give a single argument in favour of java, which i am sure,there must be !!

the cause of all the troubles is the jvm, which takes up a lot of memory.
but we should not forget the advantages ..mainly 
1. security ...which i think is a very strong point for the future (i dont know if python provides this)

2. cross-platform nature - though even python is an interpreted language, but i dont know if it can also be used to make cross-platform applications.

3. advantage over c++ - if there can be a lot of development in c++, why not in java ..since jit compilation proves out to be comparably faster than c++ .plus, java is a much more object-oriented and even linus torvalds condemns c++ .

to add this..there are applications like java web-start which can be of lot of help in the future..and even the present.

I would even like to know about Jython ..if it can help a better purpose than java and python alone.

to quote CptPicard:
"Java on top of Linux is a very popular server platform, plus an embedded device platform "

can you please throw some more light on this ...and give some examples.

i may seem to favour java at the moment ...but now i am fed up with changing my  progamming styles..from c to c++ to java ..
i want to be a much better programmer in a single language, which has a better future...thats why i am try to analyse these points. thanks.

---

### Post by dexter.deepak on 2008-06-26
talking the other way round...i am really influenced by python...i was till now forced to believe that java is the best language for all reasons...but now i have a different outlook.
has python got some supporting web server architecture ..like servlet/jsp and tools like rmi ?

---

### Post by xlinuks on 2008-06-26
> **pmasiar said:**
> Java reimplemented every tool Unix/Linux has, to be "platform-independent". So now, if you know your way around Linux, you need to learn another incompatible and huge Java API and many tools to do same things you already know. Why anyone would want to do that?

People who want to promote Java on Linux mostly came from Java on Windows. We just need to show them how much simpler and faster is developing in Python or Ruby, and they will not miss Java anymore :-)

Can you do an app in the browser using "Python or Ruby"?
Flash - no problem, Java - same, but Python ..oh wait.. the browsers don't support Python nor Ruby.. Exactly, make sure next time you compare apples to apples. There are things where you cannot do with those langs (unless you "call libraries" to speed things up so that they don't behave so pathetically slow), or where it would be better to not use them.
Sony Playstation 3 uses Java, BluRay is on Java, NASA world wind. What serious app or platform uses Python or Ruby?
Once again, don't compare bears to crocodiles, because what defines the victory is the ground.

---

### Post by kknd on 2008-06-26
> **xlinuks said:**
> Can you do an app in the browser using "Python or Ruby"?...

Browsers don't run Java code.

This is implemented as a plugin. I someone want, its possible to make a plugin to run Python and etc.

About speed:

Python / Lua / etc are much more dynamic than Java, so its more dificult to optimize things. But there are JIT compilers (at least for Python and Lua).

If you really need speed or access another library, you can make a C module (its very easy in Python or Lua, now try using JNI ...)

---

### Post by xlinuks on 2008-06-26
hahaha
> I someone want, its possible to make a plugin to run Python and etc.
No comments :))))
If you want your app to run on your mobile just create the Python plugin!! haha
I'm not promoting Java - it lacks some important features just like other languages including Python and Ruby, but what I want to mention( once again ), that this thread/forum is the most Python biased one I have ever seen! Haha

---

### Post by Phenax on 2008-06-26
Well, I know for a fact JRuby allows you to make your Ruby programs applets (as it is closely connected with Java). Jython probably allows similar functionality I'm sure.

---

### Post by xlinuks on 2008-06-26
> **Phenax said:**
> Well, I know for a fact JRuby allows you to make your Ruby programs applets (as it is closely connected with Java). Jython probably allows similar functionality I'm sure.
It is not just closely connected - JRuby is a Java implementation of the Ruby interpreter. "Java owns Ruby" :)
Jython - roughly same issue, but with Python.
Java is so powerful and fast that other languages tend build on top of it, which once again tells us who is who and of their capabilities.

---

### Post by pmasiar on 2008-06-26
> **xlinuks said:**
> Can you do an app in the browser using "Python or Ruby"?

You so obviously have no clue what you are talking about, and any blub programmer does. So keep it up! Why to let facts rob you from your biases!

and BTW it's possible to make Jyton app plugin. I don't care about it myself but others do.

and Mozilla is considering replacing Lua with Python.

---

### Post by Phenax on 2008-06-26
> **xlinuks said:**
> It is not just closely connected - JRuby is a Java implementation of the Ruby interpreter. "Java owns Ruby" :)
Jython - roughly same issue, but with Python.
Java is so powerful and fast that other languages tend build on top of it, which once again tells us who is who and of their capabilities.

Well sure, you can keep going up the hierarchy. Why not use what Java was written in? Why not use what *that* was written in? Why not just revert to machine code, as that's what everything amounts to.

Because of convenience and application. Languages like Ruby and Python excel in many places and it is totally logical to write many programs in them. Do I want to write a x86 machine emulator in Ruby or Python? Probably not. Java or C? That's realistic.

---

### Post by xlinuks on 2008-06-26
@pmasiar
But, under the hood, it's Java - right? That's what I mean man.
And, since according to you Python is sooo cool - why you still didn't give me some examples of serious applications written in Python? I mean such as NetBeans, Eclipse, on Mobile..
so..? I'm just very curious..

---

### Post by kknd on 2008-06-26
> **xlinuks said:**
> hahaha

No comments :))))
....


Ãh, yes. Java plugin doesn't where magically created within the creation of the universe, you know.

---

### Post by pmasiar on 2008-06-26
> **xlinuks said:**
> @pmasiar
But, under the hood, it's Java - right? 

under hood of what? can you please quote when to refer to something?

> And, since according to you Python is sooo cool - why you still didn't give me some examples of serious applications written in Python? I mean such as NetBeans, Eclipse, on Mobile..
so..? I'm just very curious..

YouTube and many other cool websites. Google build/cluster management. Ubuntu Launchpad and may desktop apps. And yes, Python runs on mobile phones too.

Just because you are ignorant about existence of those apps, it does not mean they cease to exist.

---

### Post by LaRoza on 2008-06-26
> **xlinuks said:**
> Can you do an app in the browser using "Python or Ruby"?
Flash - no problem, Java - same, but Python ..oh wait.. the browsers don't support Python nor Ruby.. Exactly, make sure next time you compare apples to apples. There are things where you cannot do with those langs (unless you "call libraries" to speed things up so that they don't behave so pathetically slow), or where it would be better to not use them.

Sony Playstation 3 uses Java, BluRay is on Java, NASA world wind. What serious app or platform uses Python or Ruby?

Yes, you can run Python in a browser (it isn't that widespread, and isn't worth doing as it is limited in what browsers can do it). You can write Python for the Java platform and run applets (Jython) in a browser. (Same deal with Ruby, JRuby)

Tcl on the other hand has a better plugin for "Tclets", but I haven't used that before.

Nasa uses Python, Google uses Python, Canonical uses Python. Blue-Ray uses Java, yes, but HD-DVD didn't. Sun pushed Java, MS pushed their technology to each specification, it wasn't really a choice ;)

As for the original question: **why doesnt linux use java a bit "more"?**. Because that is not for what Java was designed.

---

### Post by skeeterbug on 2008-06-26
> **xlinuks said:**
> @pmasiar
But, under the hood, it's Java - right? That's what I mean man.
And, since according to you Python is sooo cool - why you still didn't give me some examples of serious applications written in Python? I mean such as NetBeans, Eclipse, on Mobile..
so..? I'm just very curious..

Google wrote their search in Python/C++. They also hired Guido van Rossum (Python creator). That should tell you something.

[http://www.python.org/about/quotes/](http://www.python.org/about/quotes/)


I know curse.com (pretty big media site), uses python/Django.

---

### Post by Sukarn on 2008-06-26
> **skeeterbug said:**
> Google wrote their search in Python/C++. They also hired Guido van Rossum (Python creator). That should tell you something.

[http://www.python.org/about/quotes/](http://www.python.org/about/quotes/)


I know curse.com (pretty big media site), uses python/Django.

Curse uses Python? I didn't know that. Thanks for pointing it out.

---

### Post by xlinuks on 2008-06-26
thanks, I should have made myself clear, I meant _desktop_ applications (like the ones I mentioned). I know that Google uses Python (and C++ and Java and .. perhaps other langs including assembly since they do a lot of software for server-side, desktops, mobile(s) ... ).

---

### Post by ankursethi on 2008-06-26
I wrote this as it came to my mind, so there is barely any organization throughout the text. This post contains a lot of what I've always wanted to say about Java but never got around to saying it. I hope it reflects what many other people here think. If it doesn't, flame me dead :)

People who use Java and people who use scripting languages generally have very different ideologies.

Sun created Java, as we all know very well, to enable people to write "write once run anywhere" applications. But the design of Java tries hard to drive home another point : don't be clever. In fact, this is probably the defining feature of Java. It's difficult to write cryptic code in Java. It's pretty difficult to write quick, one-line throwaway scripts to a dirty job that you don't want to do by hand. In terms of new, ground-breaking concepts, Java has very little to offer. It takes barely a week to go through a Java book. Same old looping construct, same old OO model. You can't even extend the language! Java is not a "programmable programming language" (but Ruby is).

Now, what could drive Sun to choose such a design? Obviously, they wanted their language to be so easy to learn and so light on deep theoretical concepts, they they dumbed the entire thing down until they were sure that even a monkey could program in Java. This is not to say that all Java programmers are monkeys, there are intelligent people in the Java community who regularly push the language to the limit. But the actual intent of Java, IMHO, was to make "assembly line programming" as easy as possible. Java assumes the programmer is stupid, and tries to protect him from himself.

Talking of Perl/Python/Ruby, these languages are outrageously expressive. They all assume you know what you are doing. They assume you are an intelligent, competent programmer. These languages will allow you to write code that does a large amount of work in very few lines of code. Moreover, all of them contain cutting edge features borrowed from languages like Lisp and Smalltalk. Features that can be difficult to understand at first, but can save a lot of time later.

It is these features that make Java-only programmers shrink away from dynamic languages. Of course, they make excuses and ignore all facts and try to prove that Java, indeed, is The Answer. Widely used? Java is widely used because there are more Java programmers. And there are more Java programmers because Java is dead easy to learn.

For a seasoned Linux user, Java is nothing short of an insult. Intellectuals gravitate towards languages such as Lisp, and come back to Ruby/Python when they want to get something done. Systems programmers use good ol' C since anything else would be overkill. Web programmers use RoR/Django/some PHP thingy because they are easy to set up and don't unnecessarily complicate things. Researchers and scientists don't want to mess around with complicated Java code. Who would? With Python/Ruby, you can simply try stuff out in an interactive shell.

One place Java wins hands down is the mobile phone market. The only reason for this is that mobile phone operating systems are not as open as PC systems, and it's difficult to get stuff running on them. Sun knew this, and pushed very hard to get Java onto as many handsets as possible. But this is changing. You can have Python running on any Nokia mobile and easily access the camera, MP3 player, radio, the message inbox etc. in the traditional Python style of simply importing whatever functionality you need from a library (provided by Nokia of course). I know, since I run it on my mobile.

So, here's a short summary :
1. Anybody can learn Java. It's like mainstream pop music in this respect. It's occasionally brilliant, but mostly it just sucks.
2. Java protects you from yourself.
3. Non-programmable programming language.
4. An insult to any Linux user above the intellectual level of an ape.

Speed and licensing barely has anything to do with this. You should go see how the programmers on the programming sub-Reddit hate Java. Needless to say, a majority of them are hardcore Linux geeks.

---

### Post by LaRoza on 2008-06-26
> **xlinuks said:**
> thanks, I should have made myself clear, I meant _desktop_ applications (like the ones I mentioned). I know that Google uses Python (and C++ and Java and .. perhaps other langs including assembly since they do a lot of software for server-side, desktops, mobile(s) ... ).

I already said, Java wasn't intented for desktop applications.

> **LaRoza said:**
> 
As for the original question: **why doesnt linux use java a bit "more"?**. Because that is not for what Java was designed.

---

### Post by Tomosaur on 2008-06-26
In short - Java is very good for enterprise kinda stuff, because it has a lot of professional backing, and Sun has a vested interest already in enterprise products. There are a lot of dedicated Java-based offerings for pretty much anything you would care to do with your business. This is great for businesses, but Java is neglected on the desktop for a variety of reasons - the sheer mind blowing ugliness of Swing, the debate over Java's speed, and other such things.

Python is used very widely on Ubuntu, maybe on other Linux distributions (I'm not sure whether it's pushed quite so hard elsewhere, though) - not so much on Windows or Mac as far as I'm aware, because it is easy to learn, quick to develop with, and can do pretty much anything Java can do. It doesn't have the same professional backing as Java, but given time it may come to rival it in the enterprise markets.

But all of this is just irrelevant, really. Use whichever is the best tool for the job. If you need your product to be compatible with other software on other platforms, Java may be your best option. If you need your software to be lightweight, cross-platform, and deployed quickly, use Python.

---

### Post by LaRoza on 2008-06-26
> **Tomosaur said:**
> 
Python is used very widely on Ubuntu, maybe on other Linux distributions (I'm not sure whether it's pushed quite so hard elsewhere, though) - not so much on Windows or Mac as far as I'm aware, because it is easy to learn, quick to develop with, and can do pretty much anything Java can do. It doesn't have the same professional backing as Java, but given time it may come to rival it in the enterprise markets.

OS X uses Python and comes with it.

---

### Post by xlinuks on 2008-06-26
> **LaRoza said:**
> I already said, Java wasn't intented for desktop applications.

Although in that post I asked about Python desktop applications, and since you hijacked it, may I ask you - who told you so, and most importantly - "when"?
What language would you refer as "intended" for the desktop?
Is that the great and super language called Python?

---

### Post by LaRoza on 2008-06-26
> **xlinuks said:**
> Although in that post I asked about Python desktop applications, and since you hijacked it, may I ask you - who told you so, and most importantly - "when"?
What language would you refer as "intended" for the desktop?
Is that the great and super language called Python?

When did I hijack?

It is simple, Java wasn't developed for desktop applications. That wasn't its purporse for being created. If it weren't for the web, it wouldn't even be used on desktops mostly likely.

The fact that Java can be used is just extra, it makes it more useful than its original focus.

---

### Post by CptPicard on 2008-06-26
> **ankursethi said:**
> If it doesn't, flame me dead :)

Will do ;)

> 
People who use Java and people who use scripting languages generally have very different ideologies.

Not necessarily. I use Java as my "C++" sort of language, but appreciate greatly those languages a lot of people would refer to as "scripting" languages...

> But the design of Java tries hard to drive home another point : don't be clever.

It is pretty much equally hard to be "clever" in any other language of the same class (static typing, OOP...) -- actually, the sort of "cleverness" you are referring to is probably not to be encouraged in *any* language. Where-ever I prefer other languages than Java, it is *not* because they allow me to be particularly "clever" in the fashion you probably suggest.

> It takes barely a week to go through a Java book.

I have taken about a decade going through lots of Java books. It's not necessarily a good thing, mind you.

>  Same old looping construct, same old OO model.

Exactly the same as in the same old other language...

> Obviously, they wanted their language to be so easy to learn and so light on deep theoretical concepts, they they dumbed the entire thing down until they were sure that even a monkey could program in Java.

Java is not any worse on this than other languages in its class. Actually, Java has nice features in comparison, such as GC etc., whereas languages like C++ just have unnecessarily complexity.

Java is *nicely* simplified for a language of its kind. Which means it has a lot of features other languages don't, but still lack the deep theoretical constructs languages of its class usually do not have.

> Java assumes the programmer is stupid, and tries to protect him from himself.

Java takes away a lot of the drudgery of other languages of its class, but doesn't add much.

> They all assume you know what you are doing.

Actually, Python aims to have "one obvious way to do it".

> It is these features that make Java-only programmers shrink away from dynamic languages.

Most Java-only programmers are just one-language-only programmers in general...

> For a seasoned Linux user, Java is nothing short of an insult.

No, it's not. Java is an OK language for this seasoned Linux user.

> Intellectuals gravitate towards languages such as Lisp, and come back to Ruby/Python when they want to get something done.

Yes, this intellectual gravitates towards Lisp and uses Lisp when one wants to get something done. Or Python. It works too.

> Researchers and scientists don't want to mess around with complicated Java code.

One of my friends from uni who is writing his PhD thesis is probably still a Java-only programmer, because he is a researcher (yes, he should try out something else, but he's too busy with theory)...


> 1. Anybody can learn Java.

Anyone who is able to learn programming is able to learn Java.

> 2. Java protects you from yourself.

Java is a "more convenient C++" but not much more else... it protects you from having to do grudgery.

> 
3. Non-programmable programming language.


As are most other languages except Lisp.

> 
4. An insult to any Linux user above the intellectual level of an ape.


Thanks.

---

### Post by ankursethi on 2008-06-26
Python desktop apps?

Deluge, Transmission, Editra, BitTorrent (yep, the original client was all in Python), Exaile, the Ubuntu installer (Ubiquity), a lot of Ubuntu setup tools, several maintainance tools in HP OEM systems are written in Python.

Emacs, Vim, Blender, Pidgin etc. are scriptable in Python. Several games use Python, such as Civilization 4.

All this is true not only for Python, but also for Lua, Ruby, Perl etc. This is not "Python Vs. Java", this is the answer to why FOSS prefers dynamic scripting languages. Java is not "bad" or "evil", it's just so-so. I wouldn't mind *writing* Java, but I wouldn't *choose* it myself for anything. It simply doesn't excite me.

For languages that can change the way you think, try Lisp, Haskell, Scheme, OCaml, Forth, Smalltalk, Ruby ... Just go back to Java when you've had enough.

No flamewars.

EDIT@CptPicard
You got me there :) Looks like my ideologies *are* pretty different from other Linux users. Oh well, I'm not really a professional developer, just a hobbyist for whom the programming sub-Reddit is the world. I probably need to get out more.

---

### Post by xlinuks on 2008-06-26
> **LaRoza said:**
> When did I hijack?

It is simple, Java wasn't developed for desktop applications. That wasn't its purporse for being created. If it weren't for the web, it wouldn't even be used on desktops mostly likely.

The fact that Java can be used is just extra, it makes it more useful than its original focus.

Thanks!
Would you tell me please what language has been intended for the Desktop?

---

### Post by LaRoza on 2008-06-26
> **xlinuks said:**
> Thanks!
Would you tell me please what language has been intended for the Desktop?

Most languages have many uses. C was original made for programming operating systems, but is widely used elsewhere because it is portable.

If you want to learn the origins of languages, wikipedia helps a lot. 

A language designed for the desktop would be one like Visual Basic as an example. (VS is a bit extreme in this discussion, as it very UI focused)

---

### Post by xlinuks on 2008-06-26
Wow, thanks.. if "Visual Basic" is intended for the Desktop then I guess I need a language that isn't quite meant for Desktop to create the desktop apps I need.. I guess I'll stick to C++ as being a language not intended for the Desktop apps :)
I think in this case "intended" (for the Desktop) and "the best solution" aren't synonyms.

Not related to this thread: if someone has an icon for files of type ".so" (library files) please let me know in private, I'm doing a file manager and can't find a decent icon for this type of file.

---

### Post by xlinuks on 2008-06-26
You can easily code a calculator in Visual Basic, as you can see in the example below:
```

Sub Calculator
On Error Resume next
a=InputBox("Please Insert The First Number")
b=InputBox("Please Insert The Second Number")
c=InputBox("Please Insert The Desired Operation. (eg. -)")
d=InputBox("Please Insert The Result")
Msgbox "The Result Is: " & d
End Sub


```

---

### Post by Sukarn on 2008-06-26
> **xlinuks said:**
> You can easily code a calculator in Visual Basic, as you can see in the example below:
```

Sub Calculator
On Error Resume next
a=InputBox("Please Insert The First Number")
b=InputBox("Please Insert The Second Number")
c=InputBox("Please Insert The Desired Operation. (eg. -)")
d=InputBox("Please Insert The Result")
Msgbox "The Result Is: " & d
End Sub


```

:lolflag:

---

### Post by Steveway on 2008-06-26
> **xlinuks said:**
> Wow, thanks.. if "Visual Basic" is intended for the Desktop then I guess I need a language that isn't quite meant for Desktop to create the desktop apps I need.. I guess I'll stick to C++ as being a language not intended for the Desktop apps :)
I think in this case "intended" (for the Desktop) and "the best solution" aren't synonyms.

Not related to this thread: if someone has an icon for files of type ".so" (library files) please let me know in private, I'm doing a file manager and can't find a decent icon for this type of file.
If your are writing a file-manager then you should use the users icon-set instead of including icons. Take a look at other file-managers and  see how they did what you want to do.

---

### Post by xlinuks on 2008-06-26
There are 3 main reasons I'm creating my own, and one of them is I don't like the icons used in the other file managers (I use "modern" icons, like the ones in Leopard, but perhaps even better - a matter of taste, I find the icons from Ubuntu not so pleasant and old). But, please let's not talk about my file manager in this thread since I think it would mean hijacking it, I would welcome this little help if someone has got such an icon.

---

### Post by lisati on 2008-06-26
> **Phenax said:**
> Well sure, you can keep going up the hierarchy. Why not use what Java was written in? Why not use what *that* was written in? Why not just revert to machine code, as that's what everything amounts to.

Because of convenience and application. Languages like Ruby and Python excel in many places and it is totally logical to write many programs in them. Do I want to write a x86 machine emulator in Ruby or Python? Probably not. Java or C? That's realistic.

And why not go one above machine code and look into microcode?

But seriously, at the end of the day a decisions must be made about platform and language. The answers depend on what's best for what you're trying to achieve.

I've never bothered to learn Java (or Python, for that matter): when I was thinking about learning Java a few years ago I looked at a beginner's tutorial (Google is your friend) and was put off by its idiom.

---

### Post by LaRoza on 2008-06-26
> **xlinuks said:**
> Wow, thanks.. if "Visual Basic" is intended for the Desktop then I guess I need a language that isn't quite meant for Desktop to create the desktop apps I need.. I guess I'll stick to C++ as being a language not intended for the Desktop apps :)
I think in this case "intended" (for the Desktop) and "the best solution" aren't synonyms.

Not related to this thread: if someone has an icon for files of type ".so" (library files) please let me know in private, I'm doing a file manager and can't find a decent icon for this type of file.

I am saying that is its focus. Most language don't have such narrow foci. Look at Python/Ruby/Perl. They are all good at "scripts" and text processing, web sites, and desktop applications. 

For the library files, I noticed my file manager just uses an archive file (the same for all archives) (Thunar)

---

### Post by xlinuks on 2008-06-26
> **ankursethi said:**
> Python desktop apps?
Deluge, Transmission, Editra, BitTorrent (yep, the original client was all in Python), Exaile, the Ubuntu installer (Ubiquity), a lot of Ubuntu setup tools, several maintainance tools in HP OEM systems are written in Python.
Emacs, Vim, Blender, Pidgin etc. are scriptable in Python. Several games use Python, such as Civilization 4.

All this is true not only for Python, but also for Lua, Ruby, Perl etc. This is not "Python Vs. Java", this is the answer to why FOSS prefers dynamic scripting languages. Java is not "bad" or "evil", it's just so-so. I wouldn't mind *writing* Java, but I wouldn't *choose* it myself for anything. It simply doesn't excite me.


The only app I would use is Deluge (since I don't like that the Azureus devs are pulling lots of marketing cruft into it), but then I looked at its source code and, guess what.. "the core" is written in C++ (about half of all the code, I found lots of C++ files). Python looks like a toy that can't stand on its feet and constantly borrows power from other languages, so I wouldn't mind *writing* Python, but I wouldn't *choose* it myself for anything. It simply doesn't excite me.

---

### Post by LaRoza on 2008-06-26
> **xlinuks said:**
> The only app I would use is Deluge (since I don't like that the Azureus devs are pulling lots of marketing cruft into it), but then I looked at its source code and, guess what.. "the core" is written in C++ (about half of all the code, I found lots of C++ files). Python looks like a toy that can't stand on its feet and constantly borrows power from other languages, so I wouldn't mind *writing* Python, but I wouldn't *choose* it myself for anything. It simply doesn't excite me.

Python is a toy that can't stand on its feet....

I think you are looking at it oddly. Other languages need to be extended by Python.

---

### Post by Wybiral on 2008-06-26
> **xlinuks said:**
> Python looks like a toy that can't stand on its feet and constantly borrows power from other languages, so I wouldn't mind *writing* Python, but I wouldn't *choose* it myself for anything. It simply doesn't excite me.

Oh no, it sounds like another "pointer kiddy"/"speed kiddy"...

Python can stand on its own feet very well for most applications. I've only once needed to write a module for Python in C and it was for rendering 3d models (a very tiny portion of the program, everything else was coded in Python).

Python is a tool. A very expressive, fast prototyping, well designed... Tool. The fact that it's so easy to extend with C doesn't make it a "toy", it's actually just a very convenient feature. Why write the bulk of the program in C when only tiny portions need it?

---

### Post by LaRoza on 2008-06-26
> **Wybiral said:**
> 
Python is a tool. A very expressive, fast prototyping, well designed... Tool. The fact that it's so easy to extend with C doesn't make it a "toy", it's actually just a very convenient feature. Why write the bulk of the program in C when only tiny portions need it?

Also, why does C need a language like Python to speed up development? C is a toy, real programming is done in Python and is only used when it is needed.

---

### Post by slavik on 2008-06-26
I honestly want to know how many Python advocates that say that "writing modules in C for Python programs is easy" have actually done so?

---

### Post by Can+~ on 2008-06-26
> **xlinuks said:**
> ...Python looks like a toy that can't stand on its feet and constantly borrows power from other languages...

Question: Why?

---

### Post by Wybiral on 2008-06-26
> **slavik said:**
> I honestly want to know how many Python advocates that say that "writing modules in C for Python programs is easy" have actually done so?

I have... Are you questioning the easiness? It's _very_ easy with tools like SWIG (which literally generates a wrapper for you) and PyRex (a sort of intermediate language for writing wrappers), and even the ctypes module (a FFI module that lets you easily wrap dynamic libraries from within Python).

You write your Python program the way you want it to be, test it to make sure it works logic-wise (disregarding performance), then profile to determine whether or not you need to improve any bottlenecks, and where exactly the bottlenecks are. Sometimes something as simple as importing psyco will speed it up enough... Other times you can take the tiny portions that aren't up to par, and implement them in C.

---

### Post by kknd on 2008-06-26
> **slavik said:**
> I honestly want to know how many Python advocates that say that "writing modules in C for Python programs is easy" have actually done so?

I'm not a Python advocate, but I've done it. Very easy.

I remember when I was doing the same with Java. JNI is a HELL.

---

### Post by LaRoza on 2008-06-27
> **slavik said:**
> I honestly want to know how many Python advocates that say that "writing modules in C for Python programs is easy" have actually done so?

I actually haven't done it, but I know how (and I know where to look for how) and I know people who have done it.

If one has to write C code because Python isn't enough, then I would bet the programmer is sufficiently advanced/skilled enough to do it.

---

### Post by YaroMan86 on 2008-06-27
Personally, I dislike Java. For a language its not very decent. Interpreted languages are not typically a favorite of mine though.

The problem with Java is its slowness and relative bloat. A lot of programmers like to say to people who refer to Java almost exclusively as "programming" often flame these Java coders and say they should "learn a real language."

Though I think its rude, a serious programmer will never swear by Java on any platform if he can help it. YES it makes cross platform a no-brainer, but then you get all the massive issues Java has: That slowness and bloat I mentioned before.

I prefer C and C++ for most of my stuff. If I am doing cross platform work, I play it smart: I only use libraries I know are readilt available on the other operating systems I develop for. SDL is an excellent example.

But, to me, Java is like Mono and .Net. Its for the developer who wants to avoid a little extra work, even at the sacrifice of portability (.net), efficiency (Java), or stability (Mono).

I dislike all three of those.

Now, as for writing modules for C, it really depends. I've not had any problems. Just make sure you keep things like headers damn simple. Remember one can leave all the confusing code and terse documentation and comments on the C source itself if needed. It's just like writing code for just about everything else in C or C++.

Can't comment on Python. Never tried it. Would love to dabble, though.

---

### Post by pmasiar on 2008-06-27
> **xlinuks said:**
> Python looks like a toy that can't stand on its feet and constantly borrows power from other languages, so I wouldn't mind *writing* Python, but I wouldn't *choose* it myself for anything. It simply doesn't excite me.

If Python borrows from so many languages, is obviously better than any of them :-)

... and you sound like prime example of a blub programmer, who is smarter by himself alone than half of Google. When is your IPO? Or maybe if so many successful millionaires like Python and you don't, maybe there is a link?

---

### Post by dexter.deepak on 2008-06-27
what a discussion !!:guitar:
but i would like to know whether python or the "other" languages have a leading edge over java in terms of web technology (in terms of quality and not quantity...which is obviously more).

---

### Post by LaRoza on 2008-06-27
> **dexter.deepak said:**
> 
but i would like to know whether python or the "other" languages have a leading edge over java in terms of web technology (in terms of quality and not quantity...which is obviously more).

Yes, they do IMO.

PHP, Python, Ruby, Perl are much better suited for almost all web programming. Not only are they almost designed for it (PHP was designed for it, Python has modules and frameworks for it, Ruby is most famous for it, Perl was/is the number one CGI language and was the majority of all web scripts for a time), but they are more rapid for development and easier to use. Their dynamic typing, and speed of development makes for more work in less time.

---

### Post by Quikee on 2008-06-27
> **LaRoza said:**
> Yes, they do IMO.

PHP, Python, Ruby, Perl are much better suited for almost all web programming. Not only are they almost designed for it (PHP was designed for it, Python has modules and frameworks for it, Ruby is most famous for it, Perl was/is the number one CGI language and was the majority of all web scripts for a time), but they are more rapid for development and easier to use. Their dynamic typing, and speed of development makes for more work in less time.

If you mean Java as the language then I agree, but if you combine existing frameworks, libraries (Spring WebFlow, Spring MVC for example) with a dynamic language (like Groovy, JRuby, Jython,..) it is at least as good compared to native dynamic languages.

Generally I think it is useless to talk about Java as the language anymore as this is not what is important on a Java platform anymore or where the Java platform will head on in the future - more and more other languages (like Scala, Groovy, Jython, JRuby...) are used combined with Java language - similar as Python, Ruby, Perl combines C.

---

### Post by Timdejager on 2008-06-27
> **LaRoza said:**
> Yes, they do IMO.

PHP, Python, Ruby, Perl are much better suited for almost all web programming. Not only are they almost designed for it (PHP was designed for it, Python has modules and frameworks for it, Ruby is most famous for it, Perl was/is the number one CGI language and was the majority of all web scripts for a time), but they are more rapid for development and easier to use. Their dynamic typing, and speed of development makes for more work in less time.

Yes that's true but lets not forget that java has proven to be extremely scalable and is still often used for integration with legacy back-ends like banking systems written in COBOL. And frameworks like Apache Tapestry do increase developer productiveness, of course it doesn't really provide extra language features it does make developing java apps more less tedious.
 
So if your focus would be on developing these kind of applications the java language or rather the enterprise aspect of the language would definitely be worthwhile to learn. And while the Java language is indeed fairly easy the enterprise aspect of java is confusing and quite complicated.

---

### Post by Timdejager on 2008-06-27
> **Quikee said:**
> If you mean Java as the language then I agree, but if you combine existing frameworks, libraries (Spring WebFlow, Spring MVC for example) with a dynamic language (like Groovy, JRuby, Jython,..) it is at least as good compared to native dynamic languages;) is not what is important on a Java platform anymore or where the Java platform will head on in the future - more and more other languages (like Scala, Groovy, Jython, JRuby...) are used combined with Java language - similar as Python, Ruby, Perl combines C.

Exactly, the nice thing is that is seems the people at sun are also embracing this fact: [http://java.sun.com/](http://java.sun.com/) even the featured content on the Java front page is focused on languages being hosted on the JVM.

Btw, don't forget clojure which also looks quite promising :)

---

### Post by xlinuks on 2008-06-27
> **pmasiar said:**
> If Python borrows from so many languages, is obviously better than any of them :-)

If you really think so - man you gotta grow up and remove head from ***

---

### Post by pmasiar on 2008-06-27
> **dexter.deepak said:**
> but i would like to know whether python or the "other" languages have a leading edge over java in terms of web technology (in terms of quality and not quantity...which is obviously more).

Java web app frameworks scales up well - but they do not scale down at all. Learning curve is extremely steep, just try to create simple "hello world" app in Java/Struts. Once you get beyond 10 programmers/100 pages, Java might be competitive, but for any small project, Java is vast overkill.

And for anyone who ever used dynamic typing, static typing of Java is such a productivity killer. Java's  tools for string processing, compared to Perl/Python/PHP/Ruby, is so abysmal it's not even funny. Checked exceptions can by tamed by IDE which inserts definitions or wraps try/catch blocks, without IDE it would be major pain too.

Strongest and weakest point of Java is library: strong is that it is big - has solution for anything. Weak point that library is mindnumbigly freaking huge that there is no way in hell to understand and know it - with help of an expert guide you can investigate some corners and use them, but you know there are wast areas where might be treasures but you do not dare to go there alone. So it's easier to become code monkey, use the same bag of old tricks and crank the code, because it's just too time consuming to research if some other class would be better match for the task. Why Java needs more than 60 file-like object types? 

Compare it with small consistent language like Python: using dynamic typing allows to use same function, len() to find length of array/list, number of keys in dict (hash), or anything you defined in your own classes. Same iteration "for x in y" will iterate through array/list, hash keys, file (line by line) and any generator/iterator.

Python is being redesigned (even breaking backward compatibility - with automated syntax fix of course) to make it simpler and more consistent, even removing some rarely used and obsolete features. Python is a language what can fit in brains of one person.

---

### Post by pmasiar on 2008-06-27
> **xlinuks said:**
> If you really think so - man you gotta grow up and remove head from ***

I am glad you run out of arguments and gave up.

Yes, Python is more productive than Java, and I am glad you are stuck with Java - more possible interesting jobs for me. Enjoy your chains :-)

---

### Post by slavik on 2008-06-27
> **skeeterbug said:**
> Google wrote their search in Python/C++. They also hired Guido van Rossum (Python creator). That should tell you something.

[http://www.python.org/about/quotes/](http://www.python.org/about/quotes/)


I know curse.com (pretty big media site), uses python/Django.
You are incorrect, MapReduce is a C++ library with Python bindings.

Yahoo hired the Hadoop (Open SOurce MapReduce) leading developer and that is written in Java.

---

### Post by Wybiral on 2008-06-27
> **slavik said:**
> You are incorrect, MapReduce is a C++ library with Python bindings.

Yahoo hired the Hadoop (Open SOurce MapReduce) leading developer and that is written in Java.

... Yes, MapReduce is written in C++, but a hefty portion of the applications using it are written in Python. This is what everyone has been saying... Develop low-level libraries in C/C++, then develop your actual applications in Python.

---

### Post by pmasiar on 2008-06-27
> **slavik said:**
> You are incorrect, MapReduce is a C++ library with Python bindings.

Yahoo hired the Hadoop (Open SOurce MapReduce) leading developer and that is written in Java.

Yes, that's all true.

But most of the code is not the search engine, but server management and deployment - and that is mostly in Python. Say, code to deploy new version of C++/Java search engine binaries to 1% of the servers (a mere 10K servers), and profile the performance, compare with previous version - and undeploy it if not good. Would you want to code **that** in C++ or Java?

Head of Google Production server management team is Alex Martelli, one of leading Python experts. He says "we use Python if we can get away with it, C++ if we have to".

---

### Post by CptPicard on 2008-06-27
Another really annoying feature of Java web app development is that unless you go for the insanely complex J2EE stack with, say, JSF for front-end, there are N different frameworks to choose from. Most of your time is actually spent integrating these frameworks -- something for the ORM, something for the front-end, some way to model the business logic.

Hacking all these to play nicely together is crazy, esp. considering that a lot of frameworks have lacking documentation when it comes to the deep issues you are going to run into when trying to achieve something that is possibly slightly outside the scope of the simple intended usage. At worst, you end up with an integration issue that you could possibly not have foreseen, that stops your project dead in it tracks... and that tosses a simple NullPointerException at your face from somewhere deep inside some component.

Spring helps a lot with integration, but to be honest I still never could get a combination of Spring, Hibernate and (some view technology) to really play nicely in the case of a user transaction that spans multiple requests...

---

### Post by slavik on 2008-06-27
> **pmasiar said:**
> Yes, that's all true.

But most of the code is not the search engine, but server management and deployment - and that is mostly in Python. Say, code to deploy new version of C++/Java search engine binaries to 1% of the servers (a mere 10K servers), and profile the performance, compare with previous version - and undeploy it if not good. Would you want to code **that** in C++ or Java?

Head of Google Production server management team is Alex Martelli, one of leading Python experts. He says "we use Python if we can get away with it, C++ if we have to".
Actually, I would want to use Perl for obvious reasons. :)

---

### Post by pmasiar on 2008-06-27
> **Wybiral said:**
> This is what everyone has been saying... Develop low-level libraries in C/C++, then develop your actual applications in Python.

... and develop the prototypes of libraries in Python first, try different approaches, and when you have the best algorithm you can think (and you profiled your app and you proven that code speed is the bottleneck), reimplement the same tested and tried API in C - for speed and speed only.

---

### Post by xlinuks on 2008-06-27
> **pmasiar said:**
> I am glad you run out of arguments and gave up.

Yes, Python is more productive than Java, and I am glad you are stuck with Java - more possible interesting jobs for me. Enjoy your chains :-)

Haha that's what a kid like you can understand, I feel sorry for you! Python is the Java from the '99 when it was almost nothing more than an interpreted language and everybody was dreaming (on the sly) of having a runtime compiler and all the Java fans kept saying that speed is irrelevant, that you can use C/C++ libraries when you need, that it's all about productivity! You repeat this pathetic history. Now Java is much more powerful than your toy lang and I've proven that, Python is nothing compared to its scalability and (as you know) speed. As a side note I'm also learning C++ and as you grow up you'll realize there's things you have to do Python stands no chance to accomplish in a good way, so sometimes you'll have to drop your toy language and learn some C/C++-like language too. And do yourself a favor, go to the Linux kernel devs and tell them what you said here (common, don't be shy!), that Python "is obviously better than those langs", thus also than C and watch closely their reaction :))) you little homegrown Python troll :)))

---

### Post by Wybiral on 2008-06-27
> **xlinuks said:**
> As a side note I'm also learning C++ and as you grow up you'll realize there's things you have to do Python stands no chance to accomplish in a good way, so sometimes you'll have to drop your toy language and learn some C/C++-like language too.

You know, C++ was one of my first languages. Eventually I grew up and stopped thinking childishly that low-level programming is special... Because it isn't. Raw execution speed holds nothing in terms of scalability... Your ability to do an operation 10x faster than me doesn't mean anything if you can't reduce the computational complexity. You "speed kiddies" can keep your blub toys and spend the rest of your life pushing bits around and trying to debug segfaults, while us grown-ups get something done :) FWIW, I can program in C and Assembly. The fact is that I don't because I value my development time and I've realized that there are concepts far more important than juggling pointers... When you're a little older I'll explain it to you.

---

### Post by xlinuks on 2008-06-27
I tried Python and, no-thanks, keep it for yourself :)

---

### Post by Wybiral on 2008-06-27
> **xlinuks said:**
> I tried Python and, no-thanks, keep it for yourself :)

Yes. Me, Google, Viacom, YouTube, NASA, Reddit... You know... Us little guys over here.

---

### Post by xlinuks on 2008-06-27
Google which acquired YouTube can be referred as same company, but for eloquence you might keep that, it's ok:)
Google also heavily uses Java, C++ and lots of other languages, so what?
Same about NASA (Nasa world wind, ever heard? does it have a Python version? Only a Java one - guess why).

---

### Post by Wybiral on 2008-06-27
> **xlinuks said:**
> Google which acquired YouTube can be referred as same company, but for eloquence you might keep that, it's ok:)
Google also heavily uses Java, C++ and lots of other languages

Yes, but YouTube was using Python (scalably and successfully) before Google, so it's still a valid example of Python doing what you say is impossible. Google does use C++ and Java, but from what I understand, for their libraries and lower level server communication, mostly Python for their actual application development.

What is so special about C++? What are you intellectually gaining from it? Why isn't it practical to write low-level modules in C/C++ and develop your applications in something like Python (the sane way to do low-level development).

I'm aware that C has its place for kernel hacking and low-level library development, but I don't see any practical benefit from developing the bulk of your applications in C unless it's an absolute necessity (which it rarely is).

---

### Post by pmasiar on 2008-06-27
> **xlinuks said:**
> Haha that's what a kid like you can understand, I feel sorry for you!

I almost feel sorry for you - and I do wish I was 30 years younger :-)

Go use your Java and be happy. I have to use it to, that's why I hate Java so passionately and with information about it's strengths and weaknesses - what cannot be said about your biased short-sighted blabberings.

It's better to ignore fool like you, or after fighting you, it will be hard to distinguish the fool I fight from me :-) I'll let people to form own opinions. Preferably based on first-hand knowledge of **both** languages, like I do :-)

---

### Post by LaRoza on 2008-06-27
Posts have been reported a lot and although I don't want to do any moderating in a thread I have participated in, I don't want things to get worse so I am closing the thread and letting someone else review.

---

