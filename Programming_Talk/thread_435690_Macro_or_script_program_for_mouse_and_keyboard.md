---
title: "Macro or script program for mouse and keyboard"
date: 2007-05-07
forum: Programming Talk
---

### Post by grzecisz on 2007-05-07
Hello. I'm looking for simple (or advanced :P ) program that will be able to create macro and simulate mouse click/movement and also keystrokes. I'm running Ubuntu Edgy and Gnome. Thanks for any info.

---

### Post by LaRoza on 2007-05-07
I am not exactly sure what you want, but if you want to automate multi-step tasks, you could write a shell script to do it.

---

### Post by grzecisz on 2007-05-07
> **LaRoza said:**
> I am not exactly sure what you want, but if you want to automate multi-step tasks, you could write a shell script to do it.

sure, but can shell script emulate mouse clicks or keystrokes in other program?

---

### Post by LaRoza on 2007-05-07
As I said, I do not exactly what you wanted, I am not familiar enough with Bash scripts so I am using a batch script to demonstrate:

This 

@echo off
defrag c: -w -v > c:\users\laroza\desktop\defragResults.txt


Would make defragmenting c: fully and outputting the statistics to a text file an my desktop a click away.

To do this any other way, you would indeed have to click the mouse and type.

However, if you wanted to do some thing without command line arguments, you would have to use something else. Like opening Firefox, going to yahoo!, logging in, and entering my inbox couldn't be done with Batch. (You can get a Firefox add-on called Deja-click though.)

---

### Post by grzecisz on 2007-05-07
> **LaRoza said:**
> However, if you wanted to do some thing without command line arguments, you would have to use something else. Like opening Firefox, going to yahoo!, logging in, and entering my inbox couldn't be done with Batch. (You can get a Firefox add-on called Deja-click though.)

Yes, this is what i want :) I want this macro program to be able to CLICK with my mouse pointer on specific coordinates, for example icon on a desktop or a button on some webpage. I think its impossible in Shell script.

This Firefox add-on would be great, but it is working only for FF and i want something that would work also 'outside' Firefox.

thanx though :]

---

### Post by Darkness3477 on 2007-05-08
I tried doing something similar to this in Python. I was trying to make a macro for an online Java game just for a bit of fun as some of my friends are really into doing things like this. I looked around, but couldn't find anything incredibly helpful.

However, I know you can quite easily do this in Java. I'm not sure what you would need to search for, so I can't help you too much though. However, if you'd like I can ask a friend on how he managed to get everything working for you.

---

### Post by cwaldbieser on 2007-05-09
> **grzecisz said:**
> Yes, this is what i want :) I want this macro program to be able to CLICK with my mouse pointer on specific coordinates, for example icon on a desktop or a button on some webpage. I think its impossible in Shell script.

This Firefox add-on would be great, but it is working only for FF and i want something that would work also 'outside' Firefox.

thanx though :]

[http://www.gnu.org/software/xnee/www/index.html]("http://www.gnu.org/software/xnee/www/index.html")
It looks like xnee is in the repositories, though I have never used it.

---

### Post by grzecisz on 2007-05-10
> **cwaldbieser said:**
> [http://www.gnu.org/software/xnee/www/index.html]("http://www.gnu.org/software/xnee/www/index.html")
It looks like xnee is in the repositories, though I have never used it.

Hey, that looks like the one i'm lookin for :) Haven't tried it out yet, but description is promising.

Thank You very much, and all of You guys for replies.

---

