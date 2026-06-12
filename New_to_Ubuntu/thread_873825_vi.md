---
title: "vi"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by broivan on 2008-07-29
What can I do in the VI editor that can be useful?

---

### Post by geenux on 2008-07-29
Look for the vimtutor. If you dont have vim you can find it with google.
If you have vim, just do
```
vimtutor
```

---

### Post by ibuclaw on 2008-07-29
Vi is extremely useful for:
[LIST]
[*]Programming/Writing scripts
[*]Making quick tweaks to config files
[*]Saving time and effort on repetitive tasks (for those who don't know how to use sed)
[*]Working with editable text files in servers.
[/LIST]
Also, note that it is now the default text editor if you wish to edit the sudoers file (**visudo**)

I love Vi/Vim...

Although, I recommend you get the IMproved version (Vim), and perhaps a GUI version too.
```
sudo apt-get install vim vim-runtime vim-gtk
```

And in your "~/.vimrc" file, have **syn on** inside (this turns on syntax highlighting, very useful feature :D).

To learn how to use Vi/Vim and it's useful feature, check out **vimtutor** by typing that in the terminal.

Regards
Iain

[ESC] :wq!

---

### Post by pauper on 2008-07-29
[http://www.viemu.com/a-why-vi-vim.html](http://www.viemu.com/a-why-vi-vim.html)
[http://thomer.com//vi/vi.html](http://thomer.com//vi/vi.html)


:guitar: :-\"

---

### Post by t0p on 2008-07-29
> **broivan said:**
> What can I do in the VI editor that can be useful?

Anything that can be done in a text editor.  Or a SDK.  Or...

Hell, loads.

---

### Post by estyles on 2008-07-29
> **broivan said:**
> What can I do in the VI editor that can be useful?

Nothing!  Use emacs.  :)

Sorry, old flamewars die hard.  Never could deal with vi.

---

### Post by Dr Small on 2008-07-29
Loads of things. Vim is my favorite text editor... well let's see here, my *only* text editor :)

---

### Post by Sydius on 2008-07-29
Vi took a while for me to learn to the point of it becoming more efficient than other development environments, but now I can't live without it.  The real appeal of vi to me is the .vimrc file and all the fancy setups you can have--just type in what you want to do with it in Google, and you can generally find someone who has a .vimrc posted that will have many useful features for that task enabled (such as PHP programming, etc.).

There's a bit of a competition, it seems, between emacs and vi.  I've never tried emacs, though, as my coworkers all use vi.

---

### Post by bodhi.zazen on 2008-07-29
> **estyles said:**
> Nothing!  Use emacs.  :)

Sorry, old flamewars die hard.  Never could deal with vi.

> **Sydius said:**
> Vi took a while for me to learn to the point of it becoming more efficient than other development environments, but now I can't live without it.  The real appeal of vi to me is the .vimrc file and all the fancy setups you can have--just type in what you want to do with it in Google, and you can generally find someone who has a .vimrc posted that will have many useful features for that task enabled (such as PHP programming, etc.).

There's a bit of a competition, it seems, between emacs and vi.  I've never tried emacs, though, as my coworkers all use vi.

+1 vim. It is true it takes some time to learn the tricks, but once you do there are some handy features.

Don't tell the vi guys, but vi uses emacs key bindings (by default), lol

---

### Post by ilrudie on 2008-07-29
emacs is just like vi only optimized for carpal tunnel instead of efficiency.

---

### Post by phidia on 2008-07-29
> **ilrudie said:**
> emacs is just like vi only optimized for carpal tunnel instead of efficiency.

:D Good one! I like vim's efficiency too & recommending vimtutor was  the right thing it will get you through the basics & more.

---

### Post by estyles on 2008-07-29
> **ilrudie said:**
> emacs is just like vi only optimized for carpal tunnel instead of efficiency.

I have carpal tunnel.  That must be why I like emacs.  ;)  

Back when I used vi and emacs (now I'm too lazy - I use gedit, even for small files and small changes, and I use Notepad++ in Windows for scripting - still need to find a good analog in Linux, but I do most/all of my scripting at work, in Windows), I just couldn't get over the fact that vi used cryptic, unlisted keystrokes for common commands (like, you know, enter text), and it annoyed me that there were two modes, and if you started typing while you were in the wrong mode, you could do no end of harm to your document.  And if you didn't remember all the shortcuts, there was no way to undo that harm, and it was difficult even to exit vi without just killing the terminal session (which the sysadmins definitely didn't like).  Emacs, to me, was like a halfway point to a graphical application, and IMHO made things way easier.  Lots of people like vi, though, and I admit it can be way more efficient *if* you know all of the editing keys.

---

### Post by ilrudie on 2008-07-29
Yeah.  The big negative to vi is the nearly vertical learning curve.  Once you know it its the best text editor around but until then its just confusing.

---

### Post by Frenske on 2008-07-29
In the beginning of my college years I used vi for programming Fortran. God only knows how much I disliked it, but it was the default editor in unix in the early nineties. It has an awful odd command sets for your actions, but after months you get used to it.
Now I use gedit most of the times but often my brain makes a shortcut and I type in vi to edit a file.

---

### Post by Growbag on 2008-07-29
The good thing about vi is that is is ALWAYS there!

Your GUI just went down = no Gedit, thankfully you have vi.
You just installed and need to edit a file, can't connect to the net to install emacs?  Guess what, vi is there (although sadly crippled under Ubuntu!).
You are at a friend's/customer's place trying to fix their machine, vi is there too.
You move to another distro, or even a BSD or Unix variant; vi is still there waiting like a faithful dog :).

You learnt the basics of vi, problem solved in seconds.

---

