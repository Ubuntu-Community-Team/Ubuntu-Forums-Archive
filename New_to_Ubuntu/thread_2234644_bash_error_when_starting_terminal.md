---
title: "bash error when starting terminal"
date: 2014-07-15
forum: New to Ubuntu
---

### Post by Eleana_Martinez on 2014-07-15
I recently tried (and failed) to install the powerline plugin for vim. Now I'm getting this error everytime I open a terminal:

bash: /home/eleana/.local/lib/python2.7/site-packages/powerline/bindings/bash/../../../scripts/powerline: No such file or directory

Everything still works fine and I editted out the stuff that I added to my ~/.profile file.

---

### Post by Impavidus on 2014-07-16
It seems there is still a line referring to powerline in either your .profile or your .bashrc, or a file sourced from there.

In principle, it could also be in /etc/profile or /etc/bash.bashrc, but those are root-owned files so I guess you didn't modify them.

---

### Post by Eleana_Martinez on 2014-07-16
Is there anyway to get a clean copy of these files?

---

### Post by steeldriver on 2014-07-16
You can copy default ones from the /etc/skel directory, e.g. (assuming you want to back up the current ones - just in case)

```

cp ~/.bashrc{,.bak}

cp ~/.profile{,.bak}

cp /etc/skel/{.profile,.bashrc} ~/

```

---

### Post by Eleana_Martinez on 2014-07-16
I did all of that but the bash error is still there :-| Is there anything else I can try?

---

### Post by Habitual on 2014-07-16
you should either restart the terminal or issue a ```
source ~/.bashrc
``` in the current one.
If the message remains, try running ```
bash --no-rc
``` then try the cp from the skeleton again with
```
cp /etc/skel/{.profile,.bashrc} ~/
source ~/.bashrc
```

anytime you make a change to the bash environment file ~/.bashrc you either have to logout and back in,
or use what's called "sourcing" to pick up the changes in ~/.bashrc, or 
restart the terminal.

Any of these should do it.

---

### Post by Eleana_Martinez on 2014-07-16
I'm still getting the same error :-/ I'm thinking this situation is just hopeless now

---

### Post by Habitual on 2014-07-17
> **Eleana_Martinez said:**
>  I'm thinking this situation is just hopeless now NOT!

shows us this result of:
```
grep -i powerline /etc/skel/.bashrc ~/.vimrc ~/.bashrc
```

---

### Post by Eleana_Martinez on 2014-07-17
Here is the output of that grep command:

grep: /home/eleana/.vimrc: No such file or directory

I know there is a file called "vimrc" in /etc/vim/ and doing that grep command on it produces no output

---

### Post by Habitual on 2014-07-18
I don't know then, sorry.
powerline has be sourced "somewhere".

---

### Post by Eleana_Martinez on 2014-07-19
I found it! I found it! I found it!

It was in /etc/bash.bashrc

---

### Post by Basil_Seal on 2014-09-04
I am having the same problem installing powerline on ubuntu 14.04 by following [this guide]("http://askubuntu.com/questions/283908/how-can-i-install-and-use-powerline-plugin"). Powerline is working fine in both vim and gvim; however, when I open up terminal, the following appears

[FONT=courier new]/home/basil/.local/lib/python2.7/site-packages/powerline/bindings/zsh/powerline.zsh:198: no such file or directory: /home/basil/.local/lib/python2.7/site-packages/scripts/powerline-config
[/FONT][FONT=courier new]/home/basil/.local/lib/python2.7/site-packages/powerline/bindings/zsh/powerline.zsh:202: no such file or directory: /home/basil/.local/lib/python2.7/site-packages/scripts/powerline-config


[/FONT]

When I run 
$ [FONT=courier new]grep -i powerline /etc/skel/.bashrc ~/.vimrc ~/.bashrc ~/.profile ~/.gvimrc[/FONT]

I get the following.
[FONT=courier new]/home/basil/.vimrc:set guifont=Source\ Code\ Pro\ for\ Powerline\ Medium\ 12[/FONT]
[FONT=courier new]/home/basil/.vimrc:set rtp+=$HOME/.local/lib/python2.7/site-packages/powerline/bindings/vim/[/FONT]
[FONT=courier new]/home/basil/.bashrc:if [[ -f ~/.local/lib/python2.7/site-packages/powerline/bindings/zsh/powerline.zsh ]]; then[/FONT]
[FONT=courier new]/home/basil/.bashrc:	source ~/.local/lib/python2.7/site-packages/powerline/bindings/zsh/powerline.zsh[/FONT]
[FONT=courier new]/home/basil/.profile:# for powerline -- see [http://askubuntu.com/questions/283908/how-can-i-install-and-use-powerline-plugin](http://askubuntu.com/questions/283908/how-can-i-install-and-use-powerline-plugin)[/FONT]
[FONT=courier new]/home/basil/.gvimrc:set guifont=Source\ Code\ Pro\ for\ Powerline\ Medium\ 12[/FONT]
[FONT=courier new]/home/basil/.gvimrc:set rtp+=$HOME/.local/lib/python2.7/site-packages/powerline/bindings/vim/[/FONT]



Any ideas how to get rid of the error?

---

