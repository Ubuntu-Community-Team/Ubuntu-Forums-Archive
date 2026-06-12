---
title: "Finding Python Executable?"
date: 2012-01-08
forum: Programming Talk
---

### Post by Carpentr on 2012-01-08
Edit: Actually, it seems that I figured it out after all. The Python executable file was in /usr/bin/env. I was just looking in the wrong place! 

Thanks everyone,
Carpentr
--------------
Hey everyone,

I'm trying to set a new Python Executable in my IDE so I can use Python 3.1 instead of 2.6. I have located /usr/lib/python3.1 (if that is the correct location) but I have no idea what file to choose. I'm kind of embarrassed to be asking this but I don't have much programming experience in Linux (or directories at the moment). I've done a lot of googling and could only find helpfiles related to the Windows.

Any help would be greatly appreciated. Thank you for reading.

---

### Post by oldfred on 2012-01-08
Whatever you do, do not uninstall the 2.7 or current version of python as it is used by Ubuntu for many internal programs.

If from terminal

python3

I like to use geany (have to change editor settings from tabs to spaces) and then in each file the first line is:

#!/usr/bin/env python3

I think both python3 and python3.1 work, but use python3 so as the version of python3 gets updated, I do not have to update program. I think it has internal links from python3 to the current version of 3.

---

### Post by Carpentr on 2012-01-08
> **oldfred said:**
> Whatever you do, do not uninstall the 2.7 or current version of python as it is used by Ubuntu for many internal programs.

If from terminal

python3

I like to use geany (have to change editor settings from tabs to spaces) and then in each file the first line is:

#!/usr/bin/env python3

I think both python3 and python3.1 work, but use python3 so as the version of python3 gets updated, I do not have to update program. I think it has internal links from python3 to the current version of 3.

Thanks for the tip. My need for python 3.1 was based on a book I have which I am using to learn from. I've read that Python 3 is backwards compatible for all 3.x versions, so I will definitely keep that in mind.

Thank you very much.

---

### Post by cgroza on 2012-01-08
Get the right python path by:

```

which python3

```

---

