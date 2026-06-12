---
title: "Looking for an extended terminal"
date: 2017-02-24
forum: New to Ubuntu
---

### Post by vanillasnake21 on 2017-02-24
Right now I'm using gnome terminal and it does the job, however I'm thinking how much easier it would be if the terminal had some basic gui build in. Like it would be nice if I had recent locations that I can just click on and it would take the terminal there, or even be able to click on text in the terminal if I wanted to place the cursor there. Do these "extended" terminals exist and if so what are they?

---

### Post by TheFu on 2017-02-24
No.  Terminals work like a printer. Once the line is printed, you can't get it back. It is only available in the buffer, which you can scroll back through, depending on your buffer size setting.

You can select/paste from a terminal into the same/different terminals.  Not copy/paste - select/paste. This is a normal X-Windows thing using the x-buffer.

Also, don't confuse the terminal program with the shell.  Learn the shell. There are thousands of little time savers built-into most shells.  **pushd**, **popd** or **cd -** just to start.  Use **history** big time.  Want to run the last grep command again?  **!gre**  Want to run the command from 8 steps ago?  **!-8**

Don't forget about command substitution. Handy to run the same command again, just with a different option or input.  There is documentation about all these things.  **man bash** to start.  Many of the terms are probably beyond your current understanding.  Check out some youtube videos on mastering the shell.  There are hundreds of books written over the last 30 yrs about this stuff.  It actually hasn't changed much in that time.  

BTW, if you want a basic TUI, feel free to make one.  [http://explainshell.com/](http://explainshell.com/) might be helpful.  There are similar things that will run locally, I just don't remember the name. Sorry.

Oh ... and some terminals will open URLs when dbl clicked. I hate that, but I suppose some people might like it?  It just uses xdg-open and passes the URL in.

You probably already know most of this [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) - but for some lurkers, it could be helpful.

---

### Post by vanillasnake21 on 2017-02-25
Sorry I'm not sure I understand, isn't that up to the developer of the terminal? I mean as far as I understand a terminal is just a rendering of the output of the shell, so why can't you have a gui wrapper on top of it?

Edit: Also I'm not looking for anything crazy, I mean even things like a terminal with a gui that has buttons for favorite locations, you click a button and the terminal is cd'd to that directory. Or something along the lines of visual history of commands, that can also be clicked.

Edit2: Also why is it impossible to use the mouse on the line that you're currently typing, like why can't I click on a part of the line to place a cursor and instead have to use the l/r keys?

---

### Post by TheFu on 2017-02-25
Anything is possible. I can't claim to be an expert on terminals, since I've been using xterms for the last 20+ yrs and dislike being forced to use other terminals. Had to use an lxterm last weekend during a presentation - drove me crazy.

BTW, what you are describing sounds like 4dos or 4NT from JP software. [https://jpsoft.com/blogs/2011/01/why-no-4linux/](https://jpsoft.com/blogs/2011/01/why-no-4linux/) 

Also, 
* Servers don't have mice. 
* ssh to a server 10km away doesn't include mouse events
* **X/Windows --> terminal --> ssh --> bash**  Only the terminal might be running locally or remote.  
* ssh and bash don't know anything about mice.

When I'm using an xterm, I think differently. Generally don't touch the mouse - that would slow input down too much. Sorta like the same reason I prefer vim over other editors - the others are all too slow. Don't want to take my fingers off the keyboard. 
Of course, other people might prefer using the mouse, until they learn to use the keyboard.  For people tied to a mouse, I'd suspect they'd use a file manager interface and right-click to "Open Shell here" as a way to move around.

I can only guess that by the time someone loves a terminal enough to consider creating a new one, they've probably converted to avoiding the mouse?  Just a guess.

Windows powershell doesn't use a mouse. Why not?  Powershell is the closest thing to a Unix terminal.

---

### Post by howefield on 2017-02-25
> **vanillasnake21 said:**
> Also why is it impossible to use the mouse on the line that you're currently typing, like why can't I click on a part of the line to place a cursor and instead have to use the l/r keys?

Just partly picking up on this point, there are a number of useful keyboard shortcuts for moving along the typed line, not quite what you want but might you/others.

Ctrl + a to jump to the start of command and Ctrl + e to go to the end of command.
Alt + b to jump one word backward and Alt + f to jump one word forward.
Ctrl + u to delete from the cursor to the start of the command and Ctrl + k to delete from the cursor to the end of the command.

---

### Post by TheFu on 2017-02-25
**ctrl + w** to delete one word to the left.
**meta + w** to delete one word to the right <-- doesn't always work for me.

Actually, many admins I know will change the default emacs keybindings to vi mode on the command line. Then the arrow keys stop working. But it is highly customizeable.
[https://unix.stackexchange.com/questions/74075/custom-key-bindings-for-vi-shell-mode-ie-set-o-vi](https://unix.stackexchange.com/questions/74075/custom-key-bindings-for-vi-shell-mode-ie-set-o-vi)

But it really comes down to the "terminal" not really being in control.  The shell is ... and actually the shell is dependent on what **readline** does.  Run **bind -p** to see the keys that can be remapped.

---

### Post by Impavidus on 2017-02-25
One GUI thing that works in the terminal (some terminals at least): you can drag and drop a file into the terminal, which is equivalent to typing the path to that file.

---

