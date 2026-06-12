---
title: "Reverse Engineering Java Stuff?"
date: 2010-04-13
forum: Programming Talk
---

### Post by fallenshadow on 2010-04-13
Ok I have a game for my phone, apparently its been tranlated into english but its not all been translated and even the english parts are spelled wrong.  :lolflag:

The game is Freeware so getting at the source is out of the question. However as a personal project I want to improve this game.

Is there a way to reverse engineer the files so I can pursue a better english translation for me and others?

---

### Post by phrostbyte on 2010-04-13
A Java decompiler is what you are looking for. Eg: [http://java.decompiler.free.fr/](http://java.decompiler.free.fr/)

I'm not going to go into the legal issues of treating closed source like it is FOSS. You can do your own research on that. :)

---

### Post by fallenshadow on 2010-04-13
Wow thanks! That is a really nice bit of software. Okay I got the code decompiled.  :)

Next question is how do I compile Java code? :lolflag:


EDIT: Ok I think I need Netbeans for a start... correct?  If so then which version do I download? "Java" I think but I want confirmation before I waste my bandwidth.

---

### Post by PaulM1985 on 2010-04-13
Are you using Ubuntu?  Netbeans can be added easily using Applications->Ubuntu Software Centre and then searching for Netbeans.

You don't need Netbeans to compile Java code, but it works well as an IDE.

Paul

---

### Post by fallenshadow on 2010-04-14
Ok thanks Paul... Im already comfortable with Geany so I will probably use that as my IDE. 

Is there some line I can use in the terminal then?

Note that I already have sun-java6-jdk installed. :)

---

### Post by PaulM1985 on 2010-04-14
To compile Java at command line you can use javac.

So:

javac myClass.java

should create a myClass.class file in the same folder if compiling was successful.

Paul

---

### Post by fallenshadow on 2010-04-14
Hmm out of 25 files I tried to compile only 3 were successful.

However I am hoping to just compile one file and replace the existing .class to see does it make a difference. 

Or would I have to compile the whole lot again?

Anyway I have 100 errors in this file I have changed... I hope someone can shed some light on what they mean.

I think the first 3 show why im getting so much errors:

> 
r.java:2: package javax.microedition.lcdui does not exist
import javax.microedition.lcdui.Font;
                               ^
r.java:3: package javax.microedition.lcdui does not exist
import javax.microedition.lcdui.Graphics;
                               ^
r.java:4: package javax.microedition.lcdui does not exist
import javax.microedition.lcdui.Image;



I believe javax.microedition is a Java package I don't have. 
Let me know if im right plz.

---

### Post by kaivalagi on 2010-04-14
Compiling for a phone is potentially vastly different to your PC...the JVM might be different, the libraries might be different.....just different

You need to do more research, maybe trying to write and compile a simple app for your phone separately first to understand what is needed

---

### Post by PaulM1985 on 2010-04-14
> I believe javax.microedition is a Java package I don't have.

This is probably the case.  This package is in Java ME (Java Platform, Micro Edition).  I'm guessing that you have the standard java development kit installed, but nothing for phone apps.  Have a look into Java ME.  You will need to install this to compile and run apps for you phone.  I don't really know how it works, but this is the direction I think you should be looking.

[http://java.sun.com/javame/index.jsp](http://java.sun.com/javame/index.jsp)

Paul

---

### Post by fallenshadow on 2010-04-14
Thanks Paul... its all a bit more clear now. So I believe I need to get JavaME 2 or 3. Im not sure which one yet.

However there is no Linux version. sigh... :(

---

### Post by PaulM1985 on 2010-04-14
This tutorial looks like you may not need to whole of the Java ME SDK and just some of it, which is available for Linux:

[http://www.linux.com/archive/feature/122050](http://www.linux.com/archive/feature/122050)

Paul

---

### Post by fallenshadow on 2010-04-14
Wow I was surprised to be able to get the development software for mobile games on Linux. Good job Sun! ;)

Anyway I setup the wirelesstoolkit (mobile phone development stuff) and I setup a new project with the settings as similar to the original game.

I compiled the code and got a whopping 100 errors so Im sure now its because the game was developed with JDK 1.5 and im using 1.8.

There is nothing I can do about the JDK version as its the one in the repo. Looks like im gonna have to fight through these errors one by one then! 

Onwards to victory! For the WIN!! :lolflag:

--
I shall return if the errors defeat me and get some advice from here.

---

### Post by fallenshadow on 2010-04-14
Okay I got frustrated trying to fix the 100 errors so I decided to just do the Tutorial you gave me.

I did it and when I tried running Helloworld I got the same message as when I try to run the sourcecode of the game im working on.

> 
Unable to create MIDlet Helloworld
java.lang.ClassNotFoundException: Helloworld
	at com.sun.midp.midlet.MIDletState.createMIDlet(+29)
	at com.sun.midp.midlet.Selector.run(+22)


Anyone with Java knowledge out there? :)

---

### Post by PaulM1985 on 2010-04-15
Is this on compiling or execution?

Paul

---

### Post by Some Penguin on 2010-04-15
Java is case-sensitive.

---

### Post by fallenshadow on 2010-04-15
Thanks for that tip some penguin!

The Helloworld app can now compile because I renamed the file helloworld.java. to HelloWorld.java.

Its when I try and run it I still get this message:

> 
java.lang.ClassNotFoundException: Helloworld
	at com.sun.midp.midlet.MIDletState.createMIDlet(+29)
	at com.sun.midp.midlet.Selector.run(+22)


EDIT: OMG! I fixed it. It had to do with the project settings still saying Helloworld... now changed to HelloWorld. Now back to work with the game since I learned something new. :)

---

### Post by fallenshadow on 2010-04-15
Right so with the game:

--
1. I can't build it... because 100 errors show up.

2. I can't run it because the same message about class not found shows up.
--

Right if I can't build it then obviously I won't be able to run it. So Im gonna start working through some of these errors and hope none of em are hard to fix.

This line is causing alot of errors so im hoping to fix it.
Here is the error: i.java:26: = expected

Warning looking at this code may make some people feel sick! It did for me!! :)

LINE 26 of i.java:
```

    new int[] { 16711680, 13369395, 13369446, 10027110, 10027161, 6684825, 3342540, 3342591, 255, 13311, 13260, 26265, 26214, 39270 }[14] = 39219;

```

Obviously an = is expected somewhere but where could it be needed?

---

### Post by PaulM1985 on 2010-04-15
Can you post a few lines either side of the line?  It would make it a bit easier to see it in context.  Can't tell if the new int[] is some sort of assignment to a type or creating a new unreferenced object.

Paul

---

### Post by fallenshadow on 2010-04-15
Ok, I thought it would be better to give you this chunk.

They are all above like this:
```

public static final int[][][] I;
  public static final short[][][] J;
  public static final byte[][] K;
  public static final byte[] L;
  public static final short[][] M;
  public static final byte[][] N;
  public static final int[][] O;

```

and here is the rest below which includes line 26. LINE 26 is the first one. (new int[])

```

static
  {
    new int[] { 16711680, 13369395, 13369446, 10027110, 10027161, 6684825, 3342540, 3342591, 255, 13311, 13260, 26265, 26214, 39270 }[14] = 39219;
    I = new int[][][] { { { 1, 1, 10460572 }, { 0, 0, 2236962 } }, { { 1, 1, 10460572 }, { 0, 0, 2236962 } }, { { 1, 1, 9571328 }, { 0, 0, 5244416 } }, { { 1, 1, 13421772 }, { 0, 0, 6710886 } }, { { 1, 1, 16745728 }, { 0, 0, 10373376 } } };
    J = new short[][][] { { { 1, 18, 1 }, { 32, 26, 58 } }, { { 0, 20, 38 }, { 2, 12, 58 }, { 3, 15, 1 } }, { { 1, 35, 19 } }, { { 1, 19, 38 }, { 4, 18, 1 }, { 29, 7, 24 } }, { { 3, 19, 58 } }, { { 30, 58, 43 }, { 7, 32, 58 }, { 6, 30, 38 } }, { { 5, 52, 30 } }, { { 5, 31, 5 }, { 31, 31, 58 }, { 9, 9, 4 } }, { { 31, 27, 1 } }, { { 7, 54, 3 }, { 10, 1, 50 } }, { { 9, 58, 49 }, { 11, 19, 38 }, { 15, 35, 58 } }, { { 10, 48, 18 }, { 12, 15, 4 } }, { { 11, 19, 8 }, { 13, 15, 3 } }, { { 12, 50, 9 }, { 14, 53, 31 } }, { { 13, 53, 54 } }, { { 10, 35, 1 }, { 16, 52, 51 }, { 17, 19, 38 } }, { { 15, 7, 29 } }, { { 15, 36, 5 }, { 18, 31, 54 } }, { { 17, 19, 1 }, { 19, 28, 62 } }, { { 18, 31, 1 }, { 20, 5, 4 } }, { { 19, 56, 8 }, { 21, 8, 4 } }, { { 20, 56, 7 }, { 22, 8, 4 } }, { { 21, 57, 53 }, { 23, 22, 1 } }, { { 22, 8, 32 }, { 24, 37, 6 }, { 25, 5, 4 } }, { { 23, 3, 12 } }, { { 23, 42, 12 }, { 26, 58, 4 } }, { { 25, 6, 49 }, { 27, 7, 46 } }, { { 26, 57, 53 }, { 28, 19, 38 } }, { { 27, 11, 28 } }, { { 3, 58, 32 }, { 30, 25, 1 } }, { { 29, 25, 58 }, { 5, 1, 45 } }, { { 7, 9, 45 }, { 8, 19, 48 } }, { { 0, 18, 5 }, { 33, 36, 40 } }, { { 32, 31, 9 }, { 34, 60, 4 } }, { { 33, 30, 2 }, { 35, 58, 52 } }, { { 34, 53, 43 }, { 36, 58, 9 } }, { { 35, 58, 9 } } };
    K = new byte[][] { { 36, 34 }, new byte[2], new byte[2], { 35, 19 }, new byte[2], { 10, 20 }, new byte[2], new byte[2], new byte[2], new byte[2], { 23, 23 }, new byte[2], new byte[2], new byte[2], new byte[2], { 39, 22 }, new byte[2], new byte[2], new byte[2], new byte[2], { 28, 39 }, new byte[2], new byte[2], { 23, 21 }, new byte[2], new byte[2], new byte[2], new byte[2], new byte[2], new byte[2], new byte[2], new byte[2], new byte[2], new byte[2], new byte[2], new byte[2], new byte[2] };
    L = new byte[] { 0, 0, 1, 0, 0, 0, 0, 1, 1, 0, 0, 2, 2, 2, 2, 0, 1, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 0, 0, 1, 1, 1, 2, 2, 2 };
    M = new short[][] { { 110, 4, 340, 11, 9, 5 }, { 150, 4, 330, 20, 32, 15 }, { 200, 13, 330, 29, 71, 25 }, { 300, 14, 340, 40, 115, 40 }, { 400, 23, 350, 49, 159, 50, 1 }, { 650, 18, 340, 57, 205, 60, 4, 5 }, { 800, 44, 340, 66, 245, 70, 2, 6 }, { 900, 35, 340, 75, 293, 80, 3, 5 }, { 1000, 55, 360, 84, 342, 90, 1 }, { 1200, 41, 350, 93, 391, 100, 4, 5 }, { 1400, 95, 350, 101, 441, 110, 2, 6 }, { 1600, 69, 350, 110, 481, 120, 3, 5 }, { 1700, 110, 360, 119, 532, 130, 1 }, { 2000, 75, 360, 128, 583, 140, 4, 5 }, { 2300, 165, 360, 137, 638, 150, 2, 6 }, { 2700, 120, 360, 147, 695, 165, 3, 5 }, { 3000, 210, 360, 155, 747, 175, 1 }, { 3500, 132, 360, 164, 786, 185, 4, 5 }, { 3700, 260, 360, 173, 847, 195, 2, 6 }, { 4000, 180, 360, 184, 899, 210, 3, 5 }, { 1000, 60, 340, 70, 500, 100, 6, 3 }, { 4000, 120, 350, 130, 880, 200, 6, 2 }, { 8000, 240, 360, 150, 1440, 400, 6, 5 }, { 20000, 480, 400, 200, 1700, 800, 6, 2 } };
    N = new byte[][] { new byte[5], { 0, 0, 1 }, { 3, 2, 1 }, { 3, 2 }, { 3, 2, 0, 4 }, { 0, 0, 5, 4 }, { 7, 6, 5 }, { 0, 6, 5 }, { 7, 6, 0, 0, 21 }, { 7, 0, 0, 8 }, { 7, 0, 0, 8 }, { 0, 0, 9, 8 }, { 0, 10, 9 }, { 11, 10, 9 }, { 11, 10, 0, 0, 22 }, { 11, 0, 0, 12 }, { 11, 10, 0, 12 }, { 0, 0, 13, 12 }, { 0, 14, 13 }, { 15, 14, 13 }, { 15, 14 }, { 15, 14 }, { 15, 0, 0, 16 }, { 15, 0, 0, 16 }, { 0, 0, 0, 0, 23 }, { 0, 18, 17 }, { 19, 18 }, { 19, 0, 0, 20 }, { 19, 0, 0, 0, 24 }, { 3, 0, 0, 4 }, { 0, 0, 5, 4 }, { 7, 6 }, { 11, 10, 9 }, { 15, 14, 0, 16 }, { 19, 18, 17 }, { 19, 18, 0, 20 }, { 19, 18, 0, 0, 21 } };
    { { 915, 3 }, { 939, 5 }, { 959, 10 }, { 975, 15 }, { 987, 18 }, { 995, 20 } }[6] = { 999, 40 };
    O = new int[][] { { 0, -1 }, { 0, 1 }, { -1 }, { 1 } };
  }

```

If I get in trouble for this I will take ALL the blame so feel free to help me anyone! :)

---

### Post by PaulM1985 on 2010-04-15
So I guess the questions are:
1) Removed
2) Is this really something that you should be doing? I have gone along with this as innocent general help and 
> If I get in trouble for this I will take ALL the blame so feel free to help me anyone! 
is amazing how much just one sentence can put someone off helping.

---

### Post by fallenshadow on 2010-04-16
>>is amazing how much just one sentence can put someone off helping.

It was a joke... geez! :lolflag:

I can't really get in trouble as its for a game from a company who is now liquidated. Also all im doing is translating not stealing code to make my own game or anything like that.

Im sorry if my small bit of humor put you off... (my quirky sense of humor gets me in trouble again :( )

---

### Post by fallenshadow on 2010-04-16
Eh... seems nobody knows enough Java to help me.

I might post up on a Java forum and get advice. Thanks to all that helped! At least I got a HelloWorld app going! :P

Dear Paul, im not sure what caused you to become negative towards the topic. You were just giving me "innocent general help" (apparently) but I can't understand how you could miss out on reading the title of this thread. Which clearly states something not innocent or general! :-?

---

### Post by kaivalagi on 2010-04-16
> **fallenshadow said:**
> Eh... seems nobody knows enough Java to help me.

I might post up on a Java forum and get advice. Thanks to all that helped! At least I got a HelloWorld app going! :P

Dear Paul, im not sure what caused you to become negative towards the topic. You were just giving me "innocent general help" (apparently) but I can't understand how you could miss out on reading the title of this thread. Which clearly states something not innocent or general! :-?

eh.....seems like YOU need to learn more about Java and the libraries you need.

I earn good money writing Java and C# apps but I won't sit here spending all my spare time helping you do something trival that requires you to learn something about it all first, sorry.

Best of luck on the java forums...tbh you'll get the same response as soon as people figure out that you are new to it all.

No-one will do all the work for you [-(

---

### Post by fallenshadow on 2010-04-17
Well I guess when I first started out I thought that it would be quite easy. Looks like its never that easy eh!

I did think it would turn out like this:

1. De-compile Java code.
2. Do all the translating via Google translate.
3. Re-compile code and create Jar file.
4. Put Jad and Jar files on phone.
5. Play my translated version of the game! :)

Unfortunately I will most likely give up on this as I haven't got any help from people in a Java forum. Im not going to learn a full programming language to try and do this.

Im pretty sure even if I knew alot of Java I still wouldn't be able to make sense of this convoluted spaghetti code. (endless random numbers and stuff)

---

### Post by kaivalagi on 2010-04-18
> **fallenshadow said:**
> Well I guess when I first started out I thought that it would be quite easy. Looks like its never that easy eh!

I did think it would turn out like this:

1. De-compile Java code.
2. Do all the translating via Google translate.
3. Re-compile code and create Jar file.
4. Put Jad and Jar files on phone.
5. Play my translated version of the game! :)

Unfortunately I will most likely give up on this as I haven't got any help from people in a Java forum. Im not going to learn a full programming language to try and do this.

Im pretty sure even if I knew alot of Java I still wouldn't be able to make sense of this convoluted spaghetti code. (endless random numbers and stuff)

A lot also depends on the quality of the dis-assembler I would imagine...I expect some do a better job than others...

A good analogy for this stuff would be taking a wind-up watch apart and expecting to be able to put it back together, ideally you need to know how to build watches to be successful but may just scrape by if not an expert...but the watch wouldn't work as well as if an expert did it...

---

