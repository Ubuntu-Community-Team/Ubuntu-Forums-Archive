---
title: "Emacs Colors?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Syndacate on 2008-04-28
Hey,

This may be a trivial question, but in the solaris labs in my school, it has syntax highlighting text on a black background.  Now usually I use eclipse for my java, but sometimes I use emacs to edit some things quickly.

Though when I opened emacs on Ubuntu it has the java syntax highlighting, but it's on a white background.  Anybody know how to "invert" the colors?  I checked the options, but to no avail.

---

### Post by Cypher on 2008-04-28
If you're using XEmacs then you can put the following in your ~/.init/.xemacs/init.el file
```

(set-face-background 'default "bisque")          ; frame background
(set-face-foreground 'default "black")           ; normal text

```

---

### Post by Syndacate on 2008-05-02
> **Cypher said:**
> If you're using XEmacs then you can put the following in your ~/.init/.xemacs/init.el file
```

(set-face-background 'default "bisque")          ; frame background
(set-face-foreground 'default "black")           ; normal text

```

No, I'm using the Ubuntu default, I'm using Emacs 22.1.1.

So I installed xemacs through the package manager, and it runs, but the location you gave me doesn't exist. (*home/<user>/.init*)

---

### Post by unutbu on 2008-05-02
You can make a file called ~/.emacs.
Put inside:

```
(set-foreground-color "bisque")
(set-background-color "black")
```

This file is automatically read by emacs upon startup.

---

### Post by Syndacate on 2008-05-02
> **unutbu said:**
> You can make a file called ~/.emacs.
Put inside:

```
(set-foreground-color "bisque")
(set-background-color "black")
```

This file is automatically read by emacs upon startup.

That did it, thanks man.

EDIT:
I can't find the "mark thread as solved" button - any help here?  It used to be under thread tools but now ... *shrugs* ?

---

