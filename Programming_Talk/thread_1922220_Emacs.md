---
title: "Emacs"
date: 2012-02-08
forum: Programming Talk
---

### Post by katarinca1help2me on 2012-02-08
Hy everyone!!!!

I need help. I am miserable. I don't know how to use Emacs: I want to write python code in it and also run it from emacs. I find many many sites on google with help, but non of them useful for me. Because I don't understand them. I don't know where to write something. I need help in this way: click this button, then click this button, write this in this specific area; open this file; tell me how to open this file; and so long. I really need something where it would be everything told, all steps, just clicking and following the instructions.

I really want to learn using emacs. I just follow the tutorials for using keys and opening and saving files. But I want to learn, how to use python in it. And I want to use both, python 3.2 and python 2.7. Problem is just I am not possible to run code wriiten in emacs.  I am using python for 3 years know, but using python shell editor coming with python (all on MS windows).

Few days ago I decides to start using ubuntu, I install ubuntu. And install emacs from ubuntu software center. I also don't know anything about terminal, except that, I can run python from it, if python code is written in the way that it output something. But I am not possible to call function written in python at all.

Sorry for my bad english, and confused writing.

I will be really very very happy, if someone could help me.

By.

---

### Post by karlson on 2012-02-08
Why not install Eclipse, Code::Bloks or similar IDE?

---

### Post by JDShu on 2012-02-08
emacs has a pretty intense learning curve. It is possible to run python from emacs and it can be very convenient, but my recommendation is to learn to use the terminal to run your python programs and emacs for text editing. Over time, you'll figure out what you need and how to extend your knowledge of emacs to do it.

---

### Post by katarinca1help2me on 2012-02-08
> **karlson said:**
> Why not install Eclipse, Code::Bloks or similar IDE?
I just want to use Emacs.

---

### Post by sir.sargento on 2012-02-08
> **JDShu said:**
> emacs has a pretty intense learning curve. It is possible to run python from emacs and it can be very convenient, but my recommendation is to learn to use the terminal to run your python programs and emacs for text editing. Over time, you'll figure out what you need and how to extend your knowledge of emacs to do it.

^^^ What he said. I think the best way to learn emacs is to use it as a text editor and use the cli to run your py programs.  I do the same thing and little by little have learned how to use emacs and use different settings etc.. A good place to ask questions would be on IRC. 

irc.freenode.net - #emacs is a good channel to get help with using emacs. 

hope this helps.

---

### Post by katarinca1help2me on 2012-02-08
> **JDShu said:**
> emacs has a pretty intense learning curve. It is possible to run python from emacs and it can be very convenient, but my recommendation is to learn to use the terminal to run your python programs and emacs for text editing. Over time, you'll figure out what you need and how to extend your knowledge of emacs to do it.
It is problem I don't know any pretty way to call functions from terminal. I can do it only if I import this function. And I don't know how to change the environment in emacs to be nicer with python. I just know that emacs is really good editor and I wanted to learn it. But like I see it is not so easy as I thought. I wanted to be editor for python, latex, R, html, ...

---

### Post by pixiq on 2012-02-08
Hi and welcome to the Ubuntu Forums

I suggest that you browse the internet for ***emacs tutorial*** and find some introductory texts that help you get going (for example ***Emacs-Beginner-HOWTO.pdf***)

Emacs is a very old and rather difficult tool (from the golden days of Unix). It is very powerful, but I think it is easier to start using some editor that looks more like what you are used to from word processing and simple editing, for example ***gedit***. Run the programs in a terminal window, as suggested in two posts before. Later on, when you have managed to create some python programs, you can start advanced stuff with emacs.

Good luck :-)

---

### Post by katarinca1help2me on 2012-02-08
Thanks for answers.
Some more details.I have enough knowledge to create some games in python (for example  tetris, some puzzles, ...) and knowledge on databases (for example we  made little bank). We were having this in our courses on our faculty.  But we just used to learn python programming. Nobody ever didn't even  try to learn us how to use some other editors, or using terminals. We  are having Ms windows 7 install on our computers. So python is not  problem for me. I am not learning programming in python (of course I am  learning, because we are learning the whole life). I wanted to learn how to  use editor emacs. This is it. I just don't know where to start.

And this is why I wanted to run python in emacs, because I know python, and I wanted to learn using emacs.

I would be probably satisfied for now if I could call functions from terminal.

For example:
I wrote next function (this was the first function we wrote when studying loops):

def banana(n):
    b = 0
    for i in range(n):
        if i%2 == 0: b = b + i
     return b

And saved as foo.py. Put this file in some folder (on my usb stick). Now I wanted to call this function in terminal. How to do it? I know that this was written for million times already (probably), but I would be very glad if I get an answer here.

Thank you all for answers. I am just so awaiting to learn something useful.

---

### Post by cortman on 2012-02-08
I'm all for anyone putting effort into learning emacs- with a little determination I learned it early on, and now I wouldn't switch to any other text editor. There definitely is a learning curve, but to get around that you simply have to use it. I mean REALLY use it. Use it to take notes. Use it to write letters. Use it to write simple code. Use it for any kind of text editing you do. Once you get used to it, you'll be able to use it twice as fast as anyone with an GUI editor. But you have to stick with it. I found it was well worth the effort.
You can learn emacs by writing code in Python, but you have to be patient. If you're writing advanced code, and are still in the process of learning, I'd say do your learning separate and wait till you have more experience to do it in emacs. Use emacs for everything else, and Eclipse for your advanced Python coding.

---

### Post by matthew.ball on 2012-02-08
Open GNU Emacs, type: [FONT="Courier New"]C-h t[/FONT] - spend a few minutes *interactively* going through that tutorial. Don't just skip stuff because it seems irrelevant. You'll be comfortable using GNU Emacs after that.

If you want to write Python with GNU Emacs, you should have a fairly good idea how to use the integrated help system (in particular, [FONT="Courier New"]C-h m[/FONT]) this all comes from the tutorial though. As I said, just go through the whole thing, it will pay off.

You have a couple of paths you could take with writing Python with GNU Emacs; either start an inferior Python session (i.e. [FONT="Courier New"]C-c C-z[/FONT]) inside a Python-mode enabled buffer, or start a terminal session ([FONT="Courier New"]M-x term[/FONT]) inside a GNU Emacs session, navigate to the project directory and run Python that way.

---

### Post by pixiq on 2012-02-09
> **matthew.ball said:**
> Open GNU Emacs, type: [FONT=Courier New]C-h t[/FONT] - spend a few minutes *interactively* going through that tutorial. Don't just skip stuff because it seems irrelevant. You'll be comfortable using GNU Emacs after that.

If you want to write Python with GNU Emacs, you should have a fairly good idea how to use the integrated help system (in particular, [FONT=Courier New]C-h m[/FONT]) this all comes from the tutorial though. As I said, just go through the whole thing, it will pay off.

You have a couple of paths you could take with writing Python with GNU Emacs; either start an inferior Python session (i.e. [FONT=Courier New]C-c C-z[/FONT]) inside a Python-mode enabled buffer, or start a terminal session ([FONT=Courier New]M-x term[/FONT]) inside a GNU Emacs session, navigate to the project directory and run Python that way.
+1
This is a good idea, now that I understand that you know enough, I suggest that you work with emacs (exploring it's built-in tutorial etc) and at the same time use the tutorials available on the internet. I'm sure you find tutorials and similar texts, that will help you succeed with emacs.

---

### Post by Khayyam on 2012-02-09
hello all ..

Emacs is a great operating system, all it needs is a decent editor .. sorry, mia culpa, mia culpa, what a way to start a stupid war! Its a good joke though, no?

I started (way, way, back) with emacs, it was the default editor for the mail system I was using (go figure) and not knowing how to change it (or that I could be changed) I learned it diligently. However, some years later I was confunded when emacs returned "command not found: emacs", and I realised that of the various machines I was asked to work on none of them had emacs installed (and this became a recuring theme that doesn't seem to have improved with time). So, vi (in one form or other) became a requirement and I diligently learnt that also. In the course of time vim was gradually replacing vi, but it was a fairly easy switch, and vim offered many of the features that I might have had reason to grumble about with the switch from emacs.

I've been present at all kinds of LUG's with emacs enthusiasts downplaying vim for all kinds of reasons -- normally a 'missing feature' or the 'modal' refrain (like 'M-x' isn't somehow changing input behavior) -- but in my experience I've yet to really find anything that I could honestly say makes emacs a more advanced editor. Yes, vim isn't a mailreader, newsreader, debugger, IDE, etc, etc, but strickly speaking neither is emacs. Vim can intergrate one or other feature in the same way, if not as a frontend then a backend. Bascially, the only difference that I could clearly make between emac and vim is that vim doesn't try to be a shell.

I would never argue that vim is superior, it isn't, vim is just an editor with features. It follows the *nix principle of 'do one thing, and do it well'. It is for that reason that I can find it everywhere, or at minimum some form of vi. This 'feature' alone is for me an important one, I expect the tools I've invested time to learn to be accessable to me under most, if not all, working conditions.

Having 'swiched', mostly for practical reasons, and having been exposed to more than my fair share of editor skirmishes (or "sqwermishes" as Sarah Palin expertly calls them) I hope I'm fairly non-partisan. I'd like to think that should I have to go back to emacs for some reason I'd do so without much of a grumble. I can't see my willing doing so though, and I don't know if that is a matter of habit or something more substantial.

Both vim and emacs take some time to learn, and yet more time to master, so I would look at both before throwing time and energy into seriously tackling one. In some ways I'd like to recoup what I'd spent on emacs as I can't really see the investment paying off in the long term. Perhaps if your more situated on localhost then this is less of an issue, a systems admin will have different a set of priorities to that of a programmer, as they say 'different strokes'.

Anyhow, I didn't want to start any kind of war, only to make the last point about time investment and the like to the OP .. before its too late ... hehhehe j/k

best ..

---

### Post by lykwydchykyn on 2012-02-09
Sheesh; post an emacs question to UF and you'll get a full page of people telling you to use another IDE/TE before anyone actually knows the answers.

 - Make sure the "python-mode" package is installed.  You can install this through synaptic or apt-get at the console.

 - Start emacs and open your python file.  If you're starting a new file, just save it with a .py extension.  Either action should trigger emacs to enter python-mode.

 - C-c-C-c (that's Ctrl-C, Ctrl-C in non-emacs speak) will execute your python script.  If there's output, Emacs will create a buffer called *Python Output* to display it.

---

