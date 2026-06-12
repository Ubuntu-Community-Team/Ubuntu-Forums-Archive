---
title: "Help with views in VIM"
date: 2009-04-14
forum: Programming Talk
---

### Post by helino on 2009-04-14
Hi,

I need some help with views in VIM. I've just learned about code folding, and I love it. At the moment, I save all my views when I exit VIM with the current lines in my vimrc:
```

au BufWinLeave * mkview
au BufWinEnter * silent loadview

```

My problem is that I'm using GIT for my all my code, and I want to save all the view files in the repo, so I can pull the views files along with the source files. 

All the view files are stored in .vim/views, and I don't want that folder in all my repos. Instead I was thinking of a system where I save all my view files in the same folder as the source files according to the following name-standard:
```

."source-code-filename".view

```

In VIM, you can save views to a file with the function:
```

mkview "filename"

```

and you can load a specific view file with the function:
```

source "filename"

```

What I need is some kind of script that writes to the correct view file when I leave a buffer in VIM, and loads the correct view file when I load a buffer. Does anyone have any suggestions?

Thanks a lot for reading my post, I'm grateful for any help.

---

