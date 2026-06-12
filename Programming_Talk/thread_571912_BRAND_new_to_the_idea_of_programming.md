---
title: "BRAND new to the idea of programming"
date: 2007-10-09
forum: Programming Talk
---

### Post by wallsofjericho on 2007-10-09
Okay...So I've never written a line of code in my entire life but i understand some basic concepts. I want to eventually program for games. What would be the best starter language? Also what is the current language used for programming games?

---

### Post by rfruth on 2007-10-09
Get the build essential package and go for it !

[http://laroza.pbwiki.com/]("http://laroza.pbwiki.com/")

---

### Post by ryno519 on 2007-10-09
> **wallsofjericho said:**
> Okay...So I've never written a line of code in my entire life but i understand some basic concepts. I want to eventually program for games. What would be the best starter language? Also what is the current language used for programming games?

The most common language in game development  is C++, which is what I suggest you start learning if game development is truly your goal. It's not as hard to learn as people say.

There are a few languages that are commonly used for game development, like C, Java as well as C# and python to a lesser extent. However, if you want to make a career of it C++ is a must.

And after a while you will want to pick up some assembly. You don't need to do that right away though.

---

### Post by Wybiral on 2007-10-09
Python + PyGame is a really good approach for a beginner to get into game development. You can write 2d or 3d games with it (there is also Soya3d which is a complete engine for game design in Python).

But, if you choose to take the C/C++ route, you should look into SDL and OpenGL, and if you choose to look into a game engine, several are listed here (a similar thread): [http://ubuntuforums.org/showthread.php?t=566144](http://ubuntuforums.org/showthread.php?t=566144)

Most modern game developers wont ever see code below the C++ level, occasionally C but rarely assembly these days (especially not in professional development).

---

### Post by pmasiar on 2007-10-10
More modern approach to games is to write all code in highly productive language like Python, profile it, and rewrite 5% time critical code in C for speed. Using fast C libraries for graphics of course. Pygame is good start for that.

---

### Post by aitorcalero on 2007-10-10
I suggest to start with Python. You can read "Dive into Python" guide which comes with Ubuntu default help documentation.
Nevertheless game programming is a "major-league" issue IMHO.

---

### Post by LaRoza on 2007-10-10
There are many resources for a new programmer that can be had for free. As said before, Python with PyGame are problem the quickest road to your goal. For the learning aspect, my wiki has resources for many languages, including Python.

Game programming can be extremely advanced, but is a common goal for beginners. By yourself, you will be limited to what kind of games you can write. You can join or modify existing open source code, however, which may be more rewarding than trying to hack your own completely new game. At first, games like Tic-Tac-Toe, Tetris, Astroids and card games are good to start with.

---

### Post by pmasiar on 2007-10-10
"Dive into Python" is book for experienced programmers, please DON'T suggest it to known beginners. Wiki in my sig has couple other books, aimed directly to beginners.

---

### Post by aitorcalero on 2007-10-10
It seems to be very RUDE response to my suggestion, DON'T you think? I found this book really helpful, I am absolutely free to recommend whatever I want.

---

### Post by slavik on 2007-10-10
I recommend Perl. :)

Not only is it dynamically and loosely typed, but it was built for text processing and has OpenGL and SDL bindings. :)

---

### Post by LaRoza on 2007-10-10
> **slavik said:**
> I recommend Perl. :)

Not only is it dynamically and loosely typed, but it was built for text processing and has OpenGL and SDL bindings. :)

Just like Python...

To the OP, Perl and Python are often the subject of long threads. Both are widely used, and have common features. For games however, PyGame is probably the best for a beginner, and I don't know of anything comparable for Perl. Learning both won't be hard, but Perl might be more confusing at first than Python.

---

### Post by pmasiar on 2007-10-10
> **aitorcalero said:**
> It seems to be very RUDE response to my suggestion, DON'T you think? I found this book really helpful, I am absolutely free to recommend whatever I want.

I assume you are experienced programmer, right?

But OP is BRAND new, so book good for you is not right for him, right?

You are free to advise whatever you want, I am am free to suggest any misunderstandings. I mistakenly assumed you care about improving of quality of your advice. Of course you are free to do whatever you want. Me too. :-)

---

### Post by CptPicard on 2007-10-10
> **slavik said:**
> 
but it was built for text processing and has OpenGL and SDL bindings. :)

Umm.. yes, and I know a farmer whose tractor was built for pulling agricultural machinery and hauling grain and it's got spoilers and speed stripes and a jacuzzi! :)

---

### Post by slavik on 2007-10-10
> **CptPicard said:**
> Umm.. yes, and I know a farmer whose tractor was built for pulling agricultural machinery and hauling grain and it's got spoilers and speed stripes and a jacuzzi! :)
AWESOME! Where can I get one?

---

### Post by pmasiar on 2007-10-10
> **LaRoza said:**
> [Perl is] Just like Python...

To the OP, Perl and Python are often the subject of long threads. Both are widely used, and have common features. ... but Perl might be more confusing at first than Python.

(One of mentioned threads is just about to start :-) )

One overlooked difference between Perl and Python is that Perl is weakly typed. It means that in Python "1" + 3 is error, while in Perl it's values is 4, and you can also do "1" _ 3 (IIRC) which makes "13". In Python, you have to do either "1" + "3" == "13" or 1 + 3 == 4, or use int() or str() to make appropriate conversion. Python is little picky, but it's nothing to compare how picky are C++ or java :-)

One of fundamental difference in approach between Perl and Python is, that Python deeply cares about code readability and ease to learn, while Perl prefers powerful if terse  code for experts.

[http://99-bottles-of-beer.net/](http://99-bottles-of-beer.net/) is a website with examples of code in many languages to compare (all printing text of the song "99 bottles of beer"). Go compare yourself to make your own opinion.

---

### Post by slavik on 2007-10-10
> **LaRoza said:**
> Just like Python...

To the OP, Perl and Python are often the subject of long threads. Both are widely used, and have common features. For games however, PyGame is probably the best for a beginner, and I don't know of anything comparable for Perl. Learning both won't be hard, but Perl might be more confusing at first than Python.
just like python?

you mean python has opengl and sdl binding just like perl. remember, perl was here first. :)

---

### Post by Wybiral on 2007-10-10
NO... We absolutely must not get into this again. I hate seeing peoples threads closed over silly little debates like this. I know we all want to say "my language is better" but we must resist for the integrity of this post. If a language debate begins, can we at least try to keep it relative to game development? Possibly with good examples and links to back up all the mudslinging?

I will start by saying that I haven't seen any serious games (especially nothing beyond simple 2d interfaces) written in Perl, while I have in Python. I would be open to links if you know of any projects that would prove this assumption wrong. Secondly AFAIK, Perl doesn't have any major game development modules such as PyGame or Soya3D. This would be a pretty big hindrance when developing any full-featured game.

Perl would probably by just as suited as Python for development of a text based game, but then again just about any language with decent string handling features would. I do want to make it clear that I'm not saying it isn't possible to write games in Perl, it just isn't as practical as Python.

---

### Post by slavik on 2007-10-10
> **Wybiral said:**
> NO... We absolutely must not get into this again. I hate seeing peoples threads closed over silly little debates like this. I know we all want to say "my language is better" but we must resist for the integrity of this post. If a language debate begins, can we at least try to keep it relative to game development? Possibly with good examples and links to back up all the mudslinging?

I will start by saying that I haven't seen any serious games (especially nothing beyond simple 2d interfaces) written in Perl, while I have in Python. I would be open to links if you know of any projects that would prove this assumption wrong. Secondly AFAIK, Perl doesn't have any major game development modules such as PyGame or Soya3D. This would be a pretty big hindrance when developing any full-featured game.

Perl would probably by just as suited as Python for development of a text based game, but then again just about any language with decent string handling features would. I do want to make it clear that I'm not saying it isn't possible to write games in Perl, it just isn't as practical as Python.

By the same reasoning C and C++ aren't suited for game development. Perl has access to SDL and OpenGL, what else do you need for a 3D game that those 2 don't provide?

As to the OP, pick anything with SDL(optional) and OpenGL(mandatory) bindings. :)

---

### Post by Wybiral on 2007-10-10
> **slavik said:**
> By the same reasoning C and C++ aren't suited for game development. Perl has access to SDL and OpenGL, what else do you need for a 3D game that those 2 don't provide?

As to the OP, pick anything with SDL(optional) and OpenGL(mandatory) bindings. :)

How so? There are tons of game engines for C and C++ and even more games written in C and C++. My point was that I haven't seen any for Perl (and I was hoping you would prove me wrong, but you didn't).

There are 3d engines and game engines for C, C++, and Python. From what I can tell, there are not any for Perl. There are plenty of games written in C, C++ and Python... From what I can tell, there are none in Perl. That's the only point I was trying to make.

---

### Post by slavik on 2007-10-10
> **Wybiral said:**
> How so? There are tons of game engines for C and C++ and even more games written in C and C++. My point was that I haven't seen any for Perl (and I was hoping you would prove me wrong, but you didn't).

There are 3d engines and game engines for C, C++, and Python. From what I can tell, there are not any for Perl. There are plenty of games written in C, C++ and Python... From what I can tell, there are none in Perl. That's the only point I was trying to make.
fine, [http://www.frozen-bubble.org/](http://www.frozen-bubble.org/)

---

### Post by wallsofjericho on 2007-10-10
Can anyone point me toward a good book for python, C, or C++? Beginner book of course.

---

### Post by slavik on 2007-10-10
C:
[http://www.amazon.com/C-Programming-Language-2nd/dp/0131103628/ref=pd_bbs_2/102-9858193-7031307?ie=UTF8&s=books&qid=1192059356&sr=8-2](http://www.amazon.com/C-Programming-Language-2nd/dp/0131103628/ref=pd_bbs_2/102-9858193-7031307?ie=UTF8&s=books&qid=1192059356&sr=8-2)

C++:
[http://www.amazon.com/C%2B%2B-Programming-Language-Special-3rd/dp/0201700735/ref=pd_bbs_4/102-9858193-7031307?ie=UTF8&s=books&qid=1192059356&sr=8-4](http://www.amazon.com/C%2B%2B-Programming-Language-Special-3rd/dp/0201700735/ref=pd_bbs_4/102-9858193-7031307?ie=UTF8&s=books&qid=1192059356&sr=8-4)

---

### Post by ryno519 on 2007-10-10
> **slavik said:**
> C:
[http://www.amazon.com/C-Programming-Language-2nd/dp/0131103628/ref=pd_bbs_2/102-9858193-7031307?ie=UTF8&s=books&qid=1192059356&sr=8-2](http://www.amazon.com/C-Programming-Language-2nd/dp/0131103628/ref=pd_bbs_2/102-9858193-7031307?ie=UTF8&s=books&qid=1192059356&sr=8-2)

C++:
[http://www.amazon.com/C%2B%2B-Programming-Language-Special-3rd/dp/0201700735/ref=pd_bbs_4/102-9858193-7031307?ie=UTF8&s=books&qid=1192059356&sr=8-4](http://www.amazon.com/C%2B%2B-Programming-Language-Special-3rd/dp/0201700735/ref=pd_bbs_4/102-9858193-7031307?ie=UTF8&s=books&qid=1192059356&sr=8-4)

I wouldn't consider "The C++ Programming Language" a beginners book. I'd start with something like Accelerated C++. It's a little bit easier to take in for a beginner.

---

### Post by Fbot1 on 2007-10-10
*The C++ Programming Language* and *Dive into Python* are fine for the noob, don't scare the poor guy. Most people who are in to game making don't really care about some aspects of programing so I think you should learn Perl, it's not great but it's fast with OpenGL. If you're willing I think you should learn C too.

---

### Post by shynko on 2007-10-11
> **pmasiar said:**
> I assume you are experienced programmer, right?

But OP is BRAND new, so book good for you is not right for him, right?

You are free to advise whatever you want, I am am free to suggest any misunderstandings. I mistakenly assumed you care about improving of quality of your advice. Of course you are free to do whatever you want. Me too. :-)

Who are you to say that "Dive into Python" is bad for the OP to look through.discrediting one another posts does nothing to help the 'quality' of the advice it does more of the opposite. I think it is pretty hateful of you to accuse aitorcalero of not wishing to help the OP ,and all it will ultimately do his bring about more questions.

now to the OP this website has more than 300 python tutorials [http://awaretek.com/tutorials.html](http://awaretek.com/tutorials.html)
so if you wish to learn python look through some of the tutorials :)
,also don't worry too much about what your first language is. it might not make a lot of sense right now ,but if you don't like it you can just go try something else.
good luck  :guitar:

---

### Post by LaRoza on 2007-10-11
> **slavik said:**
> just like python?

you mean python has opengl and sdl binding just like perl. remember, perl was here first. :)

Yes Perl was here first, and Python (most likely) learned from Perl among other languages.

FrozenBubble was written in Perl? Cool, I guess I'll have to brush up on my Perl skills.

---

### Post by pmasiar on 2007-10-11
> **shynko said:**
> Who are you to say that "Dive into Python" is bad for the OP to look through.

I am professional programmer with 25 years of experience. Who are you?
Edit: and maybe more importantly: I actually READ the book :-) [here](http://diveintopython.org/getting_to_know_python/index.html) is first code shown to reader. Do you think it is suitable for beginners with no clue?

[http://en.wikipedia.org/wiki/Dive_into_Python](http://en.wikipedia.org/wiki/Dive_into_Python) 
> Dive into Python assumes that the reader already knows a bit about programming, although not necessarily much about the Python programming language. This assumption may place the book out of reach of the first-time software developer. Although Python is a language through which it is possible to learn modern programming techniques, this book is not written with this intention.

> discrediting one another posts does nothing to help the 'quality' of the advice it does more of the opposite. I think it is pretty hateful of you to accuse aitorcalero of not wishing to help the OP ,and all it will ultimately do his bring about more questions.

aitorcalero has good intention but obviously has not enough experience to distinguish that book good for experienced programmer might not be the best for OP who is BRAND NEW to programming. And same applies to you, obviously.


now to the OP this website has more than 300 python tutorials [http://awaretek.com/tutorials.html](http://awaretek.com/tutorials.html)
so if you wish to learn python look through some of the tutorials :)

I looked through many tutorials, and selected half a dozen which are better than others, and linked them in my wiki. Providing links to 5 best of them is IMNSHO much BETTER ADVICE  than providing links to 300.

> also don't worry too much about what your first language is. 

Well, my EXPERIENCE (and experience of many many professionals, ie MIT) says that there IS difference and for a beginner is better to start with Python and not ie C++. Do you have some links to support your claims? Or you might not be aware that MIT uses Python as first language? I disregard high school and colleges using java as first language - they needed replacement for Pascal, and they obviously don't have a clue. Compared to that MIT does have a clue. They stated the term "hacking" :-)

@OP: about books for Python - just see my sig. And sticky to this forum.

---

### Post by ryno519 on 2007-10-11
> **Fbot1 said:**
> *The C++ Programming Language* and *Dive into Python* are fine for the noob, don't scare the poor guy.

I'm telling you, *The C++ Programming Language* is not designed for beginners. I've been programming for years, I've read and own the book. I am certain of this. Consider this excerpt from the preface.

"The book is aimed at programmers with some experience and a wish to master C++. It is not aimed at non-programmers trying to learn their first programming language or casual programmers trying to gain a superficial understanding of C++ as fast as possible. Consequently, this book focuses on concepts and techniques and goes to some pain to be complete and precise.

- Bjarne Stroustrup"

Take *Accelerated C++* on the other hand which IS intended for beginners. Take a look at the first programming example.

```

#include <iostream>

int main()
{
    std::cout << "Hello, World!" << std::endl
    return 0;
}


```

With that code there are 4 pages explaining what each line does.

---

### Post by pmasiar on 2007-10-11
It is such a waste of time to respond to misleading advice of ppl like Fbot and shynko, who strive to misled. Some forums have points, like karma, so after time one can build reputation, and then supposedly opinion of an established expert carries more weight than random guy, but until then, the only way I can see is to start heated debate every time misinformation is presented. Such a waste of time.

---

### Post by aks44 on 2007-10-11
> **pmasiar said:**
> Some forums have points, like karma, so after time one can build reputation, and then supposedly opinion of an established expert carries more weight than random guy

+1

Unfortunately this question has already been debated numerous times and the forum staff is not willing to implement such a "karma" system for now. Too bad IMHO.

---

