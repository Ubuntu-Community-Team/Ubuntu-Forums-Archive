---
title: "Running Code::Blocks programs with gnome terminal"
date: 2010-04-28
forum: Programming Talk
---

### Post by Eragon0605 on 2010-04-28
It seems that Code::Blocks uses xterm as it's default terminal when running programs. I was wondering what command you would use to run gnome-terminal instead. I tried simply replacing 'xterm' with 'gnome-terminal', but, not surprisingly, it didn't work. I am running Ubuntu 10.04, if that makes any difference.

---

### Post by harrismh777 on 2010-04-28
Greetings,
     Be careful with these steps; they are safe, but be careful.
     1) sudo su -
          changes your authority into root... enter your password
     2) cd /usr/bin
           changes directory where xterm and gnome-terminal live
     3) mv xterm xterm~
           change the name of the xterm program without deleting it...
           the ~ character is the tilde in the upper left hand corner of
                  your keyboard
     4) ln -sf /usr/bin/gnome-terminal xterm
           creates a symbolic link (xterm) to gnome-terminal
     5) exit
           exits root

     Now enter xterm in your command terminal... it will open gnome-terminal instead of xterm.
     Symbolic links are a powerful tool, so be careful. Also, notice that
     since this is done in /usr/bin it is in effect for the whole system.
     When code::blocks calls xterm... it will pull up gnome-terminal instead.
     code::blocks ide may be looking expecting a certain shell?? I don't know.  Try it an see.

regards,
\\:D/

---

### Post by Eragon0605 on 2010-04-28
It didn't work. This does the same thing as changing 'xterm' to 'gnome-terminal' in the code::blocks settings. The reason this doesn't work is because there are certain flags that must be run, and the ones you use for xterm aren't compatible with gnome-terminal. A friend of mine actually figured out what I needed to do, just change the command from ```
xterm -T $TITLE -e
```to```
gnome-terminal $TITLE -x
```Thanks for the info, anyway!

---

### Post by dodo3773 on 2010-05-01
> **Eragon0605 said:**
> It didn't work. This does the same thing as changing 'xterm' to 'gnome-terminal' in the code::blocks settings. The reason this doesn't work is because there are certain flags that must be run, and the ones you use for xterm aren't compatible with gnome-terminal. A friend of mine actually figured out what I needed to do, just change the command from ```
xterm -T $TITLE -e
```to```
gnome-terminal $TITLE -x
```Thanks for the info, anyway!

I know this is old but if you ever come back across this thank you very much.

---

### Post by amireldor on 2010-11-23
there's one more problem when using the gnome-terminal as the console for code::blocks.
the gnome-terminal always returns the code 255 and not the code of the program you are running.

just anyone know how to solve this? although it's not such a big deal since the return value of the program is shown in the gnome-terminal when the program terminates.

---

### Post by silverzhao on 2010-12-17
> **lousygarua said:**
> there's one more problem when using the gnome-terminal as the console for code::blocks.
the gnome-terminal always returns the code 255 and not the code of the program you are running.

just anyone know how to solve this? although it's not such a big deal since the return value of the program is shown in the gnome-terminal when the program terminates.
I have this annoying problem too, and I've googled so much but nothing useful found.:(

---

### Post by silverzhao on 2010-12-18
I've found something interesting: if I open the gnome-terminal before  executing the program in codeblocks, it will not show the red line any  more. But once I close the gnome-terminal and execute the program again,  the annoying red line comes back at once! Is there anything different  here?

---

### Post by Humpparitari on 2010-12-24
I found a solution! :D

Here's the command I use:
```
gnome-terminal --disable-factory -t $TITLE -x
```

The "--disable-factory" argument runs gnome-terminal in it's own process, apart from other gnome-terminal processes you have running. Without it gnome-terminal will return 255 upon exit, unless you have another gnome-terminal already open.

This is still only a partial solution, since gnome-terminal will return 0 to Code::Blocks, regardless of what your program returns... If anyone has a solution to this problem, please let us know.

---

### Post by dsr007rana on 2012-06-04
Thank you very much "Humpparitari". 
I was looking for this so long. :guitar:  
Thank you once again.

---

