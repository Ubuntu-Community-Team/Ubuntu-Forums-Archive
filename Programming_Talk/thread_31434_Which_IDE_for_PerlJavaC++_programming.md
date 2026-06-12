---
title: "Which IDE for Perl/Java/C++ programming?"
date: 2005-05-03
forum: Programming Talk
---

### Post by coolblue on 2005-05-03
Dear Ubuntu lovers

Please tell me what would be the ideal IDEs/programs for programming in the following languages:

1) Perl/BioPerl
2) C/C++ 
3) Java

All suggestions welcome:)

Thanks

CoolBlue

---

### Post by Xerampelinae on 2005-05-03
I use vim.

Many people like eclipse.

---

### Post by j-rock on 2005-05-03
Perl     == vim
C/C++ == vim/kdevelop
Java    == Eclipse

Thats all me though.

---

### Post by mendicant on 2005-05-03
ActiveState has a thing called Komodo for perl--never used it, but others like it.
Eclipse can be used for C/C++, as well.  It's not as good as with Java, but isn't too bad.  Emacs with ecb/cedet is also nice.
For Java, I really like Eclipse, and before that, I used emacs with JDE (which I think has a problem currently in Ubuntu wrt beanshell).

---

### Post by atoponce on 2005-05-03
[QUOTE=coolblue]Dear Ubuntu lovers
 
Please tell me what would be the ideal IDEs/programs for programming in the following languages:
 
1) Perl/BioPerl
2) C/C++ 
3) Java
 
All suggestions welcome:)
 
Thanks
 
CoolBlue[/QUOTE]
 
Although not an IDE, nothing beats a good text editor.  Either gedit or kate are absolutely wonderful.  Gedit is installed in Ubuntu by default and kate is installed by default with Kubuntu.  They have syntax highlighting, and smart indenting.  However, they are not capable of building projects, and do not have the dynamic drop-menus and a built in compiler.
 
In this case, I would say KDevelop for C/C++ and Eclipse Java.  Although C++ will work in Eclipse, for the most part use KDevelop.  I do not program in Perl/BioPerl, so I don't have any recomendations there.
 
Good luck!

---

### Post by defkewl on 2005-05-04
Bluefish is nice :)

---

### Post by gratefulfrog on 2005-05-04
If you're a serious developer, then only **emacs ** will satisfy you. It may appear hard to learn but the return on investment is very high. 

As a software project manager I would _never hire a developer who didn't know emacs_!
 ;-)

---

### Post by Xerampelinae on 2005-05-04
[QUOTE=gratefulfrog]If you're a serious developer, then only **emacs ** will satisfy you. It may appear hard to learn but the return on investment is very high. 

As a software project manager I would _never hire a developer who didn't know emacs_!
 ;-)[/QUOTE]
 die.

;)

---

### Post by mendicant on 2005-05-04
It is always handy to know a variety of text editors, espicially the big two: vim and emacs, because when you are looking over somebody's shoulder, there's a good chance that they're using one of those.

It also lets you use bash in whatever keybindings are being used...

---

### Post by jerome bettis on 2005-05-04
[QUOTE=gratefulfrog]If you're a serious developer, then only **emacs ** will satisfy you. It may appear hard to learn but the return on investment is very high. 

As a software project manager I would _never hire a developer who didn't know emacs_!
 ;-)[/QUOTE]
 not to get off topic, but what are your thoughts on vim?

i need to learn emacs .. will you hire me when i'm done? :-P

---

### Post by dataw0lf on 2005-05-04
And I wouldn't ever hire a guy who used emacs.  So ha!
Anybody who needs an extra OS (emacs) to become a competent coder isn't worth hiring anyways.

---

### Post by lao_V on 2005-05-05
[QUOTE=dataw0lf]And I wouldn't ever hire a guy who used emacs.  So ha!
Anybody who needs an extra OS (emacs) to become a competent coder isn't worth hiring anyways.[/QUOTE]

Looks like we're all going to stay unemployed :-)

---

### Post by gratefulfrog on 2005-05-09
[QUOTE=jerome bettis]not to get off topic, but what are your thoughts on vim?
[/QUOTE]

I have no thoughts on vim. My opinion is that vi is a powerful, standard tool that every professional who works in the UNIX or Linux envt. should know. It is the baseline tool that will always be there, when you get beeped in the middle of the night to get the nuclear power plant's system back up, you can count on vi being there, and presenting its standard functionality.

Despite the remarks on this page, and I must say I am shocked by the amount of heat generated, in the world of pros and particularly amongst GNU users, emacs is the tool that does it; and has been doing it for a long long time. As someone commented in this thread, it's almost and OS. In fact, it is a developer's interface to the OS, like eclipse or any of the other IDE's. But it is again a standard, customizable with a very powerful and standard language LISP (perhaps the most powerful of all...), which means that any pro can use it.

However, if your goal is simply to write some programs for your own use, and you are not doing so in a professional framework, or with a professional goal, then I'm not sure that either vi or emacs is the right tool for you. 

If you only want to drive to the corner store, then would you want to spend the time to learn to drive a Ferrari, or a semi-rig, when a bicycle would be good enough?

As always on the forums, when someone asks what a "good" xyz is, it is always necessary to define the criteria for goodness for xyz.

**But what surprises me is why anyone would get so excited about a text editor in a Ubuntu thread?**

---

### Post by transkinetic on 2005-05-10
double post

---

### Post by transkinetic on 2005-05-10
What about xemacs?

---

### Post by rplantz on 2005-10-31
[QUOTE=gratefulfrog]
**But what surprises me is why anyone would get so excited about a text editor in a Ubuntu thread?**[/QUOTE]

Uh, I think you started the "excitement" by underlining your statement that you would never hire a developer who doesn't know emacs.

I've been in the business since the early 1960s. I've used many editors. Each has its strengths and weaknesses. Furthermore, "strength" and "weakness" depend on many, many factors.

I spent the last 21 years of my career teaching computer science at a university. I always recommended to students that they learn several editors. I've met a lot of people who learn one editor very well. Then they claim that to be the best one. I find that to be limiting. I told students that when they're looking for a job, if they know the basics of how to use several editiors, they can quickly learn how to use a new one.

My general take on emacs vesus vim: emacs uses modifier keys (control, alt) for a lot of commands; vim uses two modes -- movement and editing. Yes, this is a huge generalization, but it might help a beginner to think about which way he/she likes to work.

I like the gui editors a lot; e.g., gedit on my unbuntu box, bbedit on my Mac.

All of them are vast improvements over the first ones I used. I learned programming using a keypunch machine. I recall when Intel provided their first editor that erased a deleted character on the screen instead of simply repeating it (as was done with a teletype machine).

Oh, I also pointed out to my students that a job interview works both ways. They should be evaluating whether they want to work for manager or not.

Bob

---

### Post by LorenzoD on 2005-10-31
[QUOTE=gratefulfrog]
**But what surprises me is why anyone would get so excited about a text editor in a Ubuntu thread?**[/QUOTE]

That's right. We were talking about an IDE here. I prefer zsh, with the vim editor plug-in.

---

### Post by Klunk on 2005-11-08
Pesonally I would use Eclipse for all of these.

You can get the GNU C++ plug-in (CDT) from eclipse.org which allows you to write C++, write make files, compile C++ and debug it all from within the IDE. You can get the EPIC plugin for Perl which gives you a colour editor window and of course it is written in Jave for Java.

If your project spans the 3 technologies you can use the one IDE for all 3. Of course I could use vi but I prefer not to.

There are hundreds of plug-ins for many technologies available for Eclipse which makes it a very powerfull tool. I use UML and databse plug-ins as well.

---

