---
title: "Identation in Code"
date: 2007-06-17
forum: Programming Talk
---

### Post by fatsheep on 2007-06-17
What is the standard for indentation in code?  VIM and gedit are set up so they use tabs 8 spaces long.  I'm editing a python file written by another programmer who uses tabs that are 4 spaces long and the tabs are converted into spaces.  Is there any sort of standard for code indentations?

---

### Post by 5-HT on 2007-06-17
> **fatsheep said:**
> What is the standard for indentation in code?  VIM and gedit are set up so they use tabs 8 spaces long.  I'm editing a python file written by another programmer who uses tabs that are 4 spaces long and the tabs are converted into spaces.  Is there any sort of standard for code indentations?

For python: doesn't really matter as long as you're consistent, but all the books I've read  suggested using 4 spaces. Here's a relevant excerpt from my .vimrc if it helps:
```
"Indentation
set smartindent

" Tabs to 4-spaces
set shiftwidth=4
set tabstop=4
set expandtab
set smarttab
```

---

### Post by PaulFr on 2007-06-17
See the PEP (Python Enhancement Proposal) 8 at [http://www.python.org/dev/peps/pep-0008/](http://www.python.org/dev/peps/pep-0008/) for the "official" word on Python indentation :-)

---

### Post by finer recliner on 2007-06-17
no standard, however i like to use 4.

many programmers advocate to use IDE features that turn tabs into spaces. this will make sure that the code looks the same on everyone's computer. this is very helpful when multiple people will be looking/editing the code.

---

### Post by samjh on 2007-06-17
I like 4.

8 is too much, IMHO.

---

### Post by Modred on 2007-06-17
Note that if you need to override the indentation for a specific filetype, you can put the appropriate commands in a filetype config file.  For example: **~/.vim/ftplugin/python.vim**.  I use it, for example, to use the 2-space tab convention in Ruby for .rb files, while maintaining a 4-space tab in everything else.

If you want to change code you've already written to use 4-spaces instead of 8-space tab characters, which is actually a ^I unless you had expandtab turned on, then you can use the following command in VIM (will work for a simple Perl script too):
```
s/\t/    /g
```

---

### Post by pmasiar on 2007-06-17
> **fatsheep said:**
> What is the standard for indentation in code?  VIM and gedit are set up so they use tabs 8 spaces long.  I'm editing a python file written by another programmer who uses tabs that are 4 spaces long and the tabs are converted into spaces.  Is there any sort of standard for code indentations?

4 spaces, tabs-to-spaces conversion is Python standard.
(BTW Python in Google uses only 2 spaces :-) )

And make sure you don't mix tabs with spaces. 

It might be different (and more flexible) in other languages - and people have long wars about that.

---

### Post by brooksbp on 2007-06-18
Mainly preference.  BUT once you've started, it's a BITCH to switch to another indenting scheme.

I prefer tabs over spaces, tabs - 4 spaces width.  8 spaces width tabs I find the code harder to read.

---

### Post by ankursethi on 2007-06-18
I use tabs, 4 characters. No tabs-to-spaces conversion.

---

### Post by the_unforgiven on 2007-06-18
Mostly, it's matter of personal preference. Any indent style is good as long as it is consistent.
However, I guess, it would be helpful to know what all indent styles exist:
[http://en.wikipedia.org/wiki/Indent_style](http://en.wikipedia.org/wiki/Indent_style)

---

### Post by ssam on 2007-06-18
i like a tab. makes my file sizes smaller :-)

---

### Post by tr333 on 2007-06-18
you can change the indenting on a source-code file using the "indent" program.  you might need to install it with "sudo apt-get install indent indent-doc".

---

