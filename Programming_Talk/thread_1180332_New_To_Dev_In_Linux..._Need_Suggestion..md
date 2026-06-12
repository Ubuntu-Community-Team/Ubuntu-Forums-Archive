---
title: "New To Dev In Linux... Need Suggestion."
date: 2009-06-06
forum: Programming Talk
---

### Post by dharvell on 2009-06-06
As the title states, I'm new to developing in a Linux environment, but I've been a Linux user for the better part of decade.  Now, that I've switched platforms, I need your help finding the right tools.

I need an editor that colorizes the code, depending on the type of code being written.  The types of code that will be used are:

HTML
PHP
CSS
JavaScript

As I write everything in code (no Dreamweaver-types programs needed), an editor is all I need.

Thanks for pointing me in the right direction!

+dharvell

---

### Post by kvarley on 2009-06-06
I strongly recommend Quanta Plus or Kate.

Install:
> sudo apt-get install quanta
> sudo apt-get install kate

Kate is KDE

Or use Notepad Plus through wine.

---

### Post by dharvell on 2009-06-06
> **vitium said:**
> I strongly recommend Quanta Plus or Kate.

Install:



Kate is KDE

Or use Notepad Plus through wine.

Thanks!  I tried looking at the sticky, but ran into a bunch of dead links.  I'll try the editors you recommended.

---

### Post by Can+~ on 2009-06-06
If you're on ubuntu, the basic ubuntu notepad (gedit) alreay highlights syntax, open "Edit > Preferences" and adjust it to have numbered lines, bracket mactching, 4 tabs, etc.

If you need bigger tools (I know you don't want another dreamwaver, but even though...), check [Aptana]("http://aptana.com/")

---

### Post by Mirge on 2009-06-06
I've tried Aptana, Eclipse, etc... all were just too slow/bloated for me. I tried Geany and never looked back. Fantastic editor.

---

### Post by jbruced on 2009-06-06
Eclipse has a lot of power and support for various languages.

---

### Post by dharvell on 2009-06-06
I just made an awesome discovery!  When I was using... ahem... Windows, I was using an editor called Araneae.  Just for kicks, I tried it under Wine.  It works!  

Really, between KATE and Araneae, the thing I like about Araneae is the fact that the cursor is automatically placed indented the same amount as the previous line.  So no more hitting TAB to get where I need to be (which is another feature I forgot to mention that I was looking for... oops).

If anybody here is familiar with Araneae, does anybody know if there is a Linux equivelant that has the same functionality?  KATE and Quanta are both close, but the cursor returns to hard left everytime you hit <ENTER>.

---

### Post by Can+~ on 2009-06-06
> **dharvell said:**
> Really, between KATE and Araneae, the thing I like about Araneae is the fact that the cursor is automatically placed indented the same amount as the previous line.  So no more hitting TAB to get where I need to be (which is another feature I forgot to mention that I was looking for... oops).

[IMG]http://img.photobucket.com/albums/v517/CanXp/screenshot1-6.png[/IMG]

---

### Post by dharvell on 2009-06-06
> **Can+~ said:**
> 

I use Kubuntu, so gEdit isn't currently installed on my machine (doesn't mean it couldn't be, though...).

---

### Post by monraaf on 2009-06-06
VIM has all that stuff you mentioned and lots more, it's one of the most powerful editors out there, comes standard with most if not all Linux distro's and you don't even need to have an X Server running to use it.

---

### Post by dharvell on 2009-06-06
> **monraaf said:**
> VIM has all that stuff you mentioned and lots more, it's one of the most powerful editors out there, comes standard with most if not all Linux distro's and you don't even need to have an X Server running to use it.

As it turns out, I found the setting in Kate that allows the cursor to return to the same indentation point as the previous line.  It was found in:

Settings > Configure Kate
Editing > Indentation > Default Indentation Mode = "Normal" (default is "None")

Looks like Kate will work just fine... and not suck resources like a Wine application seems to.

---

### Post by krzysz00 on 2009-06-06
emacs

---

### Post by sujoy on 2009-06-07
you can choose to use IDE or not. however, pick one text editor and learn it inside out. it really helps in a lot of situations, and depending on the editor, it can also save you from having to write a few scripts to get things done.

---

