---
title: "Environment Confusion"
date: 2009-02-23
forum: Programming Talk
---

### Post by ch0d3 on 2009-02-23
I am getting quite confused about my environment configuration, by this I mean what version of programs and libraries I am using. 

1. I have vim-tiny, vim71, and gnome-vim installed. Should I have a $VIM path set in my .bashrc?

2. Should I have a $PYTHONPATH set? I have py2.5, 2.6, and would like 3.0 available, but how do I set which one I am using?

Thanks

---

### Post by pdwerryhouse on 2009-02-23
> **ch0d3 said:**
> 
1. I have vim-tiny, vim71, and gnome-vim installed. Should I have a $VIM path set in my .bashrc?

Your best bet is to use the alternatives system to configure which version of vim you use by default:

```
update-alternatives --config vim

There are 2 alternatives which provide `vim'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/vim.tiny
*+        2    /usr/bin/vim.basic


```

---

### Post by ch0d3 on 2009-02-25
> **pdwerryhouse said:**
> Your best bet is to use the alternatives system to configure which version of vim you use by default

Awesome, thank you!

Anyone know the best way to make use of multiple python versions?

---

