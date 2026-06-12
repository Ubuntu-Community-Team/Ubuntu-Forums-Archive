---
title: "Scripting"
date: 2006-11-04
forum: Programming Talk
---

### Post by docetes on 2006-11-04
hi

i was wondering if someone could point me twoards a tutorial or tell me how to :

search a text file and if it finds a particular patter write a different pattern to another file(add to it not completely rewrite)

thanks,
Dave

ps
sorry if this is the wrong forum i cudn't see a scripting forum

---

### Post by quux on 2006-11-04
Hi Dave,

there a a lot of ways how you can achieve this. 

To get an overwie, IBM Developerworks has some nice articles on text processing. For a quick intro look at [http://www-128.ibm.com/developerworks/aix/library/au-textprocess.html]("http://www-128.ibm.com/developerworks/aix/library/au-textprocess.html"). If you only plan to do some simple pattern matching + text replacement you can go for e.g. "sed" or "awk". You'll find lots of tutorials when googling around (e.g [http://www-128.ibm.com/developerworks/linux/library/l-sed1.html]("http://www-128.ibm.com/developerworks/linux/library/l-sed1.html") and following). If you need more functionality a scripting language like e.g. Perl or Python might be worth a look. For Python you could start with something like [http://www-128.ibm.com/developerworks/linux/library/l-python5.html]("http://www-128.ibm.com/developerworks/linux/library/l-python5.html").

HTH

---

### Post by darth_vector on 2006-11-05
if your scripting in BASH i would start with sed. here is a great tute: [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

---

### Post by rydow on 2006-11-05
Awk is also a powerful language featuring regexps, just as sed. For some jobs awk is better than sed, for example if you want some calculations done based on the input files. Here is one tutorial [http://stud.wsi.edu.pl/~robert/awk/](http://stud.wsi.edu.pl/~robert/awk/) but if you google on "awk tutorial" you may find others that better suits your needs. If you want a language with embedded support for regexps yuo may choose perl or python. Since I am not fluent in nether perl nor python my usual approach is to embed awk or sed into bash scripts. Hope this helps.

/Jonas

---

