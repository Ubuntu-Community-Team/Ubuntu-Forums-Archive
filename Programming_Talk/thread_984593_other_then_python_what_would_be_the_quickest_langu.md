---
title: "other then python what would be the quickest language to make games in"
date: 2008-11-16
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-11-16
the title says it all.  i dont like python so please dont recommend it

C++ with sdl isnt too bad but i have a time consuming schedual so anything faster would be great

as long as its not python post any ideas

---

### Post by Phenax on 2008-11-16
[http://love2d.org/](http://love2d.org/)

---

### Post by aszxcv on 2008-11-16
flash

---

### Post by jimi_hendrix on 2008-11-16
new requirement:

free

---

### Post by slavik on 2008-11-16
Perl, it even has better performance with OpenGL (and has SDL bindings).

---

### Post by jimi_hendrix on 2008-11-16
link?

---

### Post by snova on 2008-11-16
It's Perl. Of course slavik is going to recommend it. ;)

This looks promising: [http://learn.perl.org/](http://learn.perl.org/)

---

### Post by Kilon on 2008-11-17
> **jimi_hendrix said:**
> the title says it all.  i dont like python so please dont recommend it

C++ with sdl isnt too bad but i have a time consuming schedual so anything faster would be great

as long as its not python post any ideas


How about JAVA ? I was going for python as well, But I have found the support was not very good , especially for the MAC platform. Java on the other hand seems to be both easier than C++ and implement most of the Libraries of C++ like SDL and be truly crossplatform.  

[http://jsdl.sourceforge.net/](http://jsdl.sourceforge.net/)

of course , there are alot more libraries out there written for java.

---

### Post by wrtpeeps on 2008-11-17
> **jimi_hendrix said:**
> new requirement:

free

Until you said this I was going to recommend XNA.

---

### Post by Zootropo on 2008-11-17
Maybe you should explain why you didn't like Python so that people now better what you are looking for.

Just a suggestion, of course.

PyGame uses SDL, btw.

---

### Post by slavik on 2008-11-17
Python OpenGL bindings are braindamaged by design. It's a price to pay when you must have exceptions as the only error detection mechanism.

Perl vs. other Langs comparison by the POGL maintainer.
[http://graphcomp.com/pogl.cgi?v=0111s3m3](http://graphcomp.com/pogl.cgi?v=0111s3m3)

---

### Post by jimi_hendrix on 2008-11-18
> **wrtpeeps said:**
> Until you said this I was going to recommend XNA.

thats free

and as requested i dont like python because i find if i write large programs i get lost in my variables and the indentation...

---

### Post by slavik on 2008-11-18
how much do you indent???

if you everything correctly and split your program up into proper pieces, you shouldn't be able to get lost.

---

### Post by samjh on 2008-11-19
Lua: the most widely used game scripting language in the world.

Lua-SDL: a library I have no idea on how to compile and use. :p

Try them, if you can figure out how to install them.  Lua as a language is easy, fast, and small.

Otherwise, I strongly recommend Java.

---

### Post by Greyed on 2008-11-19
There's a good reason why Lua is the most widely used **embedded** game scripting language.  It is also the same reason why it is ill suited as the primary language in which to create a game.  Namely it was designed to be embedded into other languages which provide all the heavy work.

---

### Post by curvedinfinity on 2008-11-19
[MirthKit]("http://www.mirthkit.com")?

I designed it specifically to be the easiest way to code and publish a small game.

---

### Post by curvedinfinity on 2008-11-19
Also, [www.processing.org](www.processing.org) is bad ***

---

### Post by olejorgen on 2008-11-19
(Common) Lisp :)

Sdl/opengl/gamelib:
[http://common-lisp.net/project/pal/](http://common-lisp.net/project/pal/)

Games using it:
[http://code.google.com/p/cletris/](http://code.google.com/p/cletris/)
[http://www.cliki.net/Bermuda](http://www.cliki.net/Bermuda)

Also:
[http://www.cliki.net/admin/search?words=game](http://www.cliki.net/admin/search?words=game)

There's lots of free lisp books. eg. On lisp, Practical Common Lisp

---

### Post by Luke has no name on 2008-11-19
Assembly?

---

### Post by pgatrick on 2008-11-19
> **olejorgen said:**
> (Common) Lisp :)

Sdl/opengl/gamelib:
[http://common-lisp.net/project/pal/](http://common-lisp.net/project/pal/)

Games using it:
[http://code.google.com/p/cletris/](http://code.google.com/p/cletris/)
[http://www.cliki.net/Bermuda](http://www.cliki.net/Bermuda)

Also:
[http://www.cliki.net/admin/search?words=game](http://www.cliki.net/admin/search?words=game)

There's lots of free lisp books. eg. On lisp, Practical Common Lisp

[A Gentle Introduction to Symbolic Computation]("http://http://www.cs.cmu.edu/~dst/LispBook/index.html") is another great book for learning lisp, and it's free. :D

---

### Post by nvteighen on 2008-11-19
> **jimi_hendrix said:**
> 
and as requested i dont like python because i find if i write large programs i get lost in my variables and the indentation...

Then, you'll lose yourself in any programming language... Split stuff!

Ok, if you don't like Python, the "nearest" would be Perl... but Perl requires some special attention, as it is developed focusing on semantics... So, if you compare an array against a number, Perl will test the array's length against the number and so on... Also, if you care, Perl is not OOP-native (though there are nice ways to get OOP in it).

It's a nice language, but you won't get something too different to what Python already offers.

Ah... my sig links to a game written in Scheme, doesn't that count? :p (ok, ok, it's a really experimental idea I'm working on, so forget it...)

---

### Post by Sacrifice on 2008-11-19
> **jimi_hendrix said:**
> thats free

and as requested i dont like python because i find if i write large programs i get lost in my variables and the indentation...


Yeah, he's right. You need to learn how to program more efficently; it's not the languages fault, it's yours. In all honesty. :P Use more precise variable names and not generic ones.

---

### Post by wmcbrine on 2008-11-19
> **jimi_hendrix said:**
> i dont like python because i find if i write large programs i get lost in my variables and the indentation...How do other languages help you with that?

---

### Post by jimi_hendrix on 2008-11-19
i dont know...when i tried the pygame tutorial i was half lost in the variables...i find C++ easier to follow (dont ask how)

---

### Post by Kilon on 2008-11-20
> **jimi_hendrix said:**
> i dont know...when i tried the pygame tutorial i was half lost in the variables...i find C++ easier to follow (dont ask how)


DELPHI .NET is also cross platform. The catch is that I do not know if it is available on Linux. Delphi used to have a special version for linux called Kylix but that was bedore the .NET. 

What makes DELPHI special besides being the easiest language I used and unlike python coming with all the libraries you will need, it was the first language to be truly OO a feature that languages like java and C# later copied. Also Java copied another feature from Delphi , JAVABEANS, which in DELPHI are called components. 

A big plus for Delphi is that is not only an enhanced Pascal language anymore. Delphi .NET is actually 3 languages and an excellent IDE , it is DELPHI +C# +VB.NET. So you can pick which one fits you best or even mix them as all three can work together. Another good news is that Delphi .NET not only has the .NET libraries but even Delphi's ow libraries called VLC. VLC are actually where the .NET has been based, for example if you compare VLC and Winforms you will find and enormous amount of similarities.  That is no suprise as Delphi programmers left Delphi and joined Microsoft to make .NET framework , Java and even Google. That is was when Delphi faced crisis and the product was almost dead. But now it is up and running again and with a very recent version that came out this August. 

Another good news is that the .NET part of the Delphi language is also Open source, something that does not apply for the other two .NET languages made by Microsoft. However the .NET of Delphi is tied to the IDE and the IDE is not free, the Personal version is very cheap though.

Here are the links if you are interested. 

Delphi and Linux 

[http://coding.derkeiler.com/pdf/Archive/Delphi/borland.public.delphi.non-technical/2007-06/msg03443.pdf](http://coding.derkeiler.com/pdf/Archive/Delphi/borland.public.delphi.non-technical/2007-06/msg03443.pdf)

Delphi .Net opensource

[http://delphinet.sourceforge.net/](http://delphinet.sourceforge.net/)

Turbo Delphi .NET (the IDE itself with all its glory)

[http://www.turboexplorer.com/delphinet](http://www.turboexplorer.com/delphinet)
 
The only thing that makes me hesitate use Turbo Delphi .NET and prefer Java is actually MONO, I am not fully  convinced about it true cross platform ability. But if you choose .NET my advice is do not waste your time with other IDEs, the do not offer even half of Delphi offers. Maybe eclipse , can change this opinion I am in the process of learning , but as a RAD tool there is no comparison with Delphi.

---

### Post by wmcbrine on 2008-11-20
> **Kilon said:**
> What makes DELPHI special besides being the easiest language I used and unlike python coming with all the libraries you will need, it was the first language to be truly OO a feature that languages like java and C# later copied.Eh, no. AFAIK, the first object-oriented language was Simula, followed by Smalltalk, C++, and a bunch of others, long before Delphi.

---

### Post by Kilon on 2008-11-20
> **wmcbrine said:**
> Eh, no. AFAIK, the first object-oriented language was Simula, followed by Smalltalk, C++, and a bunch of others, long before Delphi.

My fault , that I did not expain further.

By me saying "trully OO" languahe, do not mean a language which can do OO. I have studied C++ long before Delphi and I knew what OO was. 

A "trully OO" language for me is a language that its whole library is OO everywhere you look there is OO. Delphi was the first to enclose everything in objects, classes etc. from the first version. But even in the case I am wrong and there is other languages that done this as well earler, none has done it to the level of  Delphi. Java and later C# were the ones to copy this feature. 

Of course a language and by language I mean not just syntax but IDEs, Libraries, third party plugin and whatever , being fully enclosed in OO can be considered a bad thing. For example python is against this ideology and does not force OO unless is truly needed.   

So basically someone can argue that to that respece python is easier and he would be right. But what makes Delphi easier than python is the quality of tools that are RAD and can really help build applications very very fast, hiding unecessary complexity from the user. For example the Gui editor is still top of the tops plus the components which with simple drag n drop can save you from writing many pages of code. And the nice thing is that even though many things are hidden they are there for you to change and edit, if you wish to make your hands dirty. 

These are features that you can easily find in other IDEs and languages but not as concentrated as found in Delphi. Delphi might not be the best language , but it is a hidden diamond waiting to be found.

---

### Post by nvteighen on 2008-11-20
> **Kilon said:**
> 
By me saying "trully OO" languahe, do not mean a language which can do OO. I have studied C++ long before Delphi and I knew what OO was. 

A "trully OO" language for me is a language that its whole library is OO everywhere you look there is OO. Delphi was the first to enclose everything in objects, classes etc. from the first version. But even in the case I am wrong and there is other languages that done this as well earler, none has done it to the level of  Delphi. Java and later C# were the ones to copy this feature. 

Of course a language and by language I mean not just syntax but IDEs, Libraries, third party plugin and whatever , being fully enclosed in OO can be considered a bad thing. For example python is against this ideology and does not force OO unless is truly needed.   


Probably you mean "Object-oriented programming language" vs. "Multiparadigm language that, among others, supports OOP"? In the first group, you have Java, Smalltalk (and Ruby?). In the second, Python, C++, Common Lisp. But there is also a third group of languages in which you are capable of creating OOP using another paradigm (usually structured-procedural: C, Perl, for example). This last group is not OOP-native, but allows you to create OOP.

Other languages, like Assembly or BASIC, just don't allow OOP.

---

### Post by Kilon on 2008-11-20
> **nvteighen said:**
> Probably you mean "Object-oriented programming language" vs. "Multiparadigm language that, among others, supports OOP"? In the first group, you have Java, Smalltalk (and Ruby?). In the second, Python, C++, Common Lisp. But there is also a third group of languages in which you are capable of creating OOP using another paradigm (usually structured-procedural: C, Perl, for example). This last group is not OOP-native, but allows you to create OOP.

Other languages, like Assembly or BASIC, just don't allow OOP.

Yes you are correct, that is the proper way of addressing the issue. Thank you for showing me the proper way to address it with proper terminology. 

Of course here my emphasis is not a library which simply does not comply with OO principles. But generally the fact that the Library is well organised.

For example I was a C++ lover but when I tried to move to windows programming from msdos I came face to face with Windows MFC. MFC Gui deisgn was a joke, everything were really messed up, difficult to remember and did not make sense largely based on functional programming. 

Then Delphi came and its VCL(Visual Component Library) where everything belonged to a class which inherited functions from father classes and all was well organized and made perfectly sense. Of course now this type of programming is pretty much standard in C# and Java or even python but then when I sat down , MFC was the only other choice ( i think it was 1995 or somewhere around that time) . 

  
Now GUI programming  with most programming languages has really improved and it owes alot to Delphi. I love to see now that these things are considered the minimum and not the maximum as once were.

I would like to additionally emphasize here that people are overly concerned with choosing the righ languages. IDEs , libraries and other tools come second or third. I think this way of thinking is plain wrong. For instance a issue that I had with python is documentation, another big issue that someone must consider. 

So you sit down and ask yourself what is the easiest language for making games and after days of search even months it should not surpise you if your quest take you back to your "difficutl" choice. What seams easy today might proven difficult tomorrow cause needs changing all the time. Maybe that is why it preferable even though time consuming to know pretty much most languages and of course their librires , IDEs etc. 

For example I have invested in JAVA but I keep learning .NET just in case. Python is not out of my agenda either. I love to have many options.

---

### Post by samjh on 2008-11-20
Can we please get back on topic? ;)

---

### Post by Kazade on 2008-11-20
I guess it depends on what type of game you are developing? Is speed an issue? I mean, if you are writing Doom4 you wouldn't do it in Python or Ruby. But if you are writing SuperTux2 then you might...

If you are after speed, but don't like the hair-brained complexity of C++ (I love it, but I'm weird ;) ) then take a look at D. It compiles to ASM and can use C libraries (SDL, OpenAL etc.) but it's a far more sensible language than C++..

That said, it is quite an immature language so you might find documentation difficult to find.

Otherwise, I'd stick with Python. It's easy, it works and it's portable.

---

### Post by Kilon on 2008-11-20
> **samjh said:**
> Can we please get back on topic? ;)
When we actually left ? Are we not discussing RAD for games?

---

### Post by jimi_hendrix on 2008-11-20
> **Kazade said:**
> I guess it depends on what type of game you are developing? Is speed an issue? I mean, if you are writing Doom4 you wouldn't do it in Python or Ruby. But if you are writing SuperTux2 then you might...

If you are after speed, but don't like the hair-brained complexity of C++ (I love it, but I'm weird ;))
im weird too lol
> **Kilon said:**
> When we actually left ? Are we not discussing RAD for games?

fastest language to make a game in

---

### Post by Kilon on 2008-11-20
> **jimi_hendrix said:**
> im weird too lol


fastest language to make a game in


R.A.D = Rapid Application Development , is actually what you are searching here and alot more , because is not only the language you should be concerned with. Thus I was never out of topic.

For more info what RAD is check these links

[http://www.webopedia.com/TERM/R/Rapid_Application_Development.html](http://www.webopedia.com/TERM/R/Rapid_Application_Development.html) 

[http://209.85.129.132/search?q=cache:lKJ2kr2LxcMJ:en.wikipedia.org/wiki/Borland_Delphi+delphi+rad&hl=en&ct=clnk&cd=1](http://209.85.129.132/search?q=cache:lKJ2kr2LxcMJ:en.wikipedia.org/wiki/Borland_Delphi+delphi+rad&hl=en&ct=clnk&cd=1)

unless you are talking about speed of execution. Sorry then I did not relised it. Though we were talking about speed of development. But again my advice is on topic cause Delphi has the same execution speed as C++ programms and Delphi .NET the same execution speed with .NET applications. So you wont face any slow downs. Delphi can also write and communicate directly with C++ and Assembly code.

---

### Post by SeanHodges on 2008-11-20
> **jimi_hendrix said:**
> fastest language to make a game in

In terms of performance, Assembly language, C or C++.

In terms of RAD, and excluding Python; probably Flash using Eclipse FDT ([http://fdt.powerflasher.com/](http://fdt.powerflasher.com/)) or the Flex SDK.

If by "Free" you meant freedom, there are numerous options, but Ruby/SDL is a good option to consider.

---

### Post by ufis on 2008-11-20
I am no expert on game development or have had enough exposure to compare in depth development of various programming languages so I'll just tell you what I know.

You have mentioned "games", but there are various types of games (in terms of graphics). From your text based, to 2D and then 3D.

As a java developer I have been looking for ways to develop games in, you guessed it, java. And along comes Java3D. Read more at [https://java3d.dev.java.net/](https://java3d.dev.java.net/)

It may or may not be the fastest way to develop a game (for me it is the fastest because it is what I know best :) ) but it is a viable option.

---

### Post by Jonas thomas on 2008-11-20
This might be slight OT but.....
My daugther have spent much bonding time on [http://pbskids.org/fetch/games/coaster/game.html]("http://pbskids.org/fetch/games/coaster/game.html") and other games on pbskids.org.
For purely web-based app's these have impressed me.  Does anyone know the languages/applications used.  I'm assuming Flash.... Java...??? I don't know how quick to develop these languages are (notice I trying to be on-topic), but they are impressive (to me at least).

---

### Post by skullmunky on 2008-11-22
If you don't want C++ because you want clearer code, I also recommend Processing instead of straight Java for rapid development.  

Don't give up on python too quickly ... though I'll put in another vote for mirthkit as an alternative to pygame.

If you want to make 3D games very quickly try panda3d.  

If you want to make 3D games a little less quickly but with a totally  excessive amount of visual awesomeness try python-ogre.

---

### Post by doktor_apokalypse on 2008-11-28
> **pgatrick said:**
> [A Gentle Introduction to Symbolic Computation]("http://http://www.cs.cmu.edu/~dst/LispBook/index.html") is another great book for learning lisp, and it's free. :D

That book is probably *the* best to get started with.

---

