---
title: "What's going on ??"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by Vorlander on 2008-10-07
Take a look at this screenshot from my UBUNTU 8.04.

It's using Firefox (installed from repos)

[IMG]http://img369.imageshack.us/img369/1020/screenshot6mg7.png[/IMG]

What can I do to display correctly the characters that are replaced by "?"

---

### Post by Orange_and_Green on 2008-10-07
Hi :)

You might want to try View->Character Encoding from the Firefox toolbar and try UTF-8.

Or play around (More Encodings) and see if you can find a charset that works for you.

Does it get better?

If that fails, please post the link (if it's OK for us to read it, of course) and I will try and find out the encoding for it.

Also, go to System->Administration->Language Support (from the Ubuntu main menu) and make sure your language has full locale support.

---

### Post by iaculallad on 2008-10-07
You could try installing the m$ core fonts:

```
sudo apt-get install msttcorefonts
```

---

### Post by Vorlander on 2008-10-07
> **Orange_and_Green said:**
> Hi :)

You might want to try View->Character Encoding from the Firefox toolbar and try UTF-8.

Or play around (More Encodings) and see if you can find a charset that works for you.

Does it get better?

If that fails, please post the link (if it's OK for us to read it, of course) and I will try and find out the encoding for it.

Also, go to System->Administration->Language Support (from the Ubuntu main menu) and make sure your language has full locale support.


Thanks dude.
That did the trick (Occidental Windows-1252) was ok, UTF-8 does not work

---

### Post by hyper_ch on 2008-10-07
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by Vorlander on 2008-10-07
> **hyper_ch said:**
> It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Ok, no prob.
I've tried to edit the title with no luck.

Next time

---

