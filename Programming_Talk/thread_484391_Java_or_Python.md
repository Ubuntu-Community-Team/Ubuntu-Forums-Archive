---
title: "Java or Python?"
date: 2007-06-25
forum: Programming Talk
---

### Post by Baelfael on 2007-06-25
I had a previous thread about my dream of eventually creating a game. Basically either an Isometric MMORPG, or a 2D Sprite and 3D Landscape MMORPG. It's inspired by DeviousMUD and RuneScape Classic, both games that are written in Java. I had a thread on this before but there wasn't much opinions on both languages, basically only on Python. 

For my game that I will eventually create (don't worry, I'll start very small and then program bigger things until I'm prepared for my big project), which will look something like this: [http://content.answers.com/main/content/wp/en/7/7c/DeviousMUD2.PNG](http://content.answers.com/main/content/wp/en/7/7c/DeviousMUD2.PNG)

So, for my needs, what programming language should I learn, Python or Java? I would like opinions on both.

---

### Post by pmasiar on 2007-06-25
pygames for simpler games, or pysoy for MMORPG. 

You can try Java, but it is 5 times as much work IMHO. Try something simple in Python first, then try reimplement it in Java (and remember second time it should be easier - but hardly will). Then decide.

---

### Post by kknd on 2007-06-25
Try booth, and choose wath you liked most.

As a Java programmer, I recommend it =).

Python is also very good.

---

### Post by DosAge on 2007-06-26
I would like to be able to tell you Java no question, but I have little to no python experience, so any comparison would be lopsided at best. 

I will however offer that I think you might find that Java has grown leaps an bounds over the last couple of years in the area of game development. You may want to have a look at some of the 3D Java engines that are currently available. Have a look at 

Jmonkey - [http://www.jmonkeyengine.com/](http://www.jmonkeyengine.com/)
Java3D - [http://www.j3d.org/](http://www.j3d.org/)

I have had fantastic success using both of these, though I would lean towards Jmonkey for the more refined collision detection (imho)  as well as some pretty slick particle systems. 

I think the number one reason I can think of for you to go with java would be that you can start small, and build your skills. Everything you learn along the way will help you when it comes time to start digging into the game building, and you can stay 100% Java while you do it. You will only need to learn one language to take you all the way to your goal. 

If you can do the same thing in Python, then ... flip a coin =)

Cheers
DosAge

---

### Post by skullmunky on 2007-06-26
try crystalspace or ogre.  for game development, particularly if you want to make a MMORPG, it'll save time to start with a more fullblown 3D engine or game engine, that already has functionality for loading meshes, animations, shader programs, and has some work already done for physics, networking, AI and game logic,etc.  it's fun to start from scratch of course, but just takes longer.

crystal and ogre are both primarily C++ libraries. crystal has a nice high-level editor built into Blender, with python scripting.  Ogre also has python bindings though they seem to be in a big transition right now.   

for 3D and a lot of graphics intensive stuff i'd lean towards python, unless you want builtin cross-platform from the getgo.  the tradeoff with java for cross-platformability is that the graphics performance is (subjectively) abysmal on linux compared with windows and osx java ports.  i don't know why, but you'll see low framerates just from trying to refresh a decently sized window unless you get your java opengl acceleration tweaked out properly.  i blame the AWT wrapper for X.  

for crystalspace, ogre, soya, or other graphics libraries with python bindings, you can probably get better performance because the heavy lifting is done with native code.

---

### Post by xtacocorex on 2007-06-26
Does it really matter what we tell you to use? In the end, it'll be you having to deal with the syntax and the code.  Which do you prefer?  

As pmasair said, Python will be a lot easier to code in initially than Java, but if you are already a decent programmer, language shouldn't matter.  

It all comes down to understanding how to code.  I've said this numerous times to people.  Syntax isn't important, it's the process behind the language.  If you master that, it'll relate to all languages and it's a quick jump from one to another.  

I have these views because I was taught programming in my Engineering courses to help solve difficult math problems and solving those types problems gives good insight into algorithm development and logic.

---

### Post by Baelfael on 2007-06-26
Keep in mind I've never programmed in my life. I think I may be leaning towards Java, but I don't know.

---

### Post by LaRoza on 2007-06-26
> **Baelfael said:**
> Keep in mind I've never programmed in my life. I think I may be leaning towards Java, but I don't know.

Use Python then. It is much easier to learn.

You are not limited to one language, learning one makes it easier to learn others. If you learn Python first, learn C++ or Java will be much easier. You could start with C++ or Java, and Python would be even easier to learn, but if you are just starting out, Python is easier.

Consider the following programs that do the same exact thing:
```

#In Python
print "Hello world!"

```
```

#include <iostream>
//In C++
int main()
{
   std::cout << "Hello world!" << std::endl;
   return 0;
}

```
```

//In Java
class Hw
{
   public static void main(String args[])
   {
      System.out.println("Hello world!");
   }
}

```

As you can see, the languages have different syntax to do the same thing. You get used to the syntax once you understand it.

---

### Post by merinda on 2007-06-26
> **Baelfael said:**
> I had a previous thread about my dream of eventually creating a game. Basically either an Isometric MMORPG, or a 2D Sprite and 3D Landscape MMORPG. It's inspired by DeviousMUD and RuneScape Classic, both games that are written in Java. I had a thread on this before but there wasn't much opinions on both languages, basically only on Python. 

For my game that I will eventually create (don't worry, I'll start very small and then program bigger things until I'm prepared for my big project), which will look something like this: [http://content.answers.com/main/content/wp/en/7/7c/DeviousMUD2.PNG](http://content.answers.com/main/content/wp/en/7/7c/DeviousMUD2.PNG)

So, for my needs, what programming language should I learn, Python or Java? I would like opinions on both.

Python is easier. You will be much productive with Python. But.... Python is slower than Java. So do you need the performance???

---

### Post by insane_alien on 2007-06-26
python will probably be too slow as it is an interpreted language. you'll want something you can compile so it runs faster. not that python is bad, i use it all the time.

---

### Post by Smygis on 2007-06-26
Actuly Python is only a fraction slower then Java, And in some cases its faster.

And using python, The perfomence is mostly in the modules. Not in the language itself. And if something is realy slow, reimplement it in C.

Python is not too slow.

---

### Post by pmasiar on 2007-06-26
> **merinda said:**
> But.... Python is slower than Java. So do you need the performance???

Performance? He is trying to learn programming. If his java code is not working, what performance it has? I bet you that beginner will write more working code in Python than in Java.

Or, if my code might not work at all, I will write more non-working code in java than working code in Python :-) Writing non-working code is *so* much simpler :-)

---

### Post by LaRoza on 2007-06-26
> **insane_alien said:**
> python will probably be too slow as it is an interpreted language. you'll want something you can compile so it runs faster. not that python is bad, i use it all the time.

Python can be compiled to byte code, like Java. 

The OP wants to learn first, not start working on the game immediately anyway.

---

### Post by blah blah blah on 2007-06-26
I suggest you groovy or Jpython use for the client (if you must) but still mostly use C, C++, or Clean on the server.

---

### Post by steve.horsley on 2007-06-27
Python is a good language to start with and pick up the basics of programming, but you could learn some bad habits, and I don't think python is likely to teach you to think Object Oriented programming very easily. 
I think java would be better wor writing an MM game, because it's faster, safer, and you will pretty-much need OO for a large project like a game server. 

So I would say look at python for a few weeks or months, then start on java. Suns java tutorial is fantastic, and the documantation is extremely thorough.

---

### Post by vexorian on 2007-06-27
In this case, I must pick the lesser evil. Go Java, well its jit compilation is probably going to make it much faster than interpreted python anyways.

---

### Post by LaRoza on 2007-06-27
Learn both.

---

### Post by kknd on 2007-06-27
Python IS slow. Benchmark it. But there is no big disvantage, since you can build a C/C++ module for the "bottleneck code".

---

### Post by pmasiar on 2007-06-27
> **steve.horsley said:**
> Python (...snip) you could learn some bad habits, and I don't think python is likely to teach you to think Object Oriented programming very easily.

LOL. What bad habits? After you learn Python, you will laugh at the fools who struggle with clunky Java OO to get things done - because you will know from your own experience how much simpler it would be in Python. So yes, you will have bad habits - you will have to force yourself to do it hard way in Java to make your boss happy. I know I do.
 
For a hillarious rant about Java's OO, read [Execution in the Kingdom of Nouns](http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html)

> I think java would be better wor writing an MM game, because it's faster, safer, and you will pretty-much need OO for a large project like a game server. 

Funny - maybe he can just use nice flexible Python game server like twisted? Until you can prove what part is slow -- it is fast enough. Wannabes pretend by writing (slowly) game projects in "hard but fast" languages. Experts build prototype in Python, then profile to find the bottlenecks, and implement (with fixed, proven API!) time-critical part as C library. In 1/3 time it takes to make same app in Java, of course. Try it.

How many lines of code and how many weeks will take you to create simple text-based adventure game engine in Java? It is about a page of code in Python.

> So I would say look at python for a few weeks or months, then start on java. Suns java tutorial is fantastic, and the documantation is extremely thorough.

I agree - docs is great. And it is a lot of it to read :-)

Of course it is good to know Java - Java will give you safe (even if  boring) job. But friends don't let friends program games in Java for fun :-)

---

### Post by vexorian on 2007-06-28
no strict typing => bad habits.
indent based syntax highlight => bad habits
very awful syntax => bad habits.

I mean seriously, I met this python user he made an extension to another proprietary language, the idea to make the extension was very good but since he was plagued with python syntax inside his mind he implemented the new features with such horrible syntax...

And Java is probably as easy to learn as python anyways... Regarding the lines of code for a text adventure I think I could do it in 300 lines in Java and like 210 in c++ none is extremely bad, and short looking code is overrated and does not necesarily mean that it was easier to make...

---

### Post by pmasiar on 2007-06-28
> **vexorian said:**
> no strict typing => bad habits.
indent based syntax highlight => bad habits
very awful syntax => bad habits.


FYI, Python is dynamically but stricly typed language. I am not sure if you can tell the difference, but just FYI.

Obviously, we live on different planets. On my planet, we breathe oxygen, proper identation is important part of correct code and not a bad habit, and making code shorter does *not* mean cramming more statements into longer lines. 

I do not think I can explain it any cleaner, so will not waste my time anymore - any questions from oxygen-breathing lifeforms?

---

### Post by vexorian on 2007-06-28
But I know something, forced indent and lack of end blocks are an abomination. 

Lack of end blocks is what makes python code pretty much unreadable and promoting that for new users is pretty much murder to me.

---

### Post by Smygis on 2007-06-28
> **vexorian said:**
> But I know something, forced indent and lack of end blocks are an abomination. 

Lack of end blocks is what makes python code pretty much unreadable and promoting that for new users is pretty much murder to me.


So you write all your code on one line? Or without indentarion?

Actuly its proven that programmers dont normaly see the end and begin statments if the code is properly indented. They look at the indendation.

And python is wery much readable. It culd not be more simple. When the text moves left the block is over. Simple. better then THISBLOCKISOVERYOUJERK.

Unlike C and its deriviates. Where the indentation dont matter a thing. BUT HEY! They still indents ther code. WHY! if its such a bad habit.

And FYI: if a and b: is much more clearer then if(a&&b){}. And the later can only be discribed as "very awful syntax".

---

