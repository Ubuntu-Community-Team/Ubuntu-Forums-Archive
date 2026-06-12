---
title: "Eclipse or NetBeans"
date: 2009-05-29
forum: Programming Talk
---

### Post by nebu on 2009-05-29
I am trying to learn JAVA.... I would like to know which IDE should I get started on..... Eclipse or Netbeans??

Am really confused.... I searched the same thing up on google and there is a lot of conflicting opinions!

---

### Post by froggyswamp on 2009-05-29
NetBeans is (much) more user friendly and easy to use.

---

### Post by sujoy on 2009-05-29
try both, stick with the one you like the most.

---

### Post by sonicb00m on 2009-05-29
> **nebu said:**
> I am trying to learn JAVA.... I would like to know which IDE should I get started on..... Eclipse or Netbeans??

Am really confused.... I searched the same thing up on google and there is a lot of conflicting opinions!

I prefer netbeans. It's quite nice and easish to get started with.

---

### Post by Psicolonia on 2009-05-29
Ok Java Gurus, how about like this: NONE!!!! seriously! I know java, I learned it and I code it for about 5 years now, professionally for 3 years.

Start with BlueJ. Google it, it's from a University. Also to start buy the book: "Objects First" (It's from the guys who made BlueJ).

Now here's why. Java can be confusing at first if you miss the point, specially if you come from other languages. And the learning curve can be eased with BlueJ. I did learn with blueJ. I hated it. At first. And now I see why. BlueJ gives you the habillity to make java code and execute specifically parts of that code and "inspect" how the objects are in memory. It does not help you! THaNK GOD! No intellisence to make you lazy. It does have code highlight however. But this gives you proficiency on the language. Start with BlueJ to learn, it's from a University and it was built for that. Buy the book and deep into it. Once you are finnished with it, move to Eclipse or Netbeans. By then you will know what's best for you. Otherwise you will end up using netbeans for no aparent reason besides: "it's easy to make interfaces". And then, when you double click the buttons it makes "inner classes" and crap you never heard about! :) So, instead of confusing yourself just now, learn with BlueJ, you won't regret it. :)

---

### Post by gnuman on 2009-05-29
> **Psicolonia said:**
> 
....Start with BlueJ. Google it, it's from a University. Also to start buy the book: "Objects First" (It's from the guys who made BlueJ)....


I agree that BlueJ is great for learning Java.  To be able to examine the individual instances of a class makes it much better than other IDEs for those new to Java.

The author even opened up the source code earlier this year.  ;)  

[http://www.bluej.org/news/opensource.html](http://www.bluej.org/news/opensource.html)

I teach AP Computer Science and for the level of programming we cover, BlueJ is perfect.  You can also easily generate test classes, send objects as parameters, etc.--all without having to write even one runner class.

---

### Post by myrtle1908 on 2009-05-29
For enterprise Java development I much prefer Eclipse.  For UI development NetBeans is great.

---

### Post by Psicolonia on 2009-05-29
To sum up, if you know Java, you pick and as myrtle1908 said, eclipse is great for enterprise java development. Things like tomcat integration etc work great with eclipse. And as you will learn, NetBeans has Matisse. Which is by far the best UI development component (just don't look at the source code ;))

---

### Post by doas777 on 2009-05-29
both.

for java gui stuff I've chosen swing (for good or ill...) just because it's core (and updates to some swt apps have pissed me off in a past life)  so I use netbeans. Matisse is actually decent, though layout management can still be a pain. 

for cli stuff I use eclipse, because I like the debugger a little better, and the javadoc integration support seems a little smoother.  I also use PyDev for eclipse, when i find i need step-thru , or somthing more advanced than geany in python.

---

### Post by doas777 on 2009-05-29
> **gnuman said:**
> I agree that BlueJ is great for learning Java.  To be able to examine the individual instances of a class makes it much better than other IDEs for those new to Java.

The author even opened up the source code earlier this year.  ;)  

[http://www.bluej.org/news/opensource.html](http://www.bluej.org/news/opensource.html)

I teach AP Computer Science and for the level of programming we cover, BlueJ is perfect.  You can also easily generate test classes, send objects as parameters, etc.--all without having to write even one runner class.

I appluad your insistence that your students start off without intellisense (or whatever the oss word for it is). 


at the same time, i really hate bluej. I understand the philosphy, but i had been programming professionally for years before anyone asked me to use it,  it really feels like a toy.  

but then again, when i recall my first programming class i realize that, i started with a terminal session on an as400, tapping out assembly, so  perhaps trial by fire is the best approach. you gotta face the fire sometime. might as well be today.

so now that i've come to the oposite conclusion that I started this post out with... 

Good job!  I wish i had had the opertunity to take classes that early in my development.


cheers

---

### Post by HotCupOfJava on 2009-05-29
Here is my two cents:

If you REALLY want to get a handle on Java, you need to learn what is going on when you compile, make packages, .jar files, etc. And you also need to learn about setting classpaths. So I would suggest keeping it simple and go with a plain text editor and a command terminal rather than some IDE to start with. GEdit will recognize a .java file once you save it and will at least highlight the code for readability.

Once you really start digging into it and start making some larger applications, an IDE can really help out by helping you locate all references to a variable quickly, immediately pointing out syntax errors, and allowing you to "browse" methods of a class as you code, without having to keep another window open with the documentation (although I still frequently do). And for making really professional-looking user interfaces, Netbeans is tops.

---

### Post by bkarjala0001 on 2009-05-30
I'm using eclipse for no other reason than, it's the IDE I was introduced to when I started to learn java. My only one complaint is that it is poorly integrated with Ubuntu.

---

### Post by jimi_hendrix on 2009-05-30
if you are doing swing stuff, netbeans, otherwise i use eclipse

---

### Post by kpkeerthi on 2009-05-30
Eclipse gets my vote. It has everything a hardcode Java/J2EE developer would ever need. Plus, it is based on SWT so the UI is snappy and responsive and looks native to the Operating System it is run on.

Here are some (just a tip of an iceberg): 

Support for rich desktop applications using JFC/Swing & SWT: [http://www.eclipse.org/vep/WebContent/main.php]("http://www.eclipse.org/vep/WebContent/main.php")

Support for J2EE development: [http://www.eclipse.org/home/categories/index.php?category=enterprise]("http://www.eclipse.org/home/categories/index.php?category=enterprise")

Support for UML: [http://www.eclipse.org/home/categories/index.php?category=modeling]("http://www.eclipse.org/home/categories/index.php?category=modeling")

---

### Post by gnuman on 2009-05-30
> **doas777 said:**
> .... when i recall my first programming class i realize that, i started with a terminal session on an as400, tapping out assembly, so  perhaps trial by fire is the best approach....

I learned Java using the CLI and VIM.  ;)

Now that I think about it, you have a point.  Someone new to programming will probably benefit most from a simple text editor.  Most of my students, though, were already familiar with at least one other language, so teaching them Java was very much about OOP and having them see more typical Java objects was nice.  Starting with a simple text editor with Java is pretty clunky and it takes a while for a student to get to the point where they're having objects interact with other objects.  Compare that to starting Python with a simple text editor and you see what I mean.

As far as NetBeans vs. Eclipse:  I prefer Eclipse, but some of my top Java students prefer NetBeans simply for it's GUI-creation tools.

---

