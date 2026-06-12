---
title: "What is the best text editor? I did not like VI so far"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by just_linux on 2008-07-23
hi, :popcorn:
Does any one know about a very good text editor?:lolflag:
Also, I want to write C or .sh program on my own, but I could not find any good editor, or any tutorial that I could learn from

Any Audio program do you recommend?

Thanks a lot :guitar:

---

### Post by ConMan318 on 2008-07-23
Vim is the best one (imo), it just takes time to get used to.  After becoming comfortable with it, it is by far the fastest.  Stick with it.  I suppose you could try Emacs.

If you don't want to learn either of those (both have a somewhat steep learning curve), just use gedit.

If you want a tutorial, a simple one that will get you started in Vim can be found by typing 'vimtutor' at the command line.  There is also one for Emacs, but I don't know it off-hand.  It's easy to find though, just do some searching.

Also, if you don't like Vim because of its lack of mouse-control from the command line, type 'gvim' at the command line to use a graphical version.

---

### Post by jordanmthomas on 2008-07-23
For GUI editors, I highly recommend kate.  It's a KDE program so it may not seem at home in a GNOME desktop but it'll work just as well.
For commandline editors, I like vim myself, but nano is nice if you at least [enable syntax highlighting]("http://http://wiki.linuxhelp.net/index.php/Nano_Syntax_Highlighting")

---

### Post by RiceMonster on 2008-07-23
Give SciTE a try. It's a nice GUI editor.

And by the way, the default vi on Ubuntu sucks. 

Do this:
```
sudo apt-get install vim
```

Then edit your /etc/vimrc and comment out "set compatible" with a ". Now when you want to use vi, type vim. Also, if you want to learn how to use it, type "vimtutor" anywhere in a terminal, or type ":help". Make sure you're in command mode when you do that though.


For a good audio program, try one of these:
Amarok
Exaile
Audacious
bmpx

---

### Post by compnut41 on 2008-07-23
I would recommend openoffice.org word processor. I have found it completely trumps Microsoft word. As for programing go simple. Just use the basic text editor and when naming ad the extension you want and it should open like you want it (works great in python).

---

### Post by jordanmthomas on 2008-07-23
> **compnut41 said:**
> I would recommend openoffice.org word processor. I have found it completely trumps Microsoft word.

I disagree, but I am a stickler for fonts.  :)

---

### Post by RiceMonster on 2008-07-23
He said he wanted a text editor, not a word processor.

---

### Post by mcduck on 2008-07-23
Actually the default editor in Gnome, Gedit, is pretty advanced one.

While it seems very simple on the first look, it comes with a bunch of great plugins, and the package "gedit-plugins" contains even more. Enable the ones that you like and you'll end with extremely versatile text editor..

For a command-line editor I prefer nano.

Edit: What kind of audio program are you looking for? Wave editor, software synth, sequencer, multitrack recorder, some kind of mixing or looping tool or perhaps a complete software studio? Or just some music player?

---

