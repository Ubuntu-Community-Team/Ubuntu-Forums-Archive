---
title: "vim installed via software centre, but no .vim file"
date: 2012-08-12
forum: New to Ubuntu
---

### Post by joetait on 2012-08-12
Hi

I have been trying to get the latex suite working vim, and the instructions I have seen have each time said that I would need to edit files in .vim or .vimrc folders in /home, but these files do not exist.

I have tried installing vim via the software, synaptics and command line  (making a complete removal via synaptics in between each install), to see if the files would be made on any of the installs.

Given how the software centre works I assumed that accessing the folders was only for manual installs, but this does not seem to be the case.

So my question is, can I just make a .vim file, and then vim will detect it. I don't see why this should be the case, I would have thought it only looks where the config files were placed on install. Also, I am not sure what a .vimrc folder would be, how it would differ from a .vim folder etc.

Lastly, if I can make these folders, or if I can go elsewhere in the file system and use a premade file, can/should I download the tex suite and install it as a .deb file to the appropriate folder?

Thanks in advance for the help, and sorry if this is more of a vim than Ubuntu question!

---

### Post by Bashing-om on 2012-08-12
joetait:

 I have not used the latex suite ... but look at these links:

[http://insane-on-linux.blogspot.com/2009/08/vim-latex-suite-on-ubuntu-jaunty.html](http://insane-on-linux.blogspot.com/2009/08/vim-latex-suite-on-ubuntu-jaunty.html)

that advises:
First install vim-latex package using synaptic packet manager. Then run following command on a terminal :
```
sudo vim-addons -w install latex-suite
```

Now opening a tex document with gvim should show tex related menus on the menu bar.
see also this link:
[http://rafeiro.wordpress.com/2010/07/12/vim-latexsuite-on-ubuntu-10-4/](http://rafeiro.wordpress.com/2010/07/12/vim-latexsuite-on-ubuntu-10-4/)

which essentially says the same thing.

[INDENT]HTH
[/INDENT]

---

### Post by Terl on 2012-08-12
Yes, you can create your own .vimrc file in your home and vim will use it.

Some ideas here at [VIM wikia]("http://vim.wikia.com/wiki/Open_vimrc_file")

---

### Post by joetait on 2012-08-12
> **Bashing-om said:**
> joetait:

 I have not used the latex suite ... but look at these links:

[http://insane-on-linux.blogspot.com/2009/08/vim-latex-suite-on-ubuntu-jaunty.html](http://insane-on-linux.blogspot.com/2009/08/vim-latex-suite-on-ubuntu-jaunty.html)

that advises:
First install vim-latex package using synaptic packet manager. Then run following command on a terminal :
```
sudo vim-addons -w install latex-suite
```Now opening a tex document with gvim should show tex related menus on the menu bar.
see also this link:
[http://rafeiro.wordpress.com/2010/07/12/vim-latexsuite-on-ubuntu-10-4/](http://rafeiro.wordpress.com/2010/07/12/vim-latexsuite-on-ubuntu-10-4/)

which essentially says the same thing.
[INDENT]HTH
[/INDENT]


Hi, thanks for the reply. I had found that suggestion elsewhere actually, and it did help it work, but there are other things that I need to change manually, and even after running that command the files I mentioned didn't exist.

Thank you for the links though, still good to have extra info :)

---

### Post by joetait on 2012-08-12
> **Terl said:**
> Yes, you can create your own .vimrc file in your home and vim will use it.

Some ideas here at [VIM wikia]("http://vim.wikia.com/wiki/Open_vimrc_file")

Okay, that explains a lot, thanks :)

---

