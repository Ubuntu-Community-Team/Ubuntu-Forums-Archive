---
title: "Nuked spellcheck dictionary when switching from Open Office to Libre Office in 10.04"
date: 2012-06-07
forum: New to Ubuntu
---

### Post by nosehat on 2012-06-07
A while ago I switched from Open Office to Libre Office on a 10.04 machine, but apparently I did something wrong because now my spell check dictionary is gone.  This is not just for Libre Office, but for** everything system-wide** (Thunderbird, web text boxes, etc.)  I've lost spellchecking everywhere.

I probably did something in the wrong order when I made the switch.  Maybe I installed LO from the PPA before uninstalling OO?  On a second 10.04 machine I made the switch without a problem, so I know it should work.  I'm sure I just screwed something up here.

Any ideas where to look to try to fix this?  

Thanks in advance!

---

### Post by ajgreeny on 2012-06-07
Make sure you have the aspell, myspell and hunspell installed and that may help.

For any added words in your own personal dictionary from OOo, see if there is still a hidden .openoffice.org folder in your home where the old configuration including dictionary will still be.

---

### Post by nosehat on 2012-06-07
Thanks for the reply, ajgreeny.

I seem to have some libraries installed:  libaspell15, libhunspell-1.2-0 *and* libhunspell-1.3-0.  Oops!  Could the two versions of libhunspell be a problem?

I don't seem to have aspell or hunspell itself installed though.  I don't see a "myspell" package in the repositories, just a "myspell-tools" and some language specific myspell dictionaries.

Do I need all three?

I also have installed libenchant1c2a ("a wrapper library for various spell checker engines")

I *do* have a hidden .openoffice.org folder in my home folder!  I found a file ~/.openoffice.org/3/user/wordbook/standard.dic which is only 53 bytes long and contains 5 words and a bunch of null bytes.  Is there anywhere else to look for more words?  I'm pretty sure I'd added more than 5 to OO.

Thanks again.

---

### Post by nosehat on 2012-06-08
Solved by simply installing:

aspell
aspell-doc
aspell-en
dictionaries-common
hunspell
hunspell-en-us

Not sure if all of these were necessary, but now it works so I'm happy regardless.
Thanks! :D

---

