---
title: "Allegro Library + Anjuta"
date: 2007-06-25
forum: Programming Talk
---

### Post by ios_base on 2007-06-25
How do I add Allegro in my Anjuta IDE in a way that will let me use "auto code completion", or "symbols look-up" or however you say it.  You know, when you start typing and it pops a little box up to show you what functions it thinks you could be referring to.  I go to "Settings>Compiler and Linker Settings>Libraries tab" and can't find it in the default options.  *sigh* if anyone even knows of an IDE I can use for allegro that will allow this feature please tell me.  I'd be happy to hear.

---

### Post by kh_naba on 2007-06-25
If you use anjuta 2.2.0 (if not I suggest upgrading to it), You can create your own system tags in Settings->Preferences->Symbol Browser. Just select the directories to scan for allegro and it will create a new entry in system symbols list. Once you enable it you will get the autocompletion for it.

---

### Post by kh_naba on 2007-06-25
Of course, it is assuming allegro doesn't use pkg-config. If it does, then an entry for it should already be there in the list system tags. Just enable it.

---

