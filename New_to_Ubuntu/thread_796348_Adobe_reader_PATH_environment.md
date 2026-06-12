---
title: "Adobe reader PATH environment??"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2008-05-16
I have just installed Adobe Reader8 and it seems to work fine , except , when I want to open a web page then I get " unable to open Adobe Reader check PATH environment ". Cant seem to find this in the help files . Help would be appreciated.

---

### Post by Falcorian on 2008-05-16
I think it means something (adobe reader?) is missing from your $PATH that it wants to use. The Path is a list of places the OS looks for programs to exicute.

You can check your path with:

```

echo $PATH

```

And you can add directories (dir) with:

```

PATH="${PATH}":dir

```

You can edit your .bashrc you add that line so that it always adds it to your path on start up.

However, I don't know what directory you should add... Is there more of an error message? Can you maybe load it from the terminal so it's prints more of an error:?

---

