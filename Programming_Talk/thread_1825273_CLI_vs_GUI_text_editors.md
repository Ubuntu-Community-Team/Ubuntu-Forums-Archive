---
title: "CLI vs GUI text editors"
date: 2011-08-15
forum: Programming Talk
---

### Post by ninjaaron on 2011-08-15
So, this isn't a question of vim vs emacs or gedit vs kate.  Those questions are already solved.  Everyone knows that vim is better than emacs and gedit owns every other gui text editor out there.

I've begun to do a lot more with my text editor, partially because I'm writing more scripts these days, and partially because I've started doing all of my academic work in pure text and then dropping it into an ott, TeX, or html template when it comes time to publish (cause pure text is compatible with everything and always will be).  Up until now, I've normally just used gedit (or pyroom, a fullscreen "distraction free" editor), but I've played around with vim a little.

I'm wondering, if I'm doing all my writing in plain text, do the interfaces provided by CLI editors provide great advantages over GUI editors or vice versa.  I can see some advantages but also some drawbacks to both, especially when it comes to writing sentences and paragraphs where the lines are much longer than in a program.

edit: also significant: for academics, I deal a lot with linguistics, I tend to use a lot of special diacritics and unicode characters as well as RTL languages like Hebrew, Aramaic, and Syriac.

---

### Post by FreeTheBee on 2011-08-15
I hope that first line doesn't start another vim vs. emacs war, I'd say both have their strengths and which is better is fairly subjective. In the end you should just play with different editors I think and pick the one that works best for you.

Personally, I almost exclusively use vim, either on cli or gvim. In gvim I hide the toolbars, so there's not much difference between the two, except with some colour schemes. I don't have any problems problem writing long lines or paragraphs. You can let vim do wrapping with either soft or hard breaks or none at all, and have it depend on the file type. 

I never have the need to for writing Hebrew and such, but it seems there is a Hebrew mode in Vim.

[http://vimdoc.sourceforge.net/htmldoc/hebrew.html]("http://vimdoc.sourceforge.net/htmldoc/hebrew.html")

---

### Post by don_quixote on 2011-08-15
> **ninjaaron said:**
> So, this isn't a question of vim vs emacs or gedit vs kate.  Those questions are already solved.  Everyone knows that vim is better than emacs and gedit owns every other gui text editor out there.

I don't know about gedit, but it is true that vim has no peer!

> **ninjaaron said:**
>  I've begun to do a lot more with my text editor, partially because I'm writing more scripts these days, and partially because I've started doing all of my academic work in pure text and then dropping it into an ott, TeX, or html template when it comes time to publish (cause pure text is compatible with everything and always will be).  

Good for you!  Seriously, all work, academic or not, should be done this way.  The triumph of the WYSIWYG editors has been a huge step back for basic productivity, and all because of the perceived learning curve (which, with tools like pan2doc which let you mix ludicrously simple Markdown with full LaTeX makes this point moot).

> **ninjaaron said:**
> Up until now, I've normally just used gedit (or pyroom, a fullscreen "distraction free" editor), but I've played around with vim a little.

I'm wondering, if I'm doing all my writing in plain text, do the interfaces provided by CLI editors provide great advantages over GUI editors or vice versa.  I can see some advantages but also some drawbacks to both, especially when it comes to writing sentences and paragraphs where the lines are much longer than in a program.

edit: also significant: for academics, I deal a lot with linguistics, I tend to use a lot of special diacritics and unicode characters as well as RTL languages like Hebrew, Aramaic, and Syriac.

I love dropping into tty and using vim, frankly, because I really think it's the most distraction free way to edit (though I've never tried pyroom).  Gedit is not a bad program but it's not nearly as quick as vim is for most tasks.  Vim is very, very (very!) fast and that is the reason why I prefer it to anything.  I'm not sure how comfortable you are with vim but it does take a little bit of time to be lightning quick with it, but frankly not as much as I think most people make it out to be.  I find the learning curve to be very intuitive, and I also think vi is considerably more extensible than Gedit.    

I can't help with special diacritics and unicode, but I do know that vim can be made to do RTL.

---

### Post by 3Miro on 2011-08-15
I think being sufficiently comfortable with at least one CLI editor is a must, you can't always rely on graphics. On the other hand, if you can get fast enough graphical editor with all the functionality that you need, then go for it.

The other point is that you can have multiple editors for different tasks. I am using several GUI editors:

1. Leafpad is lightning fast and it is the default for every text file. Just click and you have it.
2. Geany provides syntax highlights, tabs and formatting, although slower, it is more advanced and this is what I use for C++ and Python.
3. Texmaker is for LaTeX specifically, IMO nothing comes even close to its power. The only problem is that Texmaker is very specialized and it isn't good for anything other than LaTeX.
4. Code::Blocks is also very specialized and I don't use it much, but it provides great tools for C/C++. I used to need more project management tools and Code::Blocks comes with quite a few of those.
5. Gedit is a mid-way thing between Geany and Leafpad, I do get some syntax highlights and tabs, but not all the functions of Geany. I don't use it very often.

---

### Post by ssam on 2011-08-15
if you can spend a bit of time learning vim (or emacs) then they can be very powerfull, especially for coding. they are actions and movements, and you can string them together. for example "df)", delete-find-")", dlete everything up to the next ")".

if you have lines that are longer than the screen width (i do a whole paragraph without a line break), then you can use 'gk' and 'gj' for up and down. also if you enable mouse mode then you can click to move the cursor ( [http://vim.wikia.com/wiki/Using_the_mouse_for_Vim_in_an_xterm](http://vim.wikia.com/wiki/Using_the_mouse_for_Vim_in_an_xterm) ).

---

### Post by FuturePilot on 2011-08-15
> **ninjaaron said:**
> Everyone knows that vim is better than emacs and gedit owns every other gui text editor out there.

Are you trying to start a flame war?

---

### Post by DZ* on 2011-08-15
A great CLI editor: ```
emacs -nw
```;)

---

### Post by cgroza on 2011-08-15
I am an emacs user. And the GUI/CLI difference is not that big in my case.
I can use the GTK GUI, or drop in a terminal and start it using emacs -nw.
In the CLI version, you even get a GUI-like menubar.

The shortcuts make you incredibly fast, and you don't even need to leave the editor, except for web browsing.

I normally have a bunch of source files, a few IRC channels, a shell and a man page buffer (Yes, I don't leave my emacs just to look at a man page, they have an extension for that.) opened in my Emacs.

---

### Post by ninjaaron on 2011-08-15
> **don_quixote said:**
> I don't know about gedit, but it is true that vim has no peer!
gedit is nice. It handles bi-directional text better than vim, so it's a necessity for me at certain points in the editing process.  It's quite extensible, and I hear it can even be made to support vi style modes and bindings.  It has a lot of nice plugins for TeX and stuff as well. It may not be as extensible as vim, but it's pretty darn extensible.

> 
I love dropping into tty and using vim, frankly, because I really think it's the most distraction free way to edit (though I've never tried pyroom).This was my initial plan, but the console fonts don't seem to support all the unusual diacritics I find myself needing. Using a full screen terminal in the GUI seems to work just as well and I can use more complete fonts there.  Of course, it isn't quite as speedy as the console.

The other problem I'm having is that it becomes a bit difficult to read paragraphs of text when the lines span across the entire screen.  This is isn't really a problem with scripting so much, since you read each line as idea unto itself, and most of them are rather more short than in prose.  I have a sneaking suspicion that there must be a way to modify the width of the buffer, but I haven't discovered it.
> I'm not sure how comfortable you are with vim but it does take a little bit of time to be lightning quick with it, but frankly not as much as I think most people make it out to be.  I find the learning curve to be very intuitive, and I also think vi is considerably more extensible than Gedit.It won't be a problem for me.  I had started learning it in the past, and I forgot, but I'm doing the tutorial again, and it's coming back quickly.  I also just installed the "pentadactyl" extension in Firefox, which allows you to navigate and edit with vi bindings, which forces me to use them all time, and therefore reinforces the bindings while giving me a faster, keyboard-based browsing experience.
> **3Miro said:**
> I think being sufficiently comfortable with at least one CLI editor is a must, you can't always rely on graphics. On the other hand, if you can get fast enough graphical editor with all the functionality that you need, then go for it.

The other point is that you can have multiple editors for different tasks. I am using several GUI editors:

1. Leafpad is lightning fast and it is the default for every text file. Just click and you have it.
2. Geany provides syntax highlights, tabs and formatting, although slower, it is more advanced and this is what I use for C++ and Python.
3. Texmaker is for LaTeX specifically, IMO nothing comes even close to its power. The only problem is that Texmaker is very specialized and it isn't good for anything other than LaTeX.
4. Code::Blocks is also very specialized and I don't use it much, but it provides great tools for C/C++. I used to need more project management tools and Code::Blocks comes with quite a few of those.
5. Gedit is a mid-way thing between Geany and Leafpad, I do get some syntax highlights and tabs, but not all the functions of Geany. I don't use it very often.
I was using a leafpad for a while, but the lack of syntax highlighting killed it for me, and the extra half second it takes for gedit to load doesn't bother me.  As far as TeX and sophisticated syntax functions gedit has plugins for all of that stuff, though I can't comment much on their quality, not being a very serious programmer.

---

### Post by ninjaaron on 2011-08-15
> **FuturePilot said:**
> Are you trying to start a flame war?

That isn't my primary goal, but if it happens after I get the information I want, I will consider it a bonus.

:P

---

### Post by 3Miro on 2011-08-15
> **ninjaaron said:**
> I was using a leafpad for a while, but the lack of syntax highlighting killed it for me, and the extra half second it takes for gedit to load doesn't bother me.  As far as TeX and sophisticated syntax functions gedit has plugins for all of that stuff, though I can't comment much on their quality, not being a very serious programmer.

Lack of syntax is both strength and weakness. Leafpad is the fastest editor to quickly open a file and take a peek, not all files are code and not all of them require syntax, sometimes highlights are not as important as getting things done fast. If you want to edit the code you spend the extra time for Geany or Gedit.

The LaTeX plugins for Gedit does give syntax highlights, but Texmaker gives commands and has a bunch of inbuild macros and it can directly call the compiler and pdf viewer and just so much more.

In short, I don't have "One Editor to Edit All" (I had one but some hobbit took it and tossed in a volcano). What I do is I use a variety of highly specialized editors for the different tasks. Works well for me, you may think about trying it instead of looking for one editor that can do all of your needs well you may find a bunch of editors that do all of your needs great.

---

### Post by unknownPoster on 2011-08-15
> **ninjaaron said:**
> That isn't my primary goal, but if it happens after I get the information I want, I will consider it a bonus.


Really? That's one of the most immature things I've heard lately. Not sure the staff will look kindly upon you wanting a flamewar.

---

### Post by ninjaaron on 2011-08-15
> **ninjaaron said:**
> 
The other problem I'm having is that it becomes a bit difficult to read paragraphs of text when the lines span across the entire screen.  This is isn't really a problem with scripting so much, since you read each line as idea unto itself, and most of them are rather more short than in prose.  I have a sneaking suspicion that there must be a way to modify the width of the buffer, but I haven't discovered it.
got it. [FONT="Courier New"]:set tw=n[/FONT]

Perfect.

---

### Post by el_koraco on 2011-08-15
> **unknownPoster said:**
> Really? That's one of the most immature things I've heard lately. Not sure the staff will look kindly upon you wanting a flamewar.

He was obviously joking, take it easy.

---

### Post by unknownPoster on 2011-08-15
> **el_koraco said:**
> He was obviously joking, take it easy.

Obviously not. 

You can't read sarcasm.

---

### Post by ninjaaron on 2011-08-15
> **unknownPoster said:**
> Really? That's one of the most immature things I've heard lately. Not sure the staff will look kindly upon you wanting a flamewar.

It's not going to happen, so you can get over it.  It's a dead horse, and the most obvious possible troll bait on Linux forum.  If it does start a war, ubunutforums.org can hold me personally responsible for any physical casualties that may occur in the process.

---

### Post by unknownPoster on 2011-08-15
> **ninjaaron said:**
> It's not going to happen, so you can get over it.

You'd be surprised.

You should also market your ability to predict both the future and other people's actions.

---

### Post by ninjaaron on 2011-08-15
Oh! I do love surprises!

---

### Post by Elfy on 2011-08-15
moved to support forum - no support posts removed - keep the remainder of this to the support requested

---

### Post by ninjaaron on 2011-08-15
Interesting.  Gone without a trace.
:shock:

---

### Post by BrokenKingpin on 2011-08-15
For normal document editing I mainly use gedit. I do use VI on occasion when editing config files from the terminal.

In the past I used VI all my coding, but now use a graphical IDE (eclipse for example). If you know all the shortcuts for VI it is very powerful, but I have forgotten all but the basics over the years.

---

### Post by ninjaaron on 2011-08-16
I'm still trying to figure out what this thread has to do with programming, as I use plain text more for writing prose and email than programming...  and the extent of my programming ability is limited to bash...

Ah well, the issue is solved, kinda.  I'm using vim as my primary editor now.

---

### Post by Bachstelze on 2011-08-16
I reported the thread saying it had been moved in error but no effect. Go figure...

---

