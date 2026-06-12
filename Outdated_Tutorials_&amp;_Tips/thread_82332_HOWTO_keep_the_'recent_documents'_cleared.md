---
title: "HOWTO: keep the 'recent documents' cleared"
date: 2005-10-26
forum: Outdated Tutorials &amp; Tips
---

### Post by SpectralDesign on 2005-10-26
There's probably a way to remove the 'recent documents' menu item from the Places menu, but I haven't found it yet. :D 

Instead, I offer a way to disable it:

For starters, empty the recent documents list:

Places... Recent Documents... Clear Recent Documents

Then, from a terminal window with your home directory as your working directory (just type 'cd' <enter> to make sure you're in your home directory) issue this chmod command:

chmod ugo-w .recently-used

Now no more documents will be added to the menu!

---

### Post by SpectralDesign on 2005-10-27
Silly me - of course this can be made slightly easier for those that aren't comfortable in a terminal window, and/or don't know their way around the command line... instead of worrying about the 'cd' command to make your home directory your current working directory this one command will lock the recend documents list from having new items added to it:

chmod ugo-w ~/.recently-used

(the tilda (~) tells the shell to "fill in" the path to your home directory, so you can do this from any working directory.)

---

### Post by Sionide on 2005-10-28
How do you undo it again after?

...Answered my own question;

chmod ugo+w ~/.recently-used

---

### Post by SpectralDesign on 2005-10-28
Thanks, I guess I should have posted that little tidbit too!

---

### Post by MadCowDzz on 2006-03-12
I have a related question and I'm having trouble finding results by searching (the words Go and History are hard to get proper results)

While looking at an open folder, the *Go* menu has a history as well. 
Where is this stored, and is it an easy way to disable it?

---

