---
title: "Python interpreter coding?"
date: 2013-05-09
forum: Programming Talk
---

### Post by kumoshk on 2013-05-09
```
# -*- coding: utf-8 -*-
```

The above is a line of code I like to put in most of my Python scripts. This makes everything work as if it's UTF-8 without having to go through lots of coding differences and rigmarole (no typing u"á"; just "á"). Particularly in this case, I don't end up having to see and deal with sequences like this: '\xc3\xa1'

Anyway, I'm just wondering how to do the same thing from the Python interpreter. Any ideas? Is there a config setting somewhere?

I'm aware that half of the escape sequence output I'm getting is probably the terminal's fault, but I'm just wondering what the equivalent to the code I cited above is.

---

### Post by alan9800 on 2013-05-10
you might try to create a single line script containing that code and then to invoke it by setting properly the variable PYTHONSTARTUP (i.e. by assigning to it the full pathname of that script) in your .bash_profile or .profile.
If you already have a script which is invoked as above explained, then you have just to place that code at the top of that script.

---

### Post by ofnuts on 2013-05-11
> **kumoshk said:**
> ```
# -*- coding: utf-8 -*-
```

The above is a line of code I like to put in most of my Python scripts. This makes everything work as if it's UTF-8 without having to go through lots of coding differences and rigmarole (no typing u"á"; just "á"). 

Then you are mistaken.. this "pragma" only applies to the way python reads your source code, and not how it handle characters. What appears a 'à' is realyl two bytes in your source code, and if you did put that "coding" pragma you would have a two-byte character string. You get away with "à" because it fits in a single byte and it's part of the default encoding. Regular python strings contain bytes 
> **kumoshk said:**
> 

Particularly in this case, I don't end up having to see and deal with sequences like this: '\xc3\xa1'

Anyway, I'm just wondering how to do the same thing from the Python interpreter. Any ideas? Is there a config setting somewhere?

I'm aware that half of the escape sequence output I'm getting is probably the terminal's fault, but I'm just wondering what the equivalent to the code I cited above is.

If you want to "intrepret" the stream of bytes in a file as UTF-8 encoded characters, you need to use the "codecs" package. 
```

import codecs
fiile=codecs.open(filePath, 'r', encoding='utf-8')

```

---

