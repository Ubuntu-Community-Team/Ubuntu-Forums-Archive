---
title: "How am I doing so far?"
date: 2008-11-24
forum: Programming Talk
---

### Post by semitone36 on 2008-11-24
Hey all

I am 3 weeks away from completing my first semester as a CS major and I wanted to see what some of you might think of my work.  As sort of a side project I have been writing a basic math tutoring program using everything that I learned as I went along and it is pretty much finished short of having a decent GUI but I dont think that my class will be getting to that this semester.

Anyways let me know what you think as far as my programming and documentation style, creativity, and also any other areas you think I could work on.  Thanks in advance!

---

### Post by slavik on 2008-11-24
at a quick glance, too many comments ... in main, where you are reading the selection, use switch instead of cascading if-else
the idea for using sane variable names is that you don't have to write a comment describing them.
other than that, I think it's decent code and pretty good for a 1st year comp sci student. (you aren't expected to know much at this point).

if you want a more interesting challenge, write something like an ATM program that asks for a user's account number and then allows him to withdraw/deposit. maybe even store it in a text file or some such so that you can keep information between runs of the program.

---

### Post by jimi_hendrix on 2008-11-24
> **slavik said:**
> at a quick glance, too many comments

how is that bad

---

### Post by Sorivenul on 2008-11-24
I would agree with slavik on the "too many comments", in general.  The verbosity of the comments regarding the methods gives me a headache.  

Outside of that, not bad.  Java, IMO, is an eyesore, and that takes away my joy in working with it.  However, if you are enthusiastic about this project, more power to you.  Congratulations, and keep up the study!

---

### Post by Geekkit on 2008-11-24
> **jimi_hendrix said:**
> how is that bad

Quality over quantity would be my response.

---

### Post by tiachopvutru on 2008-11-25
> **jimi_hendrix said:**
> how is that bad

Too many comments can be hard to read. Plus, I believe "too many comments" here also mean that certain comments are not relevant, which really diverts the reader's attention away from the more important comments.

---

### Post by Geekkit on 2008-11-25
To OP, some feedback:

First, off, I think you are quite brave to throw yourself out like that - not sure I would be brave enough to put my head on the chopping block as it were. :)

Here's my feedback:
1) For Java programming, get yourself acquainted with the following online document from Sun:

[http://java.sun.com/docs/codeconv/html/CodeConvTOC.doc.html](http://java.sun.com/docs/codeconv/html/CodeConvTOC.doc.html)

It will help you with and all the rest of the subtleties and nuances that make up the Java 'style'.

2) From a UI standpoint, another document that will help you out greatly is:

[http://java.sun.com/products/jlf/](http://java.sun.com/products/jlf/)

This is specific to Java's Swing although many of the underlying principles and heuristics within this book are also found in Apple's design guidelines, and, yes, even Microsoft's design guidelines document (both easily found via Google).

3) Nice idea, there's an exciting market out there for computer based training programs (AKA CBTs), and you've just skimmed the surface. :)

If this type of programming/design/development excites you, the following topics may also be of interest: CBT, XML, data modeling, ontology, content management system (AKA CMS), illocutionary forces, user interface (AKA UI) heuristics, and human computer interface (HCI).

Type those words/phrases into Google and explore ... you'll quickly find yourself immersed. :)

---

### Post by Greyed on 2008-11-25
Too many comments also becomes a problem to maintainability because if in the future the code changes and the comments do not then having those comments there are worse than having no comments as all as they are misleading.

---

### Post by shadylookin on 2008-11-25
I would say that's alright for a first semester student. 

I'm slightly surprised however there's only one class and all your methods are static. I would have thought you should at least touch on object orientation in the first semester. If you haven't learned about it you should consider doing so since it's really the essence of java. 

Some other things to note is that your formatting makes it hard to read maybe that's a fluke of converting it to a txt file though. Some professors require you comment all your variables, but if they don't I think you're better off just using obvious variable names instead of commenting all of them.

---

### Post by semitone36 on 2008-11-25
> **slavik said:**
> at a quick glance, too many comments ... 
Haha I figured somebody would say something like that.  My prof is pretty uptight about commenting because he is convinced that documentation is the most underdeveloped skill among programmers.  But Im glad to hear that Im not the only one who thinks this is a little much.
[QUOTE=slavik]use switch instead[/QUOTE]
I didnt think of that... We spent about one day on switch and we use if-else for everything but I will definately try that out.
[QUOTE=geekkit]First, off, I think you are quite brave to throw yourself out like that - not sure I would be brave enough to put my head on the chopping block as it were.
[/QUOTE]
Haha thanks! I figure I have the internet between all of you and me so whats the worst that could happen lol.  But thanks for the suggestions Ill have to look into them.
[QUOTE=shadylookin]I'm slightly surprised however there's only one class and all your methods are static. I would have thought you should at least touch on object orientation in the first semester. If you haven't learned about it you should consider doing so since it's really the essence of java.[/QUOTE]
Yeah we might just barely touch on designing classes by the end but we havent learned about anything other than static methods yet unfortunately.  atm we are studying writing/reading to other files so we really arent that advanced.

But anyways I really appreciate the steady feedback! Ill keep workin on this as I go

---

### Post by Geekkit on 2008-11-25
> **shadylookin said:**
> I'm slightly surprised however there's only one class and all your methods are static. I would have thought you should at least touch on object orientation in the first semester. If you haven't learned about it you should consider doing so since it's really the essence of java.

Give the dude a break ... he's doing CS ... they don't even consider code style, for them it's not important, he's already thinking beyond what he's being taught.

---

### Post by halovivek on 2008-11-25
you can do it. do well.

---

### Post by mdawg414 on 2008-11-26
Where do they teach Java to CS majors? I would have loved that. I was stuck couting in c++ my first couple quarters at UCLA. :(
Then again, I just like Java so I guess I am biased.

But to answer the question, I would definitely say good job. CS is hard enough as it is. The fact that you are going above and beyond what you are taught and writing programs other than ones assigned to you in your first semester is a really good thing.

---

### Post by Sorivenul on 2008-11-26
> **mdawg414 said:**
> Where do they teach Java to CS majors? I would have loved that. I was stuck couting in c++ my first couple quarters at UCLA. :(
Then again, I just like Java so I guess I am biased.

It's the first CS class to take after the basic Introduction to Computers at my University in South Dakota. In fact, it is the majority of the CS curriculum here before Graduate level courses.

---

### Post by happysmileman on 2008-11-28
In your addition function you have:
```
for (int index = 0; index < 10; index++){
			...					
			//Congradulates user if answer is correct and tallies a correct answer to the quiz array
			if (userAnswer == answer){
				JOptionPane.showMessageDialog(null, "Correct! Good job!");
				quiz[index] = 1;
				}

			//Informs user of incorrect answer and tallies an incorrect answer to the quiz array
			else{
				JOptionPane.showMessageDialog(null, "Oops! The answer was " + answer + ".");
				quiz[index] = 0;
			}
		}
		
		//This for statement counts the number of questions answered correctly
		for (int index = 0; index < 10; index++){
			if (quiz[index] == 1)
				correctAnswers += 1;
		}

```

This could easily be done as:
```
for (int index = 0; index < 10; index++){
	...					
	//Congradulates user if answer is correct and tallies a correct answer to the quiz array
	if (userAnswer == answer){
		JOptionPane.showMessageDialog(null, "Correct! Good job!");
		correctAnswers += 1;
	} //Informs user of incorrect answer and tallies an incorrect answer to the quiz array
	else{
		JOptionPane.showMessageDialog(null, "Oops! The answer was " + answer + ".");
	}
}

```
Without the need for an int[] quiz, unless you wanted to update it so that it told you which question numbers you got right and wrong, which admittedly my way doesn't do.
Same for the rest of the functions.

Other than that I thought it was fairly good. Some people were suggesting OOP for it, but for a program this small I don't really think it's all that necessary.

---

### Post by Tomosaur on 2008-11-29
The problem with comments are that they should NOT be considered documentation. Who wants to read documentation in such a horrible format as a source code file? :P

Comments (imo) should be reserved for unclear parts of your code, or as a kind of 'section description' to break up parts of your code. Far more important is code readability (too many comments makes readability difficult - particularly if whoever is reading your code is doing so in a text editor with no syntax highlighting!). It is better to use descriptive variable names (where it makes sense, of course), descriptive function / method / class names, and a uniform, clean style (correct indentation, nice use of whitespace etc).

When it comes to documentation, Java uses something called 'jdoc', which you should read up about and get to know. By using the correct style of comments, the jdoc tool will create some nice HTML documentation pages for you (the java API is produced by jDoc). This is much nicer to read than source code comments.

So basically:

1: Source code comments - think about these more as 'implementation notes', where what you're doing is unclear. Anybody reading your code should be able to understand what your code does without relying on the comments.
2: Documentation - think about this as a 'developer manual'. Most of the time, developers don't particularly care how exactly your program works, they just want to be able to use it in their own software, or modify a particular part. The documentation produced by jDoc is much more suited to this than over-commenting your code.

Good luck with your course, anyway!

---

### Post by cb951303 on 2008-11-29
just for the people that uses an ide, comments can be folded :)

---

### Post by semitone36 on 2008-12-02
Thanks for the feedback happysmileman.  You are very right that would work a lot better.  I think I was originally going to use the quiz array to tell the user which questions they got wrong but decided against it and forgot to take that out of there.  Good eye!

> **Tomosaur said:**
> 
When it comes to documentation, Java uses something called 'jdoc', which you should read up about and get to know. By using the correct style of comments, the jdoc tool will create some nice HTML documentation pages for you (the java API is produced by jDoc). This is much nicer to read than source code comments.

Yup if you notice before each of my method headings I left longer comments in the  /** ... */ format which is used by javadoc to creat the html document.

---

