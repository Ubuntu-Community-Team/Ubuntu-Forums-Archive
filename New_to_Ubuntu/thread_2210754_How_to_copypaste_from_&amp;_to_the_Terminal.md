---
title: "How to copy/paste from &amp; to the Terminal"
date: 2014-03-12
forum: New to Ubuntu
---

### Post by BlueGene1402 on 2014-03-12
Just installed Lubuntu 13.10 on an old laptop & before I can ask for help in the appropriate forum sections for my other problems I need to know how to copy/paste to & from the terminal! I have no problem with this with Ubuntu, just ctrl+c & ctrl+v with a little help from the mouse. But that's not working in Lubuntu (neither is ctrl+shift+v).

I need to copy command results so people can help me. And they're too long to type by hand. And I don't know any other way. Couldn't even take a screenshot. Open to suggestions.

Many thanks for all the time & effort that goes into these forums.

---

### Post by smdubinsky on 2014-03-12
Try highlighting it and using the middle-click.

Alternatively, ctrl-shift-c and ctrl-shift-v work for me, in bash.  Not using Lubuntu, but it's something to try.

---

### Post by David D. on 2014-03-12
I use CTRL-C in the forums to copy.  In terminal I right click with the mouse and select "paste".

---

### Post by ajgreeny on 2014-03-12
In terminal (all of them, I think) it needs Ctrl+Shift+C (or V) because Ctrl+C is used to kill the current running command, though I am not sure what Ctrl+V does, if anything.

---

### Post by BlueGene1402 on 2014-03-12
I highlight the text in the terminal with the mouse, no problem. Tried the middle mouse click, and ctrl+shift+c but sadly neither worked :(

---

### Post by Rex Bouwense on 2014-03-12
> **BlueGene1402 said:**
> I highlight the text in the terminal with the mouse, no problem. Tried the middle mouse click, and ctrl+shift+c but sadly neither worked
I just used the mouse to copy from the terminal to a document and from the document to the terminal.  Merely highlight the desired passage, right click to copy and right click on your document to paste.  It also works from the document to the terminal.  Are you saying that this does not work for you in Lubuntu 13.10?
Lubuntu 13.10 has problems with print screen.  I installed screenshot from the repositories and that became a work around for the print screen problem.

---

### Post by bapoumba on 2014-03-12
Just to note that shift-ctrl-c and shift-ctrl-v work here in lubuntu 13.10 terminal.

---

### Post by Impavidus on 2014-03-12
> **ajgreeny said:**
> In terminal (all of them, I think) it needs Ctrl+Shift+C (or V) because Ctrl+C is used to kill the current running command, though I am not sure what Ctrl+V does, if anything.

Ctrl+V escapes the following control character. For example, if you type Ctrl-V Ctrl-C, an actual End-of-Text byte is send to standard input of the running process, instead of sending a signal.

---

### Post by oldos2er on 2014-03-12
> **BlueGene1402 said:**
> I highlight the text in the terminal with the mouse, no problem. Tried the middle mouse click, and ctrl+shift+c but sadly neither worked :(

Can you paste into a text document (in leafpad) with middle-mouse-button click? Odd that it doesn't work for you in a terminal.

Otherwise I use Ctrl-Insert to copy, Shift-Insert to paste.

---

### Post by ajgreeny on 2014-03-12
@ OP:
Are you talking about a GUI terminal or do you mean the cli command line, ie a tty (Ctrl+Alt+F1-6)?

I am not sure about copy/paste in that situation, never having tried it.  Of course the mouse does not work in a cli so it may not be possible at all, but certainly the mouse right click and middle click talked about above works fine in Lubuntu 14.04, which is the only version I have running at the moment.

---

### Post by BlueGene1402 on 2014-03-13
Many thanks for all the replies. We've had repeated power failures due to a thunder storm & I couldn't get back any sooner.

@ajgreeny I suppose it's a GUI terminal, since I don't even know what the other thing is.

@Ann I tried ctrl+insert / ctrl+shift .. didn't work!

@Rex I don't know how to download Screenshot without an internet connection.

I can copy & paste normally in other applications (word processor, web browser, etc) meaning by keyboard, mouse or a combination of both. It's only not working in the terminal.

---

### Post by BlueGene1402 on 2014-03-15
I don't know what happened but after the laptop rebooting a few times (power failures due to storm, laptop batter dead) it's now working normally. Go figure.

---

### Post by Rex Bouwense on 2014-03-15
Not sure how or why that happened but that is how it is supposed to be.  Great.

---

### Post by john195 on 2014-06-13
> **oldos2er said:**
> Can you paste into a text document (in leafpad) with middle-mouse-button click? Odd that it doesn't work for you in a terminal.

Otherwise I use Ctrl-Insert to copy, Shift-Insert to paste.

I'm using Ubuntu 12.04 and the Shift-Insert worked.  Ctrl + Shift + V would not work.

---

### Post by bapoumba on 2014-06-14
> **john195 said:**
> I'm using Ubuntu 12.04 and the Shift-Insert worked.  Ctrl + Shift + V would not work.

Which terminal are you using on which Ubuntu flavor ?
That is strange. Will <ctrl><shift><c> work to copy something from the terminal and paste into gedit or another word editor for ex ? Are you using custom shortcuts ?

---

