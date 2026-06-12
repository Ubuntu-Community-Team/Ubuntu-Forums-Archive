---
title: "vim question"
date: 2010-01-08
forum: Programming Talk
---

### Post by brandon88tube on 2010-01-08
I'm really new to vim and I'm having a hard time setting it up to look like this link. [http://winterdom.com/2008/08/molokaiforvim](http://winterdom.com/2008/08/molokaiforvim)

I liked the monokai theme that it was based off of so I thought it was cool that someone made a similar version for vim. I have the normal vim installed and not the tiny version that ubuntu starts out with. My issue is setting up my .vimrc file properly to look like that even in the console as I don't have the gui version as of right now. The person who made this colorscheme also made one that supports the terminal colors as well. So there shouldn't be an issue with me not having the gui version as of right now. I want to know if anyone could help me with setting my .vimrc up to use this.

---

### Post by Milk &amp; Toast &amp; Honey on 2010-01-08
[LIST=1]
[*]Create the molokai.vim files in your $HOME/.vim/colors directory
E.g.
```

/home/brandon/.vim/colors/molokai.vim

```
[*]Restart any running vim instance.
[*]You can load the colorscheme by typing this command inside vim:
```

:colorscheme molokai

```
[*]Or to make the "molokai" theme the default theme when restarting vim, edit the .vimrc file in your home directory, and put this line:
```

colorscheme molokai

```
[*]Good luck...
[/LIST]

---

### Post by brandon88tube on 2010-01-08
I did that, but for some reason I'm still not getting the correct colors. I'm at a loss here. Does my terminal not support this or something?

---

### Post by dwhitney67 on 2010-01-08
What version of vim are you using?  To find out, try:
```

vim -version

# OR

vi -version

```
It is quite possible that you do not have 'vim' installed on your system, but instead some substitute that Canonical (Ubuntu) thought was better suited to fit onto their wimpy CD distro.

I've attached a screen-shot of the vim packages I have on my system.  Make sure you have the same.

---

### Post by brandon88tube on 2010-01-08
```
VIM - Vi IMproved 7.2 (2008 Aug 9, compiled Sep 21 2009 11:22:49)
Garbage after option argument: "-version"
More info with: "vim -h"

```

That is the version and as far as packages go, I have all, but the gui related ones.


EDIT: I might have been reading it wrong or something, but either way I decided to go with the gui version for now and it seems to be using the correct colorscheme now.

---

