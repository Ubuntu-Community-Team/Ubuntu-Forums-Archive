---
title: "Emacs Configuration"
date: 2008-09-09
forum: Programming Talk
---

### Post by HexJunkie on 2008-09-09
I installed the 'emacs' package from Synaptic, but I do not have a .emacs file in my home directory

Should I just create it? Is there something I need to do to get it to be loaded by emacs? Is the configuration file somewhere else?

Thanks

---

### Post by ad_267 on 2008-09-09
Don't you mean vim and your .vimrc file? :)

But yeah, if you create one it should be loaded automatically. It should be at ~/.emacs

---

### Post by dribeas on 2008-09-10
Now that someone asked...

Do any of you know how to configure emacs so that indentation is done with tabs instead of spaces in the file while at the same time it is presented as a 4 spaces space in the screen for editing?

I found a couple of configs that promised to do that but did not fulfill the promise.

---

### Post by nvteighen on 2008-09-10
> **dribeas said:**
> Now that someone asked...

Do any of you know how to configure emacs so that indentation is done with tabs instead of spaces in the file while at the same time it is presented as a 4 spaces space in the screen for editing?

I found a couple of configs that promised to do that but did not fulfill the promise.

I also ran into the same issue when adopting Emacs. Here's what did the job for me:

```

M-x indent-tabs-mode nil

```

Which basically gets rid of <TAB>'s ability to insert \t for the session.

If you want that permanently:
```

M-x customize-group indent

```

And set "Indent tabs mode" to off (nil). 

Of course, you can just add (indent-tabs-mode nil) to your ~/.emacs file :)

But, in GNU Makefile mode, you'll still get tabs when indenting, so you get the Makefiles working.

---

### Post by dribeas on 2008-09-10
> **nvteighen said:**
> But, in GNU Makefile mode, you'll still get tabs when indenting, so you get the Makefiles working.

I guess I did not express myself properly. I want TAB characters in the file (same as Makefile) as that is my employers coding-style rule. And I want them to be represented on screen by 4 spaces, but once the file is written I need tabs. Any answer here?

---

### Post by nvteighen on 2008-09-10
> **dribeas said:**
> I guess I did not express myself properly. I want TAB characters in the file (same as Makefile) as that is my employers coding-style rule. And I want them to be represented on screen by 4 spaces, but once the file is written I need tabs. Any answer here?

Then do exactly what I told you before, but set indent-tabs-mode to **non-nil** (which is the default, btw... but you should check) and standard-indent to 4.

You can find those settings at M-x customize-group indent.

---

