---
title: "I want to try vim"
date: 2009-07-15
forum: Programming Talk
---

### Post by hoboy on 2009-07-15
I use Netbeans and Eclipse, now I want to try Vim, I have installed some vim using Synaptic Package Manager, but how can i launch the ide ?

---

### Post by RoestVrijStaal on 2009-07-15
Have you tried to run vim from a terminal?
Not all installations make a link in the applications menu :)

---

### Post by hoboy on 2009-07-15
> **RoestVrijStaal said:**
> Have you tried to run vim from a terminal?
Not all installations make a link in the applications menu :)

How do I do that ?
There must be an ide called vim, lots of people are talking about, and ide like Netbean/eclipse ?

---

### Post by RoestVrijStaal on 2009-07-15
What I get with man vim:
---
VIM(1)                                                                  VIM(1)

NAME
       vim - Vi IMproved, a programmers text editor

SYNOPSIS
       vim [options] [file ..]
       vim [options] -
       vim [options] -t tag
       vim [options] -q [errorfile]

       ex
       view
       gvim gview evim eview
       rvim rview rgvim rgview

DESCRIPTION
       Vim  is a text editor that is upwards compatible to Vi.  It can be used
       to edit all kinds of plain text.  It is especially useful  for  editing
       programs.

       There  are a lot of enhancements above Vi: multi level undo, multi win&#8208;
       dows and buffers, syntax highlighting, command line  editing,  filename
 Manual page vim(1) line 1
---
I don't know which language you want to program, but i think you must compile the programs that you make with vim with an other apllication...

---

### Post by wojox on 2009-07-15
Open terminal and type:

vi FileToOpen

---

### Post by hoboy on 2009-07-15
Hunnnnnnnnnnnnnnnnn they said curiosity kill the cat, I think that I will stay with Netbeans/eclipse...

---

### Post by hoboy on 2009-07-15
> **wojox said:**
> Open terminal and type:

vi FileToOpen

So vim and via are the same ?

---

### Post by wojox on 2009-07-15
vim is vi modal
vi is the text editior that vim derived from.
Heres the doc for vim

[http://vimdoc.sourceforge.net/htmldoc/version7.html](http://vimdoc.sourceforge.net/htmldoc/version7.html)

---

### Post by hoboy on 2009-07-15
My intention is to use vim to do some java coding, so how do I launch vim ide ? to do that ?

---

### Post by wojox on 2009-07-15
In terminal:

/etc/ sudo vim

---

### Post by TheStatsMan on 2009-07-15
If you want to be able to click on a menu to load vim, install vim-gtk. Otherwise go the the terminal and type vim. I prefer gvim as I can tell when I am in insert mode.

Make sure you read some documentation though or you will not enjoy it. 

[http://www.vim.org/docs.php](http://www.vim.org/docs.php) 

Once you have done this go hunt down the necessary plugins ,code completion, etc and install them.

---

### Post by hoboy on 2009-07-15
Ok, I must admit that vim is too difficult for me.
specially  when you are used to visual ide.
it seemed like the learning curve is high.
I wil stay with VS2008 for c# and eclispe/Netbeans for java.

---

### Post by Yacoby on 2009-07-15
> **hoboy said:**
> Ok, I must admit that vim is too difficult for me.
specially  when you are used to visual ide.
it seemed like the learning curve is high.
I wil stay with VS2008 for c# and eclispe/Netbeans for java.

It just has a very steep learning curve.

---

### Post by JordyD on 2009-07-15
> **hoboy said:**
> Ok, I must admit that vim is too difficult for me.
specially  when you are used to visual ide.
it seemed like the learning curve is high.
I wil stay with VS2008 for c# and eclispe/Netbeans for java.

If you want to do C# in Ubuntu, you can install Monodevelop. The only difference is that it uses GTK# instead of Winforms.

Otherwise, I think vim's learning curve is worth it.

---

### Post by monraaf on 2009-07-15
Yes vim is an editor that you actually have to learn how to use. I remember when I started out with vi that I was clueless on how to exit the editor, so I just used the kill command :p. But once you've mastered the basics and have used it for a while you will love it and won't regret investing some time in learning how to use it. I know I don't, I do all my editing in vim.

To get started with vim open a terminal and type:

```

vimtutor

```

---

### Post by JordyD on 2009-07-15
> **monraaf said:**
> Yes vim is an editor that you actually have to learn how to use. I remember when I started out with vi that I was clueless on how to exit the editor, so I just used the kill command :p. But once you've mastered the basics and have used it for a while you will love it and won't regret investing some time in learning how to use it. I know I don't, I do all my editing in vim.

To get started with vim open a terminal and type:

```

vimtutor

```

I never knew about vimtutor when I learned. I just got a cheatsheet from the web and used it often.

---

### Post by c0mput3r_n3rD on 2009-07-15
> **TheStatsMan said:**
> If you want to be able to click on a menu to load vim, install vim-gtk. Otherwise go the the terminal and type vim. I prefer gvim as I can tell when I am in insert mode.

Make sure you read some documentation though or you will not enjoy it. 

[http://www.vim.org/docs.php](http://www.vim.org/docs.php) 

Once you have done this go hunt down the necessary plugins ,code completion, etc and install them.


On the bottom left hand corner of the screen it will say Either: --INSERT--  --REPLACE-- (switch back and forth by pressing the insert button on keyboard), and then the command prompt in vim which is accessed by pressing ESC and then " : ".

---

### Post by c0mput3r_n3rD on 2009-07-15
> **hoboy said:**
> Ok, I must admit that vim is too difficult for me.
specially  when you are used to visual ide.
it seemed like the learning curve is high.
I wil stay with VS2008 for c# and eclispe/Netbeans for java.


It's really not that hard.  To create a new file, you type in terminal: 
```

vi fileName

```To open a file you type:
```

vi fileName

```To start typing text you have to to insert mode.  Either hit a key [a-z] or press the insert button.  So save and/or quit here are the commands. (press ESC key first)

Write to file:
```

:w

```Quit vi:
```

:q

```Write then Quit:
```

:wq

```And there you go!  Just make sure when you go to enter the commands you press ESC, then the " : " key.

---

### Post by JordyD on 2009-07-15
> **c0mput3r_n3rD said:**
> To start typing you code you have to to insert mode.  Either hit a key [a-z] or press the insert button.

Actually, no.

When not in insert mode, you are in command mode (usually), so that means you can press buttons and they won't be inserted, they will be executed as commands. So if you type 'u' you are executing 'undo' and if you type 'x' you delete a character. There are a lot more commands, those are just examples. To go into insert mode, you can either press the insert key or execute one of the insert commands. For example, 'i' is just plain 'insert here', 'a' is 'append here', 'I' is 'insert at beginning of line', and 'A' is 'append to end of line'.

The best way, I think, to learn all these commands is to just have a vim cheatsheet nearby, remember a few commands ('i' inserts, ':w' saves, ':q' quits, ':q!' quits without saving), then, whenever you think 'there must be a faster way to do this', consult either the cheatsheet or Google.

Just remember, with vim, there is *always* a faster way to do something.

---

### Post by c0mput3r_n3rD on 2009-07-15
> **JordyD said:**
> Actually, no.

When not in insert mode, you are in command mode (usually), so that means you can press buttons and they won't be inserted, they will be executed as commands. So if you type 'u' you are executing 'undo' and if you type 'x' you delete a character. There are a lot more commands, those are just examples. To go into insert mode, you can either press the insert key or execute one of the insert commands. For example, 'i' is just plain 'insert here', 'a' is 'append here', 'I' is 'insert at beginning of line', and 'A' is 'append to end of line'.

The best way, I think, to learn all these commands is to just have a vim cheatsheet nearby, remember a few commands ('i' inserts, ':w' saves, ':q' quits, ':q!' quits without saving), then, whenever you think 'there must be a faster way to do this', consult either the cheatsheet or Google.

Just remember, with vim, there is *always* a faster way to do something.


You're right, I meant to start typing your text you have to be in insert mode.  I edited it appropriately.

---

### Post by MindSz on 2009-07-15
Since we're on topic, I'd like to ask you guys something. I have to work with embedded linux machines and whenever I telnet to them and need to edit a file I have to use vi.

Being an emacs guy myself I had to learn the basics and it worked fine. However, whenever I telnet from a windows machine I can't get the backspace or the Delete key to work.

Does anyone know what to do about this?

---

### Post by dwhitney67 on 2009-07-15
> **MindSz said:**
> Since we're on topic, I'd like to ask you guys something. I have to work with embedded linux machines and whenever I telnet to them and need to edit a file I have to use vi.

Being an emacs guy myself I had to learn the basics and it worked fine. However, whenever I telnet from a windows machine I can't get the backspace or the Delete key to work.

Does anyone know what to do about this?

I know about this issue, since I used to have similar problems, many moons ago when working with dissimilar systems.

What I did back then was to set the erase key for the tty, using stty.  Something like:
```

stty erase ^H

```
If that does not work, then try:
```

stty erase ^?

```
The ^H (and the ^?) are two (2) literal characters; they do not imply any special control character.  Alternatively, in lieu of type the two characters, just press your Backspace or Delete key.

P.S.  The stty change is NOT done in vim, but within the terminal.  You may also want to consider performing the stty call within your .bashrc or other similar file.

---

### Post by e24ohm on 2009-07-15
> **Yacoby said:**
> It just has a very steep learning curve.

i have to agree. Vim has a high learning curve, and i am in the process of learning myself. Currently i use Emacs; however, vim is very attractive. Not sure which one is better, or has more/less features.

---

### Post by dwhitney67 on 2009-07-15
> **e24ohm said:**
> i have to agree. Vim has a high learning curve...
I will state that I disagree that learning vim is difficult.  :-)

I hope no one is offended that yet another email appears in their inbox with my worthless assessment of learning vim.

---

### Post by e24ohm on 2009-07-15
> **dwhitney67 said:**
> I will state that I disagree that learning vim is difficult.  :-)

I hope no one is offended that yet another email appears in their inbox with my worthless assessment of learning vim.
no not offended...do you have any recommendation for vim? I would love to learn it.

hey i'm in Maryland as well..good to see the fellow state members...Cheers!!!

---

### Post by MindSz on 2009-07-15
@dwhitney67

Thanks for the tip, I'll try it out!

---

### Post by c0mput3r_n3rD on 2009-07-15
You also have pico which is a very easy to use, very nice text editor.  All the hotkeys are listed on the bottom. to run type:
```

pico filename

```

---

### Post by jimi_hendrix on 2009-07-15
dont know if this has been mentioned, but if normal vim is intimidating, use gvim for a bit and get comfortable

---

### Post by JordyD on 2009-07-15
> **jimi_hendrix said:**
> dont know if this has been mentioned, but if normal vim is intimidating, use gvim for a bit and get comfortable

:) I found gvim *after* learning vim, so I never used the menus it had.

That said, gvim does look much better than straight vim, especially since the cursor changes looks based on mode.

---

