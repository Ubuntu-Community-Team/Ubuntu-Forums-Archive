---
title: "Now Playing Script in Python - Use info from MOC (or any other audio player)"
date: 2008-07-06
forum: Programming Talk
---

### Post by trappy on 2008-07-06
Hi guys.
I've managed to hack a little bash script together that allows me to spam some now playing-data everywhere I like. Now I am trying Python, and I really like it, so I though "Hey, it wont be that hard in python".
Though I'm completely stranded right now.

Here is my bash script that works like a charm (even though I really don't love to have to use xclip):
```

#/bin/bash
mocp --info | sed -n 's/^Title:\s//p' | xclip
```

I thought that, in python, it would've looked something like this:

```
#!/usr/bin/python
import os

Music_Info = os.system("mocp --info | sed -n 's/^Title:\s//p | xclip'")
NowPlayingOutputToIRC = "B Now Playing: ", Music_Info

```

I guess that the bash commands using sed and xclip just doesn't work in a variabel like that? Also, I was wondering how the heck I would manage to get all data to the clipboard. Tried the python gtk paste functions, but, well, I don't know...

Any suggestions?

---

### Post by ghostdog74 on 2008-07-06
> **trappy said:**
> 
Any suggestions?

yes. see [here](http://docs.python.org/tut/)

---

