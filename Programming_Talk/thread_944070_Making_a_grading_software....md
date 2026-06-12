---
title: "Making a grading software..."
date: 2008-10-10
forum: Programming Talk
---

### Post by hockey97 on 2008-10-10
Hi, I would like to know what's the best way to make a grade book type program???

I might need to have this useable on linux,windowsxp, and windows vista.

my current college class is complaining not knowing their total grades.


so I decided that I could make a program that would do the math work for them.

based on the professor grading scale I  would like to make a software that would allow users to input there grades and I would display the current grade in the class.

any good libaries that i could use.

---

### Post by Sinkingships7 on 2008-10-10
Microsoft Excel or OpenOffice.org's Calc should do the trick. ;)

In all seriousness though, if you really feel the need to code a new one, I guess a big decision for you to make is whether or not you want it to have a GUI. If that's the case, then this is going to be quite the project.

If not, then hacking out something simple in Python should be easy enough. The libraries that come with and are available for Python have plenty of tools for number manipulation, so I don't see you needing to go beyond there.

---

### Post by LaRoza on 2008-10-11
Most people use a spreadsheet for this.

I suggest OO Calc, as it is free and available for all the platforms you mention.

---

### Post by hockey97 on 2008-10-11
well I tried using excel to make a spread sheet of this.

I used the sum and  currently want to use a if condition.

the reason is our class has about 25 homework problems.

we just done 4 but I want to create a automation where when I add more hw grades in I want it to quicky update.


So like if I have 4 grades right now then I just add 5 it would add all the 5 hw percentage and then divide by 5 to get the average grade.


I need to do this for hw,test, participation and even group projects.

I want to create one for myself and I also would want to give it to my other class mates since right now they can't figure out their current grade overall.

The problem I notice is that the if statements I would need to create at least 59.

we have 25 chapters of hw and we get 2 hw grades for each chapter.


so I don't want to make 50 if statements to check where the last record is.

is there a way where I can use something that would update the division.

so if I put 6 grades it would update the division to divde by 6??

---

### Post by CptPicard on 2008-10-11
This sounds like an EXCELLENT small project for you to learn to actually program instead of throwing together code others wrote and you do not understand ;)

If I were you, I would skip having a GUI, take a language like Python, define some kind of input file format, parse the file into some kind of internal structure and then just collate the necessary sums and whatever from that structure and print it.

If you are really feeling adventurous, you might try something like awk, but I have a feeling it's beyond your competence and you would benefit more from Python.

The rest is left as an exercise for the reader. If you have a specific question, I am sure a lot of people will help.

---

### Post by Mr.Macdonald on 2008-10-11
If you need it cross platform, instead of choosing a language and having to go through all that, set up a server and web pages for all the grading. you could make it viewable by students so they can see their grades. Just don't be stupid and make it so you can hack because you would be expelled.

---

### Post by LaRoza on 2008-10-11
> **Mr.Macdonald said:**
> Just don't be stupid and make it so you can hack because you would be expelled.

Hacking is exactly what he needs to do.

It would be good practice and I believe that it is his field. Most of the posts on this forum are by hackers and no one has gotten expelled for it, in fact, many have degrees for their skills (or got their skills from degrees, whatever)

---

### Post by hockey97 on 2008-10-11
I do know how to program. I just lack experience in doing different projects.

I don't go and copy others code and use it for myself. 

Now how can you hack with a software that calculate your grade???


I seriously can just make a website page for this. The problem I will get expelled to violating privacy laws.

So I need to make a program it can't be a website or anything like that.

I need to make a function to update what the sum needs to be divided by.

Which I need to divide the sum by how many enteries that have been made.


If I have 5 grade and I just put in another grade I want it to then change the division from 5 to 6.

so it would be SUM divided by 6 that would give the % of the current class grade.

in excel I don't see any functions that would do exactly this.

---

### Post by LaRoza on 2008-10-11
> **hockey97 said:**
> 
Now how can you hack with a software that calculate your grade???

You can hack the software, which you should do.

> 
So I need to make a program it can't be a website or anything like that.

Can it be a client side script? Input the grades, and it figures it out.

> 
I need to make a function to update what the sum needs to be divided by.

In a spreadsheet, I believe there is a count() function or something or just use the average function.

> 
so it would be SUM divided by 6 that would give the % of the current class grade.

in excel I don't see any functions that would do exactly this.
[http://www.cpearson.com/excel/excelF.htm](http://www.cpearson.com/excel/excelF.htm)

[http://spreadsheets.about.com/od/excelcountfunctions/Excel_Count_Functions.htm](http://spreadsheets.about.com/od/excelcountfunctions/Excel_Count_Functions.htm)

---

### Post by LaRoza on 2008-10-11
```

#!/usr/bin/env python
# -*- coding: UTF8 -*-
#coding=UTF8

#Copyright (C) 2008  LaRoza

import sys

def main(args):
    for file in args:
        try:
            grades = []
            for grade in open(file):
                try:
                    grades.append(int(grade.strip()))
                except ValueError :
                    continue
            print "The average for %s is %d" % (file,(sum(grades)/len(grades)))
        except IOError:
            print "%s doesn't exist" % file

if __name__ == "__main__":
    main(sys.argv[1:])

```

```

~/p$cat cptpicard laroza
90
80

100
90

~/p$./p.py cptpicard laroza
The average for cptpicard is 85
The average for laroza is 95
~/p$

```

Just have each file have a list of the grades and add it as an argument. They have to be on each line, blank lines and spaces are ignored.

Would be handy if the file name is the name of the student.

---

### Post by pmasiar on 2008-10-11
> **hockey97 said:**
> I do know how to program. I just lack experience in doing different projects.

So why you refuse to take opportunity and put together some project? You need to write your own code, make your own mistakes, and learn from them. There is no royal way to programming 8-)

> Now how can you hack with a software that calculate your grade???
.

you mistake hacking and cracking. 'hack' means put code (possibly ugly, but working) together, 'crack' means break into computers of others.

---

### Post by LaRoza on 2008-10-11
> **pmasiar said:**
> So why you refuse to take opportunity and put together some project? You need to write your own code, make your own mistakes, and learn from them. There is no royal way to programming 8-)


It took me longer to type that script than it took me to think of it.

I think if this sort of project causes on to make a thread on a forum, especially if it is your major, you should rethink your major...

---

### Post by hockey97 on 2008-10-11
thanks. I decided that I will just use excel. I didn't know they had a count function.

thanks for the links I will take a look at it before I start with excel.

I didn't need a gui. I just wanted to make something that won't take much of my time but would setup in a way to help me and my other classmates on find out their exact grade in the class.

Our college provided us with crappy software from their website which only shows the grades for each assignment they don't show any current class grade until all hw and test ect at the end of the semester they then compute the grade automatically and display your class grade which by then it's  too late to shape up and try to pass a class.

Thanks for the help.

---

### Post by hockey97 on 2008-10-11
> **pmasiar said:**
> So why you refuse to take opportunity and put together some project? You need to write your own code, make your own mistakes, and learn from them. There is no royal way to programming 8-)



you mistake hacking and cracking. 'hack' means put code (possibly ugly, but working) together, 'crack' means break into computers of others.


Well I was  told many definitions of hacking. One which what you say. Then others saying an illegal activity to break in unauthorized computers.

Then I was told by software engineers that hacking just means modifying code. It dosen't mean an illegal activity but just that your modifying something.

so I guess I can be defined in many ways.

Just want to point this out since I been exposed to many definitions of hacking.

The person said don't be stupid and start hacking. I took it as if he meant to try running bad code on the page to steal cookies and many other sensitive like their college login information ect. This How I took it.

Now the other comment about hacking could of meant modifying something.

Like taking excel or something and add a few scripts to it to add new functions ect.

---

### Post by hockey97 on 2008-10-11
> **LaRoza said:**
> It took me longer to type that script than it took me to think of it.

I think if this sort of project causes on to make a thread on a forum, especially if it is your major, you should rethink your major...

No computer programming is not my major.

I am majoring in accounting currently.


computer programming is a hobby of mine. I learn on my spare time.
Same with computer hardware.
I have interests in electronics/computer hardware  and also programming.

I started in 6th grade on my  journey to programming. I started off with html and css which are markup langos. Then started with C# and then c++

My dad had c# and c++ college books. This is how I learned the lango.

Then I heard about Nasa using python and hearing positive. I started to learn python but never had time to do any project. I only make a simple calculator that prints the result to the screen.

I got some computer engineering hardware books on circuity and In high school I took a electronics class. This class first year covered in building circuits and using ohms law to figure out and control the current flow.

I am currently been thinking to start learning Ruby. I notice it's starting to be used alot. In my area there is alot of jobs that require this.


I am not script kiddie.

---

### Post by LaRoza on 2008-10-11
> **hockey97 said:**
> No computer programming is not my major.

I am majoring in accounting currently.

Interesting. Mine in Criminal Justice.

> 
computer programming is a hobby of mine. I learn on my spare time.

Same for me.

> 
I started in 6th grade on my  journey to programming. I started off with html and css which are markup langos. Then started with C# and then c++

I know what HTML and CSS are ;) CSS isn't a markup language.

I started with XHTML as well, but I was 18 when I started (20 now).

> 
I am not script kiddie.

If you were, would you admit it?

---

### Post by pmasiar on 2008-10-11
> **hockey97 said:**
> Well I was  told many definitions of hacking. One which what you say. Then others saying an illegal activity to break in unauthorized computers.

you cannot trust clueless journalist. Do your own research: [http://en.wikipedia.org/wiki/Hacker](http://en.wikipedia.org/wiki/Hacker)

---

### Post by TreeFinger on 2008-10-11
First thing you need to think of is what are you going to need from the user?

They are going to half to know their grades and what type of grade it is. (test, quiz, homework). I think you would first ask the user what are all your test grades to this point? What are all your quiz grades to this point? etc...

---

### Post by hockey97 on 2008-10-12
> **LaRoza said:**
> Interesting. Mine in Criminal Justice.


Same for me.


I know what HTML and CSS are ;) CSS isn't a markup language.

I started with XHTML as well, but I was 18 when I started (20 now).


If you were, would you admit it?

That's cool. Ya I forgot to seperate css with html. I mean html was markup. CSS is a stylesheet language.

If I were a script kiddie. I would first question you what is a scrip kiddies since script kiddies won't even know what that is.

 If you told me then yes I would say I am a script kiddie since I would rather tell you where I am at so you can assist my questions knowing where I am at.

 I currently got a job  as a php programmer. So I do know how to program. 

The problem is if I wanted to do a project I never done before I would ask here and also do some google searching. I would want positive input on what you guys would suggest me looking at.

I mean I know how to program but programming is a huge range of a skill.

I mean there are difference between programming a video and programming a space shuttles controls.

They are similar in some way but also have their differences and before you get into projects you never handled before most likely you would want to do some research and ask others how they done it or if anyone had any experience in that area. So they can give you tips like watch out when you inputting data from censors ect like what to watch out for since they had experiences and had errors which they fixed which they can pass on that experiene to you to avoid having the same error.

This is what I do. I post on here questions about stuff I never done or experience hopping someon on here had experience a similar project that could guide me on what I need to focus on learning.

just like this. I wanted to make somthing for my class and myself to help use monitor our grades.

This is something I never done. I have used excel before and I did before I posted here  make a excel spreadsheet.

I used the sum function and then notice about a pain in the neck.

I notice that when you divide the sum I had to manually change the number based on how many grades I have gotton so far.


we have 25 chapters   and 2 hw grades for each chapter So that would be 50 grades of hw.

so it would be a pain if I had to keep updating what the sum gets divided into.

so If I have 6 grades out of 50  I would then have to divide he SUM by 6. 

Now if I add 3 more hw grade I would then have to divide the sum by 9.


it would be a pain if I had to manually update this.

so I just need to countr how many grades are inputted and then use that number to divide the sum.

---

### Post by slavik on 2008-10-12
excel/calc formulas support if statements

I would suggest the original suggestion, excel/calc

---

### Post by pp. on 2008-10-12
Spreadsheet programs not even support sums, they also count.
Spreadsheet programs not even support sums and counting, they also find the average value of a number of values.

I feel justified in going RTFM here. 

For each spreadsheet program worth using, there are long and short lists of the functions they can perform. Most of them have formula editors which even explain the functions.

If you want to succesfully use a computer and programs, you will have to learn how to use the documentation that came with those.

---

### Post by LaRoza on 2008-10-12
> 
I currently got a job  as a php programmer. So I do know how to program. 

To give proof of knowledge, one gives evidence, not anecdotes. To prove you know how to program, you would have to demonstrate programming and problem solving ability, not that you "got a job as a php programmer". Read the daily wtf. Jobs are not an indication of knowledge without some evidence of ability.

> 
I mean I know how to program but programming is a huge range of a skill.

"Finding the average" is question for the books...

> 
This is something I never done. I have used excel before and I did before I posted here  make a excel spreadsheet.

I used the sum function and then notice about a pain in the neck.

I notice that when you divide the sum I had to manually change the number based on how many grades I have gotton so far.

Excel can do what you want; you just don't know it. Apparently ;)

> 
so If I have 6 grades out of 50  I would then have to divide he SUM by 6. 

Now if I add 3 more hw grade I would then have to divide the sum by 9.

I know how to get an average.

> 
it would be a pain if I had to manually update this.

Luckily, you don't have to.

> 
so I just need to countr how many grades are inputted and then use that number to divide the sum.

Yes, my code does exactly that. It will work with any amount of numbers. All you have to do is make a file, put the list of numbers in it (so, a person would only have to maintain a single file, each grade on a line) and run the program with that file (or any number of files) to get the results.

Try it. It does exactly what you said you wanted and does more.

And the solution, to what has baffled you, is:
```

sum(grades)/len(grades)

```
Where "grades" is a list of the grades.

---

### Post by LaRoza on 2008-10-12
> **LaRoza said:**
> 
In a spreadsheet, I believe there is a count() function or something or just use the average function.
[http://www.cpearson.com/excel/excelF.htm](http://www.cpearson.com/excel/excelF.htm)

[http://spreadsheets.about.com/od/excelcountfunctions/Excel_Count_Functions.htm](http://spreadsheets.about.com/od/excelcountfunctions/Excel_Count_Functions.htm)

> **pp. said:**
> Spreadsheet programs not even support sums, they also count.
Spreadsheet programs not even support sums and counting, they also find the average value of a number of values.

I feel justified in going RTFM here. 

And even giving a link to the solutions, and a program which does it, the question is still in the air for some reason.

> 
If you want to succesfully use a computer and programs, you will have to learn how to use the documentation that came with those.
Or if you want to be successful in PHB, you have to make other people do it.

---

### Post by pp. on 2008-10-12
> **LaRoza said:**
> sum(grades)/len(grades)
Not meaning to be disrespectful, but I think that ought to read
```
sum(grades)/count(grades)
```
or even
```
avg(grades)
```
I did not follow my own advice to RTFM. I coded this from off the top of my head.

---

### Post by LaRoza on 2008-10-12
> **pp. said:**
> Not meaning to be disrespectful, but I think that ought to read
```
sum(grades)/count(grades)
```
or even
```
avg(grades)
```
I did not follow my own advice to RTFM. I coded this from off the top of my head.

```

>>> grades = [1,2,3,4]
>>> len(grades)
4
>>> grades.count(2)
1
>>> avg(grades)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'avg' is not defined
>>> 

```

[http://www.python.org/doc/2.5.2/tut/node7.html](http://www.python.org/doc/2.5.2/tut/node7.html)

---

### Post by pp. on 2008-10-12
:lolflag:
I thought yours were the functions to be used in the spreadsheet.

---

### Post by forger on 2008-10-12
If you're importing from other files, you could make a program/script to create a comma-separated file, which is supported and can be opened with excel or openoffice spreadsheet :)
This way you would automatize the total grade calculation and have a spreadsheet as gui! :D

---

### Post by nvteighen on 2008-10-12
@hockey67:

1. No matter what you end up using for your "real world" need (i.e. people asking you to code some average-calculator), for which I really think OpenOffice Calc or MS Excel are the best alternatives. Why don't you also try to write something like that or related or based on that idea for your own training? For example, try to write a little terminal application that reads/saves grades in a trivial database (I mean, a text file that you parse and show like a table) and takes the average. That shouldn't be too difficult *a priori*, depending on what language do you choose, on what data structures you design, etc.

2. If you don't know what to do, why don't you join someone else's project? Look at [Launchpad]("https://launchpad.net"), [Savannah]("http://savannah.gnu.org"), [Google Code]("http://code.google.com/hosting/") or [Sourceforge]("http://www.sourceforge.net")...

---

### Post by Reiger on 2008-10-12
Well, begging you pardon but I would say (to people who can't calculate their own average grades) "learn to use a pocket calculator". That's what those are for.

@LaRoza your program fails to take into account different weights different grades may have, i.e. a 5 counting for 2 does more than an 8 counting for 1. (The average in this case being 6,0; not 6,5) ;)

Anywho 2 mins in Calc yields this trick:
[[IMG]http://img33.picoodle.com/img/img33/3/10/12/f_snapshot1m_b413a4a.png[/IMG]](http://www.picoodle.com/view.php?img=/3/10/12/f_snapshot1m_b413a4a.png&srv=img33)

Since I allow for a ridiculous amount of up to 999 grades for just one subject -- this should work just fine. The trick is in the formula selected, the other things Total Weight (=SUM(C2:C1000)) and Average (=E2/F2) are trivial. A similar thing can be readily made in Excel too.

---

### Post by LaRoza on 2008-10-12
> **pp. said:**
> 
I thought yours were the functions to be used in the spreadsheet.
Ah, actually, that was the snippet from the Python program I posted a while back, due the to the constant bemoaning of how to get the total.

Indeed, count() is the function to get the number of cells in a spreadsheet. count() in Python counts the time a certain value is in an array.

> **Reiger said:**
> 
@LaRoza your program fails to take into account different weights different grades may have, i.e. a 5 counting for 2 does more than an 8 counting for 1. (The average in this case being 6,0; not 6,5) ;)

Yes, I know. I didn't have the full specs and I was confused over the confusion of finding the number of grades. It would be simple to do though, just add sections to the file for each format.

> 
Since I allow for a ridiculous amount of up to 999 grades for just one subject -- this should work just fine. The trick is in the formula selected, the other things Total Weight (=SUM(C2:C1000)) and Average (=E2/F2) are trivial. A similar thing can be readily made in Excel too.

I was going to do a spreadsheet as well, but I figured I'd leave that as an exercise to the reader.

---

