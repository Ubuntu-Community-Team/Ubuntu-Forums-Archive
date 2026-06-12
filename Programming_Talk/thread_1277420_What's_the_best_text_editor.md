---
title: "What's the best text editor?"
date: 2009-09-28
forum: Programming Talk
---

### Post by BlackSwordD2 on 2009-09-28
as a budding cs major im learning several languages at once an dmost of the time im in linux doing so. what are some of the best text editors around that would help for multiple languaging?

i was using simply the text editor and have now moved on to kwrite, what im looking for is a editor that at least color codes code and if possible allows when i select a varible it also highlights all other instances of the varible (i've seen this done in the netbeans compiler).

for the most part kwrite is everything that i need, bu ti want to know if there is something bigger and better hiding out there.

---

### Post by pmlxuser on 2009-09-28
vi if you got the guts

or just

vim (vi improved)

---

### Post by BlackSwordD2 on 2009-09-28
is vi the one that runs out of the terminal?

---

### Post by benj1 on 2009-09-28
> **pmlxuser said:**
> vi if you got the guts

or just

vim (vi improved)

emacs is better ;)



moved to reccurring discussions in 5, 4, 3, 2, 1

---

### Post by benj1 on 2009-09-28
> **BlackSwordD2 said:**
> is vi the one that runs out of the terminal?

yes as does emacs, give them a try (with a tutorial in hand)

it very much a 'whats you favourite ice cream' question, it depends on your preferences, do a google search and give some a try, thats the best way of finding one.

---

### Post by howlingmadhowie on 2009-09-28
to be fair, both emacs and vim have huge learning curves to start with, and can both do absolutely everything once you've got the hang of them (which will probably take about a year---no joke).

---

### Post by cb951303 on 2009-09-28
if you're on kde I would try "kate" instead of "kwrite". that will do everything you need and then some more...

---

### Post by TheBuzzSaw on 2009-09-28
Code::Blocks for C++

Text Editor for everything else... :3

---

### Post by matthew.ball on 2009-09-28
> **howlingmadhowie said:**
> to be fair, both emacs and vim have huge learning curves to start with, and can both do absolutely everything once you've got the hang of them (which will probably take about a year---no joke).
I think you can get a hang of emacs after a few days of use.

I would also recommend using screen, and as a CS major, you should be familiar with either emacs or vim :p

---

### Post by MindSz on 2009-09-28
vim and exmacs are very popular (I use emacs) but if you don't want to suffer through the learning curve of these programs, try gedit. It comes with ubuntu and it has all kinds of nice things if you wanna use it for programming (line numbers, highlighting, etc). Plus, it allows you to open several files in tabs instead of new windows.

---

### Post by matmatmat on 2009-09-28
If you do decide to use vim type:
```

$vimtutor

```
for a tutorial.If you decide you like it [you can use it with firefox!]("http://vimperator.org/trac/wiki/Vimperator")

---

### Post by BlackSwordD2 on 2009-09-28
> **cb951303 said:**
> if you're on kde I would try "kate" instead of "kwrite". that will do everything you need and then some more...

i just got kate and i think i found something a lot closer to what i really want

---

### Post by chrisjsmith on 2009-09-29
Eclipse!  Undoubtably!

---

### Post by Jimleko211 on 2009-09-29
Geany is pretty awesome, as well.

---

### Post by A_Fiachra on 2009-09-29
> **BlackSwordD2 said:**
> as a budding cs major im learning several languages at once an dmost of the time im in linux doing so. what are some of the best text editors around that would help for multiple languaging?

i was using simply the text editor and have now moved on to kwrite, what im looking for is a editor that at least color codes code and if possible allows when i select a varible it also highlights all other instances of the varible (i've seen this done in the netbeans compiler).

for the most part kwrite is everything that i need, bu ti want to know if there is something bigger and better hiding out there.


If you are suddenly dropped into an unfamiliar *nix terminal and you have to get things working quickly, will kwrite be there?  Honestly, you are not always going to have X (ssh, fresh box) but you will always have vi.  So it is essential (IMO) to learn it to be productive across *nix platforms.

It takes two weeks to get it under your fingers.

---

### Post by engla on 2009-09-29
I use vim. Before that, I used gedit; both can be used very successfully I guess; I am yet to find the bottom of vim -- constantly learning new stuff and configuring new smarts after what, two three years I think.

(Today I learned that if you have the cursor inside some brackets like these, type 'ci(' all the text inside the brackets are deleted and your cursor is placed to replace with something. 'di(' is equivalent but simply deletes.)

I recommend gedit if you want something familiar. Configure the snippets plugin it is really awesome for inserting quick template code (function definitions and whatever).

I recommend vim if you have time to learn. It pays off but I think it takes dicipline. One feature I enjoy a lot is code folding, so that you can toggle hide/show of individual pieces of a file.

----
(I have never used Geany, so if others say it's great, try it!)

---

### Post by thoriumchameleon on 2009-09-29
You probably shouldn't be thinking text editor more than IDE... Integrated Development Environment if you don't already know. I would suggest a program such as Eclipse especially if your programming a lot in Java. It imports automatically when you use a method and say you start to type JOptionPane.s... as soon as you type that period it will come up with a whole bunch of suggestions of methods that use the JOptionPane... It can be very helpful when you don't fully remember how to code a certain line.

---

### Post by jimi_hendrix on 2009-09-29
> **matthew.ball said:**
> I think you can get a hang of emacs after a few days of use.

I would also recommend using screen, and as a CS major, you should be familiar with either emacs or vim :p

> **A_Fiachra said:**
> If you are suddenly dropped into an unfamiliar *nix terminal and you have to get things working quickly, will kwrite be there?  Honestly, you are not always going to have X (ssh, fresh box) but you will always have vi.  So it is essential (IMO) to learn it to be productive across *nix platforms.

It takes two weeks to get it under your fingers.

it takes less than a day imo, just memorize a few command (esc, i, v, :wq, yy, p, dd, :syn on, <indent command of choice that you can throw in your .vimrc>) and you are good

if you cant do vim, eclipse is great because of all of its plugins and it has other solid features

---

### Post by korvirlol on 2009-09-29
if youre planning on using an in-terminal one, emacs is probably the strongest in my opinion.

Otherwise, the best text editor for multiple programming languages (imo) is scite... absolutely LOVE it.

---

### Post by fiddler616 on 2009-09-29
If you haven't noticed the trend: Either Vi(m) or Emacs, eventually.

If you're running GNOME, I recommend ViGedit (a plugin for gedit that keeps it's easy gedit-y features, but also throws in many many vim commands.

<Shameless plug>Here's a blog post to get you going: [http://blog.tsmacdonald.com/archives/312](http://blog.tsmacdonald.com/archives/312) </plug>
And if you look at the last few comments, you'll see updated instructions to get a new (apparently much better) version.

---

### Post by ApEkV2 on 2009-09-30
Install Wine and then you can use Notepad++ (awesomeness incarnate). And it works perfect for me (no glitches).
But if your scripting in Bash for instance, Gedit with the plugins would probably be better.

---

### Post by Jekshadow on 2009-09-30
Eclipse for an all-in-one solution (built in cvs support!), or gEdit for lightweight stuff.

---

### Post by fiddler616 on 2009-09-30
> **ApEkV2 said:**
> Install Wine and then you can use Notepad++ (awesomeness incarnate). And it works perfect for me (no glitches).
But if your scripting in Bash for instance, Gedit with the plugins would probably be better.
What? gedit (assuming you activate IDE-y plugins (Edit>Preferences>Plugins)) is a lot better than Notepad++, IMHO. More features, easier to use, runs natively...what's not to love?

---

### Post by wmcbrine on 2009-10-01
> **BlackSwordD2 said:**
> is vi the one that runs out of the terminal?I think the vast majority of text editors (as opposed to word processors, or IDEs) run in terminals.

Personally I favor nano, with occasional vi[m].

---

### Post by bhagabhi on 2009-10-01
try SciTE

[http://www.scintilla.org/SciTE.html](http://www.scintilla.org/SciTE.html)

---

### Post by leandromartinez98 on 2009-10-03
> **ApEkV2 said:**
> Install Wine and then you can use Notepad++ (awesomeness incarnate). And it works perfect for me (no glitches).
But if your scripting in Bash for instance, Gedit with the plugins would probably be better.


Forgive him, father, he doesn't know what he is saying! :eek:


Don't waste your time, learn Vim or Emacs, these are the most
powerful editors out there. You may take some time to learn them,
but it will totally pay off. (Vim in particulary if you are a
touch-typist). I use vim. And it can run on the terminal or
not (gvim is the non-terminal one). And if you learn it you will
be editing stuff as effectivelly at your desktop, laptop, netbook,
remotelly through ssh, etc, because you don't even need the arrow or pageup/pagedown keys and it is very fast. And you won't need any
other editor (if you learn kate, for instance, to edit configuration
files you will use something else probably).

But for vim be prepared, you will probably want to kill someone
the first week before learning the basics.

---

### Post by fiddler616 on 2009-10-03
> **leandromartinez98 said:**
> Forgive him, father, he doesn't know what he is saying! :eek:


Don't waste your time, learn Vim or Emacs, these are the most
powerful editors out there....
But for vim be prepared, you will probably want to kill someone
the first week before learning the basics.
Can somebody either link to or write a tutorial entitled "Everything you need to know about Vim to survive" and cover:
[LIST]
[*]Modes
[*]:q, :wq, :w, :q!
[*]Copy and pasting
[*]A little bit of movement (hjkl, and...the next line/next paragraph ones)
[*]Find and replace
[/LIST]
And LEAVE IT AT THAT, so that amateurs (like myself) can get the same functionality out of Vim that they can get out of, say, gedit, and have a base on which to learn new things. Because I'll learn something like 'dw' deletes a word (I think...), and then forget about it since I don't use Vim on a regular basis, since I get shafted trying to do something like copy and paste.

---

### Post by river226 on 2009-10-03
If you just want a simple/powerful solution, notepad++ is the best, but emacs, and Vi/vim as this thread illustrates are the most highly regarded ones out there, but can be frustrating to use for a new user. so for a bare minimum learning curve, notepad++

---

### Post by fiddler616 on 2009-10-03
> **river226 said:**
> If you just want a simple/powerful solution, notepad++ is the best, but emacs, and Vi/vim as this thread illustrates are the most highly regarded ones out there, but can be frustrating to use for a new user. so for a bare minimum learning curve, notepad++
I don't want to flame, but...
Would someone please explain why everyone's so excited about notepad++? I've used it before (when gedit for Windows was not available), and remember a slight feeling of panic about all the icons littered everywhere. Does it have some kind of killer functionality not available in other code-friendly editors? (Kate, gedit, gVim, *Emacs, Geany (which is technically an IDE, but I see it as an editor with a "Run" button).

---

### Post by sujoy on 2009-10-03
the question was the best editor, not the easiest.
so invest some time, and learn either emacs/vim

those are worth every minute thats spent learning them

---

### Post by leandromartinez98 on 2009-10-03
> **fiddler616 said:**
> Can somebody either link to or write a tutorial entitled "Everything you need to know about Vim to survive" and cover:
[LIST]
[*]Modes
[*]:q, :wq, :w, :q!
[*]Copy and pasting
[*]A little bit of movement (hjkl, and...the next line/next paragraph ones)
[*]Find and replace
[/LIST]
And LEAVE IT AT THAT, so that amateurs (like myself) can get the same functionality out of Vim that they can get out of, say, gedit, and have a base on which to learn new things. Because I'll learn something like 'dw' deletes a word (I think...), and then forget about it since I don't use Vim on a regular basis, since I get shafted trying to do something like copy and paste.

[http://www.cheat-sheets.org/saved-copy/vimqrc.pdf](http://www.cheat-sheets.org/saved-copy/vimqrc.pdf)

To survive you only need [Esc], "i" and ":wq". With "i" you can
use vim as any other editor. 

That's the point, people that use Vim in a regular basis get used
to those commands (which are bizar at the begining, but are the
best at the end) and if you use Vim regularly you don't need 
(neither want) anything else. That is the great advantage of vim over the others, it is as powerful as the most powerful editors, and it ubiquitous
as the most ubiquitous editors. Again, this is particularly true
for touch-typists, other people may not see the advantages of the
bimodal structure as that great.

---

### Post by fiddler616 on 2009-10-03
> **leandromartinez98 said:**
> 
To survive you only need [Esc], "i" and ":wq". With "i" you can
use vim as any other editor. 
The problem (and maybe this is because I've only used Vim, not gVim) is that then you miss things in other editors--copying, pasting, finding, replacing, tabbing, untabbing...

---

### Post by fiddler616 on 2009-10-03
> **leandromartinez98 said:**
> [http://www.cheat-sheets.org/saved-copy/vimqrc.pdf](http://www.cheat-sheets.org/saved-copy/vimqrc.pdf)

Thanks.

---

### Post by TheStatsMan on 2009-10-03
> **fiddler616 said:**
> Can somebody either link to or write a tutorial entitled "Everything you need to know about Vim to survive" and cover:
[LIST]
[*]Modes
[*]:q, :wq, :w, :q!
[*]Copy and pasting
[*]A little bit of movement (hjkl, and...the next line/next paragraph ones)
[*]Find and replace
[/LIST]
And LEAVE IT AT THAT, so that amateurs (like myself) can get the same functionality out of Vim that they can get out of, say, gedit, and have a base on which to learn new things. Because I'll learn something like 'dw' deletes a word (I think...), and then forget about it since I don't use Vim on a regular basis, since I get shafted trying to do something like copy and paste.

[http://www.vim.org/docs.php](http://www.vim.org/docs.php)

The vim book is good.

---

### Post by A_Fiachra on 2009-10-04
> **fiddler616 said:**
> Can somebody either link to or write a tutorial entitled "Everything you need to know about Vim to survive" and cover:
[LIST]
[*]Modes
[*]:q, :wq, :w, :q!
[*]Copy and pasting
[*]A little bit of movement (hjkl, and...the next line/next paragraph ones)
[*]Find and replace
[/LIST]
And LEAVE IT AT THAT, so that amateurs (like myself) can get the same functionality out of Vim that they can get out of, say, gedit, and have a base on which to learn new things. Because I'll learn something like 'dw' deletes a word (I think...), and then forget about it since I don't use Vim on a regular basis, since I get shafted trying to do something like copy and paste.


[Et voila]("http://www.youtube.com/watch?v=XSXoap2h3Mw")

Or, if you prefer, [Here]("http://www.eng.hawaii.edu/Tutor/vi.html")

---

### Post by ad_267 on 2009-10-04
I found running "vimtutor" was a good way to learn vim. For everything else there's google.

---

### Post by A_Fiachra on 2009-10-04
> **jimi_hendrix said:**
> it takes less than a day imo, just memorize a few command (esc, i, v, :wq, yy, p, dd, :syn on, <indent command of choice that you can throw in your .vimrc>) and you are good

if you cant do vim, eclipse is great because of all of its plugins and it has other solid features


But how do I run eclipse on the machine I ssh to that isn't running X?  I understand your point and the question is rhetorical.  I'm pointing out my experience wrt to this issue: programmers who work on *nix systems and don't have a decent grasp of vi suffer.  Sometimes vim is a luxury!

:(

I worked with a smart guy who loved his GUI editors with syntax highlighting and command completion, we dropped some code on a vps centOS server and he'd hand the keyboard to me and say, "I'm lost!".

To the OP and anyone who suggested a GUI editor ... learn vi, the alternative is vi, and if that doesn't work, there is always vi.

:)

---

### Post by A_Fiachra on 2009-10-04
> **sujoy said:**
> the question was the best editor, not the easiest.
So invest some time, and learn either emacs/vim

those are worth every minute thats spent learning them

+2^64

:-)

---

### Post by StunnerAlpha on 2009-10-04
> **Jimleko211 said:**
> Geany is pretty awesome, as well.

+1

Geany is really lightweight but powerful.

---

### Post by fela on 2009-10-04
> **benj1 said:**
> emacs is better ;)

Anyone who says that is officially SILLY.

---

### Post by fela on 2009-10-04
If you've got the computer to run a GUI, I like kwrite.

Else, vim ftw!

---

### Post by benj1 on 2009-10-04
> **fela said:**
> Anyone who says that is officially SILLY.

nice come back.

see if you had emacs you could have used the 'comeback' mode :P

---

### Post by fela on 2009-10-04
> **howlingmadhowie said:**
> to be fair, both emacs and vim have huge learning curves to start with, and can both do absolutely everything once you've got the hang of them (which will probably take about a year---no joke).

Took me about 10 minutes to learn vim---no joke.

---

### Post by fela on 2009-10-04
> **benj1 said:**
> nice come back.

see if you had emacs you could have used the 'comeback' mode :P

emacs is a great operating system except one thing: it lacks a decent text editor :P

I know I know, it's the oldest one in the book, but still...it's a bit better than 'vi vi vi omgwtfbbq'.

---

### Post by ad_267 on 2009-10-04
> **fela said:**
> Anyone who says that is officially SILLY.

And rather suspect.

---

