---
title: "Syntax highlighting in c/c++"
date: 2006-10-02
forum: Programming Talk
---

### Post by navneeth on 2006-10-02
I'm sorry if this question has been posted before, but I wasn't able to find a related post or thread. 

How can I highlight the syntax while writing c/c++ programs from the termninal? I just installed g++ from synaptic.

Thank you.

---

### Post by po0f on 2006-10-02
navneeth,

That depends on what editor your using.  If it's Vim, do this from the terminal:
```
$ cat /usr/share/vim/vim64/vimrc_example > ~/.vimrc
```

You might want to check to make sure that file exists, I believe that's where it's installed.

---

### Post by navneeth on 2006-10-03
Mmm...I'm not sure I understand. Sorry for the noob question, but what do you mean by editor? I'm new to programming,so kindly bear with me.

---

### Post by po0f on 2006-10-03
navneeth,

Gedit has syntax highlighting, and works like your basic, run-of-the-mill GUI text editor.  If you're just starting out, I wouldn't try to bog you down with learning how to use a terminal editor and learning how to program.  Get comfortable with actually writing code, then you can move up to a more powerful editor.

---

### Post by navneeth on 2006-10-03
I'm not learning this on my own, but attending a course, where we use Fedora and it's all done from the terminal. Where do I get gedit from? I can't find it in Synaptic or Automatix.

---

### Post by navneeth on 2006-10-03
Never mind...found it. Thanks. :)

---

### Post by chamarams on 2009-07-01
How can I highlight the syntax while writing c/c++ programs from the ubuntu termninal I just installed g++.when I am coding fedora terminal It's give(syntax highlighting) but in ubuntu It's doesn't give.now i have ubuntu only.how can i do this please help me.

---

### Post by benj1 on 2009-07-01
does it have to be in the terminal, if not theres gedit already installed and any number of IDEs in the repositories.

if it has to be in the terminal, preinstalled theres vim and nano, to get nano to do syntax highlighting go to the ~/.nanorc file and at the bottom should be a list of specific rc files for specific languages including c, uncomment it (get rid of the #) save and reload nano and that should work.

not sure about vim, i assume the advice in the above post will work.

there is also emacs, which isnt installed by default, but popular.

ps 
you don't need to resurrect a 3 year old thread to ask a question, just start a new one.

---

### Post by dwhitney67 on 2009-07-01
When working with Ubuntu and vim, one needs to get the full version of vim.
```

sudo apt-get install vim-full

```
Then, it may be necessary to augment one's ~/.vimrc file with the following:
```

syntax on

```
Fedora comes with the full version of vim, thus the first step above is not required for that OS... sigh, if only Ubuntu were like this too.

---

### Post by c0mput3r_n3rD on 2009-07-01
the text editor vi highlights c/c++ syntax as long as it has a .c/.cpp extension on it.

you also have to know the commands though. but you can find that in any tutorial out there, they're easy.


ex:
esc
:wq
-saves and quits

---

### Post by c0mput3r_n3rD on 2009-07-01
i just realized vim is vi so forget that :)

good advice everyone else, i would have given the same ;)

---

