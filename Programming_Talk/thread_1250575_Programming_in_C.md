---
title: "Programming in C?"
date: 2009-08-26
forum: Programming Talk
---

### Post by NinjaNumberNine on 2009-08-26
Hi, I have used Ubuntu for 5 years but am still a complete noob when it comes to programming. So I decided to learn C. I still am not sure what is the best programming language, (but C is one one with the easiest name to remember) :) Anyway, I have read several manuals on  programming in C, but I have never been good at "compiling" manual information in my head, and I would much rather be free to ask questions as I go, thus this thread.:lol: (so for any of you viewers who are looking for a tutorial, this isn't one :)) I really want to learn for game-creating purposes, namely 2d side-scrollers like SuperTux. I have one in mind with some art already drawn up for a game described thus: "BioTux" in which Tux is a legendary hero who vanishes into a freezing sea in the legend and wakes up in the real world centuries later to find everything covered in lush rainforests and jungle. Feeling somewhat like Rip Van Winkle, our hero wanders out to explore the surroundings. The first thing he notices is that he is not alone- the forest is full of creatures- some more friendly than others...
 The first person he meets is a little dwarf named Mogle, who tells him that in order to find his forgotten history (and perhaps his legendary bride as well) he must locate the wizard Korlani. Thus Tux, (now BioTux,)  ventures forth on this quest, fighting bad guys, racing forest fires, and finally, if all goes well, will get his forgotten legend(and maybe his forgotten bride) back. :lolflag: Ok, ok, I got a little carried away.  But anyway, I want to learn how to program, and any suggestions as to what language to use, and where to start, would be well appreciated.


 Thanks!


    -NinjaNumberNine

---

### Post by Mirge on 2009-08-26
If you're set on C, then have at it... many people around here recommend [Python]("http://www.python.org/") as a first language. It is extremely easy to pick up and start seeing immediate results with.

External libraries are plentiful it seems and for your specific project, you'd probably want to look into [Pygame]("http://www.pygame.org/wiki/FrequentlyAskedQuestions").

---

### Post by NinjaNumberNine on 2009-08-26
I am not really set on C- I want the best for my purpose. I have tried pygame, but I never found an actual program "pygame". Could you explain what pygame is, please? I have read manual for python, too. :)

---

### Post by Mirge on 2009-08-26
> **NinjaNumberNine said:**
> I am not really set on C- I want the best for my purpose. I have tried pygame, but I never found an actual program "pygame". Could you explain what pygame is, please? I have read manual for python, too. :)

This should help: [http://www.pygame.org/docs/](http://www.pygame.org/docs/) :)

---

### Post by NinjaNumberNine on 2009-08-26
I found and installed the executable from the ubuntu repos. :)
How do I start pygame? It is not in any of the program menus.
like, say, type pygame in terminal?
```
ninja@PromisedFreedom:~$ pygame
bash: pygame: command not found
ninja@PromisedFreedom:~$
```

---

### Post by Can+~ on 2009-08-26
pygame is a *library* that you load to python to do that stuff, not a standalone program.

---

### Post by NinjaNumberNine on 2009-08-26
> **Can+~ said:**
> pygame is a *library* that you load to python to do that stuff, not a standalone program.
So what do I use as a program creator/editor? :confused:

---

### Post by exutable on 2009-08-26
Like for example you would load the pygame library into your "BioTux" and then you would use a lot of the classes, methods etc. to achieve what you want.

It's basically a means for using somebody else's python code so you don't have to rewrite something, that somebody already wrote(possibly better).

Regardless though, you'll still need to know Python

---

### Post by NinjaNumberNine on 2009-08-26
> Like for example you would load the pygame library into your "BioTux"
 You mean my BioTux art directory? I have not done any thing as far as programming goes for BioTux, that is for future when I learn out how to program. :)

---

### Post by NinjaNumberNine on 2009-08-26
> Regardless though, you'll still need to know Pythonwhere can I learn? I am kind of tired of reading the manuals, thats why I came here.;)

I don't even really know how to compile pygame.

---

### Post by exutable on 2009-08-26
Well first of all there is a sticky on the forum of where to learn but I would recommend picking up a book on amazon.

Reading on the internet can get very monotonous and tiring.

---

### Post by NinjaNumberNine on 2009-08-26
> I would recommend picking up a book on amazon.
Sorry, no can do. I am just 14 and I don't have a bank account and such things. :lolflag:
What sticky, though? And is it for compiling or learning how to program?

---

### Post by exutable on 2009-08-26
[http://ubuntuforums.org/showthread.php?t=1006666]("http://ubuntuforums.org/showthread.php?t=1006666"), and just ask your parents or go to a bookstore.  That's what I did when I was 14 and wanted programming books.

---

### Post by NinjaNumberNine on 2009-08-26
TY, followed your link and found this: [http://ubuntuforums.org/showthread.php?t=648909](http://ubuntuforums.org/showthread.php?t=648909)
whaddayaknow, a fellow 14yr old! :lolflag:

---

### Post by NinjaNumberNine on 2009-08-26
>  and just ask your parents or go to a bookstore.  That's what I did when I was 14 and wanted programming books.
That would be suicide. We have a family of 10 and everything is always busy- I'm about the only one interested in linux or programming, anyway. :)

---

### Post by Mirge on 2009-08-26
> **NinjaNumberNine said:**
> That would be suicide. We have a family of 10 and everything is always busy- I'm about the only one interested in linux or programming, anyway. :)

Can't hurt to ask... it'll let them know that you really are interested in the field.

---

### Post by Can+~ on 2009-08-26
And don't go with "Some guy on the internet told me to", it would sound weird. Really, really, weird.

But you can do fine with [Python doc]("http://docs.python.org/tutorial/").

---

### Post by hessiess on 2009-08-26
This ebook is good:

[http://www.freenetpages.co.uk/hp/alan.gauld/](http://www.freenetpages.co.uk/hp/alan.gauld/).

---

### Post by nvteighen on 2009-08-27
Hm... Before trying to learn how to write a game, which is a pretty difficult thing (not because of its conceptual hardness, but because you have to deal with a lot of stuff), you should first focus on learning how to program, what program is and what areas there are besides games.

Python is possibly the best current choice for an absolute beginner... Why don't you look at Python's official tutorial? You don't even need internet. Do the following in a Terminal:

```

sudo aptitude install python-doc devhelper

```

Then, go to Applications->Programming->Devhelper and choose Python Tutorial. There you have it! (Devhelper is also useful for other documentation packages)

But asking your parents wouldn't hurt. Maybe they won't buy it to you now, but maybe for Christmas/Hannukah/(whatever), birthday or something.

---

### Post by Wim Sturkenboom on 2009-08-27
> **NinjaNumberNine said:**
> That would be suicide. We have a family of 10 and everything is always busy- I'm about the only one interested in linux or programming, anyway. :)Birthday present, christmas present, ...
Or save up from your pocket money (might take a while).

If you've set your heart to it, you can do it.

---

### Post by koonsolo on 2009-08-27
Python and pygame are indeed a good way to get started. I'm personally making commercial games using python and pygame (see my signature link).

Because you haven't programmed before, you should start by programming some text-only games, like for example a number guessing game. Then you can see what other games you're able to make with only text (text adventure?). After you know how to do these things, I suggest you take a look at pygame like others said earlier. But first you need to get to know the absolute basics, and that is just programming in python with text based in and output.

---

### Post by NinjaNumberNine on 2009-08-27
Not Jewish, nor Freemason, Christian. So it would be Christmas with me. :) But I don't mind reading off the internet- (and you can usually download a pdf if you know how to google.) And for the devhelper thing, got an error message saying ```
ninja@FreedomPC:~$ sudo aptitude install python-doc devhelper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Couldn't find any package whose name or description matched "devhelper"
Couldn't find any package whose name or description matched "devhelper"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

ninja@FreedomPC:~$ 
```  so that didn't turn out.. :(
I do want a good tutorial, haven't checked the ebook yet, just turned on my computer again. Any suggestions on how to get the python docs thing working would be greatly appreciated. Thanks!

---

### Post by NinjaNumberNine on 2009-08-27
Extra info: I have Xubuntu right now, just assumed the Ubuntu would draw more attention because its more popular. 
Also, does anyone have any experience in DrPython?
And Koonsolo, how can you program a TEXT adventure game?

---

### Post by Mirge on 2009-08-27
[http://docs.python.org/3.1/tutorial/index.html](http://docs.python.org/3.1/tutorial/index.html)

---

### Post by NinjaNumberNine on 2009-08-27
All of these tutorials use the "hello, world" phrase but it seems like it wants me to print something. I don't have a printer though. Can someone do up a couple lines of code for me so I can see what the format looks like? All of the spacing, "<,>,/,|,[,],{,},(,)," is kind of confusing. For example how would you tell a program to load, lets use mplayer in this example, and play a certain file for 4 minutes or until the file is finished playing, then exit?
:)

---

### Post by grayrainbow on 2009-08-27
[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)
It can be as much low level as C, and as much object oriented as everything else(no wonder that's what profesionals use, when they understand OOP model). The biggest advantage of learning low level lenguage as your first is that you not just learn syntax, you actualy learn to program.
Good luck :)

---

### Post by Mirge on 2009-08-27
> **NinjaNumberNine said:**
> All of these tutorials use the "hello, world" phrase but it seems like it wants me to print something. I don't have a printer though. Can someone do up a couple lines of code for me so I can see what the format looks like? All of the spacing, "<,>,/,|,[,],{,},(,)," is kind of confusing. For example how would you tell a program to load, lets use mplayer in this example, and play a certain file for 4 minutes or until the file is finished playing, then exit?
:)

You need to actually learn Python (or whatever language you pick) basics before you try to do something more complicated.

I don't recommend learning C as your first language. You'll spend more time re-inventing the wheel than actually programming something useful. I'm all for people learning C, just not as a first language.

---

### Post by NinjaNumberNine on 2009-08-27
> You need to actually learn Python (or whatever language you pick) basics before you try to do something more complicated. I know, I just wanted to see what I was getting into. :)
> 
I don't recommend learning C as your first language. You'll spend more time re-inventing the wheel than actually programming something useful. I'm all for people learning C, just not as a first language. Right. I'm going for python first.

---

### Post by nvteighen on 2009-08-27
> **NinjaNumberNine said:**
> ...
And for the devhelper thing, got an error message saying ```
ninja@FreedomPC:~$ sudo aptitude install python-doc devhelper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Couldn't find any package whose name or description matched "devhelper"
Couldn't find any package whose name or description matched "devhelper"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

ninja@FreedomPC:~$ 
```  so that didn't turn out.. :(


Because I'm an idiot :P

It's **devhelp**... Sorry!

---

### Post by NinjaNumberNine on 2009-08-27
> Because I'm an idiot :razz:???

OK I got it installed and now I'm reading it. Thanks!

(btw check [this link]("http://www.thefreelibrary.com/The+evil+eye:+the+occult+symbol+chosen+for+the+Orwellian+Information...-a097422815") out.)

---

### Post by Can+~ on 2009-08-27
> **NinjaNumberNine said:**
> ???
(btw check [this link]("http://www.thefreelibrary.com/The+evil+eye:+the+occult+symbol+chosen+for+the+Orwellian+Information...-a097422815") out.)

Sounds like someone read too much Dan Brown.

---

### Post by NinjaNumberNine on 2009-08-27
> **Can+~ said:**
> Sounds like someone read too much Dan Brown.
Never heard of him. :lolflag:

---

### Post by Mirge on 2009-08-27
The official tutorials for various versions of Python seem fine to me. I gave a link a while ago.

---

### Post by NinjaNumberNine on 2009-08-27
> The official tutorials for various versions of Python seem fine to me. I gave a link a while ago. Oh, they are good. its just that most young people like me are *lazy* and would rather let someone tell them how to do it step by step than read a fat manual. :mrgreen:

---

### Post by NinjaNumberNine on 2009-08-27
Here's all of them together: ( I had to type all of the locations and links for the last ones because there is not a list anywhere else. That took time, and the first time firefox crashed so I lost the first 20 links I had typed, and decided to take it in steps. I'm calling a mod to delete the other ones now) 
Anyway, I hope this helps another beginner!
[Tutorial 1]("http://www.howcast.com/videos/200423-Python-Programming-Tutorial-1-Installing-Python")
[Tutorial 2]("http://www.howcast.com/videos/200300-Python-Programming-Tutorial-2-Numbers-and-Math")
[Tutorial 3]("http://www.howcast.com/videos/200353-Python-Programming-Tutorial-3-Variables")
[Tutorial 4]("http://www.howcast.com/videos/200343-Python-Programming-Tutorial-4-Modules-and-Functions")
[Tutorial 5]("http://www.youtube.com/watch?v=-lfWzPxOJQ8") (this one was on youtube instead for some reason)
[Tutorial 6]("http://www.howcast.com/videos/200378-Python-Programming-Tutorial-6-Strings")
[Tutorial 7]("http://www.howcast.com/videos/200362-Python-Programming-Tutorial-7-More-on-Strings")
[Tutorial 8]("http://www.howcast.com/videos/200450-Python-Programming-Tutorial-8-Raw-Input")
[Tutorial 9]("http://www.howcast.com/videos/200406-Python-Programming-Tutorial-9-Sequences-and-Lists")
[Tutorial 10]("http://www.howcast.com/videos/200364-Python-Programming-Tutorial-10-Slicing")
[Tutorial 11]("http://www.howcast.com/videos/200322-Python-Programming-Tutorial-11-Editing-Sequences")
[Tutorial 12]("http://www.howcast.com/videos/200358-Python-Programming-Tutorial-12-More-List-Functions")
[Tutorial 13]("http://www.howcast.com/videos/200374-Python-Programming-Tutorial-13-Slicing-Lists")
[Tutorial 14]("http://www.howcast.com/videos/200350-Python-Programming-Tutorial-14-Intro-To-Methods")
[Tutorial 15]("http://www.howcast.com/videos/200389-Python-Programming-Tutorial-15-More-Methods") bad link, sorry!
[Tutorial 16]("http://www.howcast.com/videos/200397-Python-Programming-Tutorial-16-Sort-and-Tuples")
[Tutorial 17]("http://www.howcast.com/videos/200451-Python-Programming-Tutorial-17-Strings-N-Stuff")
[Tutorial 18]("http://www.howcast.com/videos/200366-Python-Programming-Tutorial-18-Cool-String-Methods")
[Tutorial 19]("http://www.howcast.com/videos/200367-Python-Programming-Tutorial-19-Dictionary")
[Tutorial 20]("http://www.howcast.com/videos/200455-Python-Programming-Tutorial-20-If-Statement")
[Tutorial 21]("http://www.howcast.com/videos/200458-Python-Programming-Tutorial-21-Else-and-Elif")
 [Tutorial 22]("http://www.howcast.com/videos/200506-Python-Programming-Tutorial-22-Nesting-Statements")
 [Tutorial 23]("http://www.howcast.com/videos/200503-Python-Programming-Tutorial-23-Comparison-Operators")
 [Tutorial 24]("http://www.howcast.com/videos/200486-Python-Programming-Tutorial-24-and-and-or")
 [Tutorial 25]("http://www.howcast.com/videos/200461-Python-Programming-Tutorial-25-For-and-While-Loops")
 [Tutorial 26]("http://www.howcast.com/videos/200473-Python-Programming-Tutorial-26-Infinite-Loops-and-Break")
 [Tutorial 27]("http://www.howcast.com/videos/200480-Python-Programming-Tutorial-27-Building-Functions")
 [Tutorial 28]("http://www.howcast.com/videos/200553-Python-Programming-Tutorial-28-Default-Parameters")
 [Tutorial 29]("http://www.howcast.com/videos/200520-Python-Programming-Tutorial-29-Multiple-Parameters")
 [Tutorial 30]("http://www.howcast.com/videos/200475-Python-Programming-Tutorial-30-Parameter-Types")
 [Tutorial 31]("http://www.howcast.com/videos/200625-Python-Programming-Tutorial-31-Tuples-As-Parameters")
 [Tutorial 32]("http://www.howcast.com/videos/200424-Python-Programming-Tutorial-32-Object-Oriented-Program")
[Tutorial 33]("http://www.howcast.com/videos/200414-Python-Programming-Tutorial-33-Classes-and-Self")
[Tutorial 34]("http://www.howcast.com/videos/200629-Python-Programming-Tutorial-34-Subclasses-Superclasses")
[Tutorial 35]("http://www.howcast.com/videos/200582-Python-Programming-Tutorial-35-Overwrite-Variable-on-Sub")
[Tutorial 36]("http://www.howcast.com/videos/200637-Python-Programming-Tutorial-36-Multiple-Parent-Classes")
[Tutorial 37]("http://www.howcast.com/videos/200578-Python-Programming-Tutorial-37-Constructors")
[Tutorial 38]("http://www.howcast.com/videos/200563-Python-Programming-Tutorial-38-Import-Modules")
[Tutorial 39]("http://www.howcast.com/videos/200576-Python-Programming-Tutorial-39-Reload-Modules")
[Tutorial 40]("http://www.howcast.com/videos/200591-Python-Programming-Tutorial-40-Getting-Module-Info")
[Tutorial 41]("http://www.howcast.com/videos/200474-Python-Programming-Tutorial-41-Working-With-Files")
[Tutorial 42]("http://www.howcast.com/videos/200583-Python-Programming-Tutorial-42-Reading-and-Writing")
[Tutorial 43]("http://www.howcast.com/videos/200523-Python-Programming-Tutorial-43-Writing-Lines")
[Tutorial 44]("http://www.howcast.com/videos/200386-Python-Programming-Tutorial-44-Installing-WxPython")

---

### Post by nvteighen on 2009-08-28
> **NinjaNumberNine said:**
> 
(btw check [this link]("http://www.thefreelibrary.com/The+evil+eye:+the+occult+symbol+chosen+for+the+Orwellian+Information...-a097422815") out.)

I am part of the Order of the Sacred Lambda. Our mission is to show the world the power of the highest abstraction level programming, free those who are enslaved by the Mighty Pointer and teach the Gospels of John McCarthy, Eric S. Raymond and Paul Graham. :P

Actually, the Illuminati were at start a Freemason lodge. And the "Evil Eye" is actually a millenary religious symbol called the "Eye of Providence" adopted by the Freemasons. [http://en.wikipedia.org/wiki/Eye_of_Providence](http://en.wikipedia.org/wiki/Eye_of_Providence)

---

### Post by Drone022 on 2009-08-28
> I am part of the Order of the Sacred Lambda. 

I notice your also a keen Lisper. [A man who is not happy about Lisp including the Lambda letter in its logo]("http://xahlee.org/UnixResource_dir/lambda_logo.html").

> I love these lambda-featuring logos. However, i have a complaint. As most of you know, lisp languages are not purely functional languages. Subroutines in lisps easily have side-effects, and sometimes non-functional programing methodologies such as OOP are actually encouraged in lisp. As most of you know, the lambda symbol chosen by functional languages is to signify no side-effects. In this respect, i find the lisp languages not totally deserving the use of lambda in their logo. As i have expressed before, mathematical symbols are not to be trifled with, and the Schemers have tainted my mathematics, strictly speaking.

Although i have this minor objection with lispers using the lambda symbol, but overall i think the lispers and i share a more important common goal. That is, to kill all imperative programing ignoramuses of the world. Once the unix and C and Perl and otherwise idiots are all dead, then i'll formally raise my objection about Lisper's unfit borrowing of the lambda symbol.

(PS In America, imperative language programers are such not because they prefer such methodology, but because they know ****.)



In general I also like logos featuring lambda and other greek letters used in maths/science.

---

### Post by NinjaNumberNine on 2009-08-28
Aww man, my thread is turning occultic...

Must defeat the evil bad guys! They are [[COLOR=Red]_everywhere_[/COLOR]]("http://www.youtube.com/watch?v=H8NStD5qD5g")! :lolflag:

---

### Post by NinjaNumberNine on 2009-08-28
BTW One of the first languages I learned was the Greek. I have written pages in it, and it is a fun language, but like some programming languages, it lacks words that English sports. The alphabet took me about an hour to memorize: Alpha, beta, gamma, delta, epsilon, zeta, eta, theta, iota, kappa, lambda, mu, nu, xi, omicron, pi, rho, sigma, tau, upsilon, phi, chi, psi, omega.  Lambda has no significance as a letter or symbol. the organization must be very secret if there is one, cause google cant even find it. 8-)

---

### Post by nvteighen on 2009-08-28
Well, yeah... Curiously uppercase Epsilon had more mystical significance in Greek, as the Delphi Oracle had one at the entrance (just above the famous &#947;&#957;&#8182;&#952;&#953; &#963;&#945;&#8016;&#964;&#972;&#957; "Know yourself" inscription) and nobody knew what it stood for even at those times.

---

### Post by NinjaNumberNine on 2009-08-28
Okay everybody I am now officially banning any material that does not have significant connection with programming. :-#
That includes myself as well, the thread was getting out of hand... __8-[__8-[__8-[__

---

### Post by raydeen on 2009-08-29
I always recommend these two ebooks for beginning Python'ers:

[http://www.briggs.net.nz/log/writing/snake-wrangling-for-kids/](http://www.briggs.net.nz/log/writing/snake-wrangling-for-kids/)

[http://pythonbook.coffeeghost.net/book1/index.html](http://pythonbook.coffeeghost.net/book1/index.html)

I'm a newbie as well (40 year old newbie) and these books, especially the second one are very reminiscent of the computer magazines I used to buy when I was 14. They'd have programs in them that you could type in and run and that provided some of the best education I ever had in programming. Hope these help you. I wanna play BIOTux. :)

---

### Post by NinjaNumberNine on 2009-08-29
> **raydeen said:**
> I wanna play BIOTux. :)
So do I- thats why I'm here! :lolflag:

Those e-books are great, thanks! :)
For some reason I could not download the snake wrangling one, though.

---

