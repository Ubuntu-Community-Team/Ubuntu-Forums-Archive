---
title: "[SOLVED] Python string formatting question"
date: 2008-06-06
forum: Programming Talk
---

### Post by dbbolton on 2008-06-06
Let's say I have this string of text:

```

include "/home/daniel/.themes/NAME/gtk-2.0/gtkrc"

```

Is there a way to make python just print "NAME"? Perhaps by deleting the first 30 characters and the last 14 characters?

---

### Post by kragen on 2008-06-06
There are a number of ways you could approach this...
 
Firstly, you can access strings like you would lists, so if you wanted the 8th characters of a string, you can simply do this:

```

>>> myString = "/home/daniel/.themes/NAME/gtk-2.0/gtkrc"
>>> myString[8]
'n'

```

So, if you wanted the 22nd to the 26th characters only, I believe this would do it:

```

>>> myString = "/home/daniel/.themes/NAME/gtk-2.0/gtkrc"
>>> myString[21:25]
'NAME'

```

Look here for more info on what you can do with lists:
[http://www.diveintopython.org/native_data_types/lists.html](http://www.diveintopython.org/native_data_types/lists.html)

The other way to approach this would to use some of the methods found on strings. There is some documentation here:

[http://docs.python.org/lib/string-methods.html](http://docs.python.org/lib/string-methods.html)

But the one that strikes me as most useful to you is split, which splits the string by the string that you give it, returning a list of all the different parts, so in your case:

```

>>> myString = "/home/daniel/.themes/NAME/gtk-2.0/gtkrc"
>>> myString.split("/")
['', 'home', 'daniel', '.themes', 'NAME', 'gtk-2.0', 'gtkrc']
>>> myString.split("/")[4]
'NAME'

```

Finally, you could probably use regular expressions to solve this:

[http://docs.python.org/lib/module-re.html](http://docs.python.org/lib/module-re.html)
[http://www.regular-expressions.info/](http://www.regular-expressions.info/)

Using regular expressions you can do pretty much anything to your string, you just need to think really carefully about what it is you want to extract from your string.

I have to ask... What is it that your program is trying to do?

---

### Post by dbbolton on 2008-06-06
Thank you very much. 

I'm working on a script to print my GTK theme based on the aforementioned line in my .gtkrc.mine as well as the name of my wallpaper based on .fehbg but perhaps a few other things as well. My other problem is figuring out how to get the strings from these files. I posted about it here: [http://ubuntuforums.org/showthread.php?t=820319](http://ubuntuforums.org/showthread.php?t=820319)

---

### Post by pmasiar on 2008-06-06
> **kragen said:**
> 
```

>>> myString.split("/")

```


Instead of hardcoding split on "/", use os.pathdelimiter, it will abstract away platform's delimiter (\ or /)

---

### Post by kragen on 2008-06-06
> **pmasiar said:**
> Instead of hardcoding split on "/", use os.pathdelimiter, it will abstract away platform's delimiter (\ or /)

Ooh, very handy! Thanks :)

---

### Post by dbbolton on 2008-06-06
> **pmasiar said:**
> Instead of hardcoding split on "/", use os.pathdelimiter, it will abstract away platform's delimiter (\ or /)
What do you need to import to use os.pathdelimiter and what is its syntax ? I searched for it on python.org but didn't find anything.

---

### Post by geirha on 2008-06-06
He probably meant os.path.sep
```
>>> import os
>>> os.path.sep
'/'

```

---

### Post by pmasiar on 2008-06-06
> **geirha said:**
> He probably meant os.path.sep
```
>>> import os
>>> os.path.sep
'/'

```

Exactly. thanks

---

