---
title: "[SOLVED] Java Program - mainstream?"
date: 2008-01-18
forum: Programming Talk
---

### Post by Syndacate on 2008-01-18
Alright, here's the deal, I've tried some of the "main" ones, and I just don't like them - at all.

Eclipse is good, but you can't just "edit a document" with eclipse, you gotta create a whole 90,000 class operating system with it.  Then when you go to run it or something god forbid it just did it - no, it's gotta ask 1001 questions (none of which I'm sure about).  Big pain in the ***, though a good program.  It's like saying you need a 8.3L V10 Viper engine because you need to turn your car around in your driveway.  Good engine, but what the sh!t?

Then there's emacs...which kinda just sucks.  I don't really mind using it, if it wasn't for the fact that it drops these turds of "backup files" EVERYWHERE - you look at your folder(s) under konsole or you press <ctrl><h> and you want to cry.  Which, fine, whatever, I can live with the backup files all over the place, but then there's **** such as it not being user friendly (all the shortcuts are different), and the fact that it always does some random **** such as you turning it off and the file being blank.  It's not a very good program if you don't want to go insane.  Not to mention it lacks a lot.  Also, the ones in my java class are white on black, which is easy on the eyes, this **** is in black on BRIGHT white (not even dull white) which just blows.

Then there's GEdit and KEdit, Kate, etc. - They're good for making ONE modification, but it's not like emacs or eclipse where it knows the automatic indentation that it should be at based on what's previously above it, which is a major downfall as formatting is majorly important.

So if you remove KEdit, Kate, GEdit (I'm sure you could also stick KWrite in there, I'm sure that's not much different), eclipse, and emacs, what are you left with?  Also leave out Vi because that shouldn't count, though that's what my CS Lab teacher uses and he loves it...

TIA

---

### Post by jcwmoore on 2008-01-18
you could try jedit,  I personally use GVim.  it has the VI feel but with the functionality of a GUI

[http://www.jedit.org/]("http://www.jedit.org/")

---

### Post by pbrockway2 on 2008-01-18
> Eclipse is good, but you can't just "edit a document" with eclipse, you gotta create a whole 90,000 class operating system with it

I'm not sure I understand this.  Eclipse doesn't create any noticable bloat.

> It's gotta ask 1001 questions (none of which I'm sure about)

If you are unsure what goes into the description of an Eclipse "project" (foremost being the concept of a classpath and how it relates to how program might be run or made part of a jar archive) then you are probably better off not using an IDE until these things are sorted out.

For very simple programs - with just a few files - I find Kate very useful.  It does syntax colourise and gets the indentation right. (This is configurable from the "Settings" menu choose "Configure Kate" then under "Indentation" choose "C Style" as the indentation mode).  

It also gives you easy and integrated access to the command line.  From there you can master the commands needed to compile and run your programs without the more elaborate configuration of an IDE getting in the way.

---

### Post by Syndacate on 2008-01-18
> **jcwmoore said:**
> you could try jedit,  I personally use GVim.  it has the VI feel but with the functionality of a GUI

[http://www.jedit.org/]("http://www.jedit.org/")

I was searching earlier and found jedit - it looks just as complex as eclipse - is that just the way it looks or is it simple?

[quote=pbrockway2]I'm not sure I understand this. Eclipse doesn't create any noticable bloat.[/quote]

What is a noticeable bloat?  If you mean like I said it lags down the computer, that's not what I meant at all.

[quote=pbrockway2]If you are unsure what goes into the description of an Eclipse "project" (foremost being the concept of a classpath and how it relates to how program might be run or made part of a jar archive) then you are probably better off not using an IDE until these things are sorted out.

Well fine, I'm not claiming to be extremely knowleageble in the subject, I just want to know if I can right click on a file and "edit" it - that's possible - with eclipse, it isn't.  You need to make a new "project" - and it has to have a work directory, and it has to be set up with the right settings - it takes an epic amount of time.  Learning eclipse is like learning an entire new operating system.

[quote=pbrockway2]For very simple programs - with just a few files - I find Kate very useful. It does syntax colourise and gets the indentation right. (This is configurable from the "Settings" menu choose "Configure Kate" then under "Indentation" choose "C Style" as the indentation mode).

It also gives you easy and integrated access to the command line. From there you can master the commands needed to compile and run your programs without the more elaborate configuration of an IDE getting in the way.[/quote]

Okay, I'll give kate a try - I assumed it'd be much like KEdit, GEdit, etc.

---

### Post by pbrockway2 on 2008-01-19
Oh - I see what you mean by "edit".  You can open a file in Eclipse, so I imagine you can set up whatever file browser you use to have it start Eclipse with the file opened.  But I have never done this.  Eclipse really is designed as an IDE, not a file editor.

By little bloat all I meant is that you end up with your source files and the files you tell it to build from them (class files and jar archives).  But, you're right, you do get all the directory structure set up: because in a larger project they would be needed.

But for what you want I would recommend Kate as an editor.  (Based like such recommendations often are on ignorance of the alternatives.)  I've just read your original post again, and I think the font size/colours and stuff are all configurable too.  Post if you have trouble setting it up to work the way you want.

---

### Post by xlinuks on 2008-01-19
I'm using jEdit, I don't find it complicated, rather very extensible, I'm using it when working over my projects, while NetBeans (6) serves for working with other's projects (not Eclipse cause IMHO I find NetBeans more intuitive)

---

### Post by naugiedoggie on 2008-01-19
> **Syndacate said:**
> Alright, here's the deal, I've tried some of the "main" ones, and I just don't like them - at all.

Eclipse is good, but you can't just "edit a document" with eclipse, you gotta create a whole 90,000 class operating system with it.  
/ ... /
Then there's emacs...which kinda just sucks.  
/ ... /
Then there's GEdit and KEdit, Kate, etc. - They're good for making ONE modification, but it's not like emacs or eclipse where it knows the automatic indentation that it should be at based on what's previously above it, which is a major downfall as formatting is majorly important.
TIA

Well, there is a saying, "Get the right tool for the job."  I use numerous text editors, depending on the job.  If I just want to look at a readme file in a zip file, I open it in gEdit.  If I'm writing a shell script or small program, I use emacs.  For programming applications, and writing web apps in Java, I use NetBeans.

If I had to pick one tool that can be used for all efforts, it would be emacs.  I've used it for years.  It's kind of a religious thing for some users, less so for me but it does everything, literally.  It's an editor, a mail reader, a news reader, a web browser, frontend for compilers and shells.  Complex tools require that you take the time to learn how to use them.  For example, turning off backups in emacs is trivial:  put this entry in your .emacs file:

```
(setq make-backup-files nil) 
```

Take an hour to go through the emacs tutorial. (C-h t)  Realize that you can customize nearly every aspect of its behavior -- not just colors and key maps, you can embed your own functions in it.  The ultimate "macros" -- you're programming the editor itself.  That kind of flexibility ("extensibility" in the emacs jargon) comes with the price of complexity, so you have to learn how to use it.

Other IDEs are no different.  I've never liked Eclipse but NetBeans, which in version 6 is just awesome for about every kind of programming you want to do, -- NB also requires that you spend the time learning how to use it.  

All editors are tools.  You wouldn't build a house with just a handsaw.  And if you were building a model ship, you wouldn't just power up the band saw and start cutting.  It's no different here.

Thanks.

mp

---

### Post by Lord Illidan on 2008-01-19
I find Eclipse to be quite good for java programming. Yes, it requires you to make a project, ok..but that doesn't take more than 1 minute, and you get a pretty good IDE for free. Before emacs, I also used geany, a good one for editing small source files, too.

---

### Post by Syndacate on 2008-01-21
Yeah Kate did the trick.

Yeah, if I just wanna change a line of code kate works well - which was what I was looking for - I thought it woulda been similar to kEdit.

Though for creating something from scratch eclipse is fine.

Thanks.

---

