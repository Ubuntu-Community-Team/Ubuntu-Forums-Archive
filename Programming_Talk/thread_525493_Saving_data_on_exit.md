---
title: "Saving data on exit"
date: 2007-08-14
forum: Programming Talk
---

### Post by NeillHog on 2007-08-14
Another question which is probably easy for all you Python experts (which I am definitely not yet having been programming in Linux and Python for a week).

When I start my program I call the module that produces the GUI and then in the __init__ of that module add in the saved valued from a config file.

When the user closes the file I would like to save all the values back to the config file. 
Everyone writes that I shouldn't do anything in __def__ especially if it uses global variables.

OK! So where should I put the code to write to the config file?

At the moment I am writing back the values each time the user rund the translation which works but is not elegant.

Thanks as always
Neill

(If I have not explained things very well - the code is at [http://www.teamhogarth.de/python/archive.zip](http://www.teamhogarth.de/python/archive.zip))
:-)

---

### Post by NeillHog on 2007-08-14
I have just spent a few hours searching for an answer to this question but have had no success.

Maybe my current "inelegant" way of doing things is not so bad after all - even though it still looks ugly to me .-(

Neill

---

### Post by rekahsoft on 2007-08-14
when using pygtk just connect the destroy signal to a function that saves data and then exits :P

---

### Post by NeillHog on 2007-08-14
Thank you for that suggestion but, unfortunately, I am not using pygtk.

I created my GUI with QT Developer and have added the code manually.

But maybe here I also have a "destroy" signal. If no one else can help, I will search again tomorrow.

Thanks again.
Neill

---

