---
title: "Best way to learn Java before start of semester."
date: 2010-05-19
forum: Programming Talk
---

### Post by Quake on 2010-05-19
Well... I had a bad programming semester this year and almost failed the first class and dropped from the second. One of the concept that I can't get my mind into is the objects. What is the best way to practice?

---

### Post by soltanis on 2010-05-19
Write programs.

If you can't understand objects, you're going to have a lot of trouble doing Java my friend...after all, almost everything in Java has to do with objects, for better or for worse.

What concepts do you not understand with objects? We can do our best to try to explain them to you since it sounds like your professor did a very poor job of it.

---

### Post by ctimko on 2010-05-19
Honestly I hate Java, with a passion.  However, OOP is really easy to learn if you start writing little programs.  Try writing an inventory program, that is something that could require a LOT of OOP.  You don't necessarily have to attach a GUI to it, just make it a console application.  Or make a program that uses the aminal kingdom (or plant kindgom).

Just be like

class Squamata : Reptillia, IOrder
{
   Squamata() { // code }
}

class Serpentes : Squamata, ISuborder
{
  Serpentes() { // code }
}

List<Animalia> listOfAnimals = new LinkedList<Animalia>()
listOfAnimals.add(new Serpentes());

you know, something like that.

Practice, practice, practice.  Now if you did fine on the programming projects, then you should really learn the terminology.  Get in the habit of using it as much as you can.  When you practice, write comments that explain what you did and what OOP methods you used.

---

### Post by KdotJ on 2010-05-19
Out of interest why do you hate java?

---

### Post by KdotJ on 2010-05-19
> **ctimko said:**
> 
class Squamata : Reptillia, IOrder
{
   Squamata() { // code }
}

class Serpentes : Squamata, ISuborder
{
  Serpentes() { // code }
}

List<Animalia> listOfAnimals = new LinkedList<Animalia>()
listOfAnimals.add(new Serpentes());



isn't that C# syntax?

---

### Post by Quake on 2010-05-19
Thanks guys, to reply to Soltanis, almost the whole mental concept about how the objects works. 

I know how the Matrix, arrays... work. Junit? A little bit of trouble.
I just need a little bit of a guiding hand about how I can practice this summer so that I can be ready for this course: [http://www.site.uottawa.ca/~turcotte/teaching/iti-1121/]("http://www.site.uottawa.ca/%7Eturcotte/teaching/iti-1121/")

To give you an idea, I had a D *yeesh* on this course (Sorry, it's in french, I will try to find the english course): [http://www.site.uottawa.ca/~garbez/iti1520/]("http://www.site.uottawa.ca/%7Egarbez/iti1520/")

P.S Recommend me simple programs that I can do in order to practice, I know programming is like math.

---

### Post by cph05a on 2010-05-19
> isn't that C# syntax? 
That might explain why he hates java so much . . .


You should find a tutor that knows java well. That way you can have someone there who can give you face to face feedback. Even the little things like coding style can make a big difference.

The best way to become a good programmer is to program A LOT outside of your basic school requirements. Try thinking of some simple projects to try and gradually work on more complex projects.

Here are some basic things you can do with Swing (or in a web browser if you're learning J2EE)
Basic (one at a time):
launch a window
launch a window with a button in it
a program that does something when a button is clicked on

More Interesting:
Make a text editor with basic functions like saving a file, copy and paste, print
Make a drawing client (like Paint)
Make a chat client with a GUI


EDIT:
One more thing . . .
The API is your friend. 
[http://java.sun.com/javase/6/docs/api/](http://java.sun.com/javase/6/docs/api/)

---

### Post by Quake on 2010-05-19
> **cph05a said:**
> Here are some basic things you can do with Swing (or in a web browser if you're learning J2EE)
Basic:
launch a window
put things in the window
do something when a button is clicked on

More Interesting:
Make a text editor with basic functions like saving a file, copy and paste, print
Make a drawing client (like Paint)
Make a chat client with a GUI

Right now, we're not learning gui... but I suppose I could start by writing programs that are not in the current curriculum.

I've noticed programming is a lot like art, you need to have an imagination about what you want to accomplish and finding ways to do it. 
Right now, my mind is blank, I have no idea about what I should do. 

So for those who started studying programming, how did you start? because I've noticed that a lot of students in my class already did programming as their hobby.

---

### Post by KdotJ on 2010-05-19
Lol at cph05a


And indeed lots and lots of programming and mini projects. Swing (and AWT) itself is a very good demonstration of objects and inheritance.

---

### Post by achron on 2010-05-19
Go get a "Learn Java in 7 days" or whatever book. One that will at least have a chapter on Objects (perhaps the textbook from your prior class). You could also go check out the tutorials available at java.sun.com/docs/books/tutorial/java/javaOO/classes for example.

Now pick a subject for your programming study that you know something about.  What about your CD collection (you do own CDs, don't you)?  Choose a domain you know so you can focus on the technology.

Then model the CDs in your application. Being able to reference something concrete may make it easier to grasp the concepts.

A CD has a title, an artist [for simplicity, a solo album might be best ;)], an ISBN number, publication date, and multiple tracks. Tracks would be a class of their own, with their own attributes; a track title, a play length, and a position come to mind.

The class declaration is essentially a template telling you what a thing (object) of that type has, and can do.

---

### Post by GregBrannon on 2010-05-19
Everybody learns differently, though practicing what you're trying to learn is essential to learning programming.  You know that.  I'm still on the path to enlightenment, but I find it helpful to read difficult concepts explained by more than one author.

There are many free sources for Java info on the internet; free books, tutorials, etc.  Find 3 - 5 and read their explanations of objects and other topics you need to understand better.  Perhaps one will make more sense to you than the others, or after reading nearly the same thing 4 or 5 times, the concept will begin to make more sense.  Add some practicing to that, and your understanding will be improved and reinforced.

You also asked how others started programming.  You could get as many different answers to that as there are people here, and I don't think it would help.  The best way to start learning something is to start.  It's never too late or the wrong time.  If you're interested in learning, just get on with it.

Don't give up.  Come back and ask for help on the finer points as you take the journey.

---

### Post by KdotJ on 2010-05-19
> **GregBrannon said:**
> 
Don't give up. 

+1
It's easy to get frustrated with programming, but sticking with it is worth it. Objects and classes took me a while to understand the concepts, but I think it will eventually just click. And when you do "get it" you'll see how simple the "basic" concept of objects is

---

### Post by Some Penguin on 2010-05-19
> **Quake said:**
> Right now, we're not learning gui... but I suppose I could start by writing programs that are not in the current curriculum.

I've noticed programming is a lot like art, you need to have an imagination about what you want to accomplish and finding ways to do it.

Programming is quite mathematical in a certain sense -- if you are lousy at logically decomposing complex problems, you will probably be a poor programmer.

Regarding objects and classes, look up "abstract data types".  They're useful for such decomposition.   Example:  if you're doing matrix arithmetic using sparse matrixs ca. 500K x 500K, you may not care about the exact implementation details so long as it's resource and performance seems appropriate and it provides the interface you need, and ideally you wouldn't have to change all the client code that uses the matrix if the matrix implementation is improved.  Abstraction is quite reasonable for that sort of thing.

> Right now, my mind is blank, I have no idea about what I should do. 

So for those who started studying programming, how did you start? because I've noticed that a lot of students in my class already did programming as their hobby.

My unhelpful answer would be that I started in the mid-80's and had a slightly odd upbringing -- recreational mathematics instead of comic books, for instance.

---

### Post by Quake on 2010-05-19
Thanks everybody.

I will definitely come and ask questions. So right now, I need to practice.
And Achron, a CD Collection software will be a good idea. 

If anyone has an idea of program that I could create to practice, let me know.

Thanks.

---

### Post by soltanis on 2010-05-20
You can create basically anything, and it doesn't have to be useful. In fact, if you are just playing around and learning concepts, I recommend it not try to be useful, because useful programs tend to have to conform to things like standards which are easy to screw up, and when you get little things wrong, they really distract from the point of the exercise.

---

### Post by dragos2 on 2010-05-20
Read Thinking in Java 3,4. 
3rd version is free and still actual.

It is hard to get a better reference.

---

### Post by CSInDevelopment on 2010-05-20
look at wibit, got me through some rough patches
heres the first video , you will need to skip some because you already know the basics, but they are good for revision or for first discovering. 
[http://www.youtube.com/watch?v=Hl-zzrqQoSE ]("http://www.youtube.com/watch?v=Hl-zzrqQoSE")

---

