---
title: "Java: Beginner problems"
date: 2010-11-08
forum: Programming Talk
---

### Post by fallenshadow on 2010-11-08
I am having some stupid problems with the very simple beginnings of using a class in Java. It happens on the line where I attempt to use the class... apparently it cant find the class. 

Please look at these very small files attached.

PS: By very small I mean tiny! :)

---

### Post by GabrielYYZ on 2010-11-08
are you using an IDE or just toughing it out with a basic text editor? to use a class i think you have to type:

import class.name;

and the class should be in the same location as the main class. i'm a newbie in java too and i'm more familiar with this in an IDE (i use netbeans, personally) maybe someone more advanced could be more helpful.

---

### Post by spjackson on 2010-11-08
> **fallenshadow said:**
> I am having some stupid problems with the very simple beginnings of using a class in Java. It happens on the line where I attempt to use the class... apparently it cant find the class. 

Please look at these very small files attached.

PS: By very small I mean tiny! :)
You could tell us what errors you get!

These are the errors I get when I compile your code.
```

Tester.java:15: cannot find symbol
symbol  : variable EasyIn
location: class Tester
      name = EasyIn.getString();
             ^
Tester.java:17: cannot find symbol
symbol  : constructor Film(java.lang.String)
location: class Film
      Film name1 = new Film(name);
                   ^
2 errors

```I've no idea what EasyIn is or where to find it. Presumably you do.

As for the second error, this is because Film has no constructor. Edit Film.java and add the constructor.
```

   public Film(String nameIn)
   {
        name = nameIn;
   }

```

---

### Post by trent.josephsen on 2010-11-08
Not sure why you uploaded DOS .txt files, but you'll want to rename them as .java if you want to compile them.

---

### Post by zaheen on 2010-11-09
First of all, there is no package called EasyIn being imprted into the source files. If you found the code from somewhere then you forgot to take the class file for EasyIn (as far as I know, EasyIn is not a part of the standard JavaAPI).
Second, you do not have a constructor assigned for the Film class. You should have written that part like so:

Film film = new Film();
film.getName(name);

For input, you could have chosen to import java.util.Scanner. Use Scanner to take input from the keyboard instead of EasyIn.

---

### Post by teh_pwnzr on 2010-11-09
> **spjackson said:**
> As for the second error, this is because Film has no constructor. Edit Film.java and add the constructor.
```

   public Film(String nameIn)
   {
        name = nameIn;
   }

```
 
THIS. Write a 
 
Java is nice and will automatically create a default constructor for you at compile time. However, this default constructor will not have any arguments that you can pass to it and will be an empty block of code.
 
What you are trying to do is pass an argument to the default constructor that is not written to handle anything being passed to it. To fix this, add spjackson's code above to your Film.java.
 
Also, in your tester.java file, the "System.out.println(name);" statement will not work like you want. It will simply return the contents of String "name", not the name of the Film that you just created.
 
To return the name of the Film "name1" that you create, try "System.out.println(name1.getname());"
 
Your getName method is not much of a getName method at all, but more of a setName method, as it SETS the contents of String "name" to whatever the user passes the method when it is called.
 
You will also need to set the return type of the method "getname" in your Film.java file to return a type String. "public String getName()". The void tells the compiler that this method does not return anything. By setting this to String, you are telling the compiler that the method will return a string. Within this method now, you will need a return statement that returns a variable of type String. This will be "return name;"
 
I have attached a copy of your code that should have your errors fixed. I didn't have time to install a java compiler on the PC i'm on, but it should be pretty close to what you want.

---

### Post by fallenshadow on 2010-11-10
> Not sure why you uploaded DOS .txt files, but you'll want to rename them as .java if you want to compile them.

Thats simply because the forums dont allow me to upload a .java file, so I uploaded a .txt instead. :)

Ignore errors relating to EasyIn as its just a separate class which is used for input.

Thanks for all the input in getting me started with Java. teh_pwnzr you were exactly along the right line of what I was trying to do. Now I will know what to do for future classes. Many thanks for everyone else that posted up some help!

Now... I have a more complicated problem. I am attempting to use the .length string function in Java to extract the initials of a film. 

Check out my code and see if you can see where im going wrong. At the moment its placed in the wrong class but its only until I get something working.

---

### Post by VernonA on 2010-11-10
1) You set 'counter' to name.length() before you've read the name, so it will always contain 0. Move the line down so it is after the getString() call.

2) Your first while loop will then print all the chars in 'name' up to the end, but really you want it to stop when it reaches a space char. This code needs to be redesigned.

3) Your second loop starts with i still set to counter, so in other words it is starting at the end of the string. Thus it won't be entered, and in fact is likely to throw an exception.

4) What you really need to do is iterate over each char in the string, and detect when you move from whitespace chars to letters/digits. Here is an example:
```
boolean onSpaces = true;

for (int i=0; i < name.length(); i++)
{
    char c = name.charAt(i);

    if (onSpaces && Character.isLetter(c))
    {
         // Found start of a word. Do appropriate action...
         System.out.println("Found initial: "+ c);
    }

    onSpaces = Character.isWhitespace(c);
}
```
5) Of course, a simpler way to handle the whole problem is to use Java's String.split() function. Eg use:
```
String[] words = name.split(" ");
for (int i=0; i < words.length; i++)
    System.out.println("Got initial: "+ words[i].charAt(0) );

```Note that this simplistic code doesn't even start to address issues like skipping over "a" and "the" and handling numbers (eg Pelham 123 or Jaws II) and breaking up hyphenated words and so on. Good luck!

--Vernon

---

### Post by fallenshadow on 2010-11-11
Thanks VernonA! Much appreciated!! I was going about it the wrong way really, I should have been focusing on detecting white space instead of what I did.

Anyone know what is the best way of storing characters? I want to store the initials but im thinking an array is probably the best way to go.

If an array is the best way to do it, should I use a character array or a string array?

---

### Post by trent.josephsen on 2010-11-11
> **fallenshadow said:**
> Thats simply because the forums dont allow me to upload a .java file, so I uploaded a .txt instead. :)
Ah.  The CRLF line endings threw me off.  (When I am forced to change file extensions, I usually just add it on the end -- like Item.java.txt -- so the original identity is not lost.)

Seems like kind of a stupid rule when you think about it.  I mean, what's it supposed to prevent? :confused:

---

### Post by Some Penguin on 2010-11-11
Caveats that come to mind:

* Not all characters fit in a char.  getCodePoint() exists for a reason.  Whether or not this is an actual problem for you depends upon the input data.
* "Reno 911"
* "Blarg II:  Electric Boogaloo"
* "Great Blarg, the"

Depends on what your input data looks like, obviously.  User input may include a lot of misspellings and variations in capitalization and punctuation.  Keep this in mind if you're looking to build a similarity function or the like.

---

### Post by interval1066 on 2010-11-11
> **trent.josephsen said:**
> Ah.  The CRLF line endings threw me off.  (When I am forced to change file extensions, I usually just add it on the end -- like Item.java.txt -- so the original identity is not lost.)

Seems like kind of a stupid rule when you think about it.  I mean, what's it supposed to prevent? :confused:

Its not supposed to prevent anything, this comes from writing code on Windows that was designed on Unix. I'm not coming down on Windows, just sayin'. Here's another example; earlier today I posted an article about an encryption tool I packaged. I developed it over the course of a few weeks doing the work on both Windows and Linux consoles (depending on where I was at the time I was working on it.) One of the last things I did was write a shell integration script that is only meant to be run in a Linux bash shell, but I started the thing on my Windows box using Cygwin. One of the things it does is it checks to see if your running an X serv, and if not say so and exit gracefully, which worked great in the Cygwin environment. So I copied over to my Gnome desktop to further test it and the thing barfed immediately, it didn't even get to the X check (which it should have. Couldn't figure it out until I opened it up with vim and saw all the little ^M's everywhere. This took me a while because gedit doesn't expose those ^M's. I stripped out all those char 12's and my script started working. Always be aware of the possibilities.

---

### Post by fallenshadow on 2010-11-14
> Caveats that come to mind:

* Not all characters fit in a char. getCodePoint() exists for a reason. Whether or not this is an actual problem for you depends upon the input data.
* "Reno 911"
* "Blarg II: Electric Boogaloo"
* "Great Blarg, the"


I am not concerned about these mentioned caveats as this code will not be used in any commercial application. I will be testing with just normal characters.

However I do want to know should I use a character array or string array to store initials?

I want my end result to be something like this: 

INITIALS FILMNAME

I think the end result is going to be a string, so maybe I should use a string array for each character but I would like some advice on what to choose.

---

### Post by Reiger on 2010-11-14
You can convert a char array to String using: new String(array);

---

### Post by fallenshadow on 2010-11-16
Ok I got that character/initial thing sorted myself.

How do I call stuff from another class? 

I have tried this:

```
Film name1 = new Film(code);
      name1.getCode();
```

Doesn't seem to work though.... sorry for sucking real bad at java!

---

### Post by VernonA on 2010-11-16
I don't think you've quite got your head around object-oriented programming yet. I say this cos I see you write:
```
Film name = new Film()
```
when you really mean:
```
Film film = new Film()
```
The Film class defines a film object. It will have a name, initials, a run-length, a rating, a review and so on. These are attributes of a film, so I would expect to see properties (ie variables) with names like "parentalGuide" and "runLength" declared in the Film class. A 'name' is not a film.

Once you've decided what attributes a Film should have, the class should provide getters and setters for the values. For example, if the Film declares a String var called 'name', it should provide a function which returns that name. Then in other classes which use Films you can write thinks like:
```
Film myFavourite = new Film("Aliens");
System.out.println("My fav. film is: "+ myFavourite.getName() );

```I hope this helps you understand how you need to proceed.

--Vernon

---

### Post by fallenshadow on 2010-11-16
Believe it or not I do actually understand that. It was just named badly. :)

To make things easier lets call it:

```
Film myfilm = new Film(code);
      myfilm.getCode();
```

I have that above code in my Tester class.

Inside my Film class I do have code to return the string "code".

One question:

What goes in here: 

```
Film myfilm = new Film(**???**); 
```

At the moment I have it set to the variable I want (code). Is that correct?

Also whats the difference between:

```
String name;

//and

String name = new String();
```

---

### Post by VernonA on 2010-11-16
1) This is all elementary Java, so I'm not sure what you want me to say. The 'code' value you pass in the Film constructor is, I presume, the initials of the film. It's your code (no pun intended), so why would I be more likely to know what it is than you! If it _is_ the initials though, this doesn't feel right. I'd have thought the routine to extract the initials from the name should be in Film. The Film constructor should pass in the name of the film, then the 'code' value should be computed there. Then it would make sense to ask the Film for its code ready for filing it in a db, say. Eg:
```
Film    myFilm = new Film("Harry Potter and the...")
String  dbKey = myFilm.getCode();
    System.out.println("Adding film: "+ myFilm.getCode());
    myDB.addNewFilm( dbKey, myFilm );
```
This would print on the console:
```
Adding film: HPatOoTP
```

2) To answer your specific questions, a line like:
```
    myFilm.getCode();
```
appears to do nothing because all that function does is return a value, and this code simply ignores it! A line like "String val" declares a String variable called 'val'. In order to use it in any meaningful way, though, you need assign it a value. There are many ways to do this, but one is to create a brand-new, empty String using the 'new' operator (ie in a line like var = new String()). This is documented in any simple Java tutorial.

---

### Post by fallenshadow on 2010-11-17
The main problem I am having is that when I had all the code inside one class everything worked. Now after I split the code into two classes it does not work anymore.

For example before I would enter "the town" and my program would return "tt the town".

Now my program returns "nulltt the town".

How would I be getting a null at the start of my code?

---

### Post by VernonA on 2010-11-17
This seems easy enough. The function which is returning the code is not actually working and is instead sending back an uninitialised String var. Debug it by putting System.out.println calls throughout it, and you should soon see what is going wrong.

PS You need to repost your src code soon, as I'm sure its getting pretty different from what you first wrote.

---

### Post by fallenshadow on 2010-11-17
No the code to get the string variable is working but somehow a null slips in before it.

I will post my code so you might see something im doing wrong.

---

### Post by spjackson on 2010-11-17
> **fallenshadow said:**
> No the code to get the string variable is working but somehow a null slips in before it.

I will post my code so you might see something im doing wrong.
There are 2 obvious faults here.
1. In the Film constructor you initialise code by calling getCode. However, getCode uses code, so the first time this expression is evaluated, code is uninitialised.
```

code = code + chars[i];

```So that is where your null comes from. To correct this, in the constructor do
```

code = new String();
code = getCode();

```2. 
```

String [ ] chars = new String[7];
chars[i] = Character.toString(c);

```If name is more that 7 chars, you get out of bounds on the chars array. However, this array isn't doing anything useful. Remove it and just do
```

code = code + Character.toString(c);

```

---

### Post by VernonA on 2010-11-17
Please take advice. If you had put the println calls into getCode as I had mentioned, you would have found the bug. I even told you what the problem was (you are using a String that has not been initialised). The actual bug is the line code=code+char[i], where, on the first call, code is null. However, there are many other flaws in the code, so let's fix a few up:

1) The worst problem is definitely the global var called 'chars'. Please delete it, and then fix any code which uses it. A String is basically an array of chars, so saying chars is an array of Strings just confuses everyone (including you!). In fact you don't need the array at all, so just lose it. If you look at getCode you'll see that you copy 'c' to 'chars' then add 'chars' to 'code'. Why don't you just add 'c' to 'code' with a line like:
```
    code += c;
```

2) Java experts will be cringing at the above advice for a number of reasons. The main one is that Strings are basically immutable and it is just not right to treat them like arrays. Therefore, a better solution is to use a StringBuffer instead of a String. I will leave this to you to look up.

3) The third big problem is that you are using global variables where you should be using locals. As a good example, the function getCode() should be sent the film name as a parameter, and it should return the encoding as a String. It should not mention name or code inside itself. For example:
```
public String getCode( String filmName )
{
    StringBuffer initials = new StringBuffer(10);
    boolean      onSpaces = true;

    for (int i=0; i < filmName.length(); i++)
    {
        char c = filmName.charAt(i);

        if (onSpaces && Character.isLetter(c))
            initials.append( c );

        onSpaces = Character.isWhitespace(c);
    }
   
    return initials.toString();
}

```
This advice applies elsewhere in the code too.

---

### Post by Reiger on 2010-11-17
With regards to (2) if your StringBuffer is used inside a single thread only, use StringBuilder. It is significantly faster.

---

### Post by fallenshadow on 2010-11-17
Ok got my code all cleaned up and fixed! :) Awesome!

> Please take advice. If you had put the println calls into getCode as I had mentioned, you would have found the bug. I even told you what the problem was (you are using a String that has not been initialised).

I did understand what you said but I didn't know how to fix it because as far as I understood my string variable "code" was declared here:

```

//At the top of my film class
private String code;
```

So you told me it was not initialized but I thought it was. :(

> 1) A String is basically an array of chars, so saying chars is an array of Strings just confuses everyone (including you!). 

I loled! :lolflag:  Yes, very true!!

> 2) Therefore, a better solution is to use a StringBuffer instead of a String. I will leave this to you to look up.

Wow a string that can be added to, now thats pretty neat! Thanks! 

> 3) The third big problem is that you are using global variables where you should be using locals. 

Can you explain why this is important? I used to always think global variables were better because it avoids duplication of variables (redundant code).

Lastly,

> With regards to (2) if your StringBuffer is used inside a single thread only, use StringBuilder. It is significantly faster.

I can't understand this... im not very experienced with Java yet.  :oops:

---

### Post by Some Penguin on 2010-11-17
Declarations are not initializations.

Global variables are a great way to throw away the ability to debug and to prevent you from properly isolating problems.

---

### Post by Reiger on 2010-11-17
> **fallenshadow said:**
> I can't understand this... im not very experienced with Java yet.

It means you should not use StringBuffer unless you *know* you need it. You should use StringBuilder instead which is considerably faster.

You know you need it when you are doing something involving multiple threads accessing the *same* data (not copies of it, the exact same bits in memory).

---

### Post by fallenshadow on 2010-11-18
Ok thanks for clarifying those things I asked! :)

Feeling kinda ok working with separate classes now, I should be able to learn Java better from now on.

---

