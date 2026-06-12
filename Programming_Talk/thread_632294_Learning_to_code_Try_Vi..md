---
title: "Learning to code? Try Vi."
date: 2007-12-05
forum: Programming Talk
---

### Post by ThinkBuntu on 2007-12-05
**A little history...**

I've been coding in HTML and CSS for the past eight years, since I was about twelve years old. As time has drawn on, I have also coded in JavaScript and PHP every now and then, but more than anything I'm HTML and CSS. Now HTML tends to be very ... repetitive. The nature of it, being a markup language, means that unless you're using PHP to parse your entire page, you will need to perform many repetitions of opening and closing tags, and so on.

I began with Notepad (school computer uses Windows), graduated to SimpleText which is a simpler version of Notepad but can speak to you (Mac OS &#8804; 9's default editor) and eventually moved up to a trial of BBedit. From there I stole BBedit, and never felt bad about it since it never was anything more to me than SimpleText with code highlighting and a file pane. Finally I moved up to Dreamweaver at my first real web job (mainly for the inline FTP capabilities) and finally the excellent TextMate which I still use for most of my coding now.

**If only someone told me about Vim earlier!**

It blows my mind to think about how much time and hand stress I've wasted on repetitive syntax. I'm talking hundreds of hours here milling away at code. Recently I took a cursory glance at Vim (I've used it before but never really "got" it) and I already know that the simple "." shortcut, repeat previous command, could have saved me 90% of that time. I know I'm only scratching the surface right now, but I can already tell that coding will never be the same repetitive task that it always has been for me.

So if you are serious about coding, and expect to put in any more than 100 hours in your lifetime, I advise you to learn Vim. Your fingers will thank you.

---

### Post by Majorix on 2007-12-05
I have always wanted to use Vim myself but never really got to. I don't know how to use it to start with. Do you have any docs you can link me to?

---

### Post by ThinkBuntu on 2007-12-05
Here are a couple good ones:
* Basics: [http://jmcpherson.org/editing.html](http://jmcpherson.org/editing.html)
* More resources than I know what to do with: [http://thomer.com/vi/vi.html](http://thomer.com/vi/vi.html)
* This really demonstrated the power of Vi for me, although some parts are poorly put together: [http://www.viemu.com/a-why-vi-vim.html](http://www.viemu.com/a-why-vi-vim.html)

---

### Post by ThinkBuntu on 2007-12-05
A couple things you'll want to know right away:

**i** is to enter edit mode
**ESC key** is to leave edit mode for normal mode. Normal mode is default.

**u** = undo last change
**Control + r** = redo last change
**:w** = save
**:q!** = quit without saving
**ZZ** = save and quit (**:wq** is so slow)
**h** = left
**l** = right
**j** = down
**k** = up

Simple .vimrc options:
```

syntax on
set autoindent
filetype indent on

```
Syntax highlighting, auto-indentation.

---

### Post by geirha on 2007-12-05
vim comes with a nice tutorial which takes you through all the basics. Just type ```
vimtutor
``` in a terminal.

---

### Post by ThinkBuntu on 2007-12-05
> **geirha said:**
> vim comes with a nice tutorial which takes you through all the basics. Just type ```
vimtutor
``` in a terminal.
vimtutor did not teach me many useful gestures and in my opinion was a slow tutorial. Probably why I didn't adopt vi at the time. O'Reilly's Vim book is also tedious, would not recommend.

---

### Post by CptPicard on 2007-12-05
I recommend that you familiarize yourself with this

[http://www.dina.kvl.dk/~abraham/religion/](http://www.dina.kvl.dk/~abraham/religion/)

before condemning your soul... :(

---

### Post by mellowd on 2007-12-05
I'm a huge vim fan and at work vi is all we ever use.

---

### Post by mellowd on 2007-12-05
btw, a few more useful commands:

r - to only replace one letter or symbol
oo - insert a new line after the current line




I didn't know about ZZ, I always used :wq!   - must use it in future.

---

### Post by ThinkBuntu on 2007-12-05
o = insert line below current line and enter insert mode
O = same, but for line above current

---

### Post by Vadi on 2007-12-05
Thanks man, I'll give it a try.

Glued to notepad++ atm, so much that it's pretty much the only app I use wine for.

---

### Post by lvleph on 2007-12-05
I got this from a coworker and he didn't know where he got his, so I hope this helps out. It is the best vi quick reference I have seen. Mostly because of the organization.

It is a pdf that was too big for attaching as a pdf.

I think using things like 3y is the nicest thing about vi. 

3y=Yank 3 lines. That is so easy.
3dd=delete 3 lines

5,10y=Yank lines 5 through 10.

Oh and one I just noticed that I have never used

5,10t 13= copy line 5 through 10 to line 13. Nice!

Then of course there is regex support!

---

### Post by Majorix on 2007-12-05
Thanks for the links, I am checking them.

---

### Post by samjh on 2007-12-05
Vim reference for beginners:
[http://ubuntuforums.org/showthread.php?t=564554](http://ubuntuforums.org/showthread.php?t=564554)

---

