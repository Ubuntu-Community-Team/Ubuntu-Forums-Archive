---
title: "Vocabulary"
date: 2011-08-29
forum: Programming Talk
---

### Post by johnno56 on 2011-08-29
Hi,

I hope I am in the right place.

I am running with Ubuntu 10.10 (Gnome) and I have a programming request.

I have a VERY old Vocabulary Quiz program written in TRS80 Basic and would like to either reproduce or create a more "up to date" version.

I would like to create a GUI to control / display the the game.

I would like some advice as to which utility to use to create the gui and which programming language to use to interact with the gui. My only programming experience has been with basic. Not visual basic, plain simple basic. (now my age is showing...)

Sorry to be so vague, but the project is just an idea, at the moment.

I am not asking anyone to write it. I just need info to help me to do it myself.

Any info or assistance will be appreciated.

Regards
J

---

### Post by Bachstelze on 2011-08-29
Python  with tkinter or Qt or GTK. There's a [good book](http://www.amazon.com/gp/product/B000XPNUKO/) for Qt.

---

### Post by johnno56 on 2011-08-30
Bachstelze,

Thank you for your reply.

I already have Python and Qt installed and managed to obtain a copy of the book you recommended. I have started reading the 600+ page epic and looks like a lot of learning ahead of me.

Thank you again for the assist.

Regards

J

---

### Post by JupiterV2 on 2011-08-30
[Gratuitous Plug]You could always take a look at my project: [Vocab Builder]("http://vbuilder.sourceforge.net").[/Gratuitous Plug]

---

### Post by johnno56 on 2011-08-30
JupiterV2,

Thank you for replying.

The game that I have is more basic (no pun intended) than a Vocab Builder. It has only one set of words and definitions. Extra sets cannot be created via the program.

The plot is simple.

The game stores all the words and definitions (currently about 15,000 words) and randomly selects a word. 

The user is asked how many words to be tested on. The definition is displayed along with the correct word and 4 other randomly chosen words. The user then makes a selection. The answer is then given and the loop continues until the chosen word count is completed. The score is analyzed and a rating is then given. The user is then asked to either quit or play again.

The game is very simple but, trying to recreate it using programming languages that are both more powerful and unknown to me, is my problem. I have an OLD basic program that I would like to resurrect. If the learning curve is to steep or the amount of effort required is too great, then I may have to just let it go.

Thank you for your help and advice.

Regards

J

---

### Post by Senesence on 2011-08-31
> **johnno56 said:**
> The game is very simple but, trying to recreate it using programming languages that are both more powerful and unknown to me, is my problem. I have an OLD basic program that I would like to resurrect. If the learning curve is to steep or the amount of effort required is too great, then I may have to just let it go.

I would recommend staying away from Qt, GTK, or any other GUI library. These are fairly complex layers of 3rd party software, which tend to make relatively simple projects more complicated then they need to be.

For now, you should focus on learning the basics (no pun intended) of whatever modern language you chose to use (I recommend Python). So, write your program as a terminal application first, and then, when you're comfortable with the language, look around for GUI toolkits that seem to offer what you need (wxPython may interest you at that point).

---

### Post by johnno56 on 2011-08-31
Thank you Senesence for the advice. I will look for a "noobs" version of a Python book and start wearing out my keyboard.

Much appreciated.

Regards

J

---

