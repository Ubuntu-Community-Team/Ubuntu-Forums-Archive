---
title: "Bash or php file to display contents of directories and links?"
date: 2008-08-19
forum: Programming Talk
---

### Post by firebirdworks on 2008-08-19
Most people have seen the old apache directory content page.  If you haven't, you can see one [here]("http://dsollick.howett.net/images/hosted/BungieHQ/").

I'm basically looking for something like that.  It needs to cover one directory and all others under it.  In those directories, there will be three images in every folder.  Any ideas?

Thanks.

---

### Post by meanburrito920 on 2008-08-19
If you are accessing it locally then you can just type file://FILEPATH if your are accessing it over a network you should be able to do IP/FILENAME.

---

### Post by mssever on 2008-08-20
> **firebirdworks said:**
> Most people have seen the old apache directory content page.  If you haven't, you can see one [here]("http://dsollick.howett.net/images/hosted/BungieHQ/").

I'm basically looking for something like that.  It needs to cover one directory and all others under it.  In those directories, there will be three images in every folder.  Any ideas?

Thanks.
I'm not sure if I understand you correctly, but have you used the apache configuration Options +Indexes in the appropriate directories? You might also want to fiddle with the DirectoryIndex option.

---

