---
title: "Pygame Tutorials"
date: 2011-09-15
forum: Programming Talk
---

### Post by Ravenshade on 2011-09-15
Hi, 

I've been wandering around these pygame tutorials and I can't seem to find a decent one anywhere. Either they use things they don't explain, use methods which the rest of the community do not appear to agree with or are simply downright sloppy. 

Pygame is essentially SDL however there are lots of name changes around it appears. All I'm trying to do at the moment is just display a 2D graphic...or a sprite, preferably in the best way possible. I had found a tutorial that was dealing straight into classes. 

[http://pygametutorials.wikidot.com/tutorials-two](http://pygametutorials.wikidot.com/tutorials-two)

And sure, it's really good, a nice introduction. But it doesn't work. It should. But it doesn't, mainly due to the quality of the tutorial and due to the scale of errors I haven't the foggiest what I'm supposed to be doing. From a beginners point of view at least. 

I have tried some of the tutorials from 
[http://pygame.org/wiki/tutorials](http://pygame.org/wiki/tutorials)

Unfortunately, most fall foul of the problems above or are specific to certain designs and there is little that connects the tutorials except for "import pygame" >.>; The most I've learned about Pygame comes from the first tutorial I mentioned and another one which was specifically about a chimp application. Unfortunately, due to not being able to get the code, the tutorial is useless to me (and I had to find another). 

I would very much appreciate the help.

Regards
Ravenshade

---

### Post by Senesence on 2011-09-15
I wouldn't say that pygame is essentially SDL - it's a fairly customized wrapper, since it does provide facilities in addition to those found in SDL (such as the sprite, and other, higher-level classes).

But, those additions don't really make pygame programs any less complicated. Actually, it's just more stuff that you need to know about, and there is no set standard on how to actually program games, so even small demos are all going to be very different.

I actually made a small demo for someone a few days ago, that used pygame to display a set of small animations from a 4 x 4 spritesheet ([http://ubuntuforums.org/showthread.php?t=1841958](http://ubuntuforums.org/showthread.php?t=1841958)). If you can get that running on your machine, I can basically explain, in detail, everything in that program.

PS:

There is a really good set of SDL tutorials here: [http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php) . C++ is used there, but you'll probably need to learn that language somewhere down the line, so you might as well start now.

---

### Post by Ravenshade on 2011-09-15
I have already got a game...*cough* working in C++ SDL and I'm very familiar with LazyFoo's tutorials. *see previous threads bothering DWhitney for assistance* 

Anyway, after getting that far in C++ I decided that I didn't understand programming concepts enough to get any further with that language. It is a very technical language and while it is indeed a very useful language, it isn't good for a learner, or one who isn't familiar with OOP, Memory Management or the like. Python offers a much gentler curve and so far, far more readable and understandable, along with garbage collection and various other attributes that are often more associated with Java. There's also a variety of other reasons why I've chosen Python over Java and most other languages, but the reason I've chosen it over C++ is this... 

```
while(x<10)
{
    cout << "Hello World" << endl;
    x++
}
```

```
while x<10:
    print("Hello World")
    x += 1
```

As you can see right here, there's two less lines of code and less useless information. Python encourages readability and code structure. Where as C++ promotes machine speed and efficiency. One I should learn, the other I don't need yet.

---

### Post by P05TMAN on 2011-09-15
This book has been an outstanding tool for programming games with Python: 
[http://inventwithpython.com](http://inventwithpython.com)


It covers the use of pygame

---

### Post by Ravenshade on 2011-09-15
O_O I shall have a read. That looks like an excellent tutorial! (I'll with-hold meh final verdict though >.<)

---

