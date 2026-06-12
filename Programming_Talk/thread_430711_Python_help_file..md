---
title: "Python help file."
date: 2007-05-02
forum: Programming Talk
---

### Post by kikapu on 2007-05-02
Hi to all,

i have created a copy of my WinXP development environment (Python/Eclipse/PyDev/Qt) on Ubuntu and things are working great!
The only "problem" i have for now is this:
In Windows, i can locate the Python help file at "C:\Python25\Doc\Python25.chm" and place a shortcut of this on my Desktop for convenient use.

Where is the respective Python help file in Ubuntu so i can place a Link of it in the desktop for the same use ??

---

### Post by AdamG on 2007-05-02
make sure you've: apt-get install python-doc
Then the docs are in:
/usr/share/doc/python/html/index.html

---

### Post by kikapu on 2007-05-02
AdamG thanks! i did what you said and i have the html files now.

Thanks again!

ps: In the .chm help file  on Windows, we can...search for something in it. How we can do it in now ??

---

### Post by cwaldbieser on 2007-05-03
> **kikapu said:**
> AdamG thanks! i did what you said and i have the html files now.

Thanks again!

ps: In the .chm help file  on Windows, we can...search for something in it. How we can do it in now ??

Here are some options I thought of (though I haven't tried some):

+ The swish-e package lets you index HTML pages among other things.  It seems to be quite powerful.
+ KDE has the kchmviewer package that would let you view your Windows compressed HTML file (.chm).
+ Google when online.
+ grep the HTML directory recursively.

---

### Post by kikapu on 2007-05-03
> **cwaldbieser said:**
> Here are some options I thought of (though I haven't tried some):

+ The swish-e package lets you index HTML pages among other things.  It seems to be quite powerful.
+ KDE has the kchmviewer package that would let you view your Windows compressed HTML file (.chm).
+ Google when online.
+ grep the HTML directory recursively.

Hey thanks!

kchmviewer and swish-e, are software that i can install from Synaptic ??

---

### Post by cwaldbieser on 2007-05-03
> **kikapu said:**
> Hey thanks!

kchmviewer and swish-e, are software that i can install from Synaptic ??

Yes.  You might need universe, but I found them by searching the package lists.

---

### Post by kikapu on 2007-05-04
I downloaded and installed kchmviewer. I am able now to use Python .chm help file (Windows version) on Ubuntu and i am happy!

Thank you all!

---

