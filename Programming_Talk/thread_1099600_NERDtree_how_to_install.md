---
title: "NERDtree how to install?"
date: 2009-03-18
forum: Programming Talk
---

### Post by abhilashm86 on 2009-03-18
i just came across nerdtree, which is used in vim to browse files, but i tried apt-get and others, please tell how to install?
i just googled and din't find how to?

---

### Post by simeon87 on 2009-03-18
It's the first hit on Google...

---

### Post by bruno9779 on 2009-03-18
Here goes the link for latest linux version

[http://linux.softpedia.com/get/Utilities/NERD-tree-36487.shtml](http://linux.softpedia.com/get/Utilities/NERD-tree-36487.shtml)

post again if you need help installing

---

### Post by abhilashm86 on 2009-03-18
> **simeon87 said:**
> It's the first hit on Google...

yea friend, but just some description i got:) i don wanna mess up time searchin them:)
i just install anything through terminal sudo-apt or sometimes synaptic:)

---

### Post by abhilashm86 on 2009-03-18
> **bruno9779 said:**
> Here goes the link for latest linux version

[http://linux.softpedia.com/get/Utilities/NERD-tree-36487.shtml](http://linux.softpedia.com/get/Utilities/NERD-tree-36487.shtml)

post again if you need help installing

hey there's nothing to make or compile, so now how to install?

---

### Post by jespdj on 2009-03-18
Did you read the instructions on that page?
> Requirements:

· Vim

INSTALLATION:

· Unzip the archive into your ~/.vim directory.
· Run :helptags.
· Go :help NERD_tree.txt for the help page.

---

### Post by abhilashm86 on 2009-03-18
thanks friends, did it easily:)

---

### Post by wvxvw on 2010-04-24
Hi, I've came to this forum as an option after google and reading  other info I could find on this subject - I cannot get this plugin to work :S
I've copied the plugin files to the proper folders, and if I run 
```
:helptags /usr/share/vim
```
The tags file is generated, however, if I try later
:NERD_tree
or any other combination with or without underscore and / or caps the command isn't accepted (Not an editor command).

Is there anything that I should change? Do I have to compile VIM with some certain options?
TIA.

EDIT: Sorry, got it working, it appears I had somehow two versions installed and was running another version (w/o the plugin)...

---

### Post by perlwonk on 2012-03-20
This is how I got it to work on 11.10:

1) download nerdtree.zip to somewhere local. 
2) sudo cp nerdtree.zip /usr/share/vim/vimfiles/.
3) sudo unzip /usr/share/vim/vimfiles/nerdtree.zip

Now, all you have to do is launch vim and issue the command:

:NERDTree

I haven't figured out how to make the help files work though.

---

### Post by lisati on 2012-03-20
Back to sleep, old thread. :D

---

