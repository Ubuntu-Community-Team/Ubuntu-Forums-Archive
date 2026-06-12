---
title: "Which Gnome IDE do you recommend?"
date: 2006-05-01
forum: Programming Talk
---

### Post by el3ktro on 2006-05-01
So well I have some basic knowledge about programming, actually did Java a lot (with Eclipse) then played around with KDevelop/QT, but now I switched to Gnome entirely and want to seriously start some coding again. I've already heart about Glade and Anjute - both sound promising. But which IDE would YOU recommend for programming "real" Gnome/GTK2 applications? I definitely want some help creating a GUI, but otherwise I want some more or less plain coding tool, with code snippets, compiler/debuger integration etc.

What are your recommendations?

Tom

---

### Post by lnostdal on 2006-05-01
i'll probably be flamed for being old fashioned or something..  :) .. but for me, it's Emacs all the way ..    i even run Emacs as a front-end/interface to servers (under screen actually) .. it's rock solid

---

### Post by stuporglue on 2006-05-01
I'm almost with you Inostadal. I use vim (in screen) for all my coding, since most my stuff is just CLI programs.

I've only done GUI stuff on my Mac, but being able to drag-and-drop UI elements into place, and not have to hand write the code for it is such a great thing. I've been meaning to find a good IDE for Ubuntu/Linux, and am watching this thread for some good suggestions.

---

### Post by el3ktro on 2006-05-01
Um I know about emacs of course, but I'm more into vim for bash scripting. Well for such things vim/emacs or any CLI editor is just fine, but for "serious" programming of GUI apps, I also ant to have a nice graphical IDE. What do you guys think about Anjuta?

Tom

---

### Post by auroraborealis on 2006-05-02
Eclipse has C/C++ plugins.

---

### Post by lnostdal on 2006-05-02
[QUOTE=el3ktro]Um I know about emacs of course, but I'm more into vim for bash scripting. Well for such things vim/emacs or any CLI editor is just fine, but for "serious" programming of GUI apps, I also ant to have a nice graphical IDE. What do you guys think about Anjuta?

Tom[/QUOTE]

..what do you mean "serious"? .. heh ..  if i want something to draw the GUI with i use Glade .. :)

(when did programming/coding get "graphical" btw.?)

well, about Anjuta .. i tried it a couple of years ago - it was kind of buggy, but might have improved since then

---

### Post by asimon on 2006-05-03
If vim/emacs/etc. are not your favourite tools I would use kdevelop together with Glade if you're coding in C. If you use C# which is not unpopular for Gnome apps these days I would use monodevelop (with monodevelop I would use glade too and not the new GUI builder 'stetic', because the later is still alpha quality). 

Why not anjuta? Because kdevelop is much more powerful. Never restrict yourself to specific desktops when it comes to development tools. Use what's best suited for your task. Artificially restricting yourself to just Gnome (or KDE or ...) apps will do nothing then decrease your productivity.

---

### Post by MichaelZ on 2006-05-04
[quote=el3ktro]So well I have some basic knowledge about programming, actually did Java a lot (with Eclipse) then played around with KDevelop/QT, but now I switched to Gnome entirely and want to seriously start some coding again. I've already heart about Glade and Anjute - both sound promising. But which IDE would YOU recommend for programming "real" Gnome/GTK2 applications? I definitely want some help creating a GUI, but otherwise I want some more or less plain coding tool, with code snippets, compiler/debuger integration etc.

What are your recommendations?

Tom[/quote] 
Hello,

You can try [CodeBlocks]("http://www.codeblocks.org") and see if it fulfills your requirements and/or wishes. CodeBlocks has a RAD-plugin named wxSmith for developing GUI. 

You can download a .deb package from my signature.

Happy test :).

Best wishes,
Michael

---

### Post by kudu on 2006-05-05
[QUOTE=MichaelZ]Hello,

You can try [CodeBlocks]("http://www.codeblocks.org") and see if it fulfills your requirements and/or wishes. CodeBlocks has a RAD-plugin named wxSmith for developing GUI. 

You can download a .deb package from my signature.

Happy test :).

Best wishes,
Michael[/QUOTE]

Code::Blocks is pretty cool, though I'm not partial to QT look. How do I assign Gnome Terminal as console window instead of XTerm ?? Whats the correct setting ??

Regards,
kudu

---

### Post by tburns on 2006-05-05
you can use KDevelop in Gnome (w/ kdebaselibs). Jedit is good.

---

### Post by MichaelZ on 2006-05-05
[quote=kudu]Code::Blocks is pretty cool, though I'm not partial to QT look. How do I assign Gnome Terminal as console window instead of XTerm ?? Whats the correct setting ??

Regards,
kudu[/quote] 
Hello,

I think that you should modify the "Terminal to lunch console programs" (Settings-->Environment). Change xterm for the gnome terminal (probably you will have to change the parameters too).

Best wishes,
Michael

---

### Post by kudu on 2006-05-05
[QUOTE=MichaelZ]Hello,

I think that you should modify the "Terminal to lunch console programs" (Settings-->Environment). Change xterm for the gnome terminal (probably you will have to change the parameters too).

Best wishes,
Michael[/QUOTE]

Yes I did that but not sure of exact parameters to use. I'll read up on it I guess.
The console opens and closes again almost instantaneously, unless I run debugger and step into (F7). Then it stays open. Something is askew with my settings I think.

Code::Blocks is definitely very nice IDE. Good alternative to Anjuta. I like it!

;)

---

### Post by MichaelZ on 2006-05-06
[quote=kudu]Code::Blocks is pretty cool, though I'm not partial to QT look. How do I assign Gnome Terminal as console window instead of XTerm ?? Whats the correct setting ??

Regards,
kudu[/quote] 
Hello,

I have tried with under Settings-->Environment:

> 
gnome-terminal -t $TITLE -e
 
It seems to work, but the windows is immediatly closed after the application has been executed. I was not able to find the correct option for this (I am still learning Ubuntu).

Best wishes,
Michael

---

### Post by kudu on 2006-05-06
[QUOTE=MichaelZ]Hello,

I have tried with under Settings-->Environment:

 
It seems to work, but the windows is immediatly closed after the application has been executed. I was not able to find the correct option for this (I am still learning Ubuntu).

Best wishes,
Michael[/QUOTE]


Still having no luck with correct parameters. Anybody??

kudu

---

### Post by neehnahw on 2006-05-07
[QUOTE=lnostdal]i'll probably be flamed for being old fashioned or something..  :) .. but for me, it's Emacs all the way ..    i even run Emacs as a front-end/interface to servers (under screen actually) .. it's rock solid[/QUOTE]

Slightly OT: Does Emacs support incremental building like Eclipse, i.e. compiling as soon as you change the source?

---

### Post by yaaarrrgg on 2006-05-07
[QUOTE=neehnahw]Slightly OT: Does Emacs support incremental building like Eclipse, i.e. compiling as soon as you change the source?[/QUOTE]

I'm not sure... but the nicest thing about vim and emacs is that it's pretty easy to extend them.  This sort of stuff is usually easy to do even if it's not supported out of the box.  

I find Eclipse looks great and has good features, but in many ways is even more primitive than vi.  For instance there are no good macro tools in Eclipse (that I can find).  On one hand, if vi doesn't do something, it's fairly trivial to extend it.  The same commands used to edit and navigate through source can be recorded and saved as a macro.  But with Eclipse, it's pretty much impossible to automate a series of mouse gestures and clicks.

---

### Post by neehnahw on 2006-05-07
[QUOTE=yaaarrrgg]I'm not sure... but the nicest thing about vim and emacs is that it's pretty easy to extend them.  This sort of stuff is usually easy to do even if it's not supported out of the box.  

I find Eclipse looks great and has good features, but in many ways is even more primitive than vi.  For instance there are no good macro tools in Eclipse (that I can find).  On one hand, if vi doesn't do something, it's fairly trivial to extend it.  The same commands used to edit and navigate through source can be recorded and saved as a macro.  But with Eclipse, it's pretty much impossible to automate a series of mouse gestures and clicks.[/QUOTE]

I very much agree with you as I am a vim user myself. The templates feature of Eclipse can significantly help, but the editor is still horribly underpowered. I tried viPlugin for Eclipse, but was not satisfied with it.

---

### Post by zymurge on 2008-08-23
> **kudu said:**
> Code::Blocks is pretty cool, though I'm not partial to QT look. How do I assign Gnome Terminal as console window instead of XTerm ?? Whats the correct setting ??

Regards,
kudu

Settings=>Environment=>Terminal to launch console programs

Type: 
gnome-terminal -t $TITLE -x

This works for me.

---

### Post by nrs on 2008-08-23
edit: didn't realize the above poster resurrected a two year old thread.

---

### Post by StOoZ on 2008-08-23
I use Netbeans , its pretty slow though , maybe coz its written in java.

---

### Post by LaRoza on 2008-08-23
> **StOoZ said:**
> I use Netbeans , its pretty slow though , maybe coz its written in java.

That is nice.

See the sticky people wanting to ask about IDE's. 

Thread closed for being pointless, closable (see sticky), and necromanced.

---

