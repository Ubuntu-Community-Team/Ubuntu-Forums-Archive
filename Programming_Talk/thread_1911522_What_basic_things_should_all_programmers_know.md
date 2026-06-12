---
title: "What basic things should all programmers know?"
date: 2012-01-19
forum: Programming Talk
---

### Post by venom104 on 2012-01-19
I found a question on yahoo answers a while back that was asking, "What basic things should a Computer Programmer know?". My reponse was "At LEAST the basic data structures and algorithms that every programmer  should know, stacks, queues, hash tables, graphs, linked lists, trees,  heaps, insertion sort, quick sort, merge sort, counting sort, radix  sort, binary search, knowledge of algorithm analysis, some knowledge of  data compression/data encryption algorithms, expertise with the standard  library of functions,  AND a mastery of at LEAST ONE programming  language".

The problem here is that everything I listed, I learned in class or taught myself. I've never had a real programming job (well I worked as a web designer for a community college but that's not real programming experience) OR an internship. I actually DO NOT KNOW what is required knowledge in the workforce. So I'm asking YOU VETERAN programmers, what do you need to know to be successful as a "real" programmer in today's world? Please list any data structures, algorithms, libraries, languages, or whatever you think would answer the question in your response.

---

### Post by Arndt on 2012-01-19
> **venom104 said:**
> I found a question on yahoo answers a while back that was asking, "What basic things should a Computer Programmer know?". My reponse was "At LEAST the basic data structures and algorithms that every programmer  should know, stacks, queues, hash tables, graphs, linked lists, trees,  heaps, insertion sort, quick sort, merge sort, counting sort, radix  sort, binary search, knowledge of algorithm analysis, some knowledge of  data compression/data encryption algorithms, expertise with the standard  library of functions,  AND a mastery of at LEAST ONE programming  language".



Were there no other responses?

---

### Post by muteXe on 2012-01-19
Where the coffee machine is :)

---

### Post by lisati on 2012-01-19
Not only the coffee pot, but how to find things out.

---

### Post by muteXe on 2012-01-19
Is it really a bad thing i dont know what a graph is, and i've never heard of a radix sort?  I don't reckon it is tbh.

---

### Post by nipunshakya on 2012-01-19
The only thing i have learnt myself till now is to follow the following:
1. CODE.
2. CODE.
3. DEBUG YOUR CODE .... and so on....

---

### Post by Hetepeperfan on 2012-01-19
I think you should find a programming field in which you can be an expert if you want to be successful. Can be computer vision, networking, internet, databasing, 3D graphics, gui programming and so on. Our a open source software specialist(which is a bit broader). Since you know lots of stuff about the basics algorithms, data structures, then I suppose you have the basics. So then you ready to find a field in which you can flourish. I think you have to find this corner in a big field that suits you, something you like and want to be excellent at.
Try to find the job that suits your knowledge, fun and expertise, instead of trying to find the knowledge that suits a job, since that could still be the entire wide field of computer programming and you cant be excellent in everthing, at least  I have big problems with that.

cheers,

Maarten

---

### Post by trent.josephsen on 2012-01-19
Knowing how to implement specific algorithms and data structures isn't all that useful IRL.  I mean, it's important to be able to evaluate how algorithms differ in time complexity, but for actually writing code you'll usually be calling qsort() or whatever the library provides, not choosing and implementing your own sort.

I'd say the most important things to a programmer are how to effectively comment (including consistent and readable use of whitespace) and how to find and read documentation for whatever language you're using.

I would also say that every programmer who hopes to get a job in the modern world (unless gunning for some position with specific requirements) should know at least one of {Perl, C, Python, LISP, TCL, C#} or some other well-known language that isn't usually taught in CS1 -- reason being that the job market is saturated with CS students who think they're hotshots because they can write Java or C++.  More than one language on your resume says "I'm not just blowing smoke".

---

### Post by Barrucadu on 2012-01-19
Boolean logic, the basic data structures and algorithms, how to make use of abstraction and encapsulation... there's probably more but that's all I can think of off the top of my head.

---

### Post by Habitual on 2012-01-19
Comment your code.

---

### Post by bouncingwilf on 2012-01-19
I feel understanding the problem and the methodology of solving it is crucial. If you do that, coding's often the easy bit. 

Bouncingwilf

---

### Post by patrick-epl15 on 2012-01-19
Where to look for help (internet, friends, books, etc.)

---

### Post by CoffeeRain on 2012-01-19
I think knowing how a computer works is good, knowing man pages, knowing good sources for help, etc. As far as languages, it depends on what you want to do. On Unix, knowing shell is pretty much essential for learning other languages. After that, if you want to learn Python or another language, just look up. I learned by creating scripts, then trying some GUI, and then web languages. All of the things you listed will come when you start learning how to write code and learning about computers. Try a lot of things and learn what seems good. :)

---

### Post by Simian Man on 2012-01-19
> **muteXe said:**
> Is it really a bad thing i dont know what a graph is, and i've never heard of a radix sort?  I don't reckon it is tbh.
Radix sort is not very important, and hardly ever used (it only works for integers).  Knowing what a graph is and at least being aware of graph algorithms would be beneficial though.

> **trent.josephsen said:**
> Knowing how to implement specific algorithms and data structures isn't all that useful IRL.  I mean, it's important to be able to evaluate how algorithms differ in time complexity, but for actually writing code you'll usually be calling qsort() or whatever the library provides, not choosing and implementing your own sort.
That is true in a way.  But you should know what the different sorting algorithms are and how they work in broad terms.  One because there are cases (such as an almost totally sorted list) where something like bubble sort will actually out-perform quicksort.  Also there are cases where you can't just use the libraries implementation.  I've done work with small embedded devices where there is no library at all.  Also if you have a HUGE amount of values to sort, you will not be able to have them all in memory at once so you can't use the standard library functions.  Secondly as a programmer, you have to understand and implement algorithms.  If you can't show you can do that with standard algorithms, it may be hard to find someone who will hire you.

---

### Post by venom104 on 2012-01-19
> **Arndt said:**
> Were there no other responses?

See for yourself ( [http://answers.yahoo.com/question/index;_ylt=Ajs3fUZFCzPv7dqfIy24cpEjzKIX;_ylv=3?qid=20110328203314AAZA5dN](http://answers.yahoo.com/question/index;_ylt=Ajs3fUZFCzPv7dqfIy24cpEjzKIX;_ylv=3?qid=20110328203314AAZA5dN) ). I wouldn't call the other answers, "good" answers.

---

### Post by KdotJ on 2012-01-19
> **Habitual said:**
> Comment your code.

I think this is important, even if just fo yourself. I'm sure everyone hates going back to tinker with code they wrote only 2 weeks ago, as you have to work out what's going on lol. 

I also think its important to know the built in libraries that language provides, and to use them to make your code simpler and more readable. I remember once training at a job, the coding standards page I was reading said:

> If you're about to write a comment on your triple nested for-loop with switch statements, your code is too complicated.

---

### Post by MG&amp;TL on 2012-01-19
Knowing when to quit, but knowing when to return.

I'm a newb, and probably will be for several years, but some things I just didn't understand. Classes/OOP, for instance. The first reference I was given was really badly explained and mucked up my knowledge of them for 6 months. So I gave up, used a for loop/array instead, and went away for 6 months. Now I'm easily completing the project I started 6 months ago.

---

### Post by trent.josephsen on 2012-01-19
> **MG&TL said:**
> Knowing when to quit, but knowing when to return. <snip>

Pun... intended?

---

### Post by MG&amp;TL on 2012-01-19
> **trent.josephsen said:**
> Pun... intended?

I still don't get the pun...argh!

Enlighten me, please. It's late. :)

---

### Post by Vaphell on 2012-01-19
quit and return having programming related meaning?

---

### Post by MG&amp;TL on 2012-01-19
> **Vaphell said:**
> quit and return having programming related meaning?

Oh, I get it now. UF should have a tired-ness indicator.

That's pretty funny, actually, even if I do say so myself. :D

---

### Post by Hetepeperfan on 2012-01-19
> **MG&TL said:**
> Oh, I get it now. UF should have a tired-ness indicator.

That's pretty funny, actually, even if I do say so myself. :D


You problably need something that returns coffee,or quits the day;-)

---

### Post by lykwydchykyn on 2012-01-20
- how to dissect a problem into discrete, easily solvable units
- how to abstract and loosely-couple code to make it maximally reusable
- how to use revision control properly
- pseudo-code
- how to communicate with (and especially listen to) end users
- how to leverage existing code

---

### Post by gardnan on 2012-01-20
Well, just my thoughts, but I should think that most programmers should have at least a basic grasp on the fundamentals of concurrency and multithreading too. This would involve stuff like semaphores, reentrancy, spinlocks, and mutual exclusion principles. Also, it wouldn't hurt to focus on garbage collection techniques and security flaws.

It just seems a little ironic to me that concurrency is getting to be much more significant, but it rarely gets much attention in lists like these.

---

### Post by lisati on 2012-01-20
> **Vaphell said:**
> quit and return having programming related meaning?

I thought of another related programming term, but it might not be suitable for a family-friendly forum do to nuances associated with some non-programming situations. :D

---

### Post by hockey97 on 2012-01-23
It depends on the tasks at hand. 

I think in the workforce you need at least the basics.

the basics is the programming language, if statements variables, arrays, what you said earlier. 

without the algorithms you speak of.

[http://en.wikipedia.org/wiki/Binary_tree](http://en.wikipedia.org/wiki/Binary_tree) 

overall, all you need to know is the stuff to make a basic computer program.

that is what is required in the workforce. 

however, it depends on what jobs and what tasks.

in todays economy businesses can't afford for you to learn new theirs on their dime and time. 

so what they are looking for right now in any profession is people that can start the next day without any problems.

if you can't do that then you need to do an internship. where the y usually pay you a crappy wage. 

in the workforce when they are looking for people they want people with experience in such tasks.

for example in microsoft, there are different levels of programming, there is game programming, OS programming, low level programming making drivers etc.

So, if you where to be hired, they be looking at you if you are able to do the job or work.

In the OS type of jobs, they would like you to know everything about how an OS works, and what previous projects did you do.

If you did none then they know you won't be the type of person after a week you will be able to understand everything about their os where you can add anything to their os in the second week.

Time is money and they need you to be productive. That want you to have so much experience with their structure of code the methods where you can look at their source and be like wow that's how Windows works.. interesting. you will be able to code code for the windows OS in your sleep.

that is what they are currently looking for. This is in all professions. I got 5 associates degrees in business, in accounting, finance, and general business and general studies,

I can work at an accounting firm, or at a finance firm, or in the marketing department, or management, or be a English teacher. from high school students and below. 

If you get a degree in English then you can be a English professor for college students. 

yet, I find many jobs but never get  an interview because I have no experience. 

I am working on getting my bach degree in accounting and finance.

I applied to internships but people with 4.0s always get those jobs. 

so, right now the work force is competitive and it's due to the sluggish economy.

If we had a good economy where business don't need to worry much about money. Then they would love to hire people even if they don't have the experience but do have the degree and have a will to learn the job. They would get hired in.

Yet, since right now the economy is bad and the businesses are on a tight budget, they need less risky business decisions.

So they need you to have at least a degree mainly a bach degree. Yet have experience. Since right now the market in every profession is flooded with old babyboomers and some in their 40s that have so many years experience they are getting these jobs.

so, to answer your question depends on what kind of job or task you be doing.

if it's to make a simple program, then you need just the basics.

yet, what you learn in college they take you from the basics all the way to the advance crap and it's mainly all the skills you need to cover any task or job in the computer programming field.

in theory you would be able to do any task or job int he computer science field or job.

if you learned those algorithms those are not basic their intermediate knowledge and yes you can still write good programs without them. Just that when you want a program to perform such tasks it's great to be able to do the function but to write good code you always want to write less code as possible which will increase productivity and would make your program run faster.

this is where algorithms comes into play. You can use existing ones or create your own.

If you learn more math and study up a bit on mathematics. It will help you creating your own formulas for any program for any problem.

if your writing accounting software you need to know the math to create the graphs and the math that process the information which is too much where you need an accountant to assist you with the math well not always the math but also the rules of the accounting profession so you don't write crappy code where people will have the IRS on their butts.

writing accounting software is totally different then writing a latest graphical video game for the computer.

different kinds of math aka processes, in video games you need geometry, trigonometry, calculus, then AI and other special algorithms. 

in accounting software all you need is math (finance/accounting)

that is all you need. then create a graph.

however, your like me... you be like boring!!! lets make some AI where it can reduce accounting errors and make an accountants life less miserable.   

So you start off writing accounting software in a basic form.

lets say the software firm already done this. They are now writing add on code to the existing code to re-package it as new accounting software or a new version.

well at that point they might be looking for a programmer with more advance skills not someone that just knows the basics.

because they are not going into AI and many other topics. They already written the basic functions of accounting into the software.

So the workforce requires many ranges of skills and experience. In sluggish economies they want you to know everything of that profession so not just the basics but all advance methods and problems too so you can get to work on day 1.

If it's a good economy at the time businesses will be more relaxed. They won't have tight budgets and would allow you to get used to the job for a few weeks from 1 to maybe 3 weeks. Some would hire you straight from highschool. Then train you and then pay for your college expenses so you be working while going to school.

This still does happen but it's not frequent and you need to fight for such a position. 

hope this helps you.

I got a job for 2 years at a web development firm in Washington. but got laid off in 2007 economy was taking a dive and many firms at the time decided to move operations to india.

at that time the interview they gave me test. I failed it first time around. Because I never learned programming in college and taught myself, So I was clueless as to how the workforce actually works and what they expected of me.

well, I was told to make a simple contact information.

where a persons first and last name and phone number and e-mail address is stored in a database in php.

well I did just that sent the HR the code and they sent it to their head IT guy.

he then told them he flunked the exam.

So, I asked the lady the HR lady and she seemed young. So she said sorry I can't tell you why you failed.

I was like then how would I know what to fix and how to better myself.

I kept contacting her e-mailing her until she got annoyed. I at that point gave up on getting the job but I was curious as how I failed the exam and wanted to know what they expect from me.

so anyways the lady talked with the IT guy and she told me that my code wasn't secure and it didn't prevent duplicated records int he database.

so, I go thanks, then I made the corrected changes to my code. Submitted it and found out that lady in HR got fired because of me. I then passed the exam. Got the job had the job for 2 years then got laid off.

their exams they won't tell you exactly what they want.

they would tell you make me this and then watch your programming habits, they expect you to make sure your code prevents anyone to hack it, and make sure that duplicates of data or information dosen't occur the database.

also, they want the code written neatly and using standards.

if your going to hash something you better use md5. If you use your own method they will not want you.

Their not looking for someone to write their own custom code they want you to write code that follows standards so other programmers can read and understand what your code does.

So, I haven't been working in the force for a while.
Currently unemployed... looking for work in accounting.

I had a few semesters in a university college. Currently financial aid is giving me a hassle due to limited funds they have. So, I don't have winter semester since I didn't get my aid in time. I paid $5,000 last semester which was fall semester. took classes like business international relations... where they basically taught me that china is a different culture then the U.S. I thought that class was a waste of time and money. didn't learn anything new... just the Chinese word quanchee meaning  connections. professor always said in china the Chinese always has a saying your nothing without quanchee meaning connections.

So, hope I answer your question...

my response in short was programmers need to know how to use a programming language using variables, if statements, switches, how to store data and connect to a database.

this is for web programming with software developing jobs you need to know how to code in c++ or a programming language that allows you to write programs for an OS,  you must know how to write the programs for Windows because windows is widely it also pays off to learn how to write the code for linux OS's it would give you that edge where if everyone that applied for that job only knows how to code in windows and you know how to code in windows and linux you would have that edge over everyone.

but they be looking closly to your skills in windows and experience. Since their programs will run on windows OS and yet if you know linux then they might be open to writing some programs for linus OS.

like look overall how they can use you for their company.

the more skills and knowledge and experience you have the better odds you will get the job you applied for or wanted.

---

