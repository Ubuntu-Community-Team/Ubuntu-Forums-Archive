---
title: "vim"
date: 2008-05-10
forum: Programming Talk
---

### Post by thefestival on 2008-05-10
I'm using vim to do some programming in C and i've been trying to configure vim so that it uses colors and C syntax (or something like this).  I've found some websites that have sample .vimrc config files and I copy them to my .vimrc in my home directory but none of the colors ever work.  Am I missing something? Do i have to set something for vim to show colors? 

I realize this isn't a programming question but I don't know where else to go with it.

PS: I've upgraded my vim to the latest

---

### Post by LaRoza on 2008-05-10
> **thefestival said:**
> I'm using vim to do some programming in C and i've been trying to configure vim so that it uses colors and C syntax (or something like this).  I've found some websites that have sample .vimrc config files and I copy them to my .vimrc in my home directory but none of the colors ever work.  Am I missing something? Do i have to set something for vim to show colors? 

I realize this isn't a programming question but I don't know where else to go with it.

PS: I've upgraded my vim to the latest

```

sudo aptitude install vim

```

Ubuntu has vim-tiny which doesn't have a lot of features.

---

### Post by thefestival on 2008-05-10
It turns out that I allready had that.  Any other suggestions?

---

### Post by LaRoza on 2008-05-10
> **thefestival said:**
> It turns out that I allready had that.  Any other suggestions?

What is your .vimrc?

---

### Post by kerry_s on 2008-05-10
type> vi .vimrc
press> i
put> syntax on
press> :wq

you should now have colors.

---

### Post by thefestival on 2008-05-10
Thank you, that worked :)

---

