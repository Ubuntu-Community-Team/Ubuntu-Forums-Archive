---
title: "[SOLVED] GladeGen - A very strange error indeed!"
date: 2008-11-03
forum: Programming Talk
---

### Post by MaxVK on 2008-11-03
Having made a start with wxPython I have had to move to PyGTK. All seems fine, but I rather like the idea of using GladeGen.

The problem is that the program GladeGen.py, seems to be invisible!

Let me describe what I have done:

Downloaded GladeGen ;)
Place this into folder A
Used Glade(3) to create an interface
Saved the interface as Test.glade in the folder A (along with GladeGen.py)
Open a terminal window
CD to folder A
Type 'GladeGen.py Test.glade Test Test

According to the tutorial ([http://www.linuxjournal.com/article/7421](http://www.linuxjournal.com/article/7421)) this should now produce the required files with the event handlers etc.

However, what I get is this:
"bash: GladeGen.py: command not found"

I'm lost! Am I doing something so silly that I cant even see what it is? Surely since I have CD'ed to the folder GladeGen.py should be available!

I have tried using GladeGen as it came from the archive file, Iv tried making the file executable, but no matter what I do I get that message, which seems to make no sense!

Anyone have any ideas please.

Cheers

Max

---

### Post by happyhamster on 2008-11-03
Is GladeGen.py a binary? Try:

./GladeGen.py Test.glade Test Test

Else:

python GladeGen.py Test.glade Test Test

---

### Post by MaxVK on 2008-11-03
> python GladeGen.py Test.glade Test Test

Ah now, that did it! Thanks.

But I wonder why I needed to add 'python'? It does not suggest this in the tutorial I was reading, and having made the file executable (I'm now using the original from the archive again) in my fiddlings surely it should have worked!

Anyway, many thanks for your help.

Regards

Max

---

### Post by SeanHodges on 2008-11-04
> **MaxVK said:**
> But I wonder why I needed to add 'python'? It does not suggest this in the tutorial I was reading, and having made the file executable (I'm now using the original from the archive again) in my fiddlings surely it should have worked!

You were omitting the "./" at the beginning of your command. This is fine, as long as you're working directory is in your PATH environment variable. If you type:

```
echo $PATH
```

You'll get a list of the paths that will be looked in for the program if you omit "./" in your command; if the program is placed in any of these directories it will be found when typing "commandname [args]".

Usually, in Ubuntu you do not have your working directory in this list, so you need to type "./commandname [args]" to tell BASH that the program is in your current directory.

---

### Post by MaxVK on 2008-11-04
That makes sense - I thought it might be something so blindingly obvious that I was missing it - Cant see the wood for the trees and so on!

Thanks for your reply - Its always nice to know where you are going wrong! ;)

Regards

Max

---

### Post by SeanHodges on 2008-11-05
No problem, happy to be of some help :)

---

