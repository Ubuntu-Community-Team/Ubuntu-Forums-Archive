---
title: "Pimping out Vim?"
date: 2007-11-22
forum: Programming Talk
---

### Post by ThinkBuntu on 2007-11-22
I'd like to use Vim more often, especially for those times when I can't use my Mac with TextMate for editing. I really like the way Vim works, and I feel comfortable using it, but I need a couple things for it to really be useful for me:

[LIST=1]
[*]Syntax highlighting (SOLVED)
[*]Code completion, especially formatting (auto-indent with CSS, etc.) - Autoindent is SOLVED
[*]Easy file transfer via FTP
[*]1 and 2 for: HTML, CSS, PHP, JavaScript, Ruby
[/LIST]

How can I do this?

Note: The methods need to be portable enough that I can do it on my Mac (Unix box, no big deal). I'd expect that these options can be done by adding some sorts of libraries along with careful editing of a user's config file.

---

### Post by LaRoza on 2007-11-22
> **ThinkBuntu said:**
> I'd like to use Vim more often, especially for those times when I can't use my Mac with TextMate for editing. I really like the way Vim works, and I feel comfortable using it, but I need a couple things for it to really be useful for me:

[LIST=1]
[*]Syntax highlighting (SOLVED)
[/LIST]


Syntax highlighting: the command "syntax on", for Ubuntu, install:
```

sudo aptitude install vim-full

```

Use an FTP client through  the command line, use ":sh" to get to the shell, type "exit" to get back to Vim.

---

### Post by stroyan on 2007-11-22
vim will actually do ftp or scp access to a remote file.  Use

vim [ftp://hostname/](ftp://hostname/)
or
vim [ftp://user@hostname/](ftp://user@hostname/)
or
vim [ftp://user@hostname/filename](ftp://user@hostname/filename)
to open a directory or file on a remote system.

Use 
:help ftp
inside vim to see more information about the feature.

---

### Post by ThinkBuntu on 2007-11-23
What about basic project management in terms of easily navigating between files?

---

### Post by Yexo on 2007-11-23
Well, from inside vim you can do : o filename (without the space between : and o) to open filename.

---

### Post by stylishpants on 2007-11-23
Create a tags file for your project (using ctags, try the exuberant-ctags package) and then you can navigate around your source files simply by putting the cursor over a function or variable name and hitting Ctrl-].

Vim's online docs for this are at :help tags, but for the initial setup you might do better to find one of the many online guides that have been written to help people start using tags in vim.  Google for 'vim ctags'.


Some other handy features:

You can go to the file whose name is under the cursor with "gf".

You can go to the local declaration of the variable under the cursor with "gd", or the global declaration (may be in other file) with gD.


You should also learn about the jump list and the tag stack.  :help is your friend for these.

The Jump list:
    :ju[mps]    # show jump list
    <C-o>       # go to prev entry in jump list
    <C-i>       # go to next entry in jump list

The Tag Stack:
    :tags       # show tag stack
    <C-t>       # go to prev entry in tag stack
    :ta[g]      # go to next entry in tag stack
    <C-]>       # go to tag under cursor


Vim is fantastic for dealing with large complicated projects.

---

