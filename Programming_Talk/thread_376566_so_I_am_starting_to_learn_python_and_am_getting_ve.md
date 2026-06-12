---
title: "so I am starting to learn python and am getting very confused.."
date: 2007-03-05
forum: Programming Talk
---

### Post by billdotson on 2007-03-05
I am reading the python book from greenteapress.com, the How to Think Like a Computer Scientist python version and it is confusing me quite often.  

At the end of each chapter there seem to be a series of question there but the book just seems to leave these questions open with no clear answer and I feel like I need to know the answer to learn some of the overall meaning of that given chapter.  Maybe I am supposed to know the answers if I understand the chapter but if I cannot think about them and figure out the answer then I am not going to learn what the overall chapter was about.

Also there are just sentences that just plain confuse me like in the user defined function 
   def printTwice(bruce)
        print bruce , bruce.

then it sets michael = "Eric, the half bee"
and then runs printTwice(michael)

then it says "Notice something very important here.  The name of the variable we pass as an argument (michael) has nothing to do with the name of the parameter (bruce).  It doesn't matter what the value was called back home (in the caller); here in printTwice, we call everybody bruce."

There are just things that the book is talking about that makes no sense to me at all.   I am only 50-60 pages in and I feel like I need to read again because I do not understand most of it.

---

### Post by Tuna-Fish on 2007-03-05
```
def printTwice(bruce)
        print bruce , bruce

michael = "Eric, the half bee"
printTwice(michael)
#when run, this produces:
Eric, the half bee Eric, the half bee

```
The main point to notice is that 'bruce' in printTwice(bruce) doesn't **mean** anything. It is just a variable name, you can call printTwice(bruce) with anything and it'll still work.

actually, you don't even have to use a variable, try printTwice(3)

---

### Post by Tomosaur on 2007-03-05
Best things you can do is to sit at the computer with the book open, so you can type out the sample code and see what it does. Programming is just one of those things where it pays to get hands-on rather than simply read about it.

---

### Post by Rui Pais on 2007-03-05
> **billdotson said:**
> ...

Also there are just sentences that just plain confuse me like in the user defined function 
   def printTwice(bruce)
        print bruce , bruce.

then it sets michael = "Eric, the half bee"
and then runs printTwice(michael)

then it says "Notice something very important here.  The name of the variable we pass as an argument (michael) has nothing to do with the name of the parameter (bruce).  It doesn't matter what the value was called back home (in the caller); here in printTwice, we call everybody bruce."

...

def printTwice(bruce) it's just a definition of a function with one parameter. 
It says:
define a function called printTwice and that need to recieve something, a single parameter, that for internal use of this function we name it bruce. 

Btw, thats a terrible example. Very confusing. A better approach would be:

```
   def printTwice(aName)
        print aName, aName
```

Much more abstract and self-explanatory. 

Then it can be call with: 
```
michael = "Eric, the half bee"
   printTwice(michael)
```

---

### Post by pmasiar on 2007-03-05
Would you understand better code like this one:

```

   def printTwice(person)
        print person, person

```

> **billdotson said:**
> 
then it says "Notice something very important here.  The name of the variable we pass as an argument (michael) has nothing to do with the name of the parameter (bruce).  It doesn't matter what the value was called back home (in the caller); here in printTwice, we call everybody bruce."

Meaningful names of variables are very important. That passage of your book was trying to be entertaining and funny while refreshing very trivial concept of "parameter". Funny is great for experienced programmers who understand concept of "parameter" from previous languages (the audience of "Think like CS"), but as you just noticed, might be very confusing for a beginner.

I pesonaly think that "Think like CS" is NOT good introductory programming book for a self-learner. When you are learning by yourself, there is enough to get confused, you do not need to be entertained. There are IMHO better books for Python beginner. Baldwin book, and wikipedia books are online, free, and less confusing IMHO. Bet even before these books, "instant hacking" guide will let you test in Python shell some simple concepts.

I linked them all from [http://learnpydia.pbwiki.com/HowToStart](http://learnpydia.pbwiki.com/HowToStart).

---

### Post by studiesrule on 2007-03-05
The questions at the end are intentionally given without answers, just to make sure you peruse them long enough. If you can't answer them completely, try to write some code to check it out (this is also one it's objectives), and skim the chapter.

Also, I think you should try and read the first few again, at least skim through them. It shouldn't take much time, but it will kinda clear up some doubts. Use the Python Interpreter, because that is the most useful tool there is. Just open up IDLE or whatever you use (or just the terminal), and test stuff out. You ever have a doubt, type up something and play with it.

As with the specific example you gave, I just wanted to explain it in a bit longer fashion, just in case the above two posts didn't clear it up.

In the function printTwice,
```

def printTwice(bruce)
        print bruce , bruce

```
the function itself **internally** represents its 'arguments' as 'bruce' It's bad terminalogy, and you should never name your arguments bruce, but he was just referring to it to show that the name doesn't matter. Arguments are: 

function (argument1, argument2)

references to the variables that you want the function to use. For example if you had sqrt(x), sqrt being the square root function, 'x' is the argument. 

When you call 
```

michael = "Eric, the half bee"
printTwice(michael)

```

the first line says: micheal = some string.
The second line sends this 'some string' to the function printTwice. Though you call the function using printTwice(micheal), using 'micheal' as the argument, the printTwice function names the same 'some string' bruce, and uses it. So, while you refer to the string as micheal, the function refers to it as bruce.

I hope I haven't confused you.

---

### Post by stani on 2007-03-06
In case you are looking for a good editor, try SPE:
[http://pythonide.stani.be](http://pythonide.stani.be)

There will be a new release soon which is very focused on running smooth on Ubuntu.

Stani

---

### Post by dwblas on 2007-03-06
stani said:> In case you are looking for a good editor, try SPE:ENOUGH ALREADY.  You add this to every Python thread.  If it's so good, how come you have to promote it so much.  If it is that good it will "sell" itself.

---

### Post by dwblas on 2007-03-06
```
def printTwice(bruce)
        print bruce , bruce
```We give variables names to keep them separate.  The following code makes this point.  BTW, you can learn this.  Figure out what you can now and learn the rest as you go along.```

def printTwice(bruce, aperson)
        print "the data at the variable name bruce is", bruce , bruce
        print "the data at the variable name aperson is", aperson, aperson

michael = "Eric, the half bee"
second_var = "this is #2"
printTwice(michael, second_var )
printTwice( "some other stuff", michael) ## 'michael' corresponds to the 2nd var=aperson
```

---

### Post by pmasiar on 2007-03-06
> **dwblas said:**
> stani said:ENOUGH ALREADY.  You add this to every Python thread.  If it's so good, how come you have to promote it so much.  If it is that good it will "sell" itself.

Relax. Stani switched to Ubuntu, went through all threads mentioning python, and added link to his new blog. What is the big deal?

I personaly am *very* happy that Stani is back. I was seriously concerned about what will happen to SPE -- my favorite Python IDE -- when Stani's website went down couple months ago. Now SPE is not only back: my favorite IDE for my favorite language is developed in my favorite linux distro! Cannot get any better than that! I get all new features quicker and well tested now!

Stani contributed many, many hours to free software community by developing SPE and giving it away for free. And he wants to continue to do that, and make sure that people for whom it might be usefull know that after short 'sabbatical" he is back in business. So he let all of them he can find to let know. IMHO he earned right for little publicity.

dwblas I do not know you and you might contributed also zillion of hours. But for Stani I know it for sure and I am really, really glad he is back, and SPE will continue to be developed. If you are interested in Python, you should be happy about it too. IMHO, YMMV.

---

### Post by j_g on 2007-03-06
> ENOUGH ALREADY. You add this to every Python thread.

Actually, I'd like to see _much more_ development and promotion of software that is especially targetted for, and takes maximum advantage of, Ubuntu (and also targets a specific audience in other ways like a programming tool that focuses upon one particular language). There's way too much "one size fits all" stuff that inevitably ends up being not very good, for no one in particular. That being said, I notice that this guy's offering claims to be available for Windows, Mac, and Linux, so it sounds like yet another one of the multitude of "I'm trying to be everything to everyone" aberrations that plague the planet, rather than something especially tailored for Ubuntu.

Perhaps the "promotion" would be better if the guy explained _why_ his offering is better for Ubuntu users, in ways that the alternatives aren't. Simply claiming it is, is not convincing.

---

### Post by Tomosaur on 2007-03-06
I tried SPE and it crashes every time I launch it. I'll report the bug later on when I'm at my own computer, but it is pretty annoying. I've been using eclipse for my latest project, and it's just not working the way it's supposed to - me and IDEs just do not get along at all :(

---

