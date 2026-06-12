---
title: "run without ./"
date: 2007-05-26
forum: Programming Talk
---

### Post by Eviltelm on 2007-05-26
Hello :)

Can anyone tell me how to run without using the './' because it's anoying when programming always have to use ./example :(

Thank you all ;)


EDIT: btw, when i start vim i have to use ':syn on' so i can get vim to use colours, any way to do that automatically??

---

### Post by Jojo12a on 2007-05-26
just executing one of these lines:
```
PATH=".:$PATH" #local executables take preference
PATH="$PATH:." #other executables take preference
```
before work should be enough.

---

### Post by Eviltelm on 2007-05-26
Thanks man ;)

hoping somebody can help me with the vim thing now :P

EDIT: I edited .bashrc with those lines like i do with alias and it worked hehe :)

---

### Post by chrizel on 2007-05-26
Put syn on in ~/.vimrc

---

### Post by Eviltelm on 2007-05-26
where is .vimrc???

---

### Post by Ventrue on 2007-05-26
/usr/share/vim
/etc/vim
:)

---

### Post by rjack on 2007-05-26
Be aware that having the current directory in you path is a security risk.

If you have a malicious "ls" in your current dir, it will be launched in place of /bin/ls

---

### Post by rjack on 2007-05-26
> **Ventrue said:**
> /usr/share/vim
/etc/vim
:)

or ~/.vimrc if you want to change settings for your user only.

---

### Post by Metacarpal on 2007-05-26
The "best" way to run without ./ is to put the full path.
Second to that, if it's a script or program you run on a regular basis, move it to /usr/local/bin

---

### Post by chrizel on 2007-05-26
> **Eviltelm said:**
> where is .vimrc???

I said ~/.vimrc and ~ is your home directory. The file doesn't exists, you have to create it yourself. Here you can put all things you find useful. Mine looks like this:

```

set autoindent
set modeline
set nocompatible
set showmatch
set hlsearch
set incsearch
set ignorecase
syntax on

set ts=4 et sw=4

```

---

### Post by ruy_lopez on 2007-05-27
Create a subdirectory in your home folder called "bin", there's a path already set up for that. For all your personal scripts and stuff. They should run fine without the "./" If they don't add this line to .bash_profile

export PATH=$PATH:$HOME/bin

---

### Post by samjh on 2007-05-27
> **ruy_lopez said:**
> Create a subdirectory in your home folder called "bin", there's a path already set up for that. For all your personal scripts and stuff. They should run fine without the "./" If they don't add this line to .bash_profile

export PATH=$PATH:$HOME/bin

Or alternatively specify the directory of the file that needs to be run, in place of $HOME/bin. :)




By the way ruy_lopez, interesting name.  I take it you are a fan of chess?

---

### Post by Eviltelm on 2007-05-27
Thank you all guys ;)

I used the first post tip for the path, u think its best to use the bin thing instead???
Found that vimrc, it had "syntax on, i just had to take the " :)

---

### Post by ruy_lopez on 2007-05-28
Its better to use ~/bin for your script files, than to use the current directory as a PATH, yes.

---

