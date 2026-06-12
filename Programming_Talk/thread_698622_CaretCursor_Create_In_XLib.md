---
title: "Caret/Cursor Create In XLib?"
date: 2008-02-16
forum: Programming Talk
---

### Post by Frederick J. Harris on 2008-02-16
That little blinking thingy in a text box that indicated the text insertion point for typed characters...

What is the correct name for it in terms of XLib?  I'm studying Adrian Nye's XLib tutorial, and I'm confused about terminology.  I'm a Windows  Api programmer trying to learn a little XLib, and in windows we call the 'I' beam text insertion point (which blinks) a 'caret'.  The cursor refers to the mouse pointer.

In Windows I have never had to actually 'create' a caret from scratch as there is an Api function - CreateCaret(HWND hWnd) - for that.  I can't seem to find anything like that in XLib, so I'm curious how a caret is actually constructed and how one makes it blink.  I'm assumming the blinking would have to work off a system timer/clock of some sort.  The actual visible blinking entity itself I'm assuming would have to be a pixmap or something.  I'd like to learn how to do it but if anyone could 'flesh out' the concept a little more for me I'd appreciate it.  Are there perhaps some pre-existing routines I've overlooked?

At the moment I have materials for teaching myself XLib, Motif/Lesstif/Xt, and GTK+.  I've worked more with XLib than the other two.  Actually, if I could figure out the blinking caret thing I believe I could satisfactorily make a text box control of my own.  If I had a text box control I could make a grid.  I'd be well on my way to having made my own toolkit (I need to make buttons too).

I also like Lesstif but there is something wrong with the textbox code, and surprisingly (and unrelated to this question), it concerns the text insertion point caret (if that's what it is called in Linux circles).  When you switch focus to a second text box random pixels of the former insertion point remain in the first textbox and it looks really funky!  If I knew who to send the info/code/screenshot to I would do that so they could look at it and try to figure out what's wrong.  I know I ramble.

Fred

---

### Post by stroyan on 2008-02-16
Both lesstif and gtk call the 'little blinking thingy' a cursor or 'insertion cursor'.  The blinking is created by drawing and
redrawing the cursor array at regular intervals.  You can get the source code for the lesstif and gtk libraries and look at all the details directly.
```
mkdir lesstif2_source
cd lesstif2_source
apt-get source lestiff2
cd lesstif2-0.94.4/lib/Xm-2.1
view TextOut.c
```
The timing of the blink is in the HandleTimer callback function.
The actual drawing is spread over several functions starting with CursorInit.

---

### Post by Frederick J. Harris on 2008-02-16
Duhhh!  Why didn't I think of that, examining the source code, that is?  Well, the reason I didn't think of that is because examining the source code isn't the first thing that comes to the mind of MS Windows Programmer when he/she/it wants to know how something is done.  All kidding aside, Thanks Stroyan.  I'll run your script and see if I can't figure it out.

---

### Post by Frederick J. Harris on 2008-02-16
Say, Stroyan, I'm having a little trouble with that script.  You see, I'm still a newbie at Linux, so that's probably it.  Anyway, should that whole thing be run as a batch file?  I don't know how to do that in Linux.  I tried to run it one line at a time and it didn't work.  

First I created the directory...

 /home/fredharris/lesstif2_source

Then I changed to that directory...
 
cd lesstif2_source

Then I ran

apt-get source lestiff2

Here is the output from Terminal (bash I guess)...

fredharris@CODEWARRIOR:~$ cd lesstif2_source
fredharris@CODEWARRIOR:~/lesstif2_source$ apt-get source lestiff2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for lestiff2
fredharris@CODEWARRIOR:~/lesstif2_source$ 

Any thoughts for this lowly newbie?

---

### Post by stroyan on 2008-02-17
You need to have the source code repositories listed in your /etc/apt/sources.list file.
You could edit that file and add the lines.  For example after
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
you would add-
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

Or using synaptic you can enable the source repositories under the "Settings->Repositories" menu item.

---

### Post by Frederick J. Harris on 2008-02-17
Thanks again Stroyan.  I need to become more familiar with that (downloading sources), so I'll try it tomorrow.

Fred

---

