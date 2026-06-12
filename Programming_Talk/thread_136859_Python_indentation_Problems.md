---
title: "Python indentation Problems"
date: 2006-02-26
forum: Programming Talk
---

### Post by krypto_wizard on 2006-02-26
I am a newbie to Python. I am mainly using Eric as the IDE for coding. Also, using VIM and gedit sometimes.

I had this wierd problem of indentation. My code was 100% right but it wont run because indentation was not right. I checked time and again but still no success. I rewrote the code over again in VI and it ran.

Can you please explain whats the trick behind the correct indentation.

Thanks

---

### Post by stoffe on 2006-02-26
Python can be hopeless with that IMO, just like Make. You see, it demands that your indentation is exactly the same on all lines of the same level. Your problem is most likely from mixing tabs and spaces. Whitespace is not a good visual indicator because it's well, invisible. Setting your editors to using either consistently usually helps.

Personal opinion is that using some other language helps permanently.

---

### Post by krypto_wizard on 2006-02-26
Is it related to using a good IDE ? There are lots of Pythonist around and I am sure there is an intelligent way to handle this.



[QUOTE=stoffe]Python can be hopeless with that IMO, just like Make. You see, it demands that your indentation is exactly the same on all lines of the same level. Your problem is most likely from mixing tabs and spaces. Whitespace is not a good visual indicator because it's well, invisible. Setting your editors to using either consistently usually helps.

Personal opinion is that using some other language helps permanently.[/QUOTE]

---

### Post by stoffe on 2006-02-26
[QUOTE=krypto_wizard]Is it related to using a good IDE ? There are lots of Pythonist around and I am sure there is an intelligent way to handle this.[/QUOTE]
Of course. Making sure you have good settings for how tabs/spaces/indentation is handled in your editors, like I said. My personal preference (for any language) is that all tabs etc are made into 2 spaces, which means that I have no tab characters at all in my source files, only spaces - what I see is what I get. Others like to make sure that they have tabs only. Both works.

Any even semi-decent editor can do that.

---

### Post by psychicdragon on 2006-02-27
The easiest way to stay safe in this regard, in my experience, is to just use one editor.

---

### Post by krypto_wizard on 2006-02-27
Which is the best editor for python. 

I have like eric till now but due to these problems I kind of get frustrated when you have written the right code but for want for indentation it wont run.

Any suggestions ???


[QUOTE=psychicdragon]The easiest way to stay safe in this regard, in my experience, is to just use one editor.[/QUOTE]

---

### Post by psychicdragon on 2006-02-27
[QUOTE=krypto_wizard]Which is the best editor for python.[/QUOTE]
Vim is the best editor for everything. ;) 

Seriously though, just try them all and stick with the one you're the most comfortable/productive in.

---

### Post by jerome bettis on 2006-02-27
yeah if you do

:set expandtab
:%retab!

in vim, that will convert all tabs into spaces, also

:set noexpandtab
:%retab!

will put in all tabs.   python doesn't like mixing tabs in spaces, you have to be consistent.

i'm surprised to see i'm not the only one who wishes python had used the { } ... using whitespace was a novel idea, and a lot of people seem to like it, but i like how the braces really highlight the structure of your program.  it also means more compilation errors but less run time errors.  whitespace has been insignificant in the proramming world forever, and it should be in my opinion.

---

### Post by thumper on 2006-02-27
Oo oo fight. Emacs is better :)

I generally set emacs to just uses spaces, no tabs ever (except for makefiles).

I did find SPE quite good too though.

---

### Post by krypto_wizard on 2006-02-27
I am having some serious problems running python code and all I get is indentation errors. I have been using Eric python IDE.

How can I recover my code and get it up and running somewhere. Please help !!!

Every help is greatly appreciated.

Thanks

---

### Post by thumper on 2006-02-27
Try SPE (Stani's Python Editor) - its in the repositories.

Failing that use emacs, vi or Kate (if KDE).  Most code aware editors have some "format selected code" menu item or command.  Load your text file and run the command.  Any glaring mistakes in indentation should be really obvious.

---

### Post by stani on 2006-02-28
Don't use SPE of the repositories. It's old. Download the deb package from [http://pythonide.stani.be](http://pythonide.stani.be) instead.

Stani

---

### Post by krypto_wizard on 2006-02-28
are you the same stani from stani's python editor or its just coincidence of a name?

[QUOTE=stani]Don't use SPE of the repositories. It's old. Download the deb package from [http://pythonide.stani.be](http://pythonide.stani.be) instead.

Stani[/QUOTE]

---

### Post by stani on 2006-02-28
it's me :D

---

### Post by setori on 2008-05-17
settings -> preferences -> Editor -> General -> *check* tab key indents

---

