---
title: "Similarity Comparison within words (Python)"
date: 2013-09-08
forum: Programming Talk
---

### Post by xtremesupremacy3 on 2013-09-08
Hello,

I am attempting an ambitious project built around etymology within Germanic languages.
Coming from Holland I speak a germanic language and due to my obsession with the ancient past, I decided to attempt to find the words that bind all germanic languages.
The trouble is that many words have similarities but in different places.
For an example, the Dutch word for travelling is 'reizen' and the German equivalent is 'Reise' and also 'reise' in Norway. But other words have different spellings but similarities in other places.

What I want to ultimately do is type in a word or list of words, it will then look at other languages which use the same type of word and correctly display them, then later I can work at trying to come to a common root.
The trouble is letting the program correctly detect commonalities.

Does anyone have any ideas how I could accomplish this detection?
Take the travelling example.
Others can be a little more difficult. For instance, the Dutch for sailing is 'varen', which isnt similar to the German equivalent but the German for driving is 'fahren', an obvious common descendant.
My ultimate goal is to detect those.

Does anyone have any pointers?
Thanks

---

### Post by Nil_Pointer on 2013-09-08
Don't want to disappoint you, but I'm afraid this is going to be more complex than you'd like. It will need writing complex word analysers for each language and words will likely need to be accompanied with some metadata. Natural language processing never was an easy task.

Well, there is easy (but not precise) way to do similarity analysis. You can use SequenceMatcher from Python's difflib or fuzzy wuzzy library.

[http://docs.python.org/2/library/difflib.html](http://docs.python.org/2/library/difflib.html)

It will tell you how similar two strings are. Note, however, that this is not etymological analysis, it's based on calculating how much modifications to string A must be done to get string B.

---

### Post by MadCow108 on 2013-09-08
sklearn might be the best tool to tackle the problem.
its already has a lot of components centered around text similarity analysis (which, is as already said, a complicated topic, I recommend you go read some papers about the basics it before starting).

see this for an interesting tutorial on how to use it:
[http://pyevolve.sourceforge.net/wordpress/?p=1589](http://pyevolve.sourceforge.net/wordpress/?p=1589)

---

### Post by badactress2 on 2013-09-12
How about creating your database using phonetic dictionaries rather than using the actual spellings? I suspect this would be more likely to pick up similar or identical sounding words in different languages even if they're spelled differently?

A quick Google leads me to believe that there are phonetic dictionaries out there available to download.

---

