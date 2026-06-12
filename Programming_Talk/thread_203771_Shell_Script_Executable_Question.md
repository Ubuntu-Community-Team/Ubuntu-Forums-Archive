---
title: "Shell Script Executable Question"
date: 2006-06-25
forum: Programming Talk
---

### Post by JPMaximilian on 2006-06-25
How do I make Script executable without using ./my_script?  In other words so that I only need type my_script from any folder to run scripts that are in my home folder?   I did:

sudo gedit .bash_profile 

in my home folder and added:

export PATH=$PATH:~

But when I run echo $PATH, my home folder is still not listed.  Thanks for any help ya'll might provide.

---

### Post by scxtt on 2006-06-25
put it in .bashrc ...

[indent]PATH=$PATH:~[/indent]was all i needed ... .bashrc is loaded anytime bash is invoked ...

putting:

[indent]# set PATH so it includes user's ~ (if it exists)
if [ -d ~/ ] ; then
    PATH="${PATH}":~
fi[/indent]in .bash_profile also works ...

---

### Post by JPMaximilian on 2006-06-25
Cool, that worked.  Thanks.

---

