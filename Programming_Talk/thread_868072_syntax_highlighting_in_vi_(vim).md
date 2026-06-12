---
title: "syntax highlighting in vi (vim)"
date: 2008-07-23
forum: Programming Talk
---

### Post by cacycleworks on 2008-07-23
I wanted some syntax highlighting, as my brain uses it to quickly process php files to find certain chunks...

I saw this thread:
[http://ubuntuforums.org/showthread.php?t=626294](http://ubuntuforums.org/showthread.php?t=626294)

But the actual sequence of events required to get cli syntax highlighting:

```
sudo aptitude remove vim-tiny
sudo aptitude install vim
sudo aptitude install vim-runtime
sudo vi /etc/vim/vimrc
change:  "syntax on  to--> syntax on
```

Thank you to LaRoza for that post. :)

Chris

---

### Post by LaRoza on 2008-07-23
You don't have to do all that, just a simple "sudo aptitude install vim" will set it up. Of course, I edit my .vimrc to do the spacing and highlighting I like, but I believe syntax high lighting is done by default (or can be manually set)

---

### Post by cacycleworks on 2008-07-23
> **LaRoza said:**
> You don't have to do all that, just a simple "sudo aptitude install vim" will set it up. Of course, I edit my .vimrc to do the spacing and highlighting I like, but I believe syntax high lighting is done by default (or can be manually set)

Yeah, I tried that. It left the links from /usr/bin to /etc/alternatives/vim-tiny  :confused: 

Which is why I made the post. Also, vim-full has the gui version of vim, which I don't use, so didn't want. If I have gui, I use kate or kdevelop. My vi-foo doesn't work if the mouse is useful... that's when the shift-end type of keystrokes take over.

aptitude helped me learn that vim-runtime has the syntax highlighting.

:) 

Thanks again, though!
Chris

---

### Post by LaRoza on 2008-07-23
> **cacycleworks said:**
> 
Which is why I made the post. Also, vim-full has the gui version of vim, which I don't use, so didn't want. If I have gui, I use kate or kdevelop. My vi-foo doesn't work if the mouse is useful... that's when the shift-end type of keystrokes take over.


That was an old post of mine; I never say "vim-full" anymore :-)

---

### Post by dribeas on 2008-07-23
> **LaRoza said:**
> I edit my .vimrc to do the spacing and highlighting I like.

+1 on that one. Each so often I have to log into a coworkers to help with some c++ problems. I **really** hate it as most of them change system configurations with their preferences (including changing all highlighting colors, fg and bg colors...)

David

---

### Post by LaRoza on 2008-07-23
> **dribeas said:**
> +1 on that one. Each so often I have to log into a coworkers to help with some c++ problems. I **really** hate it as most of them change system configurations with their preferences (including changing all highlighting colors, fg and bg colors...)

David

Carry your .vimrc around with you :-)

---

### Post by dribeas on 2008-07-23
> **LaRoza said:**
> Carry your .vimrc around with you :-)

The bad part is that I use standard color scheme, my .vimrc is limited to

```

syn on
set cindent ts=4 sw=4 laststatus=2 
set winminheight=0
au VimEnter * set winheight=999

```

That last au being a work-around over a bug that vim developers don't recognize as such (even if given the patch to fix it) :P

As you see, no color definitions whatsoever

---

