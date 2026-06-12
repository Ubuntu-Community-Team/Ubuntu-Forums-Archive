---
title: "teaching c programming"
date: 2007-09-12
forum: Programming Talk
---

### Post by mitchi on 2007-09-12
I'm teaching introductory programming using the c language with gcc. so far, we have discussed logic formulation and flowcharting. we are currently learning basic c language codes. 

> 
printf
scanf
if
if-else
if-else if
case-switch
for
while
do-while
arrays
functions


i personally have learned this with borland turboc, and teaching this in linux is quite a challenge because i'm still new. if you've seen my other posts, it's all about how-to operate such codes.

Can anyone tip me how my class can excel in this field of programming? maybe a few thoughts on how i should enhance/upgrade the level of coding, since my training was purely basic.

thank you.

---

### Post by ubuntukerala1980 on 2007-09-12
Try to use 
vi  or emacs or nano editor
It will help you a lot.:guitar:
But if u want IDE use kdevelop

---

### Post by fct on 2007-09-12
Dedicate a lesson to best practices, or explain them during the class, for example:

Proper commenting and formatting of the code.
Use of advanced debuggers to detect memory errors (valgrind).
Avoiding circular dependencies in libraries using #ifndef
Writting portable code.
Writting secure code (example: fgets instead of gets).
The output of -Wall in gcc is not to be understimated.
etc.

This is a nice read on that topic:

[http://www.ibm.com/developerworks/aix/library/au-hook_duttaC.html](http://www.ibm.com/developerworks/aix/library/au-hook_duttaC.html)

---

### Post by chewearn on 2007-09-12
There has to be a chapter on pointers.  It's not c if there is no pointer.

---

### Post by Lux Perpetua on 2007-09-12
I think the thing that helped me most when I was learning C was just a slew of interesting assignments, so I'd suggest giving some thought to the programming assignments you're going to give your students.

---

### Post by pmasiar on 2007-09-12
teaching introduction to programming in C is slightly less evil than in C++, but you can see that you miss slick and simple IDE like TurboC was. 

I don't know how old your students are and if you can change language, but just to give you idea: 
for young students (and on Windows), **the** best intro is [http://en.wikipedia.org/wiki/Game_maker](http://en.wikipedia.org/wiki/Game_maker) - GUI-only (no code needed, icons only) IDE for games. Very neat.
for older students, [MIT uses Python](http://www.pythonthreads.com/news/latest/python-is-very-powerful,-very-clear-and-easy-to-learn-for-students.html) - with the book.

Please no flamewars, I like C, C is excellent **second** language to learn, but not first.

---

### Post by LaRoza on 2007-09-12
> **pmasiar said:**
> 
Please no flamewars, I like C, C is excellent **second** language to learn, but not first.

Possibly agree, but sometimes the instructor has little control over the course, so assume he is being forced :D.

---

### Post by pmasiar on 2007-09-12
Well, she still may **some** control over it, and arguing "let's do what MIT does" could hive her some leverage :-) Let's wait patiently for answer from OP

---

### Post by CptPicard on 2007-09-12
I am just slightly disturbed by the question, as it gives me the impression the OP has started having problems with these "codes" moving to Linux... but they *are* all totally standard.. :)

Using gcc from command line isn't tough on an elementary level.

---

### Post by mitchi on 2007-09-12
from my point of view, C language is the foundation of all programming languages. That's why we, teach it. Here in the Philippines, open source technology is still new, and trying to equip the students the tools they need to develop and help the demands of the world.

we are catering this to college students(16-24 yrs old average), of which are still not fully convinced about open source tech, but hopefully, we would be able to enlighten their minds and equip them to be competitive in their respective career paths.

Personally, im in search, how would these kids compete with other developers learning under proprietary software?

teaching just the basics of C is manageable, but dealing with more complex systems is still unknown.

BTW im a he, not a she... thanks...

---

### Post by fct on 2007-09-12
Then I guess it would be in their best interest to find an open source project to get involved with.

That way they can get acquainted with code programmed by people with more experience, learn from them and build up their curriculum with the collaborations.

---

### Post by LaRoza on 2007-09-12
> **mitchi said:**
> 
Personally, im in search, how would these kids compete with other developers learning under proprietary software?

teaching just the basics of C is manageable, but dealing with more complex systems is still unknown.


It shouldn't make a difference, especially for C, which is very portable. Teach Ansii C and if the students need to know specific API's, they can teach themselves, which is what programmers do.

---

### Post by pmasiar on 2007-09-12
> **mitchi said:**
> C language is the foundation of all programming languages. That's why we, teach it. 

No doubts abot that. Question is: Is it the best way to introduce students to basics of programming? You may know something MIT professor is missing :-)

> Here in the Philippines, open source technology is still new, and trying to equip the students the tools they need to develop and help the demands of the world.

You can teach basics of Python in 3 months, and after that show how different syntax is used to accomplish same results. My point is that with Python, almost everything is simpler and more obvious.

> equip them to be competitive in their respective career paths.

IMHO students are better of learning fundamental concepts, especially in CompSci: there is still no single language to rule them all, and changes are the only constant.

> teaching just the basics of C is manageable, but dealing with more complex systems is still unknown.

Python is **simpler** than  C. Much simpler.

> BTW im a he, not a she... thanks...

No offense. People use generic "he", so I decided to use generic "she" sometimes. I don't want any occasional female reader to think she is not welcome here.

---

### Post by CptPicard on 2007-09-12
> **pmasiar said:**
> 
I don't want any occasional female reader to think she is not welcome here.

What are these "females" you speak of? :confused:

---

### Post by LaRoza on 2007-09-12
> **CptPicard said:**
> What are these "females" you speak of? :confused:

A foreign and fascination species, yet mostly theory for (male) programmers/geeks: [Woman]("http://en.wikipedia.org/wiki/Women") :D

---

### Post by mitchi on 2007-09-12
the intention  of teaching phyton is good, but in this country,  the demand is a solid ground on c programming(strictly).

---

### Post by pmasiar on 2007-09-12
> **CptPicard said:**
> What are these "females" you speak of? :confused:

> **LaRoza said:**
> A foreign and fascination species, yet mostly theory for (male) programmers/geeks: [Woman]("http://en.wikipedia.org/wiki/Women") :D

Not **those**. I was thinking about devChix, like [here](http://www.devchix.com/2007/06/09/let%e2%80%99s-all-evolve-past-this-the-barriers-women-face-in-tech-communities/) or [here](http://www.devchix.com/2007/06/15/is-there-a-hierarchy-in-online-communities/). I do hope some are around, and first link would explain why they are not loud about it. Interesting read BTW.

---

### Post by CptPicard on 2007-09-12
Oh. Thanks for enlightening me. Are these the same things with last names such as "gif" and "jpg" that are all around the net? I mean I do realize I'm more of a theorist... perhaps I should get out of my chamber every now and then.

> **pmasiar said:**
>  I do hope some are around, and first link would explain why they are not loud about it. Interesting read BTW.

Hmm. I wonder if they would be interested in my continuation getting all functional with their closures... :-k

---

### Post by pmasiar on 2007-09-12
> **CptPicard said:**
> Hmm. I wonder if they would be interested in my continuation getting all functional with their closures... :-k

I might be wrong of course, but I think that the first link explained why **not**.

---

### Post by CptPicard on 2007-09-12
OT and jokes aside, I find devchix's ideas interesting, but also slightly prejudiced against the "male culture" in a dogmatic feminism sense... I really do not think we are such ego-size-comparing cavemen who are incapable of rational discourse.

Women have their own group dynamics problems, they just happen to be under the surface.. they are capable of turning everything into a little sociological game of popularity contest, where the losers can be treated quite viciously even though you can't neccessarily see it straight away. Even on the school yard, the nastiest, most creative bullies are girls.

I honestly prefer the male style of discourse you find on tech forums. Instead of some consensus reality building, you let the issues duke it out openly and honestly, and take it like a man if you're left gathering your teeth off the pavement. It's nothing personal if your idea provably sucks, but apparently women just insist on taking it personally. 

Destructive criticism is occasionally healthy, as it cuts away the crap as efficiently as possible. It spares my time, and even the time of that person who was wrong in the first place. There *is* supposed to be an objective reality out there in most issues, right?

And besides, whenever you mix genders anywhere, you are going to get a bit of flirting. I don't think it is a bad thing; it's a way of complimenting the other person. Desperation is another thing :) I for one wouldn't mind being dragged away from the keyboard by some geek girls for Death by Snu-Snu... I can't see what is so bad with that ;)

---

### Post by bigboy_pdb on 2007-09-12
The sex of the person is irrelevant with respect to the question. Anyone who's worried about offending people or being correct can use "he/she" or "he or she". The person is not teaching a women's class on computers so the rest is irrelevant. Let's please get back on subject.

> **CptPicard said:**
> 
I am just slightly disturbed by the question, as it gives me the impression the OP has started having problems with these "codes" moving to Linux... but they *are* all totally standard.. :)


I agree with this. There shouldn't be any problems moving from C with a TurboC compiler to C with a GNU compiler unless the libraries that you're using aren't standard libraries, or TurboC wasn't created based on ANSI standards (which I'm assuming that it is).

In addition to what you're teaching, I agree with the people who are stating that there is more that should be taught than what is on your list. From your statement that your students learned about flow charts and some other things, there is an implication that they might be doing more than learning about C and it is also possible that they'll learn these things in other classes, but it doesn't hurt to mention some other subjects of importance. Programming practices, debugging, handling errors, pointers and references, file input/output, and memory management should be taught as well. Also, even though the language makes a difference (because of issues with syntax, memory management, whether or not objects can be used, and differences between dynamic and static languages), programming practices and fundamentals are more important than the programming language. Mathematics, proofs, logic, and computational theories are also incredibly useful.

If your problems with switching languages are mainly due to differences in libraries (such as those that correspond to creating GUIs) then perhaps it would be best to focus on programming from the command line.

For free resources you might want to look at the following thread (the formatting is awful but the links are good):
[http://ubuntuforums.org/showthread.php?t=255970](http://ubuntuforums.org/showthread.php?t=255970)

---

