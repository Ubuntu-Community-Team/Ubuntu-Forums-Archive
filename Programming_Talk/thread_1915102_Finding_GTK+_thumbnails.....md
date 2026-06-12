---
title: "Finding GTK+ thumbnails...."
date: 2012-01-25
forum: Programming Talk
---

### Post by ragtag on 2012-01-25
I've written a Gimp plug-in in Python, that needs to access thumbnails from ~/.thumbnails/normal. The plug-in works fine on Ubuntu and is available [here]("http://registry.gimp.org/node/25975"), but now I'm trying to port it to Windows, the code that finds the name of the thumbnail simply returns the wrong result. I'm guessing it has something to do with the backslashes, but I've tried all sorts of combinations, without much luck. Here is a little code snippet that can test it.

```

import urllib
import hashlib
bla = urllib.quote("C:\g.xcf")
hashlib.md5("file://" + bla).hexdigest()

```

The result of the hashlib.md5 command is eef9b62......something, but should have been e345adf8ffb47e9a1be0fa35aa457295, as that is the name of the thumbnail gimp saved for C:\g.xcf

I'm guessing it's something simple I'm missing, but I'm pretty stumped on this one. Any ideas?

---

