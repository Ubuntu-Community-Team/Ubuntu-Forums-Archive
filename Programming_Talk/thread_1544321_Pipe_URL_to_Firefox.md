---
title: "Pipe URL to Firefox"
date: 2010-08-02
forum: Programming Talk
---

### Post by navneeth on 2010-08-02
Hi. 

The command

```
firefox <URL>
```

opens URL in new instance of the browser or opens it up in a new tab (if Fx is already running).

However, when I try to pipe the URL to Firefox, only a new empty window opens (even if another instance is running).


Here's how the situation originally came up: being the lazy keyboarder that I am, I grep'ed the URL from a package description in the terminal and tried piping it to Firefox. 

Why doesn't this work? And is there a way around this? (No wise-guy answers about copying and pasting the URL in the address bar, please. ;))

---

### Post by StephenF on 2010-08-02
```

$ firefox `grep http:// data`

```
Where data is a file containing URLs and other junk.

---

### Post by ju2wheels on 2010-08-02
Its expecting it as a command line parameter, not reading it from STDIN, so piping wont work.

Heres one of many ways:
```

firefox "$(grep http /some/file/with/url.txt)"

```

---

### Post by navneeth on 2010-08-02
Thanks for the replies, guys. Using a text file isn't exactly what I was looking for. 

More like:
```
apt-cache show <packagename> | grep -o http://.*
```
gets me the application's homepage. Now, how can I feed this to Firefox?

---

### Post by navneeth on 2010-08-02
Or I could use your method if I knew where the package descriptions are stored. :)

---

### Post by ju2wheels on 2010-08-02
Substitute the command you are using into whichever of the two above examples you choose to use, for example:

```

firefox "$(apt-cache show <packagename> | grep -o http://.*)"

```

or if you are using a bash script, store the result in a variable then use the variable:

```

pkgURL=`$(apt-cache show <packagename> | grep -o http://.*`;
firefox "${pkgURL}";

```

---

### Post by navneeth on 2010-08-02
> **ju2wheels said:**
> Substitute the command you are using into whichever of the two above examples you choose to use, for example:

```

firefox "$(apt-cache show <packagename> | grep -o http://.*)"

```

or if you are using a bash script, store the result in a variable then use the variable:

```

pkgURL=`$(apt-cache show <packagename> | grep -o http://.*`;
firefox "${pkgURL}";

```

Oh, I missed the parentheses while trying it out earlier. Thank you. :)

---

### Post by alphaniner on 2010-08-02
You can use xargs:

```
apt-cache show <packagename> | grep -o http://.* | xargs firefox
```

---

### Post by navneeth on 2010-08-02
> **alphaniner said:**
> You can use xargs:

```
apt-cache show <packagename> | grep -o http://.* | xargs firefox
```


Wonderful! Thanks a lot.

---

