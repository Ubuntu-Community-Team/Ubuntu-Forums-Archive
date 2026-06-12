---
title: "Enable syntax highlighting on vim"
date: 2008-11-25
forum: Programming Talk
---

### Post by tiachopvutru on 2008-11-25
Well, I decided to try vim editor out a bit and have learned a few basic commands so far.

That aside, I wanted to do some syntax highlighting on Python. By setting :syntax on, it was easy enough. It highlights the numbers, strings, comments, and the Python keywords. What it doesn't highlight, though, are certain built-in functions and exceptions.

Not knowing what to do, I then browsed Synaptic to see if I missed anything and installed vim-full and vim-python packages. It didn't help though.

After that, I created the folder ~/.vim/syntax and downloaded the latest version of the [python.vim]("http://www.vim.org/scripts/script.php?script_id=790") file and put it inside that folder. Following the [documentation]("http://www.vim.org/htmldoc/syntax.html"), I went to do :set syntax=python, but nothing happened. Neither did :let python_highlighting_all = 1 and all those other stuffs did anything.

The two syntax highlighting features aren't that critical, but I'm frustrated that I can't figure out what I have done wrong...

---

### Post by Sorivenul on 2008-11-26
I don't believe you've done anything "wrong", per se. Have you installed "vim" from the repositories?  By default Ubuntu only has "vim-minimal" or something to that effect, which comes with fewer features than "vim".  That said, if you followed the documentation like you said, you should have working highlighting.

---

### Post by jimi_hendrix on 2008-11-26
get gvim...its like vim + gedit and once you start it it wont hog up a terminal

---

### Post by Greyed on 2008-11-26
Regarding gvim...

On the other hand it is pretty hard to use from remote.  :twisted:

---

### Post by jimi_hendrix on 2008-11-26
you can always just not use python :)

---

### Post by tiachopvutru on 2008-11-26
> **Sorivenul said:**
> I don't believe you've done anything "wrong", per se. Have you installed "vim" from the repositories?  By default Ubuntu only has "vim-minimal" or something to that effect, which comes with fewer features than "vim".  That said, if you followed the documentation like you said, you should have working highlighting.

I have already installed vim-full, and I also have syntax highlighting on. As described in first post, what I'm trying to figure out is out to get the custom syntax highlighting file to work, which according to the website it should also highlight builtin functions and exceptions. However, in my script, it didn't highlight raw_input() or KeyError.

I can't say that I fully understand the documentation, though.

> **jimi_hendrix said:**
> get gvim...its like vim + gedit and once you start it it wont hog up a terminal

I already did. Just didn't mention it since it's not relevant to the issue at hand.

---

### Post by dribeas on 2008-11-26
> **tiachopvutru said:**
> By setting :syntax on, it was easy enough. [...]
After that, I created the folder ~/.vim/syntax and downloaded the latest version of the [python.vim]("http://www.vim.org/scripts/script.php?script_id=790") file and put it inside that folder. Following the [documentation]("http://www.vim.org/htmldoc/syntax.html"), I went to do :set syntax=python, but nothing happened. Neither did :let python_highlighting_all = 1 and all those other stuffs did anything.


Don't really know the answer, but you can try having vim source the syntax script:

:source ~/.vim/syntax/python.vim

---

### Post by tiachopvutru on 2008-11-26
Aye... This is so stupid that it's not even funny...

I found the problem. Basically, what I had to do was **:let python_highlight_all = 1**

but I did :let python_highlight**[COLOR="Red"]ing[/COLOR]**_all = 1 instead <_<

---

### Post by monkeyking on 2008-11-27
I had used vim for some time before I found out that it's enough to write the first unique letters of a command.

like
```

:syn on 
:colo desert

```
instead of

syntax on and color desert

---

