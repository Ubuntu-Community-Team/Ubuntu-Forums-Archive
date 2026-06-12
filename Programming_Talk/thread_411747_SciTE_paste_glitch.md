---
title: "SciTE paste glitch"
date: 2007-04-17
forum: Programming Talk
---

### Post by izak on 2007-04-17
Hi All

I'm using scite as an editor, but I've come across a glitch when attempting to copy and paste content.

Specifically I want to copy code from a pdf inside Evince pdf viewer. I can select the text and centre click copy it into other editors. I can also do Edit>Copy  from Evince and then paste into other editors. However when I select paste in scite nothing happens.

What's strange is that if I  reselect the code in gedit and copy it, I can paste into scite without a problem. 

Any thoughts?

---

### Post by johnnymac on 2007-04-17
I get the same issue....I don't understand it and SciTE is my preferred code editor...

---

### Post by Brucevdk on 2007-04-17
Looks like this is encoding related, most likely you're trying to paste UTF-8 encoded text into SciTE (which using the default settings isn't set to UTF-8).

Add the following to your .SciTEUser.properties file to make it use UTF-8 (this is also described in the [SciTE documentation]("http://scintilla.sourceforge.net/SciTEDoc.html")): 

```

code.page=65001

```

It should now be possible to copy and paste UTF-8 encoded text into SciTE (from evince for example). I have also attached my personal SciTE configuration for those interested.

---

### Post by izak on 2007-04-18
Thanks a lot, that worked great. It does not help that it's in the documentation if you do not know what to look for :) . I searched for "paste" but obviously did not find anythong useful.

That config file is nifty, I've started using it. I like the monofont use right though. Just added some code I got here ( [http://ubuntuforums.org/showthread.php?t=333248](http://ubuntuforums.org/showthread.php?t=333248) ) to make the default open dialog filter be "All files*".

---

