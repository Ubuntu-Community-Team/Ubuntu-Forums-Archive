---
title: "How do I set up GTK syntax highlight in vim?"
date: 2009-07-11
forum: Programming Talk
---

### Post by mmfmarin on 2009-07-11
I'm following [this]("http://zetcode.com/tutorials/gtktutorial/") tutorial about GTK+. I want to edit the .c files in vim but I don't know how to enable the syntax highlighting for GTK+.

Here is what I've done until now:

```
sudo apt-get install vim vim-syntax-gtk vim-addon-manager exuberant-ctags
```

when I ran the command: 
```

vim-addons

```

I got:

```

editexisting                removed       removed       
gtk-syntax                  removed       removed       
justify                     removed       removed       
latex-suite                 removed       removed       
matchit                     removed       removed  

```

After I ran: **vim-addons install gtk-syntax**, the output changed to:

```

editexisting                removed       removed       
gtk-syntax                  installed     removed       
justify                     removed       removed       
latex-suite                 removed       removed       
matchit                     removed       removed  

```

Does anyone know what am I missing?

---

### Post by hugmenot on 2009-07-12
What is missing for you? Do you see color at all? I not, try :syntax on

---

### Post by mmfmarin on 2009-07-13
> **hugmenot said:**
> What is missing for you? Do you see color at all? I not, try :syntax on

I do see colors, but just for C reserved words. The GTK+ words are still the same (no colors for them at all), even after I did what you suggested. Actually, the regular syntax highlighting has been always working for me.

Thanks for your reply.

---

### Post by hugmenot on 2009-07-13
Ok. Read /usr/share/doc/vim-syntax-gtk/README.Debian

---

### Post by mmfmarin on 2009-07-13
Thanks, it's working now.

After I read the file you indicated. Here is what I did:

```
cp /usr/share/doc/vim-syntax-gtk/examples/c.vim /home/user/.vim/syntax/c.vim
```

Thanks again. **SOLVED**

---

### Post by JordyD on 2009-07-13
> **mmfmarin said:**
> Thanks, it's working now.

After I read the file you indicated. Here is what I did:

```
cp /usr/share/doc/vim-syntax-gtk/examples/c.vim /home/user/.vim/syntax/c.vim
```

Thanks again. **SOLVED**

You should edit your OP's title so that it says [SOLVED] at the beginning.

---

