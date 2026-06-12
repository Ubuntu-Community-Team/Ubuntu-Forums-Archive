---
title: "Java help"
date: 2007-10-01
forum: Programming Talk
---

### Post by urk_nono on 2007-10-01
Hello! I just started at uni, and we're learning Java programming, but I don't understad a thing :(

Does anyone have a word of advice or have a good site they can redirect me to?

Any help is appreciated. 

Kind regards, Urk

---

### Post by Arwen on 2007-10-01
You can google "java tutorials" and find a lot.I started by [this]("http://java.about.com/od/beginningjava/a/beginjavatutor.htm").You can use BlueJ or Eclipse to run your programs.

---

### Post by urk_nono on 2007-10-01
Thanks for the site, Arwen. I've searched a lot using google, but I'm not sure how to use the tutorials in making a program I'm supposed to make :(

---

### Post by aitorcalero on 2007-10-01
Could you be more specific? What do you want to do exactly with Java? Do you have any programming knowledge?

---

### Post by Arwen on 2007-10-01
I started with really simple hello-world like programs,loops and then more complex stuff like classes and inheritance and even applets.Do you have experience of any other language?

---

### Post by urk_nono on 2007-10-01
**aitorcalero**: Hello, and thanks for the time to take a look! 
Right now I want to know how to use arrays in making a program for a weather statistics program which reads in the following:

A chosen month of the year.
How many days of the month you wish to use for the statistics (eg 5)
Maximum and minimum temperature for the chosen days
Amount of rain displayed in millimetres.

I don't know where to look, the book I've got is not helping me at all, and I've got no one to help me, except a few other people at school who knows about as little as me. I've got absolutely no programming backround, just some basic HTML. I'm starting to think I won't be able to make it :(

---

### Post by CptPicard on 2007-10-01
Is this some kind of an introductory Java course? How far along in it are you? IMO, your exercises should reflect the covered material...

You gave only a really vague description of what you are expected to do, but assuming from the wording that you're only at the very beginning and the concept of "arrays" has just been introduced, are you perhaps supposed to read all the data in from the command line arguments? If so... the "args" piece in the typical main method declaration 

```

public static void main(String[] args)

```

is the command line is an array of Strings. You've got args[0], args[1], args[2] and so on, which contain the data you're giving your program as parameters when you invoke it, something like

```

java MyApplication foo bar baz

```

So that args[0] = "foo", and so on.

---

### Post by urk_nono on 2007-10-01
CptPicard:

In truth my teacher has probably gone through the use of arrays, only that if I haven't done any exercises concerning arrays, I have no clue what she's talking about. 

We're supposed to write a driver program (one page for running the program it self) and another page which asks for data ( the static void). 

For the driver page I'm thinking I have to write the "engine" for the program it self, whereas the other page only asks for input of data.  

This is about as far as I've gotten into making the driver page:

public class Weather
{
     
      String months[] =  {"Jan", "Feb", "Mar", "Apr", "May", "Jun", 
                                      "July", "Aug", "Sep", "Oct", "Nov", "Dec"};
      
      private int[ ] maxTemperature;
      private int[ ] minTemperature;
      private int[ ] rain;

}

---

### Post by CptPicard on 2007-10-01
> **urk_nono said:**
> 
In truth my teacher has probably gone through the use of arrays, only that if I haven't done any exercises concerning arrays, I have no clue what she's talking about.

"Probably"? You haven't done any exercises? Uhm... first rule of university: Only skip lectures/exercises if you're completely confident you're capable of doing it on your own. Otherwise you're pretty guaranteed to be SOL later on, in particular so in subjects CS and maths.

> 
We're supposed to write a driver program (one page for running the program it self) and another page which asks for data ( the static void). 

Weird terminology. You mean two classes? Let's suppose so.

> For the driver page I'm thinking I have to write the "engine" for the program it self, whereas the other page only asks for input of data.

Ok, so you have a class for storage of Weather. Looks like you've got a start there. Now, you might consider building a **constructor** for the Weather class that initializes your data arrays to sufficient length according to a constructor parameter. Then you might write a **method** that lets you fill in the data into those arrays as it comes in from the class with main(). Finally, you will want to write a method that computes whatever statistics is wanted of the data.

As for the main method class, I'm not really sure still where you're supposed to get the input from... command line? File? I suppose at this stage it's sufficient if the input comes from hardcoded in the main() method class..

Mind you, we don't do your homework here, but if you have specific questions, let's see what can be done...

---

### Post by urk_nono on 2007-10-01
> "Probably"? You haven't done any exercises? Uhm... first rule of university: Only skip lectures/exercises if you're completely confident you're capable of doing it on your own. Otherwise you're pretty guaranteed to be SOL later on, in particular so in subjects CS and maths. 

I attend classes, I try to do the exercises, but when I can't get help in getting them right I'm screwed.

> You mean two classes? Let's suppose so.

You're right. I'm still trying to learn all the names for the specific actions.

> As for the main method class, I'm not really sure still where you're supposed to get the input from... command line? File? I suppose at this stage it's sufficient if the input comes from hardcoded in the main() method class..

I'm supposed to fill in the input when asked to by the program.

> Mind you, we don't do your homework here, but if you have specific questions, let's see what can be done...

I know, I'm just getting frustrated. I appreciate the help and the willing to help. I'll see if I can a specific question out of this.

---

