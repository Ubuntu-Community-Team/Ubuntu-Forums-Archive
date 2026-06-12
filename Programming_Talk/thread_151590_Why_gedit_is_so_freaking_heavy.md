---
title: "Why gedit is so freaking heavy?"
date: 2006-03-28
forum: Programming Talk
---

### Post by sapo on 2006-03-28
I used to code python and php using gedit at home A64 2800+, 512MB Ram.

But here at my work duron 700mhz with 128MB ram, its just impossible to use gedit.

when i open up a string for example, it highlights all the code bellow it, and it takes ages, sometimes i m writing the last character of a line, and the first is just beggining to show up.

So i m using gvim here, i like it, but for a newbie like me i think its too complicated.

I m always cutting and pasting code, and gvim doesnt simplify that for me, and i m always lost with the files i open in gvim, i miss the gedit tabs.

And also i think that the python and php highlight in gedit is prettier.


Btw.. why does it have to be SO HEAVY?? ](*,)

And why gvim can be so freaking lighweight with all those features on it?

I think that the gedit developers could ask for some advice from the gvim developers...

---

### Post by psychicdragon on 2006-03-28
Are you running Gnome on that machine as well? 128 Mb isn't much ram.

Use evim. It's included in the gvim packages. It has the usual shortcuts for copy and paste, but is otherwise the same as gvim. There's also cream, which is vim but with all the shortcuts changed to ctrl+ ones.

---

### Post by sapo on 2006-03-29
[QUOTE=psychicdragon]Are you running Gnome on that machine as well? 128 Mb isn't much ram.

Use evim. It's included in the gvim packages. It has the usual shortcuts for copy and paste, but is otherwise the same as gvim. There's also cream, which is vim but with all the shortcuts changed to ctrl+ ones.[/QUOTE]
thanx, i discovered cream yesterday in the #python channel on irc.freenode.org and i loved it, i started using it.

And about gnome, i m using xfce, but still gedit is too heavy!

---

### Post by David Marrs on 2006-03-29
[QUOTE=sapo]
I m always cutting and pasting code, and gvim doesnt simplify that for me, and i m always lost with the files i open in gvim, i miss the gedit tabs.
[/QUOTE]
Ah, but vim massively simplifies cutting and pasting. You just have to learn the knack.

You cut text with 'd' (delete) followed by what you want to delete. For example, 'dw' deletes the current word, '3dw' deletes the next 3 words, 'dd' deletes the entire line, '4dd' deletes 4 lines, 'D' (shift+d) deletes to the end of the line, and so on. Then to insert that text somewhere else in the document, move the cursor to where you want to paste and type 'p'.

You have similar commands in the form of 'y' (copy/yank) and 'c' (change).

One very useful application of this is the command 'xp' to correct mis-spelled words like "teh" or "wrold". Give it a try and you'll see how it works.

Aside from the obvious steep learning curve, there are a couple of drawbacks to using vim. The most annoying is that vim doesn't recognise ctrl-x/c/v for cut/copy/paste, so it's difficult to move text between vim and other applications. The other problem is that, after much use, you start to wish all applications behaved like vi, and sometimes you treat them like they do anyway.:wq

PS. I just loaded a c program file into gedit on my p3/256mb notebook and it was fine. If gedit isn't working out for you, and the complexity of vi or emacs doesn't cut it, try bluefish. It handles both python and php. Also, stani's python editor (SPE) is really rather nice. But it may be that you just don't have enough memory for them.

---

### Post by sapo on 2006-03-29
[QUOTE=David Marrs]Ah, but vim massively simplifies cutting and pasting. You just have to learn the knack.

You cut text with 'd' (delete) followed by what you want to delete. For example, 'dw' deletes the current word, '3dw' deletes the next 3 words, 'dd' deletes the entire line, '4dd' deletes 4 lines, 'D' (shift+d) deletes to the end of the line, and so on. Then to insert that text somewhere else in the document, move the cursor to where you want to paste and type 'p'.

You have similar commands in the form of 'y' (copy/yank) and 'c' (change).

One very useful application of this is the command 'xp' to correct mis-spelled words like "teh" or "wrold". Give it a try and you'll see how it works.

Aside from the obvious steep learning curve, there are a couple of drawbacks to using vim. The most annoying is that vim doesn't recognise ctrl-x/c/v for cut/copy/paste, so it's difficult to move text between vim and other applications. The other problem is that, after much use, you start to wish all applications behaved like vi, and sometimes you treat them like they do anyway.:wq

PS. I just loaded a c program file into gedit on my p3/256mb notebook and it was fine. If gedit isn't working out for you, and the complexity of vi or emacs doesn't cut it, try bluefish. It handles both python and php. Also, stani's python editor (SPE) is really rather nice. But it may be that you just don't have enough memory for them.[/QUOTE]
Thats my problem, memory, SPE, Dr Python, they are all slow here, the only thing that doesnt slow down everything is gvim, but its kinda hard to work with it.. i m using cream right now, but i m starting to miss some vim stuff.. like "dd" that i was using.. :e file :new...

oh god why didnt i learn vim istead of the DOS edit when i started with computers? :(

---

