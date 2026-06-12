---
title: "Emacs: No code folding?? Seriously?!"
date: 2009-05-31
forum: Programming Talk
---

### Post by Markhor on 2009-05-31
I am user of vim for several years. After constantly having to make heavy modifications to vim to suit my needs, I decided to switch to Emacs as my primary editor.

   It's ironic that I am switching to Emacs primarily for IDE features, yet it doesn't seem to have the extremely useful code-folding feature (something which vim very elegantly provides), The only code folding mechanism I have found is selective display which essentially folds based on indentation. I'd like to fold regions of code. I ran into a hackish looking solution (fold.el). I'm wondering if anyone knows of a decent implementation of folding, preferably maintaining state across saves. Thanks.

---

### Post by soltanis on 2009-05-31
You sir, have found us the vulnerability that will win the editor wars.

---

### Post by eunikorn_the_imazinator on 2010-06-30
@soltanis 
did you really think that the editor wars could be won so easily

@Markhor
Well, I would not like to comment on the code folding facilities provided by VIM because I have never used it. 
Emacs comes with code folding facility built in ( i am using emacs 24) ... no external plugins are required to achieve basic code folding
you have to activate hs-minor-mode. Check out [http://www.emacswiki.org/emacs/HideShow](http://www.emacswiki.org/emacs/HideShow)

also it is possible to have +/- symbols next to folded/foldable chucks of code. For that you need to install hideshowviz.el 
check out : [http://www.emacswiki.org/emacs/hideshowvis.el](http://www.emacswiki.org/emacs/hideshowvis.el)

---

### Post by juancarlospaco on 2010-06-30
**Get ed**

---

### Post by diesch on 2010-06-30
I'm using [outline-minor-mode](http://www.emacswiki.org/emacs/OutlineMinorMode) for code folding. You can [extend it to get vim-like folding](http://www.emacswiki.org/emacs/OutlineMinorMode#toc8)

---

### Post by soltanis on 2010-06-30
> **eunikorn_the_imazinator said:**
> @soltanis 
did you really think that the editor wars could be won so easily


I don't even remember posting that comment, but I stick by it :P

---

