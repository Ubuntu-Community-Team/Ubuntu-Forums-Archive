---
title: "vim srcipt, check for a pattern existence"
date: 2011-05-02
forum: Programming Talk
---

### Post by cybo on 2011-05-02
i'm trying to write a script which will replace a text pattern in every time i open a file and edit it.

```
function UpdateTest()
  %s/my oldpattern/new pattern/g
endfunction

```

the problem that i'm facing is whenever this function is called, if pattern in not in the file then i get an error message:
E486: Patten not found

does anybody know if there is a way to check if pattern exists before running search and replace, say something like

```
function UpdateTest()
  if /my oldpattern/
    %s/my oldpattern/new pattern/g
  endif
endfunction

```

any help is appreciated

---

### Post by gmargo on 2011-05-02
To quietly ignore a possible error, you can use the **:silent** command:
```

  silent! %s/my oldpattern/new pattern/g

```See ":help :silent" inside vim for full info.

Alternatively, you can use :silent to check for the match first. Adapted from the help:
```

  let v:errmsg = ""
  silent! /my oldpattern/
  if v:errmsg == ""
    %s/my oldpattern/new pattern/g
  endif

```

---

### Post by cybo on 2011-05-02
thanks.

---

