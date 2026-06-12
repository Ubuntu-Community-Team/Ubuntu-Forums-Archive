---
title: "Can't Compile Java Source Code in JCreator"
date: 2010-08-20
forum: Programming Talk
---

### Post by Diaby does Gallas on 2010-08-20
I am trying to compile this source code in JCreator but for some reason I keep getting error messages. 
 
[IMG]http://i34.tinypic.com/ibgflu.png[/IMG]
 
 
These are the debugging errors I am getting, it seems to be that JCreator doesn't recognise the code even though it is Java and it is correct:
 
[IMG]http://i38.tinypic.com/vjpzr.png[/IMG]
 
Do I need to download any extra add on's for this code to be able to work, as it's not just this code that isn't working it's quite a few.
 
Regards in advance.

---

### Post by dv3500ea on 2010-08-20
Try compiling the source from a terminal:

If your source file was at /home/user/Real.java, you would run this:
```

cd /home/user
javac Real.java
java Real.class

```
to compile and run your code. Any errors will be due to errors in your program.
Note you need [openjdk-6-jre]("apt:openjdk-6-jre") and [openjdk-6-jdk]("apt:openjdk-6-jdk") installed to do this.

---

### Post by Diaby does Gallas on 2010-08-20
> **dv3500ea said:**
> Try compiling the source from a terminal:
 
If your source file was at /home/user/Real.java, you would run this:
```

cd /home/user
javac Real.java
java Real.class

```
to compile and run your code. Any errors will be due to errors in your program.
Note you need [openjdk-6-jre]("apt:openjdk-6-jre") and [openjdk-6-jdk]("apt:openjdk-6-jdk") installed to do this.
 
 
I have both the jdk and the jre both installed, and those links you posted don't work, and the name real was just the name I gave the project.

---

### Post by KdotJ on 2010-08-20
Maybe a silly question, but do you have this code inside a method... inside a class? I ask as I can only see some of your code, and that code in the PDF document you show will not compile on it's own.

---

### Post by Diaby does Gallas on 2010-08-20
> **KdotJ said:**
> Maybe a silly question, but do you have this code inside a method... inside a class? I ask as I can only see some of your code, and that code in the PDF document you show will not compile on it's own.
 
 
No I created a class and called it Real, and then I created an applete to write the code in.
 
Could you write the beggining of the code if it's not too long so I can see if it works if it aint too much trouble ;).  It would be really appreciated.

---

### Post by Diaby does Gallas on 2010-08-20
Right I have solved one problem only to get another problem,I am getting the error message <identifier> expected in this code:
 
"imageWidth = image.getWidth();
imageHeight = image.getHeight();"
 
And with this code:
 
"while (imageWidth > 1 || ImageHeight > 1) { //loop until size: 1x1
 imageLevel++;"
 
I get ';' expected?
 
Help is greatly appreciated.

---

### Post by Queue29 on 2010-08-20
> **Diaby does Gallas said:**
> Right I have solved one problem only to get another problem,I am getting the error message <identifier> expected in this code:
 
"imageWidth = image.getWidth();
imageHeight = image.getHeight();"
 
And with this code:
 
"while (imageWidth > 1 || ImageHeight > 1) { //loop until size: 1x1
 imageLevel++;"
 
I get ';' expected?
 
Help is greatly appreciated.

The first problem is due to variable imageWidth and imageHeight not having been declared yet. The code in the PDF is very incomplete, and obviously assumes a lot of other stuff is going on.


Not sure what's wrong with the while loop without seeing more code.

---

### Post by KdotJ on 2010-08-20
> **Diaby does Gallas said:**
> No I created a class and called it Real, and then I created an applete to write the code in.
 
Could you write the beggining of the code if it's not too long so I can see if it works if it aint too much trouble ;).  It would be really appreciated.

As much as I'd like to help, as Queue29 said, the PDF if very incomplete and we can't really see the big picture. It's not really possible to just spawn some fully working code form that snippet without knowing the context or what is wanted to be achieved.

---

### Post by Diaby does Gallas on 2010-08-20
> **Queue29 said:**
> The first problem is due to variable imageWidth and imageHeight not having been declared yet. The code in the PDF is very incomplete, and obviously assumes a lot of other stuff is going on.
 
 
Not sure what's wrong with the while loop without seeing more code.
 
 
All the code that I have typed is in the PDF, where about do I declare the imageHeight, and like I said you can see the rest of the while loop on the PDF.

---

### Post by Diaby does Gallas on 2010-08-20
> **KdotJ said:**
> As much as I'd like to help, as Queue29 said, the PDF if very incomplete and we can't really see the big picture. It's not really possible to just spawn some fully working code form that snippet without knowing the context or what is wanted to be achieved.
 
 
so basically the solution to the problem is to become more competant at Java and then I will see where I have gone wrong.
 
I think TBH I have tried to go from an introduction to Java i.e. very basics to a bit more advance Java and that is where I am going wrong.  I think I need to learn to walk before I can run don't I.

---

### Post by KdotJ on 2010-08-21
Perhaps, it's good to practise the basics first until you have a good grasp on them. Ok, as for the errors regarding imageWidth and imageHeight... It's complaining that it can't find an identifier. You say that you have put this code inside a method, inside of a class which is named Real. Is that all there is in the file? For these two varibles to be used, you will have needed to declare them at some point, stating their types. For example:

```

int imageHeight;
int imageWidth;

```

Then they can be assigned values (which they are in the code you posted). 
As for other errors such as "; expected", you will notice after a little experience that these kind of errors can easily crop up if you forget brackets or semicolons somewhere. Some times just missing out one bracket can throw up say ten errors when trying to compile. 

My advise, practise some more on basic java, and how to construct your code and classes/methods etc. By the looks of things you are working from a tutorial of some sort? Just try to make sure you understand what is being done. Otherwise, you may end up getting things to work, but have no idea on what's going on

---

### Post by dv3500ea on 2010-08-21
> **Diaby does Gallas said:**
> I have both the jdk and the jre both installed, and those links you posted don't work, and the name real was just the name I gave the project.

/home/user/Real.java was just an example; you would have to substitute the correct path. 

I don't know what the problem with the links is - they work in both firefox and chrome/ium and should ask to install these packages on your system.

---

### Post by Diaby does Gallas on 2010-08-21
> **KdotJ said:**
> Perhaps, it's good to practise the basics first until you have a good grasp on them. Ok, as for the errors regarding imageWidth and imageHeight... It's complaining that it can't find an identifier. You say that you have put this code inside a method, inside of a class which is named Real. Is that all there is in the file? For these two varibles to be used, you will have needed to declare them at some point, stating their types. For example:
 
```

int imageHeight;
int imageWidth;

```
 
Then they can be assigned values (which they are in the code you posted). 
As for other errors such as "; expected", you will notice after a little experience that these kind of errors can easily crop up if you forget brackets or semicolons somewhere. Some times just missing out one bracket can throw up say ten errors when trying to compile. 
 
My advise, practise some more on basic java, and how to construct your code and classes/methods etc. By the looks of things you are working from a tutorial of some sort? Just try to make sure you understand what is being done. Otherwise, you may end up getting things to work, but have no idea on what's going on
 
I am thinking that it is probably something very simple, and this PDF that I am using is not for beginners and it presumes you have knowledge of Java.  That is why then it isn't giving you fully functional code in, think I will be downloading more free Java programming ebooks, but for beginners not advance.  I will also be scouring EBay and Amazon for cheap second had Java Books.
 
Thanks for the help anyway, I would give you rep but it doesn't seem possible.

---

### Post by KdotJ on 2010-08-21
No worries for the help, sorry that the answer is just to learn it lol. Have you any previous experience with programming in any language?

As for learning java, on YouTube check out java tutorials by a user named TheNewBoston
He has hundreds of videos and they range from beginner to intermediate

---

### Post by Diaby does Gallas on 2010-08-21
> **KdotJ said:**
> No worries for the help, sorry that the answer is just to learn it lol. Have you any previous experience with programming in any language?
 
As for learning java, on YouTube check out java tutorials by a user named TheNewBoston
He has hundreds of videos and they range from beginner to intermediate
 
I done a City & Guilds in programming in college a few years back, it wasn't anything serious just an introduction to programming. It basically taught you the difference between object oriented and non object oriented, it also had a few brief examples of Java, Visual Basic, and SQL. They did give us some examples in each like but as I said it was more of an introduction nothing too heavy. In Java we created a calculator, but we had all the tools that were given to us so it was more of a jigsaw puzzle that we had to put together in order to get it working. All the pieces were given to us over the duration of the course,in other projects so we did have to use our brain and figure it out, it was as simple as here are the pieces and they will all form a functioning calculator when put together. In VB we just mainly done a very small amount of programming but the VB was just boundary testing, and SQL was just a brief introduction also, just a snippet of how to SQL commands work in a database.
 
As for YouTube, I actually have been going on there, but I didn't see that bloke I will check him out.

---

