---
title: "[SOLVED] what's the difference with vim"
date: 2008-02-14
forum: Programming Talk
---

### Post by seventhc on 2008-02-14
I've been using Vim for about a month or so, and I've always just edited the vimrc to make it work the way I want for python. 
Today I decided to install vim-python, I don't really see anything different.
So my question is, if I edit the vimrc myself then I wouldn't really need vim-python? Or if I install vim-python I don't have to edit the vimrc?
Or do I do both, edit the vimrc and install vim-python?
I only just installed it, but it looks the same when opening a .py file, hence my question.
Is there a difference in using it, or any benefit, or is it more of a preference thing and doesn't matter if you use it or not as long as the vimrc is correctly set up.???
Thanks
I don't think it's been asked before if it has I haven't come across it anywhere.

---

### Post by Fixman on 2008-02-14
Editing vimrc and installing vim-python are the same.

---

### Post by seventhc on 2008-02-14
OK, thanks for the reply. I thought it was since I saw no difference, but wanted to know for sure. 
Thanks again.:)

---

### Post by stroyan on 2008-02-14
vim-python is not about adding python syntax highlight when editing .py files.
It is about having python available as a macro language for extending vim with macros.
You can read about it with ':help python' inside vim.
There is a short presentation on it at [http://www.tummy.com/Community/Presentations/vimpython-20070225/vim.html](http://www.tummy.com/Community/Presentations/vimpython-20070225/vim.html)

The vim-full package includes the same python support as vim-python, along with Perl, Ruby, and TCL scripting.

---

### Post by seventhc on 2008-02-14
I always install vim-full so I guess I don't need to install vim-python then.
Thanks for the info. :)

---

### Post by Geekkit on 2008-02-14
> **seventhc said:**
> I always install vim-full so I guess I don't need to install vim-python then.
Thanks for the info. :)

Or if you have Vim you don't need anything else period ... right LaRoza? ;)

---

### Post by LaRoza on 2008-02-14
> **Geekkit said:**
> Or if you have Vim you don't need anything else period ... right LaRoza? ;)

No, you need an operating system. (Unlike Emacs, where you need an editor)

---

### Post by Geekkit on 2008-02-14
> **LaRoza said:**
> No, you need an operating system. (Unlike Emacs, where you need an editor)

:lolflag:   I was wondering how long that would take.

---

### Post by LaRoza on 2008-02-14
> **Geekkit said:**
> :lolflag:   I was wondering how long that would take.

A soon as I read it :-)

---

### Post by seventhc on 2008-02-14
> **LaRoza said:**
> No, you need an operating system. (Unlike Emacs, where you need an editor)
:lolflag: That was great :guitar:

---

### Post by Zwack on 2008-02-14
I remember hearing that the reason that Hurd was taking so long was that Stallman was having trouble working out how to run it under Emacs.

Of course this was back in the 1980's...

Z.

---

### Post by Geekkit on 2008-02-14
> **Zwack said:**
> I remember hearing that the reason that Hurd was taking so long was that Stallman was having trouble working out how to run it under Emacs.

Of course this was back in the 1980's...

Z.

Pfft. :)  And thus the war continues.

---

### Post by LaRoza on 2008-02-14
> **Geekkit said:**
> Pfft. :)  And thus the war continues.

Zealot

---

### Post by Geekkit on 2008-02-14
> **LaRoza said:**
> Zealot

Only on the weekends. ;)

---

### Post by Zwack on 2008-02-14
It's not a weekend...

And I used emacs for a while... (it was about the only thing that allowed me to easily do what I wanted to... I was working with EGS4 code in Mortran (an extended Fortran) using a Volker-Craig VC4404 terminal attached to a Convex C220).

Z.

---

### Post by Geekkit on 2008-02-14
> **Zwack said:**
> It's not a weekend...

And I used emacs for a while... (it was about the only thing that allowed me to easily do what I wanted to... I was working with EGS4 code in Mortran (an extended Fortran) using a Volker-Craig VC4404 terminal attached to a Convex C220).

Z.

Absolutely. And when confronted with the choice of using emacs and vi I choose emacs every time. When confronted with the choice of eating broken glass and vi ... I have to think on that, but eventually I'll always choose the lesser of the two evils: eating broken glass.

I was teasing LaRoza because (a day or two ago) he managed to pull out of me the choice. Nowadays I use Geany. :P

EDIT: FORTRAN/MORTRAN, dumb terminal? You realize of course you just horribly dated yourself right?

---

### Post by Zwack on 2008-02-14
I think I made myself sound as old in another thread when I said that I used emacs about 20 years ago, and stopped... about 19 years ago...

I'm one of those "been doing it for a long time" Unix SA types now, but I started out doing radiation simulations at a research establishment in the 80s...  Pulling EBCDIC source code off of an 800 foot tape reel onto the Convex was my first introduction to using Unix... 

Convex C220 ... $2,000,000
800' tape ... $80
Learning the intricacies of character set conversion in dd on your first day using Unix... PRICELESS.   :D
 
Z.

---

### Post by Geekkit on 2008-02-14
> **Zwack said:**
> 
Convex C220 ... $2,000,000
800' tape ... $80
Learning the intricacies of character set conversion in dd on your first day using Unix... PRICELESS.   :D
Z.

:lolflag: No doubt!

My experience only goes back to the mid 80's when I was in high school and programming on a VIC 20, PEEK and POKE statements and all that. I have fond memories of attempting to recreate Joust on the VIC 20 but quickly running out of memory.

---

