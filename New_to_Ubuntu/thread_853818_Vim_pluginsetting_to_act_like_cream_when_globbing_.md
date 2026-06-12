---
title: "Vim plugin/setting to act like cream when globbing through commands. (ring switcher)"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by systemintheglitch on 2008-07-08
If you don't know what I'm talking about. You have to try it! Get cream (repositories) and say:
:colorscheme <space> <tab> <tab> <tab>

It's like it has a graphical ring switcher for globbing! FREAKING awesome!


I want to be able to do this in vim on my mac (macvim).. Which plugin lets you do this?

---

### Post by sdennie on 2008-07-08
I'm not completely sure what you mean.  You could try creating a file called ~/.vimrc and putting the following two lines in it:

```

set wildmode=full
set wildmenu

```

---

### Post by systemintheglitch on 2008-07-08
> **vor said:**
> I'm not completely sure what you mean.  You could try creating a file called ~/.vimrc and putting the following two lines in it:

```

set wildmode=full
set wildmenu

```



AWESOME! That did the trick! What are some of the other modes? Besides full?

---

### Post by sdennie on 2008-07-08
Try:

```

:help wild<tab>

```

;)

---

### Post by systemintheglitch on 2008-07-08
> **systemintheglitch said:**
> AWESOME! That did the trick! What are some of the other modes? Besides full?

Also, I'm going to ask another vim question that you might know the answer to. (on the forum)

---

