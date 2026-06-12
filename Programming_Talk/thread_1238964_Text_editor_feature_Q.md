---
title: "Text editor feature Q:"
date: 2009-08-13
forum: Programming Talk
---

### Post by Krupski on 2009-08-13
Hi all,

Is there a plain text editor in Ubuntu (like gedit or kate type) which allows cut and paste of COLUMNS?

For example, I wish to be able to do this:

```

name-01.bin
name-02.bin
name-03.bin

[COLOR="Blue"]**name_01.exe**[/COLOR]
[COLOR="Blue"]**name_02.exe**[/COLOR]  <-- select these, then cut...
[COLOR="Blue"]**name_03.exe**[/COLOR]


```


```

name-01.bin   **[COLOR="Blue"]name_01.exe[/COLOR]**
name-02.bin   **[COLOR="Blue"]name_02.exe[/COLOR]**  <-- and paste them here
name-03.bin   **[COLOR="Blue"]name_03.exe[/COLOR]**


```

Thanks!

-- Roger

---

### Post by Natr0n on 2009-08-13
[Emacs]("http://www.gnu.org/software/emacs/") can [do it]("http://www.gnu.org/software/emacs/manual/html_node/emacs/Rectangles.html#Rectangles").

---

### Post by Krupski on 2009-08-14
> **Natr0n said:**
> [Emacs]("http://www.gnu.org/software/emacs/") can [do it]("http://www.gnu.org/software/emacs/manual/html_node/emacs/Rectangles.html#Rectangles").

Thank you for the reply. I went to the link you posted (I already had emacs installed).

Maybe I'm a dummy... but I just don't seem to get what the "Control-X, R..." commands do or how to use them.

In other editors (in Windows, for example), I can do something like hold down shift or control and highlight a "box" of text, then cut and paste it anywhere I wish.

That's sort of what I was hoping to find... as well as an editor similar to NANO (i.e. a simple, console based text editor).

Concerning emacs, do you know if it's possible to bind (or re-bind) commands to different keys and/or mouse buttons?

If so, I might be able to replicate the "hold shift and select a rectangle" type of action.

Oh well.. thanks again for the info, and if you can tell me any more (or help me figure out the emacs rectangle commands), I would greatly appreciate it.

Thanks!!!

-- Roger

---

### Post by geirha on 2009-08-14
[vim](apt://vim) can too of course. Enter visual mode with Ctrl+v, move the cursor to the opposite corner of the rectangle, then y to yank or d to delete. Move to the upperleft corner of where you want to paste it and hit p.

---

### Post by kaligus on 2009-08-18
+1 for wanting simple plain editor such as Emerald/Crimson from my long gone windows days .  

I have found replacement for all of crimsons features and found new things I cant live without in Geany.

But I have not found an editor I can use in my sleep/drunken-stupor/etc. that will do rectangular blocks as well or sweetly as that pleasantly wine-enabled (if you accept a few kinks) editor

---

### Post by jpkotta on 2009-08-19
> **Natr0n said:**
> [Emacs]("http://www.gnu.org/software/emacs/") can [do it]("http://www.gnu.org/software/emacs/manual/html_node/emacs/Rectangles.html#Rectangles").

Sure, you can use the built-in rectangles, but they're so clunky.  Use CUA rectangles instead.  You can use them even if you don't want the rest of CUA mode.

[http://www.emacswiki.org/emacs/CuaMode](http://www.emacswiki.org/emacs/CuaMode)

---

### Post by knattlhuber on 2010-01-01
Geany can do that when you hold down the Ctrl-key and then drag the mouse over the columns.

---

### Post by cyberslayer on 2010-01-01
> **Krupski said:**
> Thank you for the reply. I went to the link you posted (I already had emacs installed).

Maybe I'm a dummy... but I just don't seem to get what the "Control-X, R..." commands do or how to use them.

In other editors (in Windows, for example), I can do something like hold down shift or control and highlight a "box" of text, then cut and paste it anywhere I wish.

That's sort of what I was hoping to find... as well as an editor similar to NANO (i.e. a simple, console based text editor).

Concerning emacs, do you know if it's possible to bind (or re-bind) commands to different keys and/or mouse buttons?

If so, I might be able to replicate the "hold shift and select a rectangle" type of action.

Oh well.. thanks again for the info, and if you can tell me any more (or help me figure out the emacs rectangle commands), I would greatly appreciate it.

Thanks!!!

-- Roger

You can rebind keys in emacs using global-set-key and local-set-key in your .emacs (among other methods).  However, what you need to do in this case is to select the desired column by pressing C-SPC at the first entry of the column.  Then go the last entry of the column and press C-x r k to kill the rectangle.  You can then yank it using C-x r y.

---

