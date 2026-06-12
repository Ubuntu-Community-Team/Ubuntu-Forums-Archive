---
title: "Programming in your native language"
date: 2010-02-23
forum: Programming Talk
---

### Post by smmalmansoori on 2010-02-23
Since English is my second language (Arabic is my first) I can always express myself better in my native language, so no matter how good I get at programming I feel that I could do better if it was in my native language.

I hear that in English speaking countries schools offer programming lessons (grades 10-12? maybe even before that?) I've rarely heard about a school in non-English countries (not their first language anyway) offering programming lessons given the language barrier.

What do you think? would you be a better programmer had you started in your native language?

:Pfeedback:popcorn: feedback:P

---

### Post by napsy on 2010-02-23
This is a horrible idea. How expressible a language is is not determined by the "language" used but it's structure.

E.g. a functional language is way better in expressing abstract problems then any imperative language.

---

### Post by estyles on 2010-02-23
I dunno, I tend to agree with the OP.  Programming is easier when the words it uses have innate meaning.  Sure, if the printf function was called kaetef(), I would eventually remember it and memorize that function name.  And I could remember the "new" keyword if it were called "bleargh", but it's easier to pick up a new programming language because the words that the language uses have innate meaning.  Languages that use more abstract symbols and fewer English words (perl, I think?), are more difficult for me, personally, to learn.

Not that I think that everyone should program in their own native language, because it would set open source back quite a bit to not be able to read others' code.  But I do often marvel that there are so many great programmers for whom English is not their first language.

---

### Post by MindSz on 2010-02-23
I went to school in Chile and I had CompSci classes back in high school too.

I think that since a programming language is made of various functions, it is better to have just one set of syntax. It makes it easier even when looking for help on the internet (if you type strcmp in google, you will get results from different parts of the world)

So yeah, I think it's better to keep programming languages in the (*ahem*) language they were created, so we all "speak the same language" (haha)

---

### Post by Simian Man on 2010-02-23
```

/* espanol.h */

#define si if
#define mientras while
#define por for
#define sigue continue
#define regresa return
#define haz do
#define estructura struct

/* ... */


```
Stuff like that is really not that useful though.

---

### Post by darsu on 2010-02-23
Grammar is what makes a language. In programming languages human language is only present on the symbol level, and as long as the symbol layer is always consistently from English it poses a manageable threshold to comprehension. 

The most excruciatingly painful programming experience I've ever had is having to use a domestic-language version of Microsoft Excel. Every single function name has been translated to my (also non-Indo-European) native language awkwardly. Facing a new programming language with a new syntax is a challenge; that Excel was an obstacle.

---

### Post by smmalmansoori on 2010-02-23
> **MindSz said:**
> I went to school in Chile and I had CompSci classes back in high school too.

I think that since a programming language is made of various functions, it is better to have just one set of syntax. It makes it easier even when looking for help on the internet (if you type strcmp in google, you will get results from different parts of the world)

So yeah, I think it's better to keep programming languages in the (*ahem*) language they were created, so we all "speak the same language" (haha)

Consider this, if a Spanish Java programming language is made where it actually compiles to the original ".java" source and then into java byte code. That means it is easy to implement a feature where you simply highlight the portion you want and it translates into java so that you can look it up online, if anyone suggests modifications you get that java code and turn it back into the Spanish version all through the IDE.

> **darsu said:**
> Grammar is what makes a language. In programming languages human language is only present on the symbol level, and as long as the symbol layer is always consistently from English it poses a manageable threshold to comprehension. 

The most excruciatingly painful programming experience I've ever had is having to use a domestic-language version of Microsoft Excel. Every single function name has been translated to my (also non-Indo-European) native language awkwardly. Facing a new programming language with a new syntax is a challenge; that Excel was an obstacle.


What if you grew up using this Excel that you mention, wouldn't you feel this same experience your mentioning when you see the English version for the first time?

---

### Post by CptPicard on 2010-02-23
We really should have nvteighen the resident Linguist here to explain this better, but it boils down to natural languages being far more general and ambiguous and full of connections to "implicitly understood semantic background" than most formal languages need to be.

Programming languages are a formal description of a well-defined, restricted set of things -- that is, Turing-computable functions. Just like in mathematics we do not hand-wave in natural language descriptions but use abstract symbolic descriptors with exactly defined meaning (in terms of other such descriptors), there is no reason to try to make use of natural language and introduce its ambiguities where a more limited (and exact) description will do. I much more prefer to succintly say "f(x)" than "spell it out" in any other way.

Interestingly, Lisp is an awesome programming language simply because it arose from a formal description of programs that came directly from math in the sense that the notation was originally meant to be used in academic papers to describe programs... turned out it was also implementable by machine. It abstracts syntax away almost completely to a bare minimum, while maintaining a very high level of semantic expressibility -- you can with a fairly small amount of effort give Lisp code that has the "meaning" of pretty much anything I've ever seen in any other programming language.

Simple translation of keywords or standard library function names is totally superficial and means nothing -- you can always just trivially "rename symbols" like you can call a variable anything you like.

---

### Post by hoboy on 2010-02-23
I don't know any programming language that is not written in english, and this languages are written by non english native.
Like c++ by danish guy, php by a danish guys, python by a dutch guy if i am not wrong.

---

### Post by darsu on 2010-02-23
> **smmalmansoori said:**
> 
What if you grew up using this Excel that you mention, wouldn't you feel this same experience your mentioning when you see the English version for the first time?

If that were the case, I would be ill-equipped to face the English-based world of computer science. That would be a nasty handicap, but fortunately I would have a massive worldwide knowledge base that I could tap into to get help for learning things the English way.

(...hanging on in quiet desperation?)

---

### Post by slooksterpsv on 2010-02-23
No, even though I speak english, read and write english, I still feel that no matter what the "native" language of an OS is, it still doesn't help one way or another.

Why? - I know a few programmers that program the most complex, functional, and nearly bug free programs and their english is really broken, it's hard to understand their dialect, and overall, english wasn't their native language.

It just depends on how much time you really want to take into understanding what is going on in the language and how to debug it.

---

### Post by CptPicard on 2010-02-23
> **hoboy said:**
> I don't know any programming language that is not written in english

Just because some of the named keywords and functions are named in English, does not make the language "English"... the names could be anything. But of course, English names are convenient because they are understood by the broadest base, and documentation is also typically in English for the same reason.

---

### Post by smmalmansoori on 2010-02-23
CptPicard:
I do agree with you. On the other hand, there are many out there who barely know any English, where by superficial translation you can bring programming to a whole new bunch of people (potential programmers).

It is more about the significance of its applications, introducing programming to those who don't speak English could make an interesting change.

btw it isn't always as easy as it may sound, translating a certain programming language into another doesn't consist of simply keywords and functions, you have to provide a translation of all compiler warnings, errors, compiler arguments, translations of tools such as a terminal, a version control system, a build system, etc.

It is interesting to me seeing these feedbacks as I am developing/translating an Arabic programming language based on java.

I wish if anyone can tell me why it wouldn't be a good idea assuming the language provides the following features:
1. It doesn't reinvent the wheel, it translates the Arabic source code word by word into the English java source code then compiles into java byte code.
2. It translates English java source code into the Arabic source code
3. Provides a fully unicode terminal
4. Provides an Arabic translated version of Ant build tool
5. Provides an Arabic translated Bazaar version control system

Point 1 clearly shows that there still is a common denominator to keep some sort of consistency and be able to seek if help wasn't available in the targeted language

Point 2 shows that all the java source code on the web could be learning material to whoever use this language since it can be converted to its code

Point 1 +2 shows that it is possible to collaborate in projects between those who program in English java and those who do in its Arabic translation

---

### Post by CptPicard on 2010-02-23
> 
It is more about the significance of its applications, introducing programming to those who don't speak English could make an interesting change.

Ah, you're talking more about a toolchain translation. I guess you may have some sort of a point there... but even in that case, I personally prefer having my compiler and such "speak English" simply because that way I have the same understanding of what some error is saying as the other people out there.

But, you're talking about Java "source" translation here too so I really would prefer to focus on this idea that the programming language itself somehow needs to be translated... in that context, I really mean that the superficial translation is *meaningless* and that alone is not going to make programming any more accessible to anyone, because genuine understanding of the programming language does not in any way come from understanding any of the few natural-language specific issues (such as "names of labels"). 

Programming languages have their own special semantics, the understanding of which is more important than any of the forms they may take -- those forms preferably should be as clean, consistent and unobstructive as possible, and natural language is not good fit. Consider the horrors that are COBOL and SQL that tried the "programming languages are easier when seen forced to be natural languages" route.

In any case, I fear the quality (lack thereof) of the code written by programmers that were helped to become good programmers by a natural-language translation of their chosen programming language... :(

---

### Post by s.fox on 2010-02-23
Hello,
 
I too have come across code in different languages. 
 
Last year I came across some Spanish PHP code that did a little string manipulation that I was not quite sure how to do. For the most part the script was easy enough to understand and LOGICALLY made sense. 
 
Yes some of the variables were in spanish, as were the comments but it was readable and I was able to use it to help me solve my particular problem. To an extent I don't think it really matters too much about the native language of the programmer, just the logic that their applications use.
 
-Silver Fox

---

### Post by MindSz on 2010-02-23
Hey again,

The way I see it, a programming language is made of symbols, not like a real language. So if you learn to program using the same symbols as everyone else in the world does, then eventually it'd be a lot easier to communicate with the rest of the community.

Take SilverFox's post> Yes some of the variables were in spanish, as were the comments but it was readable and I was able to use it to help me solve my particular problem.

So yeah, variable names and comments are one thing, but the key words (the 'symbols') were in the language everyone expects them to be, which makes the code easier to understand to everyone else, even across our natural-language barriers.

---

### Post by azagaros on 2010-02-23
This is funny to me.. I download sources to various things.  The comments aren't always in English.  Programming languages have been written based on their translatability to the machine level code and most were developed where the first computers were developed where the native language was English.

I do understand most of the Nuclear science in the early days was done by Germans and the physics around it reads like English in German language structures. Go Figure.

You should try reading Assembly code, both At&t and Intel styles.  JNZ just means Jump Not Zero. CMP compare.  XOR is a Math structure.  The language is very literal to English and is one of the most primitive programming language. 

if I take C++, most of the code you see is in the native language of the programmer baring the special Characters of the native language.  Like the Define statements in the previous message, but most the time the actual programming language is still the programming language, which if given to a normal individual who speaks English, without a computer background, it would look like a foreign language.

---

### Post by CptPicard on 2010-02-23
> **MindSz said:**
> 
The way I see it, a programming language is made of symbols, not like a real language.

"Language" in general is made of "symbols". Then we just assign meanings to them, and agreement on the meaning causes the language to be able to communicate.

> 
 So if you learn to program using the same symbols as everyone else in the world does, then eventually it'd be a lot easier to communicate with the rest of the community.

Yes, which is exactly the reason why a programming language gets specified the way it does. "Keyword names" are just a superficial part of it, and those could be changed into anything, as long as consistency stays.

---

### Post by lisati on 2010-02-23
Most of the programming languages I've used have had some aspects which bear a superficial resemblance to English. Occasionally the concept is obscured by the evolution of the language and the hardware. A case in point would be the "printf" family of functions (and BASIC's 'PRINT' statement) - there might have once been a connection with printing a result on paper, but how many of us use printing terminals these days?

---

### Post by azagaros on 2010-02-23
Again I may need to look up something.. Which came first Basic or C?  Basic was on the 6502 based machines and C appeared on the first AT&T Unix machines which were out about the same time, or maybe a couple years before the Apple 1 and Commodore Pet.  I remember what a computer shop looked like back in the days before the 8088 xt's and Dos.

Printf stands for Print Function, which is understandable since C is a Function based programming modal and the Original Basics were not.  Most of the modern programming languages were developed on machines with a lot less power than we have now and it fun watching the needs of C and bitwise operators discussions, which was not part of the lingo of the original C's.

I took c and c++ in the early 90's and had been around computers since about 78 or 79 when my father brought the Motorolla 68k machines home from HP.  They had Old style Basic and pascal. I didn't know if they had C at the time.

---

### Post by nvteighen on 2010-02-23
Ok... here's the resident Linguist student to save the day :) I'll try to make this the most understable as possible.

I've seen you guys have been discussing what is language. A nice topic, actually, for which several definitions have been given in history. Currently, the most accepted idea is that language is a certain device that takes advantage of symbols to have a communicable abstraction of the world. So, English is somehow a "world view" (*Weltanschauung*), while Spanish is another one... of course, things in the Western culture aren't that different and, even European languages genetically unrelated to the Indo-European "mainstream", tend to build up similar meaning structures to those ones (contact also plays a huge role in this). But, Asian cultures are radically different to the Western one, and as such, their languages reflect/determine (depending whether you support the [Sapir-Whorf hypothesis]("http://en.wikipedia.org/wiki/Sapir-Whorf") or not) the vision their speakers have of their own world.

Wilhelm von Humboldt's (Alexander von Humboldt's younger brother) idea of the *Spirit of the Nation* inspiring the language's *Inner Form* is a bit amateurish for our current scientifical mindset, but it has proven to be a quite better solution than it seemed at first.

Now, into programming languages...

Programming is done through languages because we humans need languages in order to think. Some Linguists argue humans can only think in languages; I'm not sure about that, but the fact is that a great deal of what we think is "linguistically codified". We think with our language(s), usually our mother language(s). So, programming languages are there for a reason.

These programming languages are, of course, artificial languages because they are "optimized" for a certain kind of activity beside the symbolical /abstractive function that's common to any linguistical device... even Formal Logic, for example. But, this optimization makes these language be rather useless for daily usage... Going into a bar and declaring a data structure "beer", declaring a method for the bartender for selling someone a product and then call bartender.sell(beer, me) is rather stupid... "Ein Bier", "Una cerveza", "Beer, please" are rather more likely to be succesful... :p

So, programming languages are made up with natural verbal languages in mind, but they diverge in aspects like, basically, 1) Being context-free, 2) fixed regular syntax and 3) very little native "vocabulary" but a huge amount of combinatorial "neological" systems in order to create new "words" of different kind (data structures, functions... The Forth programming language actually calls them all "words").

Now, the problem is that, to be rather practical, programmers have created languages based on English. This is just because USA was the place in which all this began to be researched in the 1940s and 1950s and because English was then becaming the international language, displacing French. Yes, you could have written C in Spanish and say escribir() instead of printf() or ausdrücken() in German, but, well, things just didn't happen that way.

The thing is that, while those symbols are effectively taken from English, they aren't English anymore, but C (or any other language). I know it's a difficult thing to do to actually work like this, but you should be able to learn programming languages independently of your knowledge of English, because the symbol "printf" is C and means something as opposed to "char" or "?:"... Being a bit structuralist/functionalist here, but language can be seen as a system of mutually delimiting concepts... a "chair" means something but also means that it *isn't* a "table"... So, just learning that some symbols have some meaning in a certain programming language should be possible.

But, and as it happens in natural languages too, knowing the etymology of a word can help. For example, if I know Latin, I'm sure I can understand French a bit quicker than if I wouldn't... because I'll be able to relate them. Well, in that sense, knowing English will help you, but isn't determinant.

Coding in your native language is a non sensical effort. Languages build up and are born from communities... Like it or not, history has established that "printf" is what you say in C and not "ausdrücken". You can't change that easily... Yes, you could use a macro, but then, although there are quite big practical reasons for not doing that, you'd be using the language's constructs to create an in-place redefinition, something that just works as an illusion and isn't quite changing the language (it could, but I won't get into Diachronical Linguistics...).

I hope to have clarified things a bit :)

---

### Post by s.fox on 2010-02-23
> **lisati said:**
> A case in point would be the "printf" family of functions (and BASIC's 'PRINT' statement) - there might have once been a connection with printing a result on paper, but how many of us use printing terminals these days?

That is a very interesting thought.  I had never really looked too deeply at things like that before.    Thank you!   I feel like I have just seen something in a new light :D

-Silver Fox

---

### Post by smmalmansoori on 2010-02-24
Thanks for all the responses!

I think now I understand a bit more about the concerns that goes with attempting to program in a different language.
Yet I am a stubborn person ](*,) so I'll continue with my project, trying to address these concerns through different solutions rather than simply sticking with what is available. Wish me luck!:P

---

### Post by Claus7 on 2010-02-24
Hello,

> **smmalmansoori said:**
> Thanks for all the responses!

I think now I understand a bit more about the concerns that goes with attempting to program in a different language.
Yet I am a stubborn person ](*,) so I'll continue with my project, trying to address these concerns through different solutions rather than simply sticking with what is available. Wish me luck!:P

Good luck then!
Undoubtedly an interesting and a kind of different thread...

Regards!

---

### Post by CptPicard on 2010-02-24
OP, how much of a programmer are you, yourself? Just wondering... before embarking on anything like this, one should have a very robust idea of your own of what things actually matter in programming; not to mention implementation is challenging enough...

---

### Post by smmalmansoori on 2010-02-24
> **CptPicard said:**
> OP, how much of a programmer are you, yourself? Just wondering... before embarking on anything like this, one should have a very robust idea of your own of what things actually matter in programming; not to mention implementation is challenging enough...

I would say that I'm a good programmer, wouldn't go as far as saying excellent though :P

I have worked on this project for quite some time now. The difficult parts were not about the actual programming of the translation, but rather providing a proper development environment in Arabic to keep consistency, such as an Arabic terminal and an Arabic version control system etc.
It seems that this project is getting bigger and bigger as I try to translate more tools for those who will program in Arabic.

---

### Post by CptPicard on 2010-02-24
One of the big issues you'll face in the toolchain translation is that the beginner programmer is not going to be able to just copy the error into google to figure out what it means... translations of technical terms can be very confusing.

---

### Post by smmalmansoori on 2010-02-24
> **CptPicard said:**
> One of the big issues you'll face in the toolchain translation is that the beginner programmer is not going to be able to just copy the error into google to figure out what it means... translations of technical terms can be very confusing.

That is why I'm thinking of the following:

[LIST=1]
[*]Extensive documentation in the targeted language
[*][URL="http://ubuntuforums.org/showthread.php?p=8876216#post8876216"][COLOR=Blue]_The linked post_[/COLOR]
[/URL]
[/LIST]

---

### Post by MinimalBin on 2010-02-24
As an example, you program in C, not in english. If you say it would be easier to program in your native language, well, it's impossible - Python is like arabic language .. for some it's simply a set of symbols with no real meaning.

---

### Post by smmalmansoori on 2010-02-24
> **MinimalBin said:**
> As an example, you program in C, not in english. If you say it would be easier to program in your native language, well, it's impossible - Python is like arabic language .. for some it's simply a set of symbols with no real meaning.
When I say in Arabic I mean simply exchanging the keywords, not programming in a "natural language" way.

---

### Post by CptPicard on 2010-02-25
> **smmalmansoori said:**
> When I say in Arabic I mean simply exchanging the keywords, not programming in a "natural language" way.

And that has been said many times over that that is meaningless :) I could name them in anything and it's not going to make any impact on anyone's actual understanding of the workings of the programming language in anything that matters....

API function/class name translation will result in horrible inconsistencies and incompatibilities, and over there the "vocabulary" is so restricted that English is not a barrier really.

---

### Post by nvteighen on 2010-02-25
> **CptPicard said:**
> And that has been said many times over that that is meaningless :) I could name them in anything and it's not going to make any impact on anyone's actual understanding of the workings of the programming language in anything that matters....

API function/class name translation will result in horrible inconsistencies and incompatibilities, and over there the "vocabulary" is so restricted that English is not a barrier really.

There's an issue here of rather huge interest if you like this kind of topics.

Programming languages, even though nothing in them forces to make them this way, are based on symbols not created from a less conventional way than, say, English words. E.g. "print" in English has no resemblance to the act of printing something... but "printf" in C has a resemblance to English's "print" because there's a metaphor going on which makes both words in different languages have a somehow equivalent reference.

In all of this there's a very understudied aspect of language called "deautonymy", which is the process from which languages create new words from metalinguistic images of words (e.g. quotation...).

That's why someone with a bad English may feel not knowing English is a disadvantage when programming. Someone like that is falling in the illusion of confusing the origin of a language with the language itself. In an earlier post I said knowing English can be helpful, but it's not determinant to learn C ... you can just learn what "printf" does to "stdout" without knowing what "print" means in English, learning a new meaning with its word.

You can perfectly learn English without learning Anglo-Saxon.

---

### Post by MindSz on 2010-02-25
I started learning C before I learned English :)

---

### Post by HalfEmptyHero on 2010-02-25
> **smmalmansoori said:**
> The difficult parts were not about the actual programming of the translation, but rather providing a proper development environment in Arabic to keep consistency, such as an Arabic terminal and an Arabic version control system etc.

Are you able to type in arabic in the terminal? I've tried getting mlterm to do it, but I haven't figured out how yet.

---

### Post by smmalmansoori on 2010-02-25
> **HalfEmptyHero said:**
> Are you able to type in arabic in the terminal? I've tried getting mlterm to do it, but I haven't figured out how yet.

Using gnome-terminal font is by default "Monospace" and encoding set to UTF-8 does it. Note that the characters will be left to right and they will not be linked together. Not sure but adding Arabic in Language Support might help too.

Back on topic, what about the warning and error messages? wouldn't it help having translations for them available?

and for those who are weaker in English, wouldn't it be better for them to have the ability to name variables and functions in their native language to remember what they're supposed to do? as far as I know that can't be done in neither C nor C++

---

### Post by SigmaSanti on 2010-02-25
> **smmalmansoori said:**
> 
Back on topic, what about the warning and error messages? wouldn't it help having translations for them available?


I have seen translated error messages for java or some other language on the internet. Someone mentioned earlier that this could cause problems when you try to solve an error - if someone solves the error in another language, you will never find it by searching for the error in english. However, this could be solved by using universal error message numbers.
I have also seen non-english speakers have trouble with english error messages.

---

### Post by lisati on 2010-02-25
> **nvteighen said:**
> 
Programming languages, even though nothing in them forces to make them this way, are based on symbols not created from a less conventional way than, say, English words. E.g. "print" in English has no resemblance to the act of printing something... but "printf" in C has a resemblance to English's "print" because there's a metaphor going on which makes both words in different languages have a somehow equivalent reference.


What I heard [citation needed] is that when the BASIC programming language was invented, the PRINT statement actually did cause something to be printed rather than displaying something on a screen.

---

### Post by slavik on 2010-02-26
As has been discussed here, changing just the keywords would not work. One such example is (it's a language in india, but I cannot remember the name :(), which does not have a word for 'if' ...

In english (and russian, for example), the following can be read as a sentence:

IF x=5
  PRINT "HELLO!"
ELSE
  PRINT "GOODBYE!"
ENDIF

In the Indian language I am referring to, however, the following could be better translated into a full sentence:

x=5 IMPLIES
  PRINT "HELLO!"
ELSE
  Print "GOODBYE!"

Now, this is stemming from a discussion I had with someone from India in #perl6 on freenode.

Usually, we talk about localizing things. Think of GNU gettext and .po files. They way it works there is that we have strings that can be interchanged, this leads to two possible implementations of a language:
1. database type based on language table (as in: keyword{1}, which would be defined as 'new' and then different language tables would have the proper word), which is predominantly seen in web-based development.
2. some type of proxy on the output that would substitute the phrase/keyword as it is being output, so 'new' would be looked up in the english table, index of 1 found and then the word substituted with whatever is in index 1 of the target language.

BUT!!! Big but here ... another idea we had was: What if you could not only do a blind translation on words, but also a translation on the structure?

Consider the following perl6 based example:

for (@list) {
  print $_;
}

AND

{ print $_ } for (@list);

With that, there is no speed penalty for either loop since they will translate into the same byte code and operations to be performed. What does change though is the possibility of one structure (when translated to the programmer's native tongue) being favored more than the other because it is easier to think of one or the other structure in the native language. (As nvteighen has mentioned, there are beliefs that people tend to think in languages).

Another idea with this is that when you are saving a code file, it is translated into something intermediary (or maybe not even) and is then translated to the locale of the editor when being open, so that prints and says go from being english to being whatever language is set by locale, along with this the structure is switched (so long as not to change actual functionality) to better fit words. This way, you can go from a language where for (list) {do stuff} makes sense to a language where {do stuff} for (list) makes sense.

But this idea is as simple as any Comp Sci idea: Take something already in existence and apply it elsewhere. (This is how relational databases were invented (from flat files with awk) and now we are seeing object oriented databases from the same application, eg: hibernate).

---

### Post by nvteighen on 2010-02-26
> **smmalmansoori said:**
> 
and for those who are weaker in English, wouldn't it be better for them to have the ability to name variables and functions in their native language to remember what they're supposed to do? as far as I know that can't be done in neither C nor C++

Never confuse script with language. You could name variables in Arabic, provided that you use some transcription system.

One of the reasons why HTML documents are used for documentation is because it allows you to translate things into any language decently supported by UTF-8... Write one if you feel the urge to document in Arabic; it's the most practical thing to do in the end.

> **lisati said:**
> What I heard [citation needed] is that when the BASIC programming language was invented, the PRINT statement actually did cause something to be printed rather than displaying something on a screen.

Yes... but again, that's linguistically irrelevant. What you have is a word in BASIC that means something and that was taken from an English word; whether it still means like in English or not is just secondary. As you know, it ended meaning something else even in BASIC.

> **slavik said:**
> As has been discussed here, changing just the keywords would not work. One such example is (it's a language in india, but I cannot remember the name :(), which does not have a word for 'if' ...

In english (and russian, for example), the following can be read as a sentence:

IF x=5
  PRINT "HELLO!"
ELSE
  PRINT "GOODBYE!"
ENDIF

In the Indian language I am referring to, however, the following could be better translated into a full sentence:

x=5 IMPLIES
  PRINT "HELLO!"
ELSE
  Print "GOODBYE!"

Now, this is stemming from a discussion I had with someone from India in #perl6 on freenode.


Good point. Really good point I totally looked over... :P

Perl has an advantage over any other programming language because it uses some natural language's procedures like relying on a morphosyntactical base... That's why you can postpone for, if, unless, etc. And that's what contexts is really about.

But again, the thing is that doing these things will render the programming language into another one... The fact that it uses words from language X is irrelevant; the relevant thing is that it's a system of signs with its own (morpho-)syntactical and semantical rules... like any other language. If you change that, you're in another language. Unless you're in a metalinguistically able language like Lisp, Forth or Perl6...

Actually, the Lisp idea is not bad... Lisp's syntax is completely regular and there you have macros to bend the syntax however you like... Maybe there's the place for your idea!

---

### Post by lisati on 2010-02-26
> **nvteighen said:**
> 
Yes... but again, that's linguistically irrelevant. What you have is a word in BASIC that means something and that was taken from an English word; whether it still means like in English or not is just secondary. As you know, it ended meaning something else even in BASIC.


True, couldn't agree more! Line numbers and use of the "LET" keyword are largely irrelevant in recent dialects of BASIC I've looked at as well.

---

### Post by Shin_Gouki2501 on 2010-03-28
Hello and Hello dear threadstarter!
Does this help you?
[http://thinkmeta.wordpress.com/2010/03/27/scala-beauty-arabic-dsl/](http://thinkmeta.wordpress.com/2010/03/27/scala-beauty-arabic-dsl/)

---

