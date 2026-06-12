---
title: "emacs vs vi"
date: 2005-03-31
forum: Programming Talk
---

### Post by jerome bettis on 2005-03-31
up until sometime last week, i always used some sort of big ide to do my programming.  but i've been doing this current project from the command line just using nano, and gmake.  i find it's a lot more efficient and productive instead of pissing around in eclipse looking for a certian feature etc.  i'm liking the simplicity of not being in an ide.

that said, nano is pretty limited.  i can't set the tab size to 4, i can't use the mouse, no syntax highlighting etc etc.  but i do very much like the ctrl + k to cut a line and ctrl + u to paste it.  

so i know nothing about emacs and vi, except that they're both a lot more powerful.  i tried using them both for a few minutes and it looks like they're actually pretty difficult to get around in, unless you know what you are doing, in which case it would be easy.

i read somewhere that emacs is "a programmable operating system"  .... wtf is that all about (it it's true)?  it sounds pretty cool.

what i'm looking for is something that is easy to use, but has a little more flexibility and features than nano.  so if you use either / both of these apps, please post up what you like about them and how difficult it was to get good with it.

---

### Post by bnutting on 2005-03-31
Boy you are opening up a can of worms by starting with 'vi' and 'emacs' in the same sentence  ;-) 
Some people will say how much better vi is over emacs and visa-versa. I use vi ( vim realy ) and it does everything I need it to do. You can customize it on how it acts and what it does by editing the .vimrc file. Here is a sample of mine:
```

" We use a vim
set nocompatible
"
" Colo(u)red or not colo(u)red
" If you want color you should set this to true
"
let color = "true"
"
if has("syntax")
    if color == "true"
        " This will switch colors ON
        so ${VIMRUNTIME}/syntax/syntax.vim
    else
        " this switches colors OFF
        syntax off
        set t_Co=0
    endif
endif
:set smartindent
:set wildmode=longest,list
:set incsearch
:set hlsearch
:set ru
:set sc
:set vb
:set wmnu
:set noeb
:set nosol
:set ic
:set ls=2
:set shm=at
:hi Comment ctermfg=DarkGreen
:hi Search ctermbg=red
:hi String ctermfg=grey
:map <up> gk
:map <down> gj
" ~/.vimrc ends here

```

Enjoy!

---

### Post by Glanz on 2005-03-31
When I use vi/vim, I feel like I am using an editor designed for editing and programming Unix releted scripts, applications, and configurations. When I use emacs, I feel like a character in one of Richard Stallman's nightmares, or at best, a prisoner of his labyrinthine thought processes which only accepts ONE way of doing things.

Now before an Emacs fan replies, I know that was an unfair generalisation and an unforgiveable abstraction (for which I won't apologize).

---

### Post by j-rock on 2005-03-31
I am also 100% for vi/vim.  emacs just didnt seem as sleek to me.  The control key sequences with emacs just turn me off.

---

### Post by fjleal on 2005-03-31
Old joke, but... Is anyone using Ed?
[http://www.gnu.org/fun/jokes/ed.msg.html](http://www.gnu.org/fun/jokes/ed.msg.html)

Will it make it into Hoary?... ;)

---

### Post by toojays on 2005-03-31
To understand the programmability of Emacs, check out [ Programming in Emacs Lisp]("http://www.gnu.org/software/emacs/emacs-lisp-intro/").

I found that it took me a while to get used to Emacs. A friend of mine used it for everything and was always telling me how good it was, but every time I tried to use it, it felt so klunky that I always went back to using KDE's Kate. Then I found myself having to program in Windows on a P166 with 24MB of RAM. I needed a good editor which wasn't too heavy, and so I decided to force myself to use Emacs.

I would say that the first part of learning Emacs (doing the online tutorial) is one of the most boring things you could do. But once you have that behind you, and you start learning about how to extend Emacs via Emacs Lisp, you realise that it was definitely worth it. The idea of a program as extensible as Emacs blows my mind sometimes.

---

### Post by cow_racer on 2005-04-05
I also prefer vi over emacs.   Yes the learning curve is high, but once you learned it it is a life saver.

---

### Post by jdonnell on 2005-04-05
I prefer vim and use it all the time. i use gvim on windows, linux, and my mac. It takes a little while to get used to the two modes, but once you do it's smooth sailing. My biggest issue with it is not being able to ctrl-c and ctrl-v for copy and paste by default. It's one of the most used features and should be consistent with every other gui text editor.

---

### Post by JeffS on 2005-04-05
vim for me.  I also use Kate and Gedit.  Both are great editors that feature tabs and syntax highlighting.  Kate even has it's own console.

But for pure command line stuff, vi/vim is great.  The only learning curve for me was the switching between command mode and editing mode.  But that was fairly straight forward, and after that, the learning curve was pretty easy.

I've played with Emacs a bit, and it's features, extensibility and overall power intrigue me.  But I find it to hard to learn and get productive with, and not worth it when considering you are using it for editing.  Emacs is kind of like delivering a toaster with a big 18 wheel truck.

---

### Post by jdonnell on 2005-04-05
[QUOTE=JeffS]vim for me.  I also use Kate and Gedit.  Both are great editors that feature tabs and syntax highlighting.  Kate even has it's own console.
[/QUOTE]

I absolutely love kate!

---

### Post by JeffS on 2005-04-05
[QUOTE=jdonnell]I absolutely love kate![/QUOTE]

Kate is great.  It's one of KDE's, and indeed Linux's, shining stars.  It is very full featured, super easy to use, and a programmer's wet dream.

Gedit, while not as full featured ad Kate, is awesome as a simple and programmer's text editor in the Gnome environment.

Syntax highlighting, tabs, are all great features for the programmer.  Kate and Gedit both do these things very well.

For me, it's Kate, Gedit, and vim.

---

### Post by HungSquirrel on 2005-04-05
Here's a neat trick: to get vim to stop leaving swapfiles (ending in ~) all over the place, do the following:

mkdir ~/.vimswaps

Edit ~/.vimrc and add:

```
set backupdir=~/.vimswaps,/tmp
```

---

### Post by sas on 2005-04-05
I use gedit, unless I'm stuck without X and then it's vim, vim is quite easy once you remember some of the shortcuts. IBMs [cheat sheet](http://www.gentoo.org/doc/en/vi-guide.xml) is quite useful for that.

---

### Post by TjaBBe on 2005-04-07
I'm one of the many voting for Vi(M) although I don't have much experience with emacs. Vi(M) fits my needs, and I don't need anything else!

---

### Post by PMO6022 on 2005-04-07
Wow sas!  I use vim all the time, and that shortcut site is great!

---

### Post by defkewl on 2005-04-07
Me too prefer Vi than Emacs. It's quite simple and it does the job well. Although I must admit that Emacs is more powerful than Vi but it's just overdo for me.

---

### Post by Suvarin on 2005-04-09
[QUOTE=cow_racer]I also prefer vi over emacs.   Yes the learning curve is high, but once you learned it it is a life saver.[/QUOTE]

The way I learnt ViM vas by running *vimtutor*.  Once you understand the difference between normal mode (Esc), commands ( : ) and input mode (i) you should grock the rest pretty fast. After that is only a question of actually using it until your fingers do the thinking for you. 

I was a nano/gedit user for a very long time, but when I started learning LaTeX I got an urge to test ViM. Can't say I regret it. The great thing about ViM (compared to GUI editors)  is that you only have to move your fingers, while your hands stay still. 

Once you have the basics down, customizing ViM will give further comfort. I find [SuperTab](http://www.vim.org/scripts/script.php?script_id=182) really useful, it makes it possible to complete words in ViM by pressing tab (like in bash) instead of using a ctrl+key sequence.

---

### Post by hamiltjr on 2005-04-21
I primarily vi to write about how much Richard Stallman influenced my life by creating emacs...

 :wink:

---

### Post by Burke on 2005-11-24
Vi is good. EMACS is maybe a tiny bit better, but this advantage is overcome by two huge failing points.  EMACS is huge.  Eight megabytes, last I heard.  I don't know how big Vi is, but I would be *very* surprised if it was over a MegaByte. This isn't a big problem, but it causes the other, more major problem:  EMACS isn't standard. Vi is only basically every *nix install anywhere. EMACS almost always has to be installed separately.

I used to be an EMACS user, but I am now fully converted to Vim,  and I love it!

Take an hour, sit down with a tutorial for Vi/Vim (don't worry about the difference).  You'll wonder how you got along without it. 

Here's a great tutorial for Vi: [http://www.jerrywang.net/vi/](http://www.jerrywang.net/vi/)
It's called 'Vi for smarties', but don't let that throw you, its one of those no-bullshit, here's whatyou need to know tutorials, and as such, is quicker and better :)

---

### Post by darth_vector on 2005-11-24
i use vim for everything; programming, report writting... everything

---

### Post by Gustav on 2005-11-24
I use emacs. 
Because it has the only five in a row game for ubuntu that I've found :) (exept gomoku.app for GNUstep)

(and it's the most GNU way)

---

### Post by GozzoMan on 2005-12-28
[QUOTE=jdonnell] My biggest issue with it is not being able to ctrl-c and ctrl-v for copy and paste by default. It's one of the most used features and should be consistent with every other gui text editor.[/QUOTE]

Sorry to derive from the topic. Might I ask you how to enable ctrl-c and ctrl-v in gvim? (I'm using Gnome/Ubuntu).

Thank you very much,

---

### Post by darth_vector on 2005-12-28
i use vi or vim, or sometimes pico. none of this graphical nonsence.

tis good, tis fast and tis very pretty with all the nice colours.

---

### Post by rolfotto on 2005-12-28
[QUOTE=jerome bettis]what i'm looking for is something that is easy to use, but has a little more flexibility and features than nano.  so if you use either / both of these apps, please post up what you like about them and how difficult it was to get good with it.[/QUOTE]

I like both of them.  But many people use vi because it's only an editor and easy to use, emacs is more.

Vi: Is a standard editor: you can sit down at almost an Unix machine and it will have Vi.  Is the easier of the two to learn.  Good to edit small stuff like scripts.

Emacs:  Harder to learn, but a better programming environment IMO.  Very extensible, it saved me hundreds of hours in drugdery.  You need to learn to learn emacs-lisp to make full use of it (which, as a programmer, you should*).  In the long term, it's worth learning, but the curve can be steep.

[http://www.gnu.org/software/emacs/elisp-manual/elisp.html](http://www.gnu.org/software/emacs/elisp-manual/elisp.html)


*"Lisp is worth learning for the profound enlightenment experience you will have when you finally get it; that experience will make you a better programmer for the rest of your days, even if you never actually use Lisp itself a lot."

- Eric Raymond, "How to Become a Hacker"

---

### Post by GozzoMan on 2005-12-29
[QUOTE=jdonnell]I prefer vim and use it all the time. i use gvim on windows, linux, and my mac. It takes a little while to get used to the two modes, but once you do it's smooth sailing. [/QUOTE]

This is also my experience.

[QUOTE=jdonnell]My biggest issue with it is not being able to ctrl-c and ctrl-v for copy and paste by default. It's one of the most used features and should be consistent with every other gui text editor.[/QUOTE]

Well, since it's proving to be a time-consuming issue by its own, I can't agree more. It should just work.

I've half-mastered the point and I'm reporting my findings in the thread [http://ubuntuforums.org/showthread.php?p=611004#post611004](http://ubuntuforums.org/showthread.php?p=611004#post611004), if you could spare some advice please have a look. Thank you very much.

---

### Post by led3234 on 2008-05-16
> **fjleal said:**
> Old joke, but... Is anyone using Ed?
[http://www.gnu.org/fun/jokes/ed.msg.html](http://www.gnu.org/fun/jokes/ed.msg.html)

Will it make it into Hoary?... ;)

Just me I suppose.

Well, vi(m) as well. I tried out emacs, but I found that I preferred vi(m).

Also, I heard something about being able to create M$ word documents in vim. Is this true/is it legal/how do you do it?

---

### Post by LaRoza on 2008-05-16
Any reason for the necromance?

---

