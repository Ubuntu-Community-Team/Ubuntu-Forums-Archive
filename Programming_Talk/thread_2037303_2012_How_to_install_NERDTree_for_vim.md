---
title: "2012: How to install NERDTree for vim?"
date: 2012-08-04
forum: Programming Talk
---

### Post by Apathetic012 on 2012-08-04
Here's what I did

[PHP]mkdir ~/.vim
mkdir ~/.vim/bundle
cd ~/.vim/bundle
git clone https://github.com/scrooloose/nerdtree.git[/PHP]

Then I executed vim:
```
vim
//enters vim
:helptags
//Argument Required Error
:help NERD_tree.txt
//Sorry no help file for NERD_tree.txt Error
```

What am I doing wrong here?

---

### Post by raja.genupula on 2012-08-04
> install details Unzip the archive into your ~/.vim directory. 
That should put NERD_tree.vim in ~/.vim/plugin and NERD_tree.txt in ~/.vim/doc. 
Run :helptags. 

Go :help NERD_tree.txt for the help page. 

Source:[http://www.vim.org/scripts/script.php?script_id=1658](http://www.vim.org/scripts/script.php?script_id=1658)

---

