---
title: "Spell Check doesn't work???"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by fishman78 on 2008-07-29
Hi All,

   Trying to use Open Office in Ubuntu for the first time, but the spell check doesn't work.  Even if I purposely type something wrong it tells me all is okay.  Does Open Office rely on a Ubuntu dictionary?  Or is this something I have to install separately?  Thanks for all your help!!

Fishman78

---

### Post by knightcoder on 2008-07-29
There are a lot of times it has happened to me. I think they really are bugs. I think they would work fine once you restart OpenOffice.

---

### Post by fishman78 on 2008-07-29
Thanks for the tip, but I started it up a couple of times and no-go.  Maybe it's spelling is worse than mine??:rolleyes:  Any other suggestions I might be able to try?  Thanks again!

Fishman78

---

### Post by pedrogent on 2008-07-30
Hey fishman78.

This, for me, is an absolute show stopper flaw in OpenOffice. If I were in the word processor development industry, having a functional spell checker would be right up there on the list of priorities. Unfortunately it doesn't seem to be the case tho'.

Here's how you fix it.

Close OpenOffice. Open up Synaptic. Do a search for spellchecker. Install the one you want. Close Synaptic. Re-open OpenOffice.

The spellchecker *should* work now.

Hope this helps.

PS: OpenOffice developers - spellchecking is important. Please re-prioritize this crazy issue.

---

### Post by tinny on 2008-07-30
You need to make sure that you have a spell checker supported language selected as your default document language.

"Tools" > "Options" > "Language Settings" > "Language" >

"Default Languages for documents" > "Western" then select a language with a "ABC tick" icon next to it.

Done! :)

---

### Post by The Pinny Parlour on 2008-09-13
The way one has to implement spell checker in OO.o is a complete joke.  
Sun really needs to improve this.

---

### Post by NewDream on 2008-12-02
Just taking a glance at this thread. . . the way to fix this is very easy.  Open a terminal, and type this command:

sudo apt-get install myspell-en-us

Enter your administrative password and install the package.

If you use synaptic package manager, the package you need to install is myspell-en-us (assuming the language you use is American English).  Hopefully this helps someone.

---

### Post by The Pinny Parlour on 2008-12-03
Thank goodness OO.o 3 implements spell checkers much easier via 'add-ons'.

---

