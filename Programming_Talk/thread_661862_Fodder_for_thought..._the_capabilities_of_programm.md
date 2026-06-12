---
title: "Fodder for thought... the capabilities of programmers"
date: 2008-01-08
forum: Programming Talk
---

### Post by dwhitney67 on 2008-01-08
I was emailed the article below.  I thought it was interesting enough to share with other s/w developers and those inspiring to be:

*jfmiller call to our attention two professors emeritus of computer science at New York University who have penned an article titled Computer Science Education: Where Are the Software Engineers of Tomorrow? in which they berate their university, and others, for not teaching solid languages like C, C++, Lisp, and ADA. The submitter wonders whether any CS students or professors would care to respond. Quoting the article: "The resulting set of skills [from today's educational practices] is insufficient for today's software industry (in particular for safety and security purposes) and, unfortunately, matches well what the outsourcing industry can offer. We are training easily replaceable professionals... Java programming courses did not prepare our students for the first course in systems, much less for more advanced ones. Students found it hard to write programs that did not have a graphic interface, had no feeling for the relationship between the source program and what the hardware would actually do, and (most damaging) did not understand the semantics of pointers at all, which made the use of C in systems programming very challenging."*

P.S.  I have no idea who is 'jfmiller'.

---

### Post by bobrocks on 2008-01-08
[B]--edit--
I feel an overwhelming need to edit this post to add some cautionary advice.

Slashdot is not such a family friendly article discussion site.  The comments can contain strong language and just plain abuse.  They do go for the freedom of speech thing over there and let the moderating be done by users modding bad posts down so they aren't visible.

There is also a tendency to hide very dodgy links within google "I'm feeling lucky" links and tinyurl links, I wont explain what the dodgy stuff is but be warned not to trust any old links that are on there.

--/edit--[/B]

This is one of the big topics today on Slashdot.

I tend to pick one article a day on slashdot to read, today it was this one.  jfmiller is a user on slashdot who submitted the article I believe.

[http://www.stsc.hill.af.mil/CrossTalk/2008/01/0801DewarSchonberg.html](http://www.stsc.hill.af.mil/CrossTalk/2008/01/0801DewarSchonberg.html) - is the full story

[http://developers.slashdot.org/article.pl?sid=08/01/08/0348239&from=rss](http://developers.slashdot.org/article.pl?sid=08/01/08/0348239&from=rss) - is the slashdot story with comments

---

### Post by lvleph on 2008-01-08
I don't even know how to program a graphic interface. My university's (University of Nevada, Reno) first programming courses were c++. In fact, I don't remember seeing a java course in the CS department. I did see it taught in some engineering courses. I am a Mathematician and not a Programmer, so I have not used pointers often, but I believe I could still use them if needed.

I have noticed that at other Universities the intro courses were not C++ and I thought that was quite stupid. I have heard plenty of people claim that intro courses should be Java, because it does all the OOP for you without much thought. But, how is that a benefit for someone just learning?

---

### Post by pmasiar on 2008-01-08
I just finished reading great (and long) [talk with Alan Kay](http://acmqueue.com/modules.php?name=Content&pa=showpage&pid=273), one of the most brilliant CompSci. 

He compares SmallTalk with Java, Lisp, explains his theory why instead of computer science we have computer pop culture (Basic and Java being prime examples), and how CompSci education todays is often just Java vocation training with no science at all.

Prime example (in other thread) poster does not grok difference between "int main()" and "void main()". Cargo cult programming indeed, copy-pasting recipes instead of understanding the stuff.

---

### Post by Lster on 2008-01-08
I mostly agree - I'm currently taking a computer science course at my college and we are tought BASIC and Java. No one, except me, on our course even knows pointers exist. Really I feel Python, C and Assembly would be a better start.

---

### Post by Wybiral on 2008-01-08
A solid understanding of C is a good thing to have, but I don't think most of us plan on being system programmers anyway. With that aside, I agree that there seem to be a large number of Java/VB "code monkeys" out there, but I don't think C is the solution or that we should all learn system programming. But we should certainly learn computer science along with our Java/VB in school!

---

### Post by dwhitney67 on 2008-01-08
I think the stance that the author's were taking is that the competence level of programmers in the US is falling.  With the decline in abilities, the US programmer faces extinction (or being made redundant) by programmers in developing countries where the cost of labor is less than in the US.

History has shown that the US was, and still is in some areas, at the forefront of developing new technologies.  However, if the computer engineers being churned out of universities haven't a clue or have never been exposed to s/w development at the system's level, then this opportunity will surely fall on those that have the experience; and the professors are arguing that those with the experience will not from the US, but from other countries.

Thus the article is favoring the notion that US universities need to reassess their educational curriculum so that better, more knowledgeable, engineers are produced.

I for one wholeheartedly agree.  There is more to CompSci than just picking up a book and studying a programming language.  Unfortunately this notion escapes most people's understanding, and we are left with discussions in which we quibble about minuscule little details about programming convention and style, whereas functionality and robustness of a design seem to come second.  This needs to be changed such that more credit is offered to the "engineer" and less is given to the simple programmer.

---

### Post by pmasiar on 2008-01-08
> 
...studying a programming language...

Better: studying a **syntax of given** programming language

Syntax is for code monkeys, and it is only remotely related to software engineering.

---

### Post by LaRoza on 2008-01-08
> **pmasiar said:**
> Better: studying a **syntax of given** programming language

Syntax is for code monkeys, and it is only remotely related to software engineering.

I agree.

I have said to the program director of the IT department at my school that the program is a bit lopsided. It teaches the "syntax" of Java, C++ and VB. He (the program director) agreed. He has been trying to get classes on algorithms and data structures added to the course and other such important programming classes.

I, and most others, can "learn" a language in a day, but learning how to use it takes years.

---

### Post by CptPicard on 2008-01-08
There's merit in something that is being said, but I think they still miss the point, and that there is an apples to oranges comparison here somewhere.

> **dwhitney67 said:**
> I think the stance that the author's were taking is that the competence level of programmers in the US is falling.  With the decline in abilities

What kind of abilities? Ability to specifically code close to the iron, or the ability to think of programs and the problems they are supposed to solve in the abstract?

> However, if the computer engineers being churned out of universities haven't a clue or have never been exposed to s/w development at the system's level

It's the engineer vs. computer scientist distinction. I feel that this gap is just going to broaden more and more the more we code on abstract machines -- after all, even the modern CPU is under the hood something completely different than the x86 it tries hard to masquerade itself as.

Not being able to code close to the iron might make you a bad engineer, but not neccessarily a bad computer scientist. Of course I am yet to meet a computer scientist who didn't at least know in principle what is going on inside that magical box of super-intelligent, computing hamsters...

My intro to programming class was in Java, but afterwards, we didn't really actually code much at all. If we did, implementation language was your choice as long as it wasn't something horribly esoteric. Grading actual programming projects is a boatload of work for TAs you know, and the benefit from making you type out a solution instead of describing it in an exam is questionable.

The typical way of actually getting your coding experience in my school was to go to work during summer. It was not something specifically taught -- that was not for university, it's for code monkey schools ;)

> I for one wholeheartedly agree.  There is more to CompSci than just picking up a book and studying a programming language.

Most of CompSci is completely language independent, except language design :) So this whole issue is slightly off topic, as there really is no point in complaining about the "wrong" language being taught...

---

### Post by happysmileman on 2008-01-08
Weird, in Ireland I've been looking at Comp Sci courses... Every single one of them teaches Java for the first year, then you continue using it in the second year, while also learning C++, then after that everything is C++... You also have to learn assembly (Motorola 68000 ASM or something, IIRC)

I'm surprised that any universitiy wouldn't teach C or C++, maybe the universities over here just take it more seriously because of the need for a lot of very experienced programmers.

---

### Post by CptPicard on 2008-01-08
> **happysmileman said:**
> 
I'm surprised that any universitiy wouldn't teach C or C++, maybe the universities over here just take it more seriously because of the need for a lot of very experienced programmers.

And I am honestly surprised that any university's *computer science* program would be so stuck on teaching actual programming languages.That's something I would expect in some more... uh.. "vocational" school.

When I went to school, there was an optional undergrad C class (easy credits for everyone who was serious about CS) and... I suppose this is hard to believe considering the tone of the thread -- no C++ class at all. There *was* a sort of OO design and methodology class using either Java or C++, but no specific "C++ the language" class.

I would not have had time for anything like that during my studies anyway, I was too busy hitting the books and lecture notes.

(Uni of Helsinki CS department in case someone wonders -- Torvalds is our alumnus and is a pretty damn good low-level coder...)

---

### Post by happysmileman on 2008-01-08
> **CptPicard said:**
> And I am honestly surprised that any university's *computer science* program would be so stuck on teaching actual programming languages.That's something I would expect in some more... uh.. "vocational" school.

Learning the languages is a very small amount of the course compared to the implementation and design and stuff, but they have to teach them a language of course, I think everyone agrees on that, and it's a lot easier in my opinion to learn about pointers and how memory is stored/allocated etc. in a language where I can physically see it happen, rather than just being told what happens and then going back to a language that you can never use it in.

So the extra effort going into teaching them C++ as well as Java is made up for it by the fact that they learn more about how this stuff really works.

Btw, this is based on what i've heard while speaking to students from universities here and from what I've read on internet and in the handouts about the university courses my school gave me, I don't actually go to university yet, so this is just my opinion on what I think it would be like, based on my experiences when I started to read about pointers etc.

---

### Post by DougB1958 on 2008-01-08
Interesting thread. I come to it from the "computer science professor" side of the room. A couple of thoughts, in no particular order...

As CptPicard and others said, focusing on languages misses most of the point of computer science. It's not about how to say things, it's about having things to say in the first place. In particular, it's about being able to conceptualize a problem and its algorithmic solutions, having a toolkit of algorithms and data structures with which to devise solutions, but also being able to design variations on those standard solutions that meet the needs of the specific problem (and, rarely, inventing a completely new solution), being able to compare both new and standard solutions on both theoretical and empirical grounds, etc. Maybe more than anything else, learning computer science is about becoming able to think and learn independently, so that you can keep up with the field as it evolves.

One also needs to be careful about the point of education. Even worse than being a professor, I'm also a professor at a liberal arts college, which means I have doubtless strange views on this subject :) It's certainly nice for people to come out of college prepared for a job, but there's a whole lot more that they ought to get out of their education too: a general ability to think effectively about the whole spectrum of issues they'll confront in the rest of their lives, an ability to communicate with people from all sorts of different backgrounds, an appreciation for the value of having an intellectually rich life, etc. So to my mind, arguments about the quality of computer science educational programs based on job preparation start off by missing half the point of any education.

Finally, it's no longer really possible to group all computing into "computer science." It's certainly meaningful to distinguish computer science from software engineering (not to mention IT, IS, etc.) as lots of colleges in the U.S. are starting to do. And on the engineering side, it's worth asking whether an undergraduate education should really be expected to produce fully qualified professional engineers, or whether some amount of graduate education is also called for (as in most other engineering disciplines). So a claim that education is failing to produce skilled software developers really ought to be framed in terms of software engineering education and all the still-being-resolved issues around what it should be and how it should be delivered.

---

### Post by pmasiar on 2008-01-08
And I think we need to distinguish very different kinds of "programmers"
- computer engineer (systems programmer): coding close to the metal
- software scientist: developing new ways/algorithms/languages/tools, comparing with existing, and making sense of it
- application developer: programming close to evil user, and whatever wretched model user has about the reality.
- web designer
- database administrator
- system administrator
- network engineer, etc

It is like medical doctors, there is difference between a cardiologist, an opthalmologist, a gynecologist and a dentist, even if all of them are MD and went to common premed school.

---

### Post by xtacocorex on 2008-01-09
I added a double major in Computer Science when I was in school and at the time, the intro to programming class was C++ and after that first year you delved into algorithms and didn't do much coding until your last year when you had the ability to take the computer graphics course.
 
This has changed a bit and they replaced C++ with Java.
 
Being an Aerospace Engineering major that liked coding, I added the extra major to help learn C++ (which I had done the semester before I added it) and I only learned about std::string and std::vector because everything else I had understood (we didn't get to pointers or OOP, that was the next class in the sequence). I also got a D in the C++ class even because the programs were rediculously lame, but in hindsight, they got you thinking outside of the box.
 
In the end, I dropped the extra major. I do know some really good CS majors from my university but I did see people in that intro to C++ class who were taking it their 3rd time because they could code but didn't care about the class.
 
I have no idea where I was going with this.

---

