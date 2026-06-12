---
title: "Suggestions on how to interest a Child in programming"
date: 2007-05-28
forum: Programming Talk
---

### Post by linuxaz on 2007-05-28
Hello fellow Ubuntu users,
I"ll keep this short, but up front, let me thank you for any responses.

My Son really likes modifying games  that are installed on his computer.  He also seems to be very interested in science and such, as he will design (if you will) new inventions and dream up ideas using Inkscape.  I feel that if I could get him interested in programming, that he  may like it.

Myself, I can use the command line with the help of internet searches, but programming in Python, C++, or using QT is slightly above me. 
With a whole summer vacation ahead of him, I want to provide the opportunity for him to learn some programming if it interests him.  Can anyone suggest a method, book, or website for a kid of 11 years old?

I remember learning to do simple things in Basic when I was about thirteen.  I never followed up on it, but I feel that if there had been the internet as we know it today, and the resources present, I may have.....
I want to try and provide an opportunity for him that would benefit him in the future.

Any suggestions are appreciated,

Thanks,

linuxaz

---

### Post by cward002 on 2007-05-28
There is a program called KPL (Kid's Programming Language). Although it is windows only you could possibly run it in wine. it is free to download.

[http://www.k-p-l.org/download.php](http://www.k-p-l.org/download.php)

Another possibility is Eclipse. It is an IDE which supports several different languages. It is available in the Ubuntu Repositories.

HTH

Colin

---

### Post by hod139 on 2007-05-28
If you have the money, the [LEGO Mindstorms NXT]("http://mindstorms.lego.com/") is a great way to keep kids entertained and have them learn too (plus robotics is close to my heart).  The downside though is that the NXT is very expensive ($250 USD) and some people claim too difficult for pre-teens, though if you are supervising I don't think the latter complaint is an issue.

---

### Post by FuriousLettuce on 2007-05-28
I started programming when I was about 11 using mostly HTML. I know it's not really a proper language, but it's really simple and you can very quickly create things which are visually gratifying, and he could incorporate his inkscape skills into it. It's also a good gateway to more advanced stuff - I progressed from basic HTML to PHP and MySQL (which allow the dynamic generation of websites, and PHP is robust enough that it can be used as a standalone scripting language), and from there onto whatever I felt like.

Doing simple stuff in any language will teach him the basic things to expect from a language, its limitations and the general programming method, meaning that he will be able to abstract from whatever language he chooses and quickly learn another language.

Just don't start him on C/Java!

---

### Post by linuxaz on 2007-05-28
Hello all,
Those are really good ideas, and I thank you!
He does have an NXT! 
It's hard to get him to follow the book though.  He'd rather invent a new robot and try to program it via an old windows laptop (no internet) running the proprietary NXT software using the blocks......

If i stay on him, He follows the book.

linuxaz

---

### Post by pmasiar on 2007-05-28
> **linuxaz said:**
> My Son really likes modifying games  that are installed on his computer. ...

With a whole summer vacation ahead of him, I want to provide the opportunity for him to learn some programming if it interests him.  Can anyone suggest a method, book, or website for a kid of 11 years old?

I had exactly the same problem with my son, and [http://en.wikipedia.org/wiki/Game_Maker](http://en.wikipedia.org/wiki/Game_Maker) was the perfect solution. It is better than logo or mindstorm: it is special GUI to program games without writing a line of code! Kid moves blocks around (they have icon reminding of function) and changes properties of these boxes. I was able to talk with my 11 years old  about events, creating and destroying object based on times, and stuff. It even allow to create 2-player games (different parts of keyboard control different avatars), so it is fun.

My son even made presentation in his elementary about platform game he made. Website has plenty of game samples and tutorials.

It is windows freeware, someone should reimplement it in Python/pygame. Please don't inflict on your kid IDE and a language with syntax, it might have opposite effect.

---

### Post by Znupi on 2007-05-28
I first started learning Pascal at the age of 9. So, that may be a good place to start, although I don't recommend Pascal, I'd rather go for C/C++. I know, I know, C/C++ is way too low-level and he won't like it... but you can give it a try. If he doesn't like it, I suggest you go for JavaScript (which he'll probably like, since the output is not a boring command line), HTML, CSS, PHP, MySQL, Python, etc... A good place to start on web-developing (html/css/php/mysql) is [W3Schools](http://w3schools.com). Good luck! :)

---

### Post by hod139 on 2007-05-28
> **pmasiar said:**
> I had exactly the same problem with my son, and [http://en.wikipedia.org/wiki/Game_Maker](http://en.wikipedia.org/wiki/Game_Maker) was the perfect solution. It is better than logo or mindstorm: 
I haven't read the wikipedia article, but can you please tell me why you feel Game Maker is better than the LEGO mindstorm NXT.  I am most likely going to be spending some time with high school students to convince them science, in particular computer science, is fun; so I am interested why you think Game Maker is superior.  If you want to PM me your answer to avoid hijacking this thread feel free.

---

### Post by pmasiar on 2007-05-28
No hijacking, that info is relevant to this thread IMHO :-)

First disclaimer: I never used Mindstorm. I have vague idea what it is, and my son (now older :-) ) participated in robotic competition using VEX kit (remote control) and EasyC. We also build some simple non-Mindstorm lego robot. It is not cheap to build enough interesting parts :-( I assume that to program Mindstorm you write code in text editor. But even if not, if it is fully GUI, you are limited not only by imagination and inventiveness, but also by physics: what robot can do.

Game Maker is completely different beast. You do not write code at all. Instead, you put tiles to event slots. GM is very high level language (4GL), optimized for games and nothing else.

Example: programming simple game "catch the dog"
- Define dimensions of game (area), 
- Define dog as object: clipart for dog was in library, or you can download clipart, or make own.
- Place score counter in some corner
- Event "start game": put "dog" at starting position, moving at random direction (tile) with random acceleration (tile). 
- Event "clicked by mouse": add tile score, properties: +1. Destroy old dog (tile: bomb), create new object (property: dog) at random position with random acceleration
- Event "dog left game field": add tile score, properties: -1. Destroy old dog, create new at random

Run it now - visual game is ready! Max one hour, including download and install!

They have tutorials (sample games with source code and explanation how to build it, how it works) for many common old games: 

Asteroids: when "big asteroid" collides with "bullet" object, destroy object "asteroid", create 2 new objects "small asteroid", which can be destroyed by bullet. Possible: timer to supply new bullets (so you can run out of bullets if you shoot too often and miss a lot).

And sources for other classic gamess: car races (fast police cars follows you, and you need to pick fuel), breakout, platfom, tank wars (2 player), pacman, etc etc. so you can see "tricks of trade" - look at events from other games for ideas how toimplement your own, instead of reading boring docs.

Even if someone is deeply interested in robots, there is only that much new moves/tricks you can invent. With games, possibilities are endless - and she will create a game which friends can come over, play, suggest changes, implement changes, and try new version! And of course: debug the new version first! :-)

---

### Post by ankursethi on 2007-05-29
Game Maker is absolutely the best for an 11 year old, especially since he can do some graphics in Inkscape. There's even a book on it, as far as I remember.

---

### Post by pmasiar on 2007-05-29
> **Znupi said:**
> II'd rather go for C/C++. I know, I know, C/C++ is way too low-level and he won't like it... but you can give it a try. If he doesn't like it, I suggest you go for JavaScript (which he'll probably like, since the output is not a boring command line), HTML, CSS, PHP, MySQL,... 

Warning: if you inflict all this over one summer on your 11 year old, don't be surprised if he would hate you, runs away from home to sell drugs by 15... :-)

C++? MySQL? What a random advice you can get on this forum!

---

### Post by Znupi on 2007-05-30
> **pmasiar said:**
> Warning: if you inflict all this over one summer on your 11 year old, don't be surprised if he would hate you, runs away from home to sell drugs by 15... :-)

C++? MySQL? What a random advice you can get on this forum!
That's how I started :| I'm 16 and still no drugs :D. If he likes programming, he won't hate you.

---

### Post by aks44 on 2007-05-30
I would advise you to tell him why programming is good, just like someone did with me when I was 9. That guy just told me : "If you need some software and it doesn't exist, you can make it yourself".
Just a few days later, I started learning 68k assembler by myself (ahh, the good ol' days...).
:p

---

### Post by dsl on 2007-05-30
> **linuxaz said:**
> Hello fellow Ubuntu users,
I"ll keep this short, but up front, let me thank you for any responses.

My Son really likes modifying games  that are installed on his computer.  He also seems to be very interested in science and such, as he will design (if you will) new inventions and dream up ideas using Inkscape.  I feel that if I could get him interested in programming, that he  may like it.

Myself, I can use the command line with the help of internet searches, but programming in Python, C++, or using QT is slightly above me. 
With a whole summer vacation ahead of him, I want to provide the opportunity for him to learn some programming if it interests him.  Can anyone suggest a method, book, or website for a kid of 11 years old?

I remember learning to do simple things in Basic when I was about thirteen.  I never followed up on it, but I feel that if there had been the internet as we know it today, and the resources present, I may have.....
I want to try and provide an opportunity for him that would benefit him in the future.

Any suggestions are appreciated,

Thanks,

linuxaz

I see a danger in this. Even if your 11 years old son really loves spending his time on a keyboard and you are not forcing him, in my modest opinion you should not even encourage him. Maybe not discourage, but keep a neutral attitude.
I've seen lots of parents pushing their children to something - music, painting, mathematics, whatever else. If the children are really gifted (what is not always the case) they may succeed. But they lose their childhood and they may have problems later.

---

### Post by Znupi on 2007-05-30
> **dsl said:**
> I see a danger in this. Even if your 11 years old son really loves spending his time on a keyboard and you are not forcing him, in my modest opinion you should not even encourage him. Maybe not discourage, but keep a neutral attitude.
I've seen lots of parents pushing their children to something - music, painting, mathematics, whatever else. If the children are really gifted (what is not always the case) they may succeed. But they lose their childhood and they may have problems later.
I agree. You should help him find something he really likes and something he's really good at, not force programming into him. As I said, if he likes it, he'll go with it.

---

### Post by linuxaz on 2007-05-30
All,
Thank you for the continuing input.  Since he's running Ubuntu the game program balks about a debugger when trying to install it with Wine.......................I think I'll set him up a test web page, and let him try his hand using Nvu.

Thanks,

linuxaz

---

### Post by Znupi on 2007-05-31
> **linuxaz said:**
> All,
...and let him try his hand using Nvu.

I strongly suggest you don't start with a wysiwyg html editor. He won't like it because it's too easy, and because he won't feel it's made by him. On top of that, if he learns how to write code himself, it will be much better for him because he'll actually understand how things work. And, he will be able to do some really cool stuff you can't do with Nvu (like js and sorts).

I suggest you start him with gedit :D (or better yet, this is what I use: [UltraEdit-32](http://ultraedit.com) -- it runs more or less perfect on wine.

---

### Post by brooksbp on 2007-06-01
> **linuxaz said:**
> Hello fellow Ubuntu users,
I"ll keep this short, but up front, let me thank you for any responses.

My Son really likes modifying games  that are installed on his computer.  He also seems to be very interested in science and such, as he will design (if you will) new inventions and dream up ideas using Inkscape.  I feel that if I could get him interested in programming, that he  may like it.

Myself, I can use the command line with the help of internet searches, but programming in Python, C++, or using QT is slightly above me. 
With a whole summer vacation ahead of him, I want to provide the opportunity for him to learn some programming if it interests him.  Can anyone suggest a method, book, or website for a kid of 11 years old?

I remember learning to do simple things in Basic when I was about thirteen.  I never followed up on it, but I feel that if there had been the internet as we know it today, and the resources present, I may have.....
I want to try and provide an opportunity for him that would benefit him in the future.

Any suggestions are appreciated,

Thanks,

linuxaz

I suggest starting out with something simple like HTML. The web was more interesting to me than application programming when I was starting out... still is even more now that the browser is somewhat transcending into it's own platform.

---

### Post by lispnik on 2007-06-01
You might try [Squeak and Etoys]("http://squeakland.org/")

---

### Post by hod139 on 2007-07-23
MIT has recently released [scratch]("http://scratch.mit.edu/"), which is designed for kids ages eight and up.

---

### Post by linuxaz on 2007-07-23
Very interesting,
By following the Scratch forums, I see somebody has made an installer script...I'll give it a try.

Thanks,

linuxaz

---

### Post by pmasiar on 2007-07-23
can you post link to installer, just in case?

---

### Post by linuxaz on 2007-07-23
I don't know anything about this site.....but here is the link.

[http://www.notesmine.com/scratch_installer](http://www.notesmine.com/scratch_installer)

---

### Post by Paul Miller on 2007-07-23
Python is not a bad choice, IMO.  It's generally considered easy to use and it's based on the "principle of least surprise."  That is, things ought to work in a consistent manner, but value practicality over purity.  I'd consider using [ActivePython]("http://www.activestate.com/store/download.aspx?prdGUID=b08b04e0-6872-4d9d-a722-7a0c2dea2758").

Although I haven't used it, I've heard that [Hackety Hack]("http://hacketyhack.net"), a beginners' programming system based on Ruby is decent.

Finally, one option I do have personal experience with is Logo, combined with a turtle-graphics implementation.  I learned Logo in fourth or fifth grade, I believe, and I've heard of even younger children picking it right up.  With turtle graphics, you get to make pretty pictures, too. :-)

---

### Post by Peyton on 2007-07-24
I have to agree with one of the earlier posts. Don't force your son into programming. If you think he'd enjoy it, then mention it to him and offer to help him. Just don't *make* him do it. More importantly, if he does get into it, remind him that there are still more important things in life.

---

### Post by jusmurph on 2007-07-24
> **linuxaz said:**
> Hello all,
Those are really good ideas, and I thank you!
He does have an NXT! 
It's hard to get him to follow the book though.  He'd rather invent a new robot and try to program it via an old windows laptop (no internet) running the proprietary NXT software using the blocks......

If i stay on him, He follows the book.

linuxaz

I would not understand why would try to encase such a creative mind? We learn best from our own experiences.

---

### Post by tr333 on 2007-07-24
Take a look at [Logo](http://en.wikipedia.org/wiki/Logo_%28programming_language%29), an educational language derived from Lisp.

---

### Post by Note360 on 2007-07-24
Ok, seriously.

I would get him involved in Python. Its decently simpler and it has room for expansion. FIRST though I would teach him how to get around a terminal comfortably.

(cd, rm, mv, cp, python, screen?, vim/emacs, and how to end something Ctrl-D Ctrl-C Ctrl-Z and their differences)

---

### Post by slavik on 2007-07-25
scheme is another viable option, remember, unlike python, it was written for teaching (and any CIS prof can explain scheme syntax in about a minute).

---

### Post by techknowmama on 2007-07-25
I agree its best not to push him, however is he is interested, many community colleges offer workshops for kids in all sorts of different subjects during the summer, the college in my area had many computer science  workshops   ranging from  learning the parts of a pc , web design  and c programing  and they had them split up  for different age levels 
if they do have something like that in your area, I would suggest getting of list of what they offer and let him choose something he would like to do.

---

### Post by bazmati on 2007-09-10
OMG yes NXT is the way to go and if he does follow the book -- even better,  LEGO as Object Programming and the internet are all similar and can be translated in simple words COPY&PASTE  you take something that exist already and use it to create something new,  There are great books outthere to assist you kids in having a positive experience with Lego and NXT programming -- i'm actually serching on NXT and lego on this forum as i'm about to get back into it (winter hobby calling me) and i have to see if i can setup bluetooth and NXT on ununtu.   keep bying lego for your kid -- just let him play with it also not just you :-)

Marc-  also member of [www.QueLUG.org](www.QueLUG.org)  (quebec-Montreal lego user group)

---

### Post by CptPicard on 2007-09-10
Don't underestimate an 11-year-old. Why would you force him to use some toy languages, when something like Python is perfectly good, and will also scale with the kid?

Slavik's idea is something I have already played with myself. What if you gave a kid, with no preconceptions about imperative programming, a Scheme interpreter? [DrScheme]("www.drscheme.org") is great - a GUI-based Scheme "shell". Scheme's syntax is really minimal, and I bet things like recursion and higher-order functions come really naturally to someone who isn't already set in his ways...

Especially if the kid shows an interest in sciences and math, functional programming even gives a really nice tool for that kind of learning...

---

