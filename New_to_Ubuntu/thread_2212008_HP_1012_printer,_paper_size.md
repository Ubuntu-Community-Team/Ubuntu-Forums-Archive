---
title: "HP 1012 printer, paper size"
date: 2014-03-18
forum: New to Ubuntu
---

### Post by wjbmd48 on 2014-03-18
Hi:

On all the distros I've used, 11.04 through the 14.04 daily builds, my HP 1012 printer defaults to a 3x5 inch page size, so every time I print something, I have to remember to go to "properties" and select "US letter."

Is there an easy way (preferably GUI) to set the hplip default to the US letter size?

Thanks!

Bill

---

### Post by Bucky Ball on 2014-03-18
You could try going into 'Printers' or 'Printing' (unsure which on Unity), select the default printer properties (presuming that is your HP), and change the default settings there. That should stick.

You should also be able to do it via a web browser, if you are using cups, by typing 'localhost:631' in the address bar and hitting return. You can then set up the printer how you wish. I actually only use this method as I have a minimal install and don't bother installing the regular 'Printers' GUI.

---

### Post by wjbmd48 on 2014-03-18
Crikey, I forgot to mention that this happens only with pdf  files--doesn't matter which reader I'm using--Foxit or Document Reader.  With Word, AbiWord, Thunderbird, or Firefox, it prints properly at  8.5x11, and now that you've directed me to the printer properties,  that's what it's set at.

So this is a .pdf specific problem.

Sorry for the confusion, my bad. 

Any ideas?

Bill

---

