---
title: "getting an url from Firefox and using it as variable"
date: 2008-11-07
forum: Programming Talk
---

### Post by lovinglinux on 2008-11-07
I have a bash script with an url variable that works pretty fine when I run the following command:

```
myscript http://www.foo.com
```

But I want to create a launcher that would automatically get the current url from Firefox address bar and use it as the url variable. Is this possible?

---

### Post by Darkhack on 2008-11-08
There may be a way to do it with just the standard Firefox, but I honestly couldn't tell you how to do it.

One option might be to create a Firefox extension that saves the current URL to a file and then have your script read the URL from the file.  It's not the prettiest option because it creates a browser specific implementation and if a user wants to use Opera, Epiphany, or something else, then it poses a problem.

---

### Post by lovinglinux on 2008-11-08
> **Darkhack said:**
> There may be a way to do it with just the standard Firefox, but I honestly couldn't tell you how to do it.

One option might be to create a Firefox extension that saves the current URL to a file and then have your script read the URL from the file.  It's not the prettiest option because it creates a browser specific implementation and if a user wants to use Opera, Epiphany, or something else, then it poses a problem.

Thanks for your suggestion. I have managed to get it working using the "Send link" in the context menu, after modifying the system default Mail Reader. It works, but is not the best solution.

---

