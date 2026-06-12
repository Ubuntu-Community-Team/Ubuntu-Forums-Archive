---
title: "search and delete files using the folder gui"
date: 2013-01-13
forum: New to Ubuntu
---

### Post by mrphud on 2013-01-13
Hi all,

I recently did a search for several files using the gui folder search tool. I was able to find the files, but now I want to delete them. Unfortunatly, I can't!! Several have root permissions because they are for an old program. I am hesistant to use:
	
```
find ./ -type d -name "file" -delete
```

because there is no oversight to this function. That is, you better make darn sure only the files you want to delete come up in the search.

The gui seems better because all I did was type in a keyword. Plus it checks multiple folders.

Anyways, I would like to hear thoughts on the topic.

MrPhuD

---

### Post by cariboo on 2013-01-13
Have you tried pressing Alt-F2 and typing:

```
gksu nautilus
```

to open the file manager as root?

---

