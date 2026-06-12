---
title: "synaptic error...heeelp..."
date: 2008-10-03
forum: New to Ubuntu
---

### Post by mycologyinx on 2008-10-03
: Type '“deb' is not known on line 57 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.how do i fix that?

---

### Post by nothingspecial on 2008-10-03
Post the output of ```
cat /etc/apt/sources.list
```

---

### Post by 3rdalbum on 2008-10-03
The error message is telling you that there's a problem on line 57 of your /etc/apt/sources.list. I imagine you've just added something to it - and judging by the way it's specifically complaining about:

```
"deb
```

it makes me think you've put a quotation mark before and possibly after the line that you entered.

If you manually edited the file, then go back into it:

```
gksudo gedit /etc/apt/sources.list
```

and remove the quotation marks. This file should not contain any quotation marks.

If you used Software Properties, then remove the quotation marks using the Software Properties program. (or through the command mentioned above, your choice)

---

