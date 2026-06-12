---
title: "python question"
date: 2008-11-24
forum: Programming Talk
---

### Post by flyingsliverfin on 2008-11-24
when I start the built-in python app in my applications bar, it looks just like a terminal (is it supposed to??) . Also, I am automatically in interactive mode, which I don't want.

all I want to do is write a script normally like in other lang. (srry, im used to QBASIC, MATHEMATICA and very little C)

By the way, I just started learning python today, but can't understand much, is that normal for a 12 year old??

---

### Post by mentallaxative on 2008-11-24
I'm guessing you opened up the Python interpreter in a terminal. If you want to write scripts, do it in a text editor/IDE like gedit/vim. Then, from the command line, type 'python @script' to execute it where @script is the name of your script.

If you are new to Python though, I suggest exploring the language through the interpreter for a while longer--it is a faster way of learning small things than writing the script out in a file. I was utterly confused when I began programming, so yes, that is quite normal. For a 12 year old, even. Do not set your bar of expectations too high.

Read the stickies at the top of this forum, and have fun.

---

### Post by flyingsliverfin on 2008-11-24
I do not quite understand what you mean. 

All I do is just (if I wanted to) open text editor, save my script or whatever I wrote on my desktop, go to applications -> programming->python(v2.5)

from inside I just type python 1st_script? (thats what I called my first document) when I tried it, it didn't work.



what stickies are you taling about? (new to this)

---

### Post by cardboardtoast on 2008-11-24
Let me see if I can help =)

Open the editor, save the file as *filename*.py

> I wrote on my desktop, go to applications -> programming->python(v2.5) from inside I just type python 1st_script?
open the regular terminal, not the python "terminal" and type:
python *filename.py*

The stickies for the forum.  They should be the at the top of the list of threads =)

> when I start the built-in python app in my applications bar, it looks just like a terminal (is it supposed to??) . 
yes, python will run in the terminal

---

### Post by ibutho on 2008-11-24
Hi. What you can do is write your python scripts and save them somewhere like /home/user/myscripts. After that run Applications -> Accessories -> Terminal and do
```
cd myscripts
python myscript.py

```

When you start Python from the menu or by entering "python" in the terminal, you run the interactive interpreter.

---

### Post by jimi_hendrix on 2008-11-24
or if your lazy put #!/bin/python at the top of your code...like

```

#!/bin/python
print "hello world"

```and twelve is fine...we have a thread around here about programming languages for kids...and i learned C# at 13 (take a look at it if you want...its made for windows, but can run on linux...python is probably better though)

also if you installed linux yourself and know C and BASIC you should be fine (try and find the analogies in the syntax... like if <tab> = if() {})

---

### Post by flyingsliverfin on 2008-11-24
I didn't install ubuntu on my own.

I really don't like C (syntax)

And I checked the thread about programming languages for kids. (I thought it was made clear that python was a good place to start)


Any good websites that explain and show all the commands and syntax for python>

ty

---

### Post by flyingsliverfin on 2008-11-24
thank you cardboardtoast, now I know how to execute scripts from the terminal

---

### Post by tiachopvutru on 2008-11-24
> **flyingsliverfin said:**
> I didn't install ubuntu on my own.

I really don't like C (syntax)

And I checked the thread about programming languages for kids. (I thought it was made clear that python was a good place to start)


Any good websites that explain and show all the commands and syntax for python>

ty

[pmasiar's wiki]("http://learnpython.pbwiki.com/HowToStart") has a collection of links which you can learn Python from. I'm only still a Python beginner, but if you are new to programming, from my experience, you can bet on having to read a few books before understanding anything.

[pmasiar]("http://ubuntuforums.org/member.php?u=130379") is a forum member here if you haven't already knew.

---

### Post by pmasiar on 2008-11-24
tiachopvutru, thanks for promoting my wiki ;-)

OP: you need to build more patience. Problems with computers is they do exactly what told to do, and not what you though you tell them to do. So if they do something different that you wanted, it is because you don't know (yet) how to tell them. And yes, it is normal to have problems learning - 20 years ago rarely 12 years old had problems you have now ;-)

See my wiki for links - try multiple tutorials, if you get stuck, try another one, then return. Each one will teach you little. And learning Python in interactive mode (shell) is the easiest way, wiki has the links.

Read more, and follow tutorials. If you want to spend some money, consider buying membership in showmedo.com/python, I assume young generations likes that stuff (screencasts etc, I prefer paper books).

---

### Post by jimi_hendrix on 2008-11-24
> **flyingsliverfin said:**
> I really don't like C (syntax)

pascal then...it was made for teaching and has a more BASIC syntax

---

### Post by tiachopvutru on 2008-11-25
> **pmasiar said:**
> tiachopvutru, thanks for promoting my wiki ;-)


Well, I have been using your wiki ever since I started learning Python. (This is to the OP as well...) In fact, Dick Baldwin's tutorial was the first tutorial of the subject that I learned (but I wish it covered more than just string, list, tuple, and dictionary). I kinda regret not following the wiki about reading the books in that order, though. I was obsessed with finding *one* single book that goes into a lot of details and settled on Learning Python 3rd Edition right after (as my second tutorial on the subject). I might have saved more time if I followed your order of books and tutorials and then used Learning Python for supplement details.

I suppose I was quite desperate to get done with Python (syntax) and got on with programming, but now that I'm here, I find it more challenging on finding where to head next. Python's "[battery included]("http://en.wikipedia.org/wiki/Python_(programming_language)#Standard_library")" model means that I need a clear goal of what I want to do (which I don't have) in order to do something (so I'm stuck) because each module does its own thing. That's also why I made a thread a while back asking for some general most widely-used modules.

Well, I suppose my experience that the OP could learn from (if it helps at all)...

---

### Post by pmasiar on 2008-11-25
Thanks again for feedback about order of learning - Would you mind if I used your comment on my wiki?

You are 100% right that you need some goals (what to code) when learning language - that's why I included so many training tasks. They are trivial for experienced programmer - so exactly right for a beginner ;-)

---

### Post by flyingsliverfin on 2008-11-25
ok, im going to check out your wiki soon, but   i found this online book at

[http://www.ibiblio.org/g2swap/byteofpython/read/index.html](http://www.ibiblio.org/g2swap/byteofpython/read/index.html)

it seems to be pretty thorough.

 when you go about 10-14 pages forward 
(link: [http://www.ibiblio.org/g2swap/byteofpython/read/choosing-an-editor.html](http://www.ibiblio.org/g2swap/byteofpython/read/choosing-an-editor.html))

it tells me about choosing an editor. I want to learn VIM, but can't seem to figure it our very much. I was wondering, could I just use text editor???


I don't want to think about learning another language right now (in reply to jimi_hendrix), but I made a plan to learn JAVA after I finish python. (I think theres also a java class in highschool)

---

### Post by jimi_hendrix on 2008-11-25
> **flyingsliverfin said:**
> 
I don't want to think about learning another language right now (in reply to jimi_hendrix), but I made a plan to learn JAVA after I finish python. (I think theres also a java class in highschool)

i never said you had to learn another language :)

if python is what you like then thats good...i personally hate whitespace langauges like python

i just mentioned pascal because its more BASIC like and you have experience with some form of BASIC...you wont find many main stream pascal things but it is still a nice language

i mentioned C# because thats what i learned at 13 and you asked if you should be confused at age 12...

(personal opinion- C# > JAVA...especially when the names of the objects make sense (panes?) and a few other quarks...why does it have to be a microsoft langauge though :( and if you know one you can program in the other)

---

### Post by tiachopvutru on 2008-11-25
> **pmasiar said:**
> Thanks again for feedback about order of learning - Would you mind if I used your comment on my wiki?

Please feel free to. :)

> **flyingsliverfin said:**
> it tells me about choosing an editor. I want to learn VIM, but can't seem to figure it our very much. I was wondering, could I just use text editor???

Yes. If Laroza was still here, she would say that gedit (the text editor in your Ubuntu installation) with its plugins provides a powerful editor and is quite sufficient for writing code. It has been what I used ever since I started learning.

---

### Post by days_of_ruin on 2008-11-25
> **tiachopvutru said:**
> Please feel free to. :)



Yes. If Laroza was still here, she would say that gedit (the text editor in your Ubuntu installation) with its plugins provides a powerful editor and is quite sufficient for writing code. It has been what I used ever since I started learning.

Vim is hard to learn but you will save a LOT of time once you get used to it.:w

---

### Post by flyingsliverfin on 2008-11-26
in reply to tiachopvutru, I think I will use text editor, but how do i install the plugins, or are they already installed? I wrote a tiny program in it, savd and re-opened. the text was already colored for me (leading me to think that the plugins are already there)

---

### Post by fiddler616 on 2008-11-26
> **flyingsliverfin said:**
> ok, im going to check out your wiki soon, but   i found this online book at

[http://www.ibiblio.org/g2swap/byteofpython/read/index.html](http://www.ibiblio.org/g2swap/byteofpython/read/index.html)

it seems to be pretty thorough.

 when you go about 10-14 pages forward 
(link: [http://www.ibiblio.org/g2swap/byteofpython/read/choosing-an-editor.html](http://www.ibiblio.org/g2swap/byteofpython/read/choosing-an-editor.html))

it tells me about choosing an editor. I want to learn VIM, but can't seem to figure it our very much. I was wondering, could I just use text editor???


I don't want to think about learning another language right now (in reply to jimi_hendrix), but I made a plan to learn JAVA after I finish python. (I think theres also a java class in highschool)
I was opening my mouth to recommend that tutorial as a concise but complete start to the language.

I was also opening my mouth to recommend gedit--it's one thing to learn a programming language, and another to learn vim/emacs, and these should not be combined. For plugins, just go to Edit->Preferences->Plugins (Tab) and check/uncheck what you want. Note that some of them require the "Bottom Pane" to be open (View menu)

Do yourself a favor, and don't learn a second language until you think you've really got a good grasp of Python. If you're wondering whether you do or not, you don't.

Welcome to the wildly wonderful world of programming!

---

### Post by tiachopvutru on 2008-11-26
In addition to the plugins, also inside Preference, click on the Editor tab. In there, set Tab width to 4, and check "Insert spaces instead of tabs," so now whenever you press Tab, it inserts 4 spaces instead.

In Python, it's never recommended to mix both tabs and spaces for indentation, so this is for that purpose. 4 spaces for each indent is sort of a standard style.

As for plugins, several of them are already there, which you can find and enable if you follow fiddler's instruction. Those should be sufficient for your need, but if you want even more plugin, you can install the package "gedit-plugins" in Synaptic.

There are even more if you google for other third-party plugins, but you have to install them manually.

---

### Post by nvteighen on 2008-11-26
> **jimi_hendrix said:**
> pascal then...it was made for teaching and has a more BASIC syntax

Actually, both BASIC and Pascal are influenced by ALGOL and ALGOL 60, respectively (among others, of course). ([http://en.wikipedia.org/wiki/Pascal_(programming_language](http://en.wikipedia.org/wiki/Pascal_(programming_language)) and [http://en.wikipedia.org/wiki/BASIC](http://en.wikipedia.org/wiki/BASIC))

Off-topic question: What languages beside Lisp, FORTRAN and COBOL are not ALGOL-influenced!? Even C is derived from there (ALGOL 60->CPL->BCPL->B->C... though B and C were just different stages of the same project)

---

### Post by flyingsliverfin on 2008-11-26
for fiddler616, you're right that I don't have a good grasp on python at all, (obviusly, I only started 3 days ago, but I don't expect you to know that) and that Im not going to start java until highschool. (Im going to take the java class in 9th or 10th grade) Im only in 7th grade so there is plenty of time to learn python. Or should I set aside more time for it?

---

### Post by fiddler616 on 2008-11-26
> **flyingsliverfin said:**
> for fiddler616, you're right that I don't have a good grasp on python at all, (obviusly, I only started 3 days ago, but I don't expect you to know that) and that Im not going to start java until highschool. (Im going to take the java class in 9th or 10th grade) Im only in 7th grade so there is plenty of time to learn python. Or should I set aside more time for it?
Oh, OK then.

Your competency in Python is directly related to how much work you put into it.
I'd recommend:

[LIST]
[*]Finishing *A Byte of Python*
[*]Doing a few easy practice programs (he recommends making an address book)
[*]Try to get involved in a collaborative project started here (the forums) the current one is PycTacToe, for example.
[*]You're probably ready for Java now.
[*]Look into GUIs, web development, more of the standard library, etc.
[/LIST]
The most important thing is not to get discouraged--I started and ended C++ in 7th grade, and have regretted it ever since.

---

### Post by flyingsliverfin on 2008-11-26
hm. of course I already have gone through a lot on languages, BASIC i stopped after a few weeks, but learned quite a bit.I tried FLASH MX ect.

I quit them all because I either 1.) was to lazy to continue 2) got discouraged or 3)got bored of it.

I'll do my best not to quit python anytime soon. 

just a question, what languages are good for web development (except java?)

I won't start them anyway. Too much on my plate. I am forced to do python only on the weekends now! (don't ask why) gotta go, dinner

---

### Post by pmasiar on 2008-11-26
> **nvteighen said:**
> Off-topic question: What languages beside Lisp, FORTRAN and COBOL are not ALGOL-influenced!? 

There are plenty: from top 50 in [http://www.tiobe.com/](http://www.tiobe.com/) index: Forth, Prolog, ML, APL (even if top 20 are mostly Algol family).

Interesting: Delphi replaced Ruby at TIOBE top 10. Python is going up, Ruby down... Seems like Python/Ruby question is beginning to settle.

@flyingsliverfin: Python is just fine for web apps. Django/Turbogears is one of the reasons why Python wrestled supremacy in web apps back from Ruby and Perl. PHP is separate category (for messy unmaintainable apps :twisted: )

---

### Post by flyingsliverfin on 2008-12-14
just wondering, (I haven't finished A BYTE OF PYTHON yet)but is python also used to make images and circles, lines ect?

for instance  quick basic could do that....it seems a tiny bit like python.

---

### Post by wmcbrine on 2008-12-14
> **flyingsliverfin said:**
> just wondering, (I haven't finished A BYTE OF PYTHON yet)but is python also used to make images and circles, lines ect?

for instance  quick basic could do that....it seems a tiny bit like python.You can do that, but not quite the way you would in QuickBASIC. That's from a DOS environment; you just tell it to go into graphics mode, and draw away. Python has no such expectations about its environment. You'll need to import a particular library to draw with, and do more setup first -- typically either a GUI-oriented library (like Tkinter), or a game-oriented one (like pygame).

---

### Post by nvteighen on 2008-12-14
> **flyingsliverfin said:**
> just wondering, (I haven't finished A BYTE OF PYTHON yet)but is python also used to make images and circles, lines ect?

for instance  quick basic could do that....it seems a tiny bit like python.
That's because DOS had a special (S)VGA graphic mode... do you remember the SCREEN statement in QB, don't you? That statement was needed in order to use CIRCLE, DRAW, etc. (SCREEN 0, (S)VGA text mode; SCREEN 1-8, graphic modes)

A tty or tty-like (aka Terminal emulator) console works differently... and provide just text-based capabilities... the most you can get from a terminal/console is what ncurses gives you. Anything else needs X11 (or the kernel's framebuffer, as the Ubuntu splash image does).

---

### Post by pmasiar on 2008-12-14
> **wmcbrine said:**
> Python has no such expectations about its environment. 

Python is cross-platform.

Many problems can be solved much simpler if you do not care about other platforms.

---

### Post by wmcbrine on 2008-12-14
Yes.

---

### Post by nvteighen on 2008-12-14
> **wmcbrine said:**
> yes.
sí

---

### Post by mssever on 2008-12-14
> **nvteighen said:**
> sí
Aet :)

---

### Post by pmasiar on 2008-12-14
> **mssever said:**
> Aet :)
igen

---

### Post by nvteighen on 2008-12-15
> **mssever said:**
> Aet :)

> **pmasiar said:**
> igen

Languages?

---

### Post by mssever on 2008-12-15
> **nvteighen said:**
> Languages?
*Aet* is one of two Marshallese words for *yes*. The other is *iñe* (if my memory serves me correctly). The Marshallese ñ is pronounced like *ng* in *sing*.

---

### Post by flyingsliverfin on 2008-12-17
thx for the replies

---

