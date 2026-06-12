---
title: "Console width - text wrapping"
date: 2006-07-02
forum: Programming Talk
---

### Post by ironfistchamp on 2006-07-02
I am writing a C++ program. I am totally new to the language. I output a paragraph of text and it looks stupid when it splits a word in half to get it on the next line. Is there something I can do about that within the program to make the text wrap?

Thanks

Ironfistchamp

---

### Post by Max Luebbe on 2006-07-02
You've either got to assume how long the console is, and write a function that keeps track of how many characters are outputted per line, and given the length of next word to be outputted, and how many characters are left are in the line.

Or.

Check out the Curses library.
It's a solid way for doing console formatting in C.

Hope this helps.

---

### Post by psychicdragon on 2006-07-02
A standard VT100 terminal is 80 characters wide, 24 lines long. Those are the default dimensions used by terminal applications like gnome-terminal and others.

---

### Post by LordHunter317 on 2006-07-02
Actually no, you pay attention to COLUMNS and fall back to that, or look up the terminal data and use that (being far perferable to just asusming).

---

### Post by ynef on 2006-07-03
COLUMNS isn't always there (not all distributions support it), so what you really should do is follow the steps outlined here: [http://julipedia.blogspot.com/2005/03/how-to-get-window-size.html](http://julipedia.blogspot.com/2005/03/how-to-get-window-size.html)

---

### Post by LordHunter317 on 2006-07-03
COLUMNS is an environment variable, so of course it's not always there (that goes without saying).  Hence my note about looking up terminal data if it's not there.

I wasn't aware that was available at all outside of X, at any rate, one should still obey COLUMNS if it is there, because the user may be intentionally overriding the size of his terminal.

---

### Post by ironfistchamp on 2006-07-03
Thanks for the replies. Seems a litte too complicated for me at the present time. I think I shall wait until I am a little less green.

Thanks

Ironfistchamp

---

### Post by Horsman on 2006-07-03
you need not worry ironfistchamp, unix has a built in command: fmt. Very simple and perhaps not what you need, but it's a good simple start.

when running your program from the shell or a .sh file, use format and pipe the output of your file into it.
```

yourprogram | fmt -w 80

```
should output at 80 char columns.

EDIT: maybe I've jumped the gun, is fmt in ubuntu?

---

### Post by ironfistchamp on 2006-07-03
The last reply didnt work I am afraid :(. The rest I really don;t understand. I have been programming properly for about a week now. Guess I am going to have to knock it on the head for now. 

Shame really as it was going quite well. I was creating a text based game. I had the character creation done almost perfectly and was getting the hang of creating some functions for battle. Can't believe it is all held up by controlling the console width.

Thanks though

Ironfistchamp

---

### Post by -Rick- on 2006-07-03
[QUOTE=ironfistchamp]The last reply didnt work I am afraid :(. The rest I really don;t understand. I have been programming properly for about a week now. Guess I am going to have to knock it on the head for now. 

Shame really as it was going quite well. I was creating a text based game. I had the character creation done almost perfectly and was getting the hang of creating some functions for battle. Can't believe it is all held up by controlling the console width.

Thanks though

Ironfistchamp[/QUOTE]
For "serious" console programs/games you really need to check out (n)curses. [Here]("http://www.tldp.org/HOWTO/NCURSES-Programming-HOWTO/") is a good howto for ncurses. The man pages are a good reference.
In ncurses it's pretty easy to get the max width/height of the screen and as a bonus you get many other things such as: colors, unblocked key handling, text windows, mouse support(on some systems) and putting text where ever you want.

---

### Post by ironfistchamp on 2006-07-03
Ooh sounds too good to be true I shall check it out thanks.

EDIT: Downloaded it. Looks good. The examples it comes with don't work. The key presses of the F keys dont work (e.g. F1 which should exit brings up the terminal help) and the mouse doesnt either.

Anyone know why? Also does it work with C++ (yes total idiot here). It looks kinda like C with the whole printw(). Reminds me of printf.

Thanks

Ironfistchamp

---

### Post by -Rick- on 2006-07-03
> **ironfistchamp]Ooh sounds too good to be true I shall check it out thanks.

EDIT: Downloaded it. Looks good. The examples it comes with don't work. The key presses of the F keys dont work (e.g. F1 which should exit brings up the terminal help) and the mouse doesnt either.
[/quote]
Ubuntu seems to have a broken terminfo said:**
> 
Also does it work with C++ (yes total idiot here). It looks kinda like C with the whole printw(). Reminds me of printf.

Thanks

Ironfistchamp
Sure, most C code works with C++. Besides there is an C++ interface for it included(libncurses++). It's not documented, but has a good example. I use it so I got experience with it, if you want some help you can call me if you want :)

---

### Post by ironfistchamp on 2006-07-04
Thanks I may be posting alot around here then. I shall explore the C++ interface but I am not exactly sure what it changes. I shall read though the documentation some more. 

Thanks again

Ironfistchamp

---

