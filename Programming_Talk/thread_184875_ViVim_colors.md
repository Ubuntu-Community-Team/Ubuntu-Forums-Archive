---
title: "Vi/Vim colors"
date: 2006-05-30
forum: Programming Talk
---

### Post by Hoffmann on 2006-05-30
How can I set colors on Vi and/or Vim editors?
All I have is just black color letters on those editors.

---

### Post by linuchsan on 2006-05-30
create a file .vimrc in you homedir, and add the line syntax enable

---

### Post by Hoffmann on 2006-05-31
[QUOTE=linuchsan]create a file .vimrc in you homedir, and add the line syntax enable[/QUOTE]
Thanks a lot! ;)

---

### Post by Zdravko on 2006-05-31
Or you can use Cream - it wraps Vim interface adding several coloring themes.

---

### Post by simplyw00x on 2006-05-31
If you put the line:
```
map <F4> :syntax enable<CR>
```
in .vimrc instead then you can turn it on manually by hitting F4 - useful to not have it on by default for some files.

---

### Post by kthuno on 2006-06-07
[QUOTE=simplyw00x]If you put the line:
```
map <F4> :syntax enable<CR>
```
in .vimrc instead then you can turn it on manually by hitting F4 - useful to not have it on by default for some files.[/QUOTE]

Great tip! Thanks

---

### Post by DirtDawg on 2006-06-07
[QUOTE=Zdravko]Or you can use Cream - it wraps Vim interface adding several coloring themes.[/QUOTE]

Cream rulez.

---

### Post by seelk on 2006-06-13
[QUOTE=kthuno]Great tip! Thanks[/QUOTE]
How can you make it a toggle?

---

### Post by simplyw00x on 2006-06-14
```
map <F4> :syntax!<CR>
```
or
```
map <F4> :invsyntax<CR>
```

---

### Post by ynef on 2006-06-15
I don't know how often you guys edit source files you **don't** want syntax highlighting for (so I don't understand the usefulness of a toggle for it) -- if you're more like me, you'll want it for certain files. Here's how to just enable it for C and C++ files:

```

autocmd Filetype c,cpp,h,hpp call ProgrammingMode()

function! ProgrammingMode()
    syntax enable
endfunction

```

You can add more useful commands in the "ProgrammingMode()" function, for instance related to folding and what ":make" should do, etc.

---

### Post by SuperTeece on 2006-09-28
First off, I appologize if I'm breaking a rule by bringing up an old thread, but I have a question.

I have followed the steps in this thread and have strange results. My .vimrc and .exrc now show colors, a few scripts that were already written show colors, but nothing new I write is showing up in color.

When I first used VIM in an older Redhat distro the syntax would automatically change to the approriate color once the syntax was complete. Are the steps in this thread what I am even looking for to duplicate this feature?

Thanks

TC

---

### Post by boban on 2006-10-03
> **SuperTeece said:**
> 
I have followed the steps in this thread and have strange results. My .vimrc and .exrc now show colors, a few scripts that were already written show colors, but nothing new I write is showing up in color.

When I first used VIM in an older Redhat distro the syntax would automatically change to the approriate color once the syntax was complete. Are the steps in this thread what I am even looking for to duplicate this feature?
TC

Have you tried saving the file and reloading it (:w :e)?

---

