---
title: "Is C as bad as everyone says C++ is?"
date: 2008-09-20
forum: Programming Talk
---

### Post by Exershio on 2008-09-20
Well, I'm about to dive into some lower level programming, having been programming in C# (windows) and Python for a while. "C++ is a messy/frustrating/etc language" is something I hear rather often on the programming boards I visit. However, what about just plain C? 

Is it as masochistic to use as a lot of people say C++ is?

---

### Post by LaRoza on 2008-09-20
[http://ubuntuforums.org/showthread.php?p=4716120](http://ubuntuforums.org/showthread.php?p=4716120)

C isn't C++. C is a small, compact language.

It is painful to do certain things in C however, because of its simplicity.

---

### Post by Exershio on 2008-09-20
I know C isn't C++. My point was I heard C++ is a bad language to use, so I was asking is C (which C++ is based off of) any better.

---

### Post by LaRoza on 2008-09-20
> **Exershio said:**
> I know C isn't C++. My point was I heard C++ is a bad language to use, so I was asking is C (which C++ is based off of) any better.

Well, you should ask those who say those things about C++ ;)

For anyone who hates C++, C is usually better favoured.

You are asking something very subjective, and I don't want to say how useless and arcane C++ is, so I won't.

---

### Post by lisati on 2008-09-20
The minimal amount of programming I've done in C (which, as LaRoza has pointed out, is a different beast to C++) suggests that in some ways it's a lot tidier than some of the other programming languages I've tried. All languages have their strengths and weaknesses...

---

### Post by pmasiar on 2008-09-20
Both C and C++ are excellent languages, if you use them in areas they were designed for:

C++ for huge projects where OOP and namespaces are important part of the solution, and you need all the speed you can get, AND you are ready to pay the price for the speed in the time and effort required to get reliable solution (hint: it will be NOT easy).

C for projects where speed is even more important (so you are not ready to pay even for  little OOP polymorfic magic) and where skills and experience, coding discipline and project managers of participants are on par to the task: because changes in huge codebase with plenty of global names are easy to bork, and skills to handle ** and even *** pointers is paid by chunks of hairs torn, bloody eyes by all night debugging, and barrels of coffee.

Of course using C or C++ on the whim if you don't need the features is like trying to make opening in the wall by banging your head: some people will like the attitude, but most people will make couple steps aside where is the door (more productive languages).

So as always it depends what you need: hacking kernel or drivers? C is your tool. Competing in speed with other team, or writing your own file system, with unlimited budget? C++ is fine. 

But writing CGI app in C++? You must enjoy the pain.

C is simple language where lots of stuff C++ handles for you you have to do manually, by proper project management. In small projects it does not matter, when you have 1MLOC it does 8-)

---

### Post by kavon89 on 2008-09-20
> **pmasiar said:**
> 
C++ for huge projects where OOP and namespaces are important part of the solution, and you need all the speed you can get, AND you are ready to pay the price for the speed in the time and effort required to get reliable solution (hint: it will be NOT easy).

C for projects where speed is even more important (so you are not ready to pay even for  little OOP polymorfic magic) and where skills and experience, coding discipline and project managers of participants are on par to the task: because changes in huge codebase with plenty of global names are easy to bork, and skills to handle ** and even *** pointers is paid by chunks of hairs torn, bloody eyes by all night debugging, and barrels of coffee.

That's gotta be the best explanation of C or C++ I've ever seen. :lolflag:

---

### Post by slavik on 2008-09-21
C is the bee's knees!!!

But besides that, no matter the language you use, it is possible to organise code in such a way that makes sense but the more the language is free, the harsher the style has to be.

Higher level languages make certain algorithms and structures easier to write and understand in fewer words. (Simple example: linked list) They also have a more rigid hierarchy (namespaces, objects, etc).

here's a comparison: [http://www.fullduplex.org/humor/2006/10/how-to-shoot-yourself-in-the-foot-in-any-programming-language/](http://www.fullduplex.org/humor/2006/10/how-to-shoot-yourself-in-the-foot-in-any-programming-language/)

---

### Post by Sockerdrickan on 2008-09-21
As said before C is very compact, I made this image to make you understand (small amount of keywords makes it harder to do stuff).

---

### Post by dribeas on 2008-09-21
> **Exershio said:**
> "C++ is a messy/frustrating/etc language" is something I hear rather often on the programming boards I visit.

Those are comments out of prejudice and not really knowing the language. On the other hand learning C++ is harder and takes more time than most other languages.

On C. C is simple, really simple. That means that it is easy to learn the language, but where python/java/c# have a huge library, C's library is really small.

---

### Post by cb951303 on 2008-09-21
C and C++ are two of the most powerful programming languages that exists today. So I wouldn't believe what they say about C++.

If you really want some examples, %99 of linux (kernel) is made of pure C.
Most of the  3D mainstream games such as quake4, doom3, crysis etc... are made of C++. So you see, these are huge and important projects. I don't think they would use C or C++ if they were "messy/frustrating/etc" :lolflag:

if you want to learn some low level stuff C is the way to go. I started with C years ago and I still use it as my main language. :popcorn:

---

### Post by CptPicard on 2008-09-21
> **dribeas said:**
> Those are comments out of prejudice and not really knowing the language. On the other hand learning C++ is harder and takes more time than most other languages.

The latter sentence really sort of proves the complaints about C++... if a language is particularly hard to learn and takes more time to use right than other languages, something is wrong with the language, IMO. I personally feel my own reservations about C++ really don't come from not "properly knowing" the language -- my exposure to C++ has been sufficient for me to decide that I really see no reason to "properly know" all the stuff I need to know to be a (really professional-level) competent C++ coder.

> **cb951303 said:**
> C and C++ are two of the most powerful programming languages that exists today. So I wouldn't believe what they say about C++.

How do you define "power"? We've had these discussions a lot on this forum... there seems to be this strange belief that the closer to the machine you are, the more powerful a language is, which completely disregards expressive power, the ability to conceptualize effectively in the language.

> If you really want some examples, %99 of linux (kernel) is made of pure C.
Most of the  3D mainstream games such as quake4, doom3, crysis etc... are made of C++. So you see, these are huge and important projects. I don't think they would use C or C++ if they were "messy/frustrating/etc" :lolflag:


The reason why kernel uses C is hardware interfacing and low-level resource management, which is what kernel is really there to do in the first place -- so what you want is a syntactic sugar layer on top of assembly, essentially. Other reason is runtime speed, why 3D mainstream games use C++ which further gives you the OOP stuff.

The same runtime speed advantages are achievable in most other languages which compile to native, and I can easily see a lot of them being "cleaner" as languages than C++ is. Interestingly, these days a lot of non-native-compiled languages can handle 99% of your codebase in a lot more higher-level way...

---

### Post by cb951303 on 2008-09-21
> **CptPicard said:**
> 
How do you define "power"? We've had these discussions a lot on this forum... there seems to be this strange belief that the closer to the machine you are, the more powerful a language is, which completely disregards expressive power, the ability to conceptualize effectively in the language.
you're mistaken me with a C/C++ fanboi. I didn't say they were the only powerful ones.

> 
The reason why kernel uses C is hardware interfacing and low-level resource management, which is what kernel is really there to do in the first place -- so what you want is a syntactic sugar layer on top of assembly, essentially. Other reason is runtime speed, why 3D mainstream games use C++ which further gives you the OOP stuff.

I'm well aware of what you stated here however it only proves that C is a powerful language

> 
The same runtime speed advantages are achievable in most other languages which compile to native, and I can easily see a lot of them being "cleaner" as languages than C++ is. Interestingly, these days a lot of non-native-compiled languages can handle 99% of your codebase in a lot more higher-level way... than why the big gaming companies like EA, ID Software, Blizzard etc. chose C++ over your cleaner native compiled languages...

I understand that there are other languages, very powerful ones. But bashing C or C++ is just ridiculous since they are very popular languages. In fact according to [this]("http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html") C/C++ is the number 1 and 2 most popular native compiled languages.

---

### Post by pp. on 2008-09-21
> **cb951303 said:**
> I'm well aware of what you stated here however it only proves that C is a powerful language

As a matter of fact, it proves that you can exert a very fine level of control over how the processor runs your program. With other languages, you can conduct thousands of instructions with one fell swoop, if that's the expression I'm looking for.

Which is more 'powerful' in the sense you're looking for, the tweezer or the bulldozer?

---

### Post by cb951303 on 2008-09-21
> **pp. said:**
> As a matter of fact, it proves that you can exert a very fine level of control over how the processor runs your program. With other languages, you can conduct thousands of instructions with one fell swoop, if that's the expression I'm looking for.

Which is more 'powerful' in the sense you're looking for, the tweezer or the bulldozer?

why is that the word powerful bothers you so much? having control over how processor runs is a powerful side of C. 

bad analogy BTW, you can tell which one is more powerful by looking their specs.

---

### Post by CptPicard on 2008-09-21
> **cb951303 said:**
> 
I'm well aware of what you stated here however it only proves that C is a powerful language

It just proves that it is a good technical fit for purpose in that case, for some specific reasons present in these particular application domains.

> 
 than why the big gaming companies like EA, ID Software, Blizzard etc. chose C++ over your cleaner native compiled languages...

Popularity is a weak argument because of the way [Sturgeon's law]("http://en.wikipedia.org/wiki/Sturgeon%27s_law") applies to software developers. 

Of course, the fundamental reason here *still* is just runtime speed advantage, and that edge is fast eroding. 

I am not in general a huge fan of any C-derivative, and not a C++ fan in particular because of the excess complexity and huge amount of "language quirks" *and* OO design you must master to get anything out of the language. For a decent attempt at ironing out C++'s issues, look at the D language...

> 
I understand that there are other languages, very powerful ones. But bashing C or C++ is just ridiculous since they are very popular languages.

It's not ridiculous if there are good reasons to see C++ as a [bloated monstrosity]("http://yosefk.com/c++fqa/defective.html")...

---

### Post by cb951303 on 2008-09-21
> **CptPicard said:**
> It just proves that it is a good technical fit for purpose in that case, for some specific reasons present in these particular application domains.
 thus very powerful in that domain. 

> 
Popularity is a weak argument because of the way [Sturgeon's law]("http://en.wikipedia.org/wiki/Sturgeon%27s_law") applies to software developers. 
 actually it's not weak since there is a reason its so popular.

> 
Of course, the fundamental reason here *still* is just runtime speed advantage, and that edge is fast eroding. it's like your saying c++ is not powrful but in some areas its very good. I don't understand your logic.

> 
I am not in general a huge fan of any C-derivative, and not a C++ fan in particular because of the excess complexity and huge amount of "language quirks" *and* OO design you must master to get anything out of the language. For a decent attempt at ironing out C++'s issues, look at the D language...
well its just not enough to bash c++. its bigger than that.

> 
It's not ridiculous if there are good reasons to see C++ as a [bloated monstrosity]("http://yosefk.com/c++fqa/defective.html")...
have I in any way stated that C++ is a perfect language? Which language is perfect? D? Again it's just not good enough reason to bash C++.

---

### Post by nvteighen on 2008-09-21
> **Tux0r said:**
> As said before C is very compact, I made this image to make you understand (small amount of keywords makes it harder to do stuff).

Sorry, you missed one: the mythical "entry" keyword :): never implemented, never defined and nobody ever knew what it was meant to be...

But, about the topic:

You want us to compare two languages that, even if they are very related, have almost the same syntax, but exactly the same "look-and-feel", are two different languages. Yes, C++ was initially an extension to C, but now it isn't.

I don't know any C++, so I won't comment on it.

C is a very tiny language, the next step in the "Abstraction scale" after Assembly, it just gives you some data types (that actually are just memory chunks of different sizes), a way to combine data types into more complex ones (struct), control flow and I just can't think of any other feature C has... because it doesn't need it for what it was meant for. If you code in C and begin to miss polymorphic OOP, lambda closures or some document formatting mark-up like XML, you're using the wrong language, even if you can write C code to implement those things... and therefore, waste a lot of time in creating extensions to C for a problem you just could do easily on a higher-level language.

If you use C for what is meant to: i.e kernels, drivers, low-level libraries, system utilities that can't depend on an interpreter(like a shell), etc. C's simplicity and low-levelness are an advantage as they give the computer less stuff to process and also some shortcuts to control computer resources more efficiently (something you definitely want for your super-new-brand kernel).

But, outside that, C's simplicity becomes a burden, unless you start making extensive usage of external libraries just to get things other languages already have (e.g. using GLib to have a list data type, when Python has a native one), or worse, you don't even look what libraries there are and start coding everything by yourself.

Higher-level languages, and that includes C++, which is definitely higher-level than C, have more expressive power... but usually at the cost of runtime speed. Your language choice should depend on what you need or want... If you want extreme expression in order to talk about "dogs", "cakes" and "eating" in your program, go for Lisp... and eventually you can have "cake-eating dogs" in your program. If you want to run at lightspeed, use Assembly or C... If you need speed and some object abstraction, there you have C++.

If your problem involves stuff not specific to the computer internals, then avoid C. If you need access to that stuff, use it and avoid anything else.

---

### Post by Sinkingships7 on 2008-09-21
> **cb951303 said:**
> 
why is that the word powerful bothers you so much? 


It's because 'powerful' can be defined in more ways than one. When you say 'powerful', you seem to imply that the more lower-level access you have to the machine, the more 'powerful' you become. However, when experienced programmers (with perhaps degrees or jobs - those experienced by age) speak of power, they usually mean in terms of the most efficient way to get things done. 

Hacking in C/C++ does not necessarily make you a more 'powerful' programmer. C is used where low-level access is required, like in our precious kernel. C++ is used in large projects, where abstract methods are required to keep the programmers sane, and also because it was the first of it's paradigm to gain popularity in the 80's and 90's. Because of the (very) large amount of people who jumped on that bandwagon, it's still used a lot today, though less and less.

---

### Post by CptPicard on 2008-09-21
> **cb951303 said:**
> thus very powerful in that domain.

Runtime speed advantage is a marginal benefit if the rest of the language is nasty to code in...

> 
 actually it's not weak since there is a reason its so popular.

As I said, Sturgeon's law says 90% of developers are crap, so therefore, they're wrong and satisfied to just use whatever is handed to them (this is valid in somewhat different sense for Java and C#). If they were right, we could just agree to use C++ for all eternity and forget about all our further language development efforts :)

The saddest part is that they're spending their intellectual resources in misguided attempts to *manage C++* instead of *managing the problem* (or maybe writing a language from scratch with all the cruft and baggage thrown out).

> 
 it's like your saying c++ is not powrful but in some areas its very good. I don't understand your logic.

No, I am not saying that C++ is "very good" at anything -- being a mediocre middle ground solution in a lot of stuff is in some sense why it's popular and why it's not "great". It seems to somehow get the job done in OOP modelling sense and gives decent performance, but *that* still doesn't make it forgivable that you need to master endless amounts of C++-specific minutiae not to trip up with the language.

> 
well its just not enough to bash c++. its bigger than that.

It is interesting how criticism is to be taken as "bashing" when there is an urgent need to ignore the criticism.

> 
have I in any way stated that C++ is a perfect language?

No, and you never needed to say that to cause me to state that it is too troublesome for what it's worth.

> Which language is perfect? D?

Well, Lisp does come close... :)

---

### Post by Wybiral on 2008-09-21
> **cb951303 said:**
> it's like your saying c++ is not powrful but in some areas its very good. I don't understand your logic.

No, it's like he's arguing against your statement of C and C++ being the most powerful, especially since we have not defined "power".

Is power a matter of performance? You can hand-craft some assembly to perform better than C++, so is assembly more powerful? I've seen brainfuck compilers that reach some ridiculous speeds too, we should probably regard brainfuck as one of the most powerful as well.

Are they more powerful for multi-threading or multi-process development?

Is power expressibility? Readability? The ability to type less and do more?

Are C and C++ more powerful in a domain like web applications? Should we write C->to->JavaScript compilers so we can write browser-end code in C as well?

Perhaps you mean power in terms of text processing and string handling... I bet C is more powerful than Perl or Python in that domain, eh?

What do you mean by "power"?

---

### Post by pp. on 2008-09-21
> **cb951303 said:**
> why is that the word powerful bothers you so much? having control over how processor runs is a powerful side of C. 

As others have said, the only 'problem' with the word 'powerful' lies with the definition. 

If having control over how a processor runs makes a language powerful, Assembly is the most powerful language there is, unless you gain access to the processor's micro code.

---

### Post by CptPicard on 2008-09-21
> **Wybiral said:**
> No, it's like he's arguing against your statement of C and C++ being the most powerful, especially since we have not defined "power".

In the interests of intellectual integrity, he really didn't make the claim of C++ being "the most powerful".

Then again it is not the point at all -- essentially the position I am defending here is the idea that the objective meanings of "power" that I am mostly interested in do not have that much to do with runtime speed -- you can always increase runtime speed by buying a bigger machine, and it has nothing to do with the language's "nature" from programmer's perspective. On the other hand if we're going to turn the issue of "power" into a totally subjective one that always depends completely on application domain, the discussion itself becomes rather meaningless.

So while C++ is being "practically" used for some specific reasons, just simple momentum being one of them, it doesn't invalidate any of the actual complaints about the language being remarkably full of pitfalls and difficulty you have to learn to code around and live with.

---

### Post by cb951303 on 2008-09-21
> **Wybiral said:**
> No, it's like he's arguing against your statement of C and C++ being the most powerful, especially since we have not defined "power".

Is power a matter of performance? You can hand-craft some assembly to perform better than C++, so is assembly more powerful? I've seen brainfuck compilers that reach some ridiculous speeds too, we should probably regard brainfuck as one of the most powerful as well.

Are they more powerful for multi-threading or multi-process development?

Is power expressibility? Readability? The ability to type less and do more?

Are C and C++ more powerful in a domain like web applications? Should we write C->to->JavaScript compilers so we can write browser-end code in C as well?

Perhaps you mean power in terms of text processing and string handling... I bet C is more powerful than Perl or Python in that domain, eh?

What do you mean by "power"?

I read only the first sentence of your post since it show that you didn't read any of mine. I didn't say anything about C/C++ bein 'most' powerful

read first than comment

---

### Post by cb951303 on 2008-09-21
> **Sinkingships7 said:**
> It's because 'powerful' can be defined in more ways than one. When you say 'powerful', you seem to imply that the more lower-level access you have to the machine, the more 'powerful' you become. However, when experienced programmers (with perhaps degrees or jobs - those experienced by age) speak of power, they usually mean in terms of the most efficient way to get things done.  I imply that? where? efficient is not a good choice of word here since C is an efficient language.

> 
Hacking in C/C++ does not necessarily make you a more 'powerful' programmer. C is used where low-level access is required, like in our precious kernel. C++ is used in large projects, where abstract methods are required to keep the programmers sane, and also because it was the first of it's paradigm to gain popularity in the 80's and 90's. Because of the (very) large amount of people who jumped on that bandwagon, it's still used a lot today, though less and less.

I also didn't say that it will make me a more powerful programmer. Jesus, You guys need to learn how to read. I feel like arguing with fanatics here.
Also C++ is definitely not the first of its paradigm.

---

### Post by pp. on 2008-09-21
> **cb951303 said:**
> efficient is not a good choice of word here since C is an efficient language....
You guys need to learn how to read.

You might assist the process of reading your posts correctly by supplying a definition or two.

Please define 'powerful' and 'efficient' as applied by you to programming languages.

'Programming language A is more powerful than programming language B if programming language A  (...) programming language B'

'Programming language A is more efficient than programming language B if programming language A (...) programming language B'.

Once you have done so, we might attempt to order a selection of programming languages by some scalars expressing 'power' and/or 'effiency' of those languages.

Until then, we might as well discuss the taste, color or weight of those languages.

---

### Post by cb951303 on 2008-09-21
> 
As I said, Sturgeon's law says 90% of developers are crap, so therefore, they're wrong and satisfied to just use whatever is handed to them (this is valid in somewhat different sense for Java and C#). If they were right, we could just agree to use C++ for all eternity and forget about all our further language development efforts :)
it's just one argument not a real law. you can't use as a fact. Frankly I found that statement quite amusing.

> 
The saddest part is that they're spending their intellectual resources in misguided attempts to *manage C++* instead of *managing the problem* (or maybe writing a language from scratch with all the cruft and baggage thrown out).

I would like to hear more about that. Some examples maybe?

> 
No, I am not saying that C++ is "very good" at anything -- being a mediocre middle ground solution in a lot of stuff is in some sense why it's popular and why it's not "great". It seems to somehow get the job done in OOP modelling sense and gives decent performance, but *that* still doesn't make it forgivable that you need to master endless amounts of C++-specific minutiae not to trip up with the language.
C++ has its disadvantages but its nothing dramatical as you describe it. Again no language is perfect. It doesn't mean they are not powerful. Also since when mastering *anything* become unnecessary or bad practice?

> 
It is interesting how criticism is to be taken as "bashing" when there is an urgent need to ignore the criticism.
 not true. It's just a bad choice of word by me. English is not my mother language. I was implying that your complaints about C++ are all superficial. Despite all the people, professionals and gurus using C++ in many projects, you find in yourself the right to call them crap (well at least 90% of them). I don't think you have enough knowledge to conclude that.

> 
Well, Lisp does come close... :)then use it by any means

---

### Post by Sinkingships7 on 2008-09-21
> **cb951303 said:**
> 
I imply that? where? efficient is not a good choice of word here since C is an efficient language.


You say it right here:

[quote=cb951303]
C and C++ are two of the most powerful programming languages that exists today.
[/quote]

You claim that C is an 'efficient' language. It is efficient ONLY where it's practical application is. It is not powerful, as you say. It does what it was designed for fairly well, which is providing a further layer of abstraction to assembly to allow programmers to have low-level access to the machine for dealing with drivers or kernels: where it is needed.


[quote=cb951303]
Also C++ is definitely not the first of its paradigm.
[/quote]

Read again.

[quote=Sinkingships7]
[...] and also because it was the first of it's paradigm **to gain popularity** [...]
[/quote]

---

### Post by Wybiral on 2008-09-21
> **cb951303 said:**
> I read only the first sentence of your post since it show that you didn't read any of mine. I didn't say anything about C/C++ bein 'most' powerful

read first than comment

I did read your reply, and you said: 
> C and C++ are two of the most powerful programming languages that exists today. So I wouldn't believe what they say about C++.

So you didn't say that they were "the [only] most powerful", but you said "two of the most powerful" which is what my reply was about, but I guess not reading my reply is a nice way to avoid having to explain yourself.

---

### Post by cb951303 on 2008-09-21
> **pp. said:**
> You might assist the process of reading your posts correctly by supplying a definition or two.

Please define 'powerful' and 'efficient' as applied by you to programming languages.

'Programming language A is more powerful than programming language B if programming language A  (...) programming language B'

'Programming language A is more efficient than programming language B if programming language A (...) programming language B'.

Once you have done so, we might attempt to order a selection of programming languages by some scalars expressing 'power' and/or 'effiency' of those languages.

Until then, we might as well discuss the taste, color or weight of those languages.

pp when are you going to read my first post? My statement was > C and C++ are two of the most powerful programming languages that exists today

I didn't compare C/C++ to any language. got it? That's why I don't need to define it. Or should I define every adjective that use to you? 

The word efficient is brought by someone else. I was responding him. 

Realy! Start reading.

---

### Post by cb951303 on 2008-09-21
> **Wybiral said:**
> I did read your reply, and you said: 


So you didn't say that they were "the [only] most powerful", but you said "two of the most powerful" which is what my reply was about, but I guess not reading my reply is a nice way to avoid having to explain yourself.

So? You see that I didn't say the [only] ... My sentence means: there are some powerful languages and C/C++ are two of them... I don't see the wrong here.

---

### Post by Wybiral on 2008-09-21
> **cb951303 said:**
> Jesus, You guys need to learn how to read. I feel like arguing with fanatics here.

We did read your reply, you just seem to not remember it or something.

---

### Post by slavik on 2008-09-21
> **Tux0r said:**
> As said before C is very compact, I made this image to make you understand (small amount of keywords makes it harder to do stuff).
Lisp has 7 basic constructs ...

---

### Post by Wybiral on 2008-09-21
> **cb951303 said:**
> So? You see that I didn't say the [only] ... My sentence means: there are some powerful languages and C/C++ are two of them... I don't see the wrong here.

Exactly, you'll notice I never used "only" either. Now, read my reply... I read yours. I'll give you a few minutes.

Hint: wtf does power mean?

---

### Post by Sinkingships7 on 2008-09-21
As a few others have stated, I'd like to know how you define 'power' before this discussion continues.

---

### Post by pp. on 2008-09-21
> **cb951303 said:**
> pp when are you going to read my first post? My statement was 

> C and C++ are two of the most powerful programming languages that exists today 

I didn't compare C/C++ to any language. got it? That's why I don't need to define it. Or should I define every adjective that use to you? 

The word efficient is brought by someone else. I was responding him. 

Realy! Start reading.

The statement "A is one of the most powerful programming languages" is equivalent to "the number of programming languages that are more powerful than A is far less than the number of programming languages which are less powerful than A".

Hence, you are comparing language A to the set of languages in existence today. 

However, the statement has no practical meaning since it does in no way indicate the means by which to establish if language A is more, equally or less powerful than any other language. 

Does "more powerful" mean it has a larger vocabulary, generates more machine instructions per statement coded, is better liked by more people?

And please stop accusing other people of not reading your posts properly.

---

### Post by cb951303 on 2008-09-21
> **Sinkingships7 said:**
> You say it right here: hmmm I really don't see such implying there. Heck I didn't even use the word low-level. Could it be that you overthink?


> 
You claim that C is an 'efficient' language. It is efficient ONLY where it's practical application is. It is not powerful, as you say. It does what it was designed for fairly well, which is providing a further layer of abstraction to assembly to allow programmers to have low-level access to the machine for dealing with drivers or kernels: where it is needed.
 So? tell me any language that is efficient in all domains? None! So which language will we call efficient then?

> 
Read again.I stand corrected

---

### Post by cb951303 on 2008-09-21
> **Wybiral said:**
> Exactly, you'll notice I never used "only" either. Now, read my reply... I read yours. I'll give you a few minutes.

Hint: wtf does power mean?

the most powerful (this is what you stated that I have said) != two of the most powerful (this is what I actually said)

---

### Post by Kadrus on 2008-09-21
> two of the most powerful (this is what I actually said)
But still...what do you mean by power?because you havent explained yet,or you seem to be trying to avoid explaining.

---

### Post by Wybiral on 2008-09-21
This reminds me of a Paul Graham article: [http://www.paulgraham.com/power.html](http://www.paulgraham.com/power.html)

---

### Post by cb951303 on 2008-09-21
> **pp. said:**
> The statement "A is one of the most powerful programming languages" is equivalent to "the number of programming languages that are more powerful than A is far less than the number of programming languages which are less powerful than A".

Hence, you are comparing language A to the set of languages in existence today.

believe me I wasn't comparing it to any language. I was simply stating that C and C++ are high on the good programming languages list. Of course it has a comparison meaning in it but It wasn't the underlined idea. 
I'm still not convinced about C++ not being a good programming language though. 

> 
However, the statement has no practical meaning since it does in no way indicate the means by which to establish if language A is more, equally or less powerful than any other language. 

Does "more powerful" mean it has a larger vocabulary, generates more machine instructions per statement coded, is better liked by more people?

good optimization, speed, simplicity(for C), OOP concepts(for C++), wide range of tools, popularity are some of that I think of right now.

> 
And please stop accusing other people of not reading your posts properly.

actually I will keep saying that as long as you claim that most powerful language = one of the most powerful language

---

### Post by cb951303 on 2008-09-21
> **Kadrus said:**
> But still...what do you mean by power?because you havent explained yet,or you seem to be trying to avoid explaining.

I'm not avoiding. It's just not the subject of the discussion. Since I didn't state that C/C++ are the most powerful languages.

---

### Post by Kadrus on 2008-09-21
> C and C++ are high on the good programming languages list
The **good** programming languages list?
Most people think that the **best** languages are C#,Java,C++,etc.
> good optimization, speed, simplicity(for C), OOP concepts(for C++), wide range of tools, popularity are some of that I think of right now.
My opinion is:it doesn't matter what programming language you use,as long as you keep it simple...and C++ surely doesn't do that.
You talk about OOP,speed,etc..OCaml has object orientation,is as fast as C,is a functional programming language,that can be an alternative to Cpp,in which you can write better code,simpler code,shorter coder,and more maintainable code.
[C++ Vs OCaml:Ray Tracer Comparaison.]("http://www.ffconsultancy.com/languages/ray_tracer/comparison.html")
All I want is simplicty,and C++ doesn't provide that.

[I]I'm going to say it now: programming fashions are stupid and counterproductive. The only things that matter are that your program is short, easy to write, easy to maintain and works correctly. How you achieve this has nothing to do with programming fads.
[/I] - [Richard W.M Jones]("http://www.annexia.org/")

---

### Post by cb951303 on 2008-09-21
> **Kadrus said:**
> The **good** programming languages list?
Most people think that the **best** languages are C#,Java,C++,etc.
 wow be careful, I only said powerful and got everyone's attention. I would think twice before saying **best** :)

> 
My opinion is:it doesn't matter what programming language you use,as long as you keep it simple...and C++ surely doesn't do that.
You talk about OOP,speed,etc..OCaml has object orientation,is as fast as C,is a functional programming language,that can be an alternative to OCaml,in which you can write better code,simpler code,shorter coder,and more maintainable code.
[C++ Vs OCaml:Ray Tracer Comparaison.]("http://www.ffconsultancy.com/languages/ray_tracer/comparison.html")
All I want is simplicty,and C++ doesn't provide that.

[I]I'm going to say it now: programming fashions are stupid and counterproductive. The only things that matter are that your program is short, easy to write, easy to maintain and works correctly. How you achieve this has nothing to do with programming fads.
[/I] - [Richard W.M Jones]("http://www.annexia.org/")

This is what I was afraid of. I said why I think C/C++ is powerful now everbody will compare it to their favorite language. since I don't knwo anything about OCaml I can't comment but I know this: there ill be always a better language according to somebody else. And believe me they will have convincing arguments.

---

### Post by pp. on 2008-09-21
> **cb951303 said:**
> 
good optimization, speed, simplicity(for C), OOP concepts(for C++), wide range of tools, popularity are some of that I think of right now.

by my purely subjective evaluation:
optimization: I was not aware that C++ actually did optimize the compiled code but are prepared to learn better if so. Java ought to win with respect to optimization with its optimizing JIT compiler.

speed: If speed of execution is meant, then Assembly ought to be fastest if you really go to the trouble of actually optimizing your code. If speed to market is your goal, then a great many other languages are better suited for almost every application domain.

simplicity: forth, assembly, lisp, REXX, Smalltalk are all structurally simpler than both C and C++.

OO Concepts: Smalltalk and Java are at least as solid and complete implementations of OO.

Wide range of tools: Arguable. Some of the languages I mentioned above appear to lack a number of tools because the need for some of those does nor arise or because they natively supply some of the capabilities other languages need tools for.

Popularity: long live Basic which presumably is much more popular than any of the professional and useful languages. Also, popularity is not an intrinsic property of a programming language, and it may be a misleading metric because it might be popular in spite of its intrinsic qualities. For instance and without meaning to imply anything: Windows is much more popular on desktop and laptop PCs than all other OSs combined. 

No one thinks the worse of you if you prefer using either C or C++ or both to many other languages. This does not make those languages any more 'powerful' than many others.

If it is a matter of personal choice, use the language you are most productive with and which you feel most comfortable with. If you are working for an industry or team where another language is being used, learn to use that language.

> **cb951303 said:**
> 
actually I will keep saying that as long as you claim that most powerful language = one of the most powerful language

Nowhere did I write or even imply such a thing.

---

### Post by CptPicard on 2008-09-21
> **cb951303 said:**
> it's just one argument not a real law. you can't use as a fact. Frankly I found that statement quite amusing.

Actually, its basis is in the normal distribution which states that 90% of everything is mediocre at best, so if your standards are high, yes, 90% of everything is crap.

> 
I would like to hear more about that. Some examples maybe?


Ok, let's add a random slap just as payback.. ;)

I don't think you have enough knowledge in C++ and been digging around in docs and whatever while learning to find out that C++ is probably the most represented language where you have to really learn lots of arcane details about the language in order to become *expert in the language* before you can become an expert problem-solver using that language. To add to the Defective C++ link, see 

[http://yosefk.com/c++fqa/](http://yosefk.com/c++fqa/)

Which is a nice retort to the C++ FAQ which is in itself a whole site dedicated to answering problems that pretty much stem from the language itself...

Even in really basic coding, C++ forces you to start considering stuff like protecting your memory allocations from exceptions, pointer ownership management in copy constructors and the like from the get-go... it's a strange mismatch of trying to make use of (slightly) higher-level constructs in a fundamentally low-level context.

> Also since when mastering *anything* become unnecessary or bad practice?

Since when did putting time and effort into learning "random something" become the rational course of action just because learning "anything" is good?

> It's just a bad choice of word by me. English is not my mother language.

Neither is it mine... "bashing" is irrational criticism, I think the "unnecessary complexity" argument of C++ is perfectly rational.

> 
 I don't think you have enough knowledge to conclude that.

I don't need knowledge, it's basic statistics against the popularity argument.

> then use it buy any means

Trust me, I do :)

---

### Post by cb951303 on 2008-09-21
> **pp. said:**
> by my purely subjective evaluation:
optimization: I was not aware that C++ actually did optimize the compiled code but are prepared to learn better if so. Java ought to win with respect to optimization with its optimizing JIT compiler.

speed: If speed of execution is meant, then Assembly ought to be fastest if you really go to the trouble of actually optimizing your code. If speed to market is your goal, then a great many other languages are better suited for almost every application domain.

simplicity: forth, assembly, lisp, REXX, Smalltalk are all structurally simpler than both C and C++.

OO Concepts: Smalltalk and Java are at least as solid and complete implementations of OO.

Wide range of tools: Arguable. Some of the languages I mentioned above appear to lack a number of tools because the need for some of those does nor arise or because they natively supply some of the capabilities other languages need tools for.

Popularity: long live Basic which presumably is much more popular than any of the professional and useful languages. Also, popularity is not an intrinsic property of a programming language, and it may be a misleading metric because it might be popular in spite of its intrinsic qualities. For instance and without meaning to imply anything: Windows is much more popular on desktop and laptop PCs than all other OSs combined.
I agree with most of you said. But it doesn't change that C/C++ are good on this areas. sure there are better (as you stated above) but I never implied they were the best anyway.

> 
No one thinks the worse of you if you prefer using either C or C++ or both to many other languages. This does not make those languages any more 'powerful' than many others.They are better than some languages.

> 
If it is a matter of personal choice, use the language you are most productive with and which you feel most comfortable with. If you are working for an industry or team where another language is being used, learn to use that language. well being a programmer for almost 5 years now I think I know whats best for me but thanks.

> 
Nowhere did I write or even imply such a thing.
I stand corrected. I replied lots of people and got confused who said what.

---

### Post by cb951303 on 2008-09-21
> **CptPicard said:**
> Actually, its basis is in the normal distribution which states that 90% of everything is mediocre at best, so if your standards are high, yes, 90% of everything is crap.it's a subjective matter and I don't agree with it.


> 
Ok, let's add a random slap just as payback.. ;)

I don't think you have enough knowledge in C++ and been digging around in docs and whatever while learning to find out that C++ is probably the most represented language where you have to really learn lots of arcane details about the language in order to become *expert in the language* before you can become an expert problem-solver using that language. To add to the Defective C++ link, see 

[http://yosefk.com/c++fqa/](http://yosefk.com/c++fqa/)

Which is a nice retort to the C++ FAQ which is in itself a whole site dedicated to answering problems that pretty much stem from the language itself...

Even in really basic coding, C++ forces you to start considering stuff like protecting your memory allocations from exceptions, pointer ownership management in copy constructors and the like from the get-go... it's a strange mismatch of trying to make use of (slightly) higher-level constructs in a fundamentally low-level context.I'll read that FAQ and then comment

> 
Since when did putting time and effort into learning "random something" become the rational course of action just because learning "anything" is good?
since when C++ is random something?

> 
Neither is it mine... "bashing" is irrational criticism, I think the "unnecessary complexity" argument of C++ is perfectly rational.

it is. but not enough since I believe there could be many more FAQs like that if wanted for any language if they were ever as popular as C++.

> 
I don't need knowledge, it's basic statistics against the popularity argument.

statistics? I would like to see your source

---

### Post by pmasiar on 2008-09-21
> **cb951303 said:**
> C and C++ are two of the most powerful programming languages that exists today. So I wouldn't believe what they say about C++.

Seems that you consider low-level and CPU-efficient languages "powerfull" for some reason. I consider as powerfull only language what cares about **my** needs, not the CPU's. Language which gives **me** the power to solve the problem in the shortest time with the least amount of code, even if CPU will work harder on it. C or C++ don't fit **my** definition of "powerfull" language 8-) ... just most CPU-efficient.

---

### Post by nrs on 2008-09-21
> **pp. said:**
> 
speed: If speed of execution is meant, then Assembly ought to be fastest if you really go to the trouble of actually optimizing your code. If speed to market is your goal, then a great many other languages are better suited for almost every application domain.

C++ is to programming languages what humans are to high-fantasy RPGs.

---

### Post by pmasiar on 2008-09-21
I mostly agree with you, just little nitpicking  and extending on comments you provided, to get your mind some food to ponder:
> **pp. said:**
> optimization: ... Java ought to win with respect to optimization with its optimizing JIT compiler.

Java's approach to JIT compilation was "state of the art" 15 years ago. Since then, huge advances were made. As a result, static typing is not only not required: it hinders optimization, because runtime compiler has much better info about variable real type than programmer ever has. Of course lots of tricky work has to be done to handle it correctly, that's why Python community is so excited about PyPy project: Python compiler in (subset of) Python: next step would be JIT compiler, and it is substantially more productive (and fun) to write it in Python than in C.

> simplicity: forth, assembly, lisp, REXX, Smalltalk are all structurally simpler than both C and C++.

I am always concerned about sanity of person who calls C++ "simple". C++ is anything but simple. 8-)

And it's great to see that there are people who know about Forth, which is IMHO forgotten gem:  one of the most simple and still most powerfull languages ever imagined.

> Popularity: long live Basic

Basic's popularity was based completely on platform: beginner-friendly language on first interactive time-shared OS with interactive source code editing and on-demand execution where 3-times weekly batch runs of punchcards were the norm. Even back then were better and more powerfull languages, like PL/1 - but not with interactive development platform.

---

### Post by pmasiar on 2008-09-21
> **cb951303 said:**
> I was simply stating that C and C++ are high on the good programming languages list. 

Good for what? They are both good in the very limited area which I described in my previous post. 

C is excellent as portable assembler for low-level development (OS, drivers - but Forth is also popular with driver community, because is even more compact than ASM). 

C++ "goodnes of fit" is even more confusing: It is slower that C but harder to develop than Java.

---

### Post by lisati on 2008-09-21
> **pmasiar said:**
> Good for what? They are both good in the very limited area which I described in my previous post. 

C is excellent as portable assembler for low-level development (OS, drivers - but Forth is also popular with driver community, because is even more compact than ASM). 

C++ "goodnes of fit" is even more confusing: It is slower that C but harder to develop than Java.

And C++, although effectively a different language these days, does have its beginnings as an extension to C.

---

### Post by pmasiar on 2008-09-21
> **cb951303 said:**
> it's just one argument not a real law. you can't use as a fact. Frankly I found that statement quite amusing.

Now you will disagree with normal distrubution? That requires **some** guts. Or maybe you should pass along what you are smoking? 8-)

> Again no language is perfect. 

True, but Lisp, Fortran, Python, C and Forth are very close to "perfect" in their respective areas - in sense that no language was able to be closer fit for the problem so far. Compared to that, languages like Basic, Cobol, Perl, PHP, Java, C++ are obviously just stepping stones, quite popular for some time but obviously targer for replacement by "better" languages, better fitting the niche.

It might be possibly hard to judge for a person  not familiar with at least some of those "perfect" languages, but oh well what I can do about it, beyond suggesting to learn them to get the feeling? 8-)


> It's just a bad choice of word by me. English is not my mother language. 

You cannot weasel out easy like that, for many people here (including me) English is not first languege (for me, English is forth 8-) )

---

### Post by pmasiar on 2008-09-21
> **cb951303 said:**
> I read only the first sentence of your post since it show that you didn't read any of mine. 

It is hard to argue with someone like you whose position is "I cannot hear you lalalala". Basic etiquette lesson for you, completely free: If you want to earn trust of other people, even if you think they are wrong, listen carefully what they say and show they that you listen and where they are wrong. Like we (some of us at least) do. 

Warning: suggested approach might require sometimes to admit **you** were wrong and they were right. Of course if you are **absolutely** sure that you are **always** right, listening to others is waste of time, and proper way is just to shout louder and listen less 8-)

---

### Post by lisati on 2008-09-21
> **pmasiar said:**
> 

True, but Lisp, Fortran, Python, C and Forth are very close to "perfect" in their respective areas - in sense that no language was able to be closer fit for the problem so far. Compared to that, languages like Basic, Cobol, Perl, PHP, Java, C++ are obviously just stepping stones, quite popular for 

Having done some programming in BASIC, Fortran, and COBOL, I'd suspect that most Linux programmers, if given a choice of only these three (BASIC, Fortran, and COBOL) they'd probably drop COBOL pretty quickly. And at least some versions of BASIC have their "Peek" and "Poke"

---

### Post by cb951303 on 2008-09-22
> **pmasiar said:**
> Seems that you consider low-level and CPU-efficient languages "powerfull" for some reason. I consider as powerfull only language what cares about **my** needs, not the CPU's. Language which gives **me** the power to solve the problem in the shortest time with the least amount of code, even if CPU will work harder on it. C or C++ don't fit **my** definition of "powerfull" language 8-) ... just most CPU-efficient.

it's been already responded by me... I didn't even say the word low-level and surely I didn't imply it. But yes, one of the meanings of powerful is CPU-efficient.

---

### Post by cb951303 on 2008-09-22
> **pmasiar said:**
> 
I am always concerned about sanity of person who calls C++ "simple". C++ is anything but simple. 8-)

where did I state that?

---

### Post by cb951303 on 2008-09-22
> **pmasiar said:**
> Good for what? They are both good in the very limited area which I described in my previous post. 

I already described it. 

> 
C is excellent as portable assembler for low-level development (OS, drivers - but Forth is also popular with driver community, because is even more compact than ASM). 
it's not an assembler. it's a procedural programming language. 

> 
C++ "goodnes of fit" is even more confusing: It is slower that C but harder to develop than Java.
C++ is almost the next best thing after C in memory consumption (not management) and speed
and it makes C++ powerful. [http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/)

---

### Post by cb951303 on 2008-09-22
> **pmasiar said:**
> It is hard to argue with someone like you whose position is "I cannot hear you lalalala". Basic etiquette lesson for you, completely free: If you want to earn trust of other people, even if you think they are wrong, listen carefully what they say and show they that you listen and where they are wrong. Like we (some of us at least) do.
I do that already but it's my right to ignore people who claims that I said something that I actually didn't. 

> 
Warning: suggested approach might require sometimes to admit **you** were wrong and they were right. Of course if you are **absolutely** sure that you are **always** right, listening to others is waste of time, and proper way is just to shout louder and listen less 8-)
it's simply not the case in this discussion. I'm sure there will be people here that will agree with me that I don't consider myself always right. This discussion is going on about the one aspect of the subject anyway so if I was a person like that you stated I would only find myself right not always but only in one (that particular one) aspect.

---

### Post by cb951303 on 2008-09-22
> **pmasiar said:**
> Now you will disagree with normal distrubution? That requires **some** guts. Or maybe you should pass along what you are smoking? 8-)

what's the liaison? I don't get it. CptPicard was simply stating that 90% of the developers were crap against my 'true stastical' data of C++ being the 2. most popular native compiled language. It's just unacceptable. I could as well create a law. Call it cb951303's law and state that everyone in the world is dumb. It doesn't necessarily mean it's true. Catch my drift?

> 
True, but Lisp, Fortran, Python, C and Forth are very close to "perfect" in their respective areas - in sense that no language was able to be closer fit for the problem so far. Compared to that, languages like Basic, Cobol, Perl, PHP, Java, C++ are obviously just stepping stones, quite popular for some time but obviously targer for replacement by "better" languages, better fitting the niche.

It might be possibly hard to judge for a person  not familiar with at least some of those "perfect" languages, but oh well what I can do about it, beyond suggesting to learn them to get the feeling? 8-)

I'm familiar with C and C++ otherwise I wouldn't comment in the first place. 

> 
You cannot weasel out easy like that, for many people here (including me) English is not first languege (for me, English is forth 8-) )
no ones weaseling, it was simply a bad choice of word.

---

### Post by slavik on 2008-09-22
> **Exershio said:**
> Well, I'm about to dive into some lower level programming, having been programming in C# (windows) and Python for a while. "C++ is a messy/frustrating/etc language" is something I hear rather often on the programming boards I visit. However, what about just plain C? 

Is it as masochistic to use as a lot of people say C++ is?
Plain C is simple, the possible problem comes when you want to have a complex data structures. While not impossible, handling complex data structures in C is not pleasant but if done right, most of the unpleasantness can be removed.

NOTE: please ignore some of the previous posts, we haven't had a language flamewar in a while, everyone is itching for one. :) Enjoy your stay. :)

---

### Post by sloggerkhan on 2008-09-22
Plain C is many times better than assembly.

While yes, C is similar to assembly in a number of ways, it sure beats mips.

---

### Post by pmasiar on 2008-09-22
... "C is excellent as portable assembler"
> **cb951303 said:**
> it's not an assembler. it's a procedural programming language. 

I am not sure how deep your experience with assemblers goes: some I worked with had frameworks of macros to handle very tricky data structures and approaches. For me, certainly C was very close to those.

Of course, your opinion might be based on difference in experince. I freely admit I did not wrote a line of ASM since I looked at architecture of i80286 ... and run away screaming ;-)

---

### Post by pmasiar on 2008-09-22
Re: normal distrubution, Sturgeon law.

BTW I find it really annoying that you when respond after quote do not mention main term, so when responding to your quote context is completely missing. Just FYI. 8-)

> **cb951303 said:**
> what's the liaison? I don't get it. CptPicard was simply stating that 90% of the developers were crap against my 'true stastical' data of C++ being the 2. most popular native compiled language. 

Your 'true statistical' data are just based on benchmark (ie data anecdote), while Sturgeon Law is based on fundamental law of nature regarding [http://en.wikipedia.org/wiki/Normal_distribution](http://en.wikipedia.org/wiki/Normal_distribution) of anything: About 67% of anything is within 1 SD around mean, so 16% is above 1SD and 16% is below 1SD. So Sturgoen law says "only 16% of anything could possibly be better than 1SD obove average" - ie be good, and rest is average crap or worse. Do you get it now?

> I could as well create a law. Call it cb951303's law and state that everyone in the world is dumb. It doesn't necessarily mean it's true. Catch my drift?

No, your law is the same crap as most others laws 8-) You don't have laws of statistics on your side, because you don't know them.

---

### Post by CptPicard on 2008-09-22
Most importantly, the more popular something is, the larger the sample size of "proponents of X" is as share of population, and as in the *whole* population "developer ability" is probably normally distributed (most variables like this are, it's a typical generally accepted assumption), as popularity grows, the stronger the claim becomes that "proponents of X" are *also* normally distributed, and ergo, large percentage of them is crap as per normal distribution -- otherwise there is something pretty remarkable going on actually that requires further explanation, and ever more so the larger the sample size, because the people outside of the group would have to be remarkably bad to compensate distribution back to normal. Look up statistical testing in any textbook of choice.

This is also the reason why a small group of superior lispers don't really show up in meaningful ways in the overall distribution :)

Of course this just shows that popularity is not *necessarily* a signifier of anything (instead it can be a signifier of mediocrity), although it can be. IMO the really smart guys figured out long time ago that C++ makes you jump through too many hoops for too little gain, and there really should be no denying that C++ *is* relatively complex (compared to pretty much any other language) to get good code written in.

---

### Post by slavik on 2008-09-22
> **CptPicard said:**
> ... Of course this just shows that popularity is not *necessarily* a signifier of anything (instead it can be a signifier of mediocrity), ...

I really like that idea, even if you think the context is gone, these words are very accurate.

---

### Post by pp. on 2008-09-22
> **CptPicard said:**
> popularity is not *necessarily* a signifier of anything

As in "Eat dung - several trillion flies can not be mistaken".

There's also to consider that someone who has spent all that time and energy learning an utterly complicated language will not be prepared to admit (or even to perceive) that the language wasn't worth the effort.

---

### Post by slavik on 2008-09-22
> **pp. said:**
> There's also to consider that someone who has spent all that time and energy learning an ... language will not be prepared to admit (or even to perceive) that the language wasn't worth the effort.

that's a good one, too.

Man, this thread is becoming a gold mine for good quotes. :)

---

### Post by CptPicard on 2008-09-22
> **pp. said:**
> 
someone who has spent all that time and energy learning an utterly complicated language will not be prepared to admit (or even to perceive) that the language wasn't worth the effort.

[http://en.wikipedia.org/wiki/Sunk_cost#Loss_aversion_and_the_sunk_cost_fallacy](http://en.wikipedia.org/wiki/Sunk_cost#Loss_aversion_and_the_sunk_cost_fallacy)
[http://en.wikipedia.org/wiki/Post-purchase_rationalization](http://en.wikipedia.org/wiki/Post-purchase_rationalization)

---

### Post by Greyed on 2008-09-22
> **cb951303 said:**
>  than why the big gaming companies like EA, ID Software, Blizzard etc. chose C++ over your cleaner native compiled languages...

Blizzard's UI is implemented in LUA.  Several recent games have implemented portions in Python.  In fact EvE-Online, the only MMO out there to have 30,000 simultaneous logins on a single universe, writes in Stackless Python and drops down to C if and when the additional speed is needed.  That's both client and server.  For a comparison most other MMOs, including Blizzard's WoW which you contend is written in C++ (though I'm not sure where you get that) top out around 3000.

> I understand that there are other languages, very powerful ones. But bashing C or C++ is just ridiculous since they are very popular languages. In fact according to [this]("http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html") C/C++ is the number 1 and 2 most popular native compiled languages.

Oooh, stats, can I play!?

[http://www.ohloh.net/languages/compare?commit=Update&l0=c&l1=cpp&l2=-1&l3=perl&l4=python&l5=ruby&l6=-1&measure=projects&percent=true](http://www.ohloh.net/languages/compare?commit=Update&l0=c&l1=cpp&l2=-1&l3=perl&l4=python&l5=ruby&l6=-1&measure=projects&percent=true)

Shows a general decline in C/C++ projects and a general increase in Python projects.  Python has not overtaken C/C++ yet but it is edging into a few percentage points.  These are active projects, mind you.

[http://www.ohloh.net/languages/compare?commit=Update&l0=c&l1=cpp&l2=-1&l3=perl&l4=python&l5=ruby&l6=-1&measure=contributors&percent=true](http://www.ohloh.net/languages/compare?commit=Update&l0=c&l1=cpp&l2=-1&l3=perl&l4=python&l5=ruby&l6=-1&measure=contributors&percent=true)

Here's contributors per month, same general trend.

[http://www.ohloh.net/languages/compare?commit=Update&l0=c&l1=cpp&l2=-1&l3=perl&l4=python&l5=ruby&l6=-1&measure=loc_changed&percent=true](http://www.ohloh.net/languages/compare?commit=Update&l0=c&l1=cpp&l2=-1&l3=perl&l4=python&l5=ruby&l6=-1&measure=loc_changed&percent=true)

...and...

[http://www.ohloh.net/languages/compare?commit=Update&l0=c&l1=cpp&l2=-1&l3=perl&l4=python&l5=ruby&l6=-1&measure=commits&percent=true](http://www.ohloh.net/languages/compare?commit=Update&l0=c&l1=cpp&l2=-1&l3=perl&l4=python&l5=ruby&l6=-1&measure=commits&percent=true)

...are telling because the commits and lines changed are, comparative to the projects/contributors, relatively flat.  It is telling because C/C++ are just all over the place.  IE, more is getting done month-after-month but the relative change the copus of code is far slower growing.  I think it speaks to the expressiveness of Python and how it enables the programmer to work the problem instead of work the language.

Hey, a look at my sig will show where my bias is.  I just wanted to point out that your examples aren't as clear-cut as you might think.  ;)

---

### Post by Greyed on 2008-09-22
> **cb951303 said:**
> since when C++ is random something?

Since when is it not?

---

### Post by cb951303 on 2008-09-22
> **pmasiar said:**
> Re: normal distrubution, Sturgeon law.

BTW I find it really annoying that you when respond after quote do not mention main term, so when responding to your quote context is completely missing. Just FYI. 8-)
 

main term is there for you to read, I don't see people mentioning main terms beside you. nested quotes are ugly and hard to read anyway.

> 
Your 'true statistical' data are just based on benchmark (ie data anecdote)
it has nothing to do with benchmarks. it's pure statistical data.

---

### Post by nrs on 2008-09-22
> **Greyed said:**
> Blizzard's UI is implemented in LUA.  Several recent games have implemented portions in Python.  In fact EvE-Online, the only MMO out there to have 30,000 simultaneous logins on a single universe, writes in Stackless Python and drops down to C if and when the additional speed is needed.  That's both client and server.  For a comparison most other MMOs, including Blizzard's WoW which you contend is written in C++ (though I'm not sure where you get that) top out around 3000.

Those limits are a design limit, not language related. EVE isn't all that impressive technically, graphically. What's impressive is what they've managed to achieve using Python, if nothing else because they're pretty much charting unknown waters as far as large scale game development is concerned, not that games haven't utilized it before but where C/C++ is the norm and Python is the exception EVE makes Python the norm and C the exception.

While you evidently got what I said earlier, in case it was too esoteric for others: C++ excels at being merely average in every regard. Unlike others, I don't see C++ as having any great weaknesses, just not any great strengths, not to say it isn't good, but if you want raw performance there are better languages, and if you want raw development speed there are better languages. I can think of several areas where you want a little of both though, I think the language is overused, but it does fill several niches well and I can't think of anything else that can come close to filling them.

---

### Post by pmasiar on 2008-09-22
Now I will get you a dose of your own poison 8-) answering without quoting the context like you do:

> **cb951303 said:**
> where did I state that?

You did not but I never said you did - can you prove that? Why you feel you are the only person worth to answer in this whole thread?

;-)

I doubt that too many people have any idea what are you complaining about. See now?

---

### Post by pmasiar on 2008-09-22
> **cb951303 said:**
> I don't see people mentioning main terms beside you. nested quotes are ugly and hard to read anyway.

FYI, if anyone points you what the rules/traditions of any forums are, your response should be to think why those rules are established (by people with more experience and presence on that forum than you do) and consider next time to apply them. Exactly wrong response is to tell old-timer that the rules they have are BS, and you are the new hero and will show us how stupid our rules are. 

Just FYI again, you don't have to dispute this ;-)

> it has nothing to do with benchmarks. it's pure statistical data.

here your age and relative lack of experience shows again. Old hardened dogs know that there are lies, big lies, and statistics, and are used to trust only statistics we fudged  according to our own needs :-)

And you just proved beyond any doubt that you have little clue what normal distribution is, and how it works 8-) Disputing any statistics-based claim with you at this point is utterly useless, because you base your opinion not on any understanding of statistics, but on your prejudices how statistics would work in some other, more just universe :-) 

EDIT: some people were offended by my bluntness. I removed some words to make censors happy...

---

### Post by cb951303 on 2008-09-22
> **pmasiar said:**
> You must be young. FYI, if anyone points you what the rules/traditions of any forums are, your response should be to think why those rules are established (by people with more experience and presence than yo do) and consider next time to apply them. Exactly wrong response is to tell old-timer that the rules they have are BS, and you are the new smart a** and will show us how stupid our rules are. 

Just FYI again, you don't have to dispute this ;-)



here your tender age and relative lack of experience shows again. Old hardened dogs know that there are lies, big lies, and statistics, and are used to trust only statistics we fudged  according to our own needs :-)

And you just proved beyond any doubt that you not have a clue what normal distribution is, and how it works 8-) Disputing any statistics-based claim with you at this point is utterly useless, because you base your opinion not on any understanding of statistics, but on your prejudices how statistics would work in some other, more just universe :-)

why personal attacks?

---

### Post by extruct on 2008-09-22
I didn't read the whole thread since its pretty long, so I may miss some points here and there.

C is not dead, and wont die at least in the close 10years.
Take assembly, seems like an old messy language but I'm pretty sure there are enough people who still looking for assembly developer. C is one level above assembly, and as I see it people will need C developers at least as I said int the next 10 years.
I don't know who said C++ is messy/bad/enter-your-anti-c++-phrase-here but I like it. I mean its flexible. I like it. Some others may say C++ is dead and now its Java/C# epoch, others would say today when we have 4GM ram speed is not that necessary, I disagree.

This is my opinion.

---

### Post by Canis familiaris on 2008-09-22
> **pmasiar said:**
> Both C and C++ are excellent languages, if you use them in areas they were designed for:

C++ for huge projects where OOP and namespaces are important part of the solution, and you need all the speed you can get, AND you are ready to pay the price for the speed in the time and effort required to get reliable solution (hint: it will be NOT easy).

C for projects where speed is even more important (so you are not ready to pay even for  little OOP polymorfic magic) and where skills and experience, coding discipline and project managers of participants are on par to the task: because changes in huge codebase with plenty of global names are easy to bork, and skills to handle ** and even *** pointers is paid by chunks of hairs torn, bloody eyes by all night debugging, and barrels of coffee.

Of course using C or C++ on the whim if you don't need the features is like trying to make opening in the wall by banging your head: some people will like the attitude, but most people will make couple steps aside where is the door (more productive languages).

So as always it depends what you need: hacking kernel or drivers? C is your tool. Competing in speed with other team, or writing your own file system, with unlimited budget? C++ is fine. 

But writing CGI app in C++? You must enjoy the pain.

C is simple language where lots of stuff C++ handles for you you have to do manually, by proper project management. In small projects it does not matter, when you have 1MLOC it does 8-)

Well Said...

---

### Post by cszikszoy on 2008-09-22
C/C++ will not be going anywhere for a long, long while.  The Computer Science kids / "Sunday Programmers" have and always will dislike C/C++ because they don't understand where, and why it is practical.  I define simplicity and beauty by being able to look at a piece of code, and know, exactly, with 100% certainty what it is doing, even down to the lowest level.  The problem with layers of abstraction, found in the more "popular" higher level languages such as C#, Java, Python, is that you really don't have a damn clue what is happening.  Sure you can accomplish some task in much fewer words, but do you even know what is happening?

This situation is unacceptable in the environments where C/C++ is used and thrives.  C/C++ is used in the vast majority of embedded devices because that's where C/C++ is powerful.  At work I write low level device drivers for embedded flash memory controllers.  If I asked my boss if we could use python because the code would be "smaller" he would probably laugh in my face, then fire me on the spot.

The reality of the situation is that by asking this kind of question here, you will inevitably get many biased and uninformed answers.  Most people here don't like C/C++ because they don't understand it, or understand where it thrives.  If you just want to write a little GUI app with pretty buttons, just use python.  It'll be much easier on your psyche anyways.

That being said however, Gnome and GTK are both written in C, and KDE and QT are both written in C++.

---

### Post by pmasiar on 2008-09-22
> **cb951303 said:**
> why personal attacks?

I am not sure why you consider me pointing at your lack of understanding of basic science (or etiquette) as personal attack.

OK, let set aside etiquette, how much education is area of statistics do you have?

Let me guess, you are 16 years old and never heard about normal distribution, and statistics as science (as compared to table with numbers in a newspaper)?

It is not wrong to be young and not learned (everyone started that way). Problem is when someone like that thinks that just because he has opinion, his opinion is as true and worthy of support like someone who really understands the matter.

But you are not the first one with this approach, and I am sure not the last one, so you are not too special in this either.

Have a nice day!

---

### Post by cb951303 on 2008-09-22
> **pmasiar said:**
> I am not sure why you consider me pointing at your lack of understanding of basic science (or etiquette) as personal attack.

OK, let set aside etiquette, how much education is area of statistics do you have?

Let me guess, you are 16 years old and never heard about normal distribution, and statistics as science (as compared to table with numbers in a newspaper)?

It is not wrong to be young and not learned (everyone started that way). Problem is when someone like that thinks that just because he has opinion, his opinion is as true and worthy of support like someone who really understands the matter.

But you are not the first one with this approach, and I am sure not the last one, so you are not too special in this either.

Have a nice day!
I'm 23 and don't need to major in statistics to have an opinion on that matter.

You seem to etiquette people a lot without knowing them. that's what I call a personal attack. Somehow you seem to be offended by what I said earlier in my posts or took it personally. Just like a child would do. Now, I'm not going to state that you're '16' as I don't know you at all but you sure seem like one. I believe I don't have to know you to state that one.

I don't think I will answer your posts till you decide to act like an adult. So write here and hijack the thread as long as you wish

so long

---

### Post by pmasiar on 2008-09-22
> **cb951303 said:**
> I'm 23 and don't need to major in statistics to have an opinion on that matter.

Being 23 does not make your "opinion" about properties of normal distribution any more valid. Scientific facts are quite stubborn. 8-)

For the record, I did not majored in Stats (although I wish I did - good jobs :-) ) but I did audited Stats 101 two times (after graduation - one of the perks of working in academia: you can learn all you want). Now i understand it little better :-)

---

### Post by cb951303 on 2008-09-22
> **pmasiar said:**
> Being 23 does not make your "opinion" about properties of normal distribution any more valid. Scientific facts are quite stubborn. 8-)

For the record, I did not majored in Stats (although I wish I did - good jobs :-) ) but I did audited Stats 101 two times (after graduation - one of the perks of working in academia: you can learn all you want). Now i understand it little better :-)
that's better.

well I did audited that class once but that doesn't make me a pro neither makes you. It's however irrelevant to our discussion. Between all the sarcasm and childish behaviour of yours, you forgot or didn't read at all the main discussion about that law. It was presented as a counter-argument to my popularity argument. The law lets us conclude that 90% of the developers are crap thus it's valid for all languages and developers and it doesn't change anything about the popularity of C++. Still the 10% part of the people who have chosen C++ (which are not crap) are more in population than other languages.

---

### Post by LaRoza on 2008-09-22
Not really a best practice, but this thread was off to a really bad start and I don't want to see any issues arise from it.

We have a thread (linked to in my first post I think) which has links to why people love or hate various things.'

Can I close this?

---

### Post by pmasiar on 2008-09-22
> I did audited that class once but that doesn't make me a pro neither makes you.

I also **took** the class and got very hard earned B for it, so my experience beats yours :-)

> **cb951303 said:**
> The law lets us conclude that 90% of the developers are crap thus it's valid for all languages and developers and it doesn't change anything about the popularity of C++. Still the 10% part of the people who have chosen C++ (which are not crap) are more in population than other languages.

You again show your lack of training in formal reasoning. Nothing proves your clam that any 10% of non-crap developers prefers C++. If fact, my experience with experts is, most of them prefer anything but C++ :-)

I think that this thread should be closed, it outlived it usefulness and entertainment value.

---

### Post by cb951303 on 2008-09-22
> **pmasiar said:**
> I also **took** the class and got very hard earned B for it, so my experience beats yours :-)

good for you, 

> 
You again show your lack of training in formal reasoning. Nothing proves your clam that any 10% of non-crap developers prefers C++. If fact, my experience with experts is, most of them prefer anything but C++ :-)

I think that this thread should be closed, it outlived it usefulness and entertainment value.

[quote=cb951303]
I understand that there are other languages, very powerful ones. But bashing C or C++ is just ridiculous since they are very popular languages. In fact according to [this]("http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html") C/C++ is the number 1 and 2 most popular native compiled languages.[/quote]

I guess you didn't read my posts at all, so here you go. it's a valid statistical data that shows that C++ is the 2. native compiled programming language as of september 2008.

I guess it's your lack of reading abilities after all

EDIT: I also didn't claim that 10% of non-crap programmers prefer C++. I said 10% of non-crap C++ programmers > other languages' 10% non crap programmers in population

---

### Post by KiwiNZ on 2008-09-22
Stop the personal attacks or further action will be taken

---

### Post by nvteighen on 2008-09-22
> **LaRoza said:**
> 
Can I close this?

Please.

---

### Post by cszikszoy on 2008-09-22
Que: War - Why Can't We Be Friends?

---

### Post by LaRoza on 2008-09-22
> **nvteighen said:**
> Please.

Thank you.

---

