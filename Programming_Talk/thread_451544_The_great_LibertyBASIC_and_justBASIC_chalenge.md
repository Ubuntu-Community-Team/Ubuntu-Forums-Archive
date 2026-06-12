---
title: "The great LibertyBASIC and justBASIC chalenge"
date: 2007-05-22
forum: Programming Talk
---

### Post by themoomin on 2007-05-22
Hello ubuntu users,
I have a linux pc and three windows computers and i have made a app for calculating the VAT on any item bought in the uk. Now this could be quite a important app for a business. it is called VATCALCBASIC

I am going to post the source here, i would like somebody to translate it so it works on windows and linux. To test it in a windows enviroment, run JustBASIC (its free) in WINE.

[start]
         print "Type a pound and pence amount."
         input "(Press 'Enter' alone for help) ?"; amount
         if amount = 0 then goto [help]
         let tax = amount * 0.17
         print "Tax is: "; tax; ". Total is: "; tax + amount
         goto [start]

[help]
         print "This tax program determines how much vat is"
         print "due on an amount entered and also computes"
         print "the total amount. The tax rate is 17%"
         goto [start]

Feel free to expand or toy around with. It is the first app i have ever made so dont laugh. Please

Oh and check out my podcast at creativecast.blogspot.com
And my wiki at matthewhughes.wikispaces.com

All the best

Matthew Hughes

---

### Post by WW on 2007-05-22
> **themoomin said:**
> 
I am going to post the source here, i would like somebody to translate it so it works on windows and linux. 

This is probably not quite what you want... I translated it to Python, which works on windows and linux (and macs and more):

**vatcalc.py**
```

# vatcalc.py

while True:
    print "Type a pound and pence amount."
    answer = raw_input("(Press 'Enter' alone for help) ? ")
    if answer == "":
        print "This tax program determines how much vat is"
        print "due on an amount entered and also computes"
        print "the total amount. The tax rate is 17%"
    else:
        amount = float(answer)
        tax = amount*0.17
        print "Tax is: ", tax, "    Total is: ", tax+amount

```
Run it with the command
```

python vatcalc.py

```
It will crash if you enter anything that is not a valid number.  Here is a more fault-tolerant version:

**vatcalc2.py**
```

# vatcalc2.py

while True:
    print "Type a pound and pence amount."
    try:
        amount = float(raw_input("(Press 'Enter' alone for help) ? "))
        tax = amount*0.17
        print "Tax is: %.2f.  Total is %.2f" %  (tax,tax+amount)
    except ValueError:
        print "This tax program determines how much vat is"
        print "due on an amount entered and also computes"
        print "the total amount. The tax rate is 17%"
    except EOFError:
        print
        break

```
Any invalid numbers result in the 'help' message being printed.  Enter ctrl-D to quit.  I also changed the print statement to format the numbers.

Both of these example [avoid using a goto statement]("http://www.acm.org/classics/oct95/").

---

### Post by themoomin on 2007-05-22
WW i think i love you.

:)

What did you think of the dialect of basic i used. LibertyBASIC.

I am getting quite nostalgic for the strands such as

10
20

Oh and i programmed a semi virus. The way JustBASIC works is that you can only end a program when it is not running any tasks.

So for example, if you wanted to annoy somebody

[start]
       Print "hello world"
       goto [start]

---

### Post by WW on 2007-05-22
> **themoomin said:**
> 
What did you think of the dialect of basic i used. LibertyBASIC.

I haven't used it. I haven't used any Basic for many years.  These days I would recommend Python over Basic.

---

### Post by themoomin on 2007-05-22
Yeah. But i rather like the line by line interface of basic. It does what you intend it to do. For example, solving a mathematical formula.

Good enough for me.

---

### Post by xtacocorex on 2007-05-22
> **themoomin said:**
> Yeah. But i rather like the line by line interface of basic. It does what you intend it to do. For example, solving a mathematical formula.

Good enough for me.
FORTRAN does line by line a whole lot better than BASIC and was made for math.  I think if you're going to stick with mainly procedural programming, move to FORTRAN or C++ (which isn't just all OOP) But if you're just going to use BASIC because it's BASIC, I'd say you're probably better off with Python.

Here is your code in FORTRAN and without error checking
```

PROGRAM VATCALC
     ! VARIABLE DECLARATIONS
     REAL :: TAX, AMOUNT

     ! GET USER INPUT
     WRITE(*,*) "ENTER AMOUNT OF ITEM: "
     READ(*,*) AMOUNT

     ! CALCULATE TAX AND OUTPUT TO USER
     TAX = 0.17*AMOUNT
     WRITE(*,*) "AMOUNT AFTER TAX IS: ", TAX

     ! END PROGRAM
     STOP
END PROGRAM VATCALC

```

---

### Post by samjh on 2007-05-22
> **themoomin said:**
> Hello ubuntu users,
I have a linux pc and three windows computers and i have made a app for calculating the VAT on any item bought in the uk. Now this could be quite a important app for a business. it is called VATCALCBASIC

I am going to post the source here, i would like somebody to translate it so it works on windows and linux. To test it in a windows enviroment, run JustBASIC (its free) in WINE.

Matthew,

I recommend you try FreeBasic ([link](http://www.freebasic.net/)).  It's the most powerful multi-platform open-source BASIC compiler I've ever seen.  Your code should be compilable in Linux and Windows with little if any changes.  But it is as I said, a compiler, not an interpreted form of BASIC.

Here is a **structured** FreeBasic code for your program.  Notice the emphasis on structured programming, with sub-routines and explicit variable declarations, full-formed selection blocks, etc.  This makes the code look longer, but it helps immensely when you write complex programs.  Try to use structured programming concepts.  The lines beginning with a single quote (ie. ' blah blah) are comments.  You can also use the REM keyword for comments.

```
' These lines declare sub-routines so they can be accessed.
Declare Sub Help
Declare Sub Main

' Runs the Main sub-routine.
Main

' Code for Main sub-routine
Sub Main
	' Create 32-bit (ie. single) floating-point variables amount and tax.
	Dim amount As Single, tax As Single
	
	' Note after the Input command, the semi-colon automatically
	' places a question mark at the end of the prompt.
	Print "Type a pound and pence amount."
	Input "(Press 'Enter' alone for help)"; amount
	
	' If nothing was entered for amount, run the Help sub-routine.
	If amount = 0 Then
		Help
	End If
	
	tax = amount * 0.17
	print "Tax is: "; tax; ". Total is: "; tax + amount
	
	' Run the Main sub-routine.  This is forms an infinite recursive loop,
	' until the program is forcibly ended.
	Main
End Sub


' Code for Help sub-routine.
Sub Help
	print "This tax program determines how much vat is"
	print "due on an amount entered and also computes"
	print "the total amount. The tax rate is 17%"
End Sub
```

---

### Post by themoomin on 2007-05-31
I tried freebasic but the lack of a gui was just too jarring. I hated the interface.

Thanks for the code. You guys are fantastic. Are there any good python and fortran guides out there? Either in PDF format or on book format. I would prefer a windows oriented book rather than a linux oriented book but either is fine.

---

### Post by themoomin on 2007-05-31
> **samjh said:**
> Matthew,

I recommend you try FreeBasic ([link](http://www.freebasic.net/)).  It's the most powerful multi-platform open-source BASIC compiler I've ever seen.  Your code should be compilable in Linux and Windows with little if any changes.  But it is as I said, a compiler, not an interpreted form of BASIC.

Here is a **structured** FreeBasic code for your program.  Notice the emphasis on structured programming, with sub-routines and explicit variable declarations, full-formed selection blocks, etc.  This makes the code look longer, but it helps immensely when you write complex programs.  Try to use structured programming concepts.  The lines beginning with a single quote (ie. ' blah blah) are comments.  You can also use the REM keyword for comments.

```
' These lines declare sub-routines so they can be accessed.
Declare Sub Help
Declare Sub Main

' Runs the Main sub-routine.
Main

' Code for Main sub-routine
Sub Main
	' Create 32-bit (ie. single) floating-point variables amount and tax.
	Dim amount As Single, tax As Single
	
	' Note after the Input command, the semi-colon automatically
	' places a question mark at the end of the prompt.
	Print "Type a pound and pence amount."
	Input "(Press 'Enter' alone for help)"; amount
	
	' If nothing was entered for amount, run the Help sub-routine.
	If amount = 0 Then
		Help
	End If
	
	tax = amount * 0.17
	print "Tax is: "; tax; ". Total is: "; tax + amount
	
	' Run the Main sub-routine.  This is forms an infinite recursive loop,
	' until the program is forcibly ended.
	Main
End Sub


' Code for Help sub-routine.
Sub Help
	print "This tax program determines how much vat is"
	print "due on an amount entered and also computes"
	print "the total amount. The tax rate is 17%"
End Sub
```


I thought my code was structured

i had

[start]
[help]

What is the difference between unstructured and structured code. Sorry, total n00b.

---

### Post by samjh on 2007-05-31
> **themoomin said:**
> I thought my code was structured

i had

[start]
[help]

What is the difference between unstructured and structured code. Sorry, total n00b.

Your code was half-way there already. :)   My code is better described as "procedural", which is an evolution of structured programming concepts.

The topic is a broad and technical one.  So I will refer to links instead of reinventing the wheel.

Basic overview: [http://en.wikibooks.org/wiki/Computer_programming/Structured_programming](http://en.wikibooks.org/wiki/Computer_programming/Structured_programming)

A more complex description: [http://en.wikipedia.org/wiki/Structured_programming](http://en.wikipedia.org/wiki/Structured_programming)

Procedural programming: [http://en.wikipedia.org/wiki/Procedural_programming](http://en.wikipedia.org/wiki/Procedural_programming)

---

### Post by xtacocorex on 2007-05-31
> **themoomin said:**
>  Are there any good python and fortran guides out there? Either in PDF format or on book format. I would prefer a windows oriented book rather than a linux oriented book but either is fine.
All the Python stuff I've done I've Googled.

As for FORTRAN, I was taught it in college 6 years ago and the books you can buy for it are operating system independent.  FORTRAN is what it is and it's hard (probably impossible) to do GUI and it's built for math.  I only threw my code into this foray just to let other users know what it looks like since most people haven't seen it.  As an up and coming programmer, don't discredit it, but know that it's there.  Once you learn programming logic, syntax is easy to come by.

---

### Post by themoomin on 2007-06-01
Thanks. I will look into it. 

One last question ( i think)

Has there been a version of autoit released for ubuntu/puppy linux? It is a great language used for automating actions. Many cheating programmes for online games are written with that language.

---

### Post by christhemonkey on 2007-06-01
You can do GUI programming with Fortran.

Though i have no idea how, my dads a fortran programmer. Ask him!

---

### Post by xtacocorex on 2007-06-01
> **themoomin said:**
> Has there been a version of autoit released for ubuntu/puppy linux?
There may be, but programs like that are not to be discussed because of the legal implications of them.  I think one of the forum rules talks about using stuff for bad things, which you may or may not be doing, but it's just best to stay away from stuff like that.
> **christhemonkey said:**
> You can do GUI programming with Fortran.

Though i have no idea how, my dads a fortran programmer. Ask him!I knew you can in Windows with Compaq Visual FORTRAN, but I never really searched Google for "fortran gui" and it turns out that there are libraries (one you have to pay for).  This is exciting news.

---

### Post by pmasiar on 2007-06-01
> **themoomin said:**
> Are there any good python and fortran guides out there? Either in PDF format or on book format. I would prefer a windows oriented book rather than a linux oriented book but either is fine.

Plenty free books about Python. See sticky to this forun and wiki in my sig

---

### Post by Samjiman on 2007-06-01
Problem with BASIC is it often includes the "goto" command which means you can end up with spaghetti code. Of course, like any language you should use constructs wisely. I have a copy of LibertyBASIC too, its not a bad language, but is not as robust as Microsoft's VB.NET.  The author intended it to stick more to its BASIC origins though than most other BASIC dialects and you can see that it does more so than Visual Basic.

Good program, Matt. But as far as I know the tax rate in the UK is 17.5%.

---

### Post by derjames on 2007-06-01
> **WW said:**
> I haven't used it. I haven't used any Basic for many years.  These days I would recommend Python over Basic.

or even Ruby...

---

### Post by themoomin on 2007-06-16
Auto it is totally legal. It can be used for anything. It is simply a programming language that tells a computer to open certain files and do something with them. Its just what you do with it that can be conceived to be illegal.

Oh and just to update you guys, my code got flamed on the reactOS forums. :(

Ah well. They can bite me.

---

### Post by samjh on 2007-06-16
Flamed?  lol, some people take this sort of thing too seriously.  They're probably jealous. ;)

---

### Post by themoomin on 2007-06-18
samjh, you are such a sweetie! :D

Yeah, what do you guys think of react os. Its supposed to be an alternative to windows and windows NT, but it is filled with bugs, still in alpha and can barely do anything useful. 

And thanks for the tips guys. I am going to start learning python on friday after my exam.

---

