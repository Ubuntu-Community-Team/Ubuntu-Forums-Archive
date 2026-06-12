---
title: "Python question: nested classes without messing with namespace?"
date: 2008-11-21
forum: Programming Talk
---

### Post by Mr. Picklesworth on 2008-11-21
First of all, this is completely unnecessary and I have already solved the problem with the obvious alternatives, but I am curious to know if this is possible so I can shave a few lines of code.

So I have a class that manages an editor's GUI. There are a bunch of callback functions that I prefer to keep hidden, so one neat way to do that would be to tuck them away inside a single object, for example with a nested class. The trouble with a nested class is that all my functions in there are in a different scope; they don't see my instance of the parent. I could pass the nested class instace its parent, but that doesn't look very nice.

So any other way to do this? I want to define my callback functions, preferably inside one specific thing. This way I won't need a whole other dictionary that links to them when I run gtk.Builder.connect(), thus saving a fair bit of space and making the code look pretty.

---

