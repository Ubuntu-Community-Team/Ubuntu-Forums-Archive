---
title: "Syntax Highlighting"
date: 2007-12-03
forum: Programming Talk
---

### Post by tennvolsmb on 2007-12-03
Okay so i've read other threads on this but im still very confused... I am going to be as plain as I can be with this.. I'm looking for a Syntax Highlighter to program using C/C++... Here is what i use to start writing my scripts

```
nano -w example.cpp
```

so can anyone please tell me how i could possibly add syntax color... I know its possible because my friend put it on my computer a while back but i had to reinstall ubuntu because of a huge crash bug i had... So anyways i would appreciate your help and please take lightly.. I'm nothing more than a beginner!

---

### Post by tennvolsmb on 2007-12-03
...

---

### Post by tennvolsmb on 2007-12-03
.

---

### Post by MicahCarrick on 2007-12-03
Try this: [http://wiki.linuxhelp.net/index.php/Nano_Syntax_Highlighting]("http://wiki.linuxhelp.net/index.php/Nano_Syntax_Highlighting")

---

### Post by tennvolsmb on 2007-12-03
hmm thanks for the reply but i still don't quite understand because my nanorc sample file is not in the 

```
/usr/doc/nano-x.x.x/nanorc.sample.gz
```

or 

```
/usr/local/doc/nano-x.x.x/nanorc.sample.gz
```

---

### Post by tennvolsmb on 2007-12-03
sorry im rushing but i really need to figure this out.. it's driving me crazy

---

### Post by ThinkBuntu on 2007-12-03
Come on. Google + "I'm Feeling Lucky" = [Nano Syntax Highlighting - Linuxhelp Wiki]("http://wiki.linuxhelp.net/index.php/Nano_Syntax_Highlighting")

Simply create .nanorc:
```
$ touch ~/.nanorc
```
and edit it with your editor of choice. Try inserting this code in it: [http://wiki.linuxhelp.net/index.php/Nano_Syntax_Highlighting#Alt_C.2FC.2B.2B.2Fh](http://wiki.linuxhelp.net/index.php/Nano_Syntax_Highlighting#Alt_C.2FC.2B.2B.2Fh)

---

### Post by CptPicard on 2007-12-04
And why are you using nano as your editor for programming? It's the most basic editor ever, and thus about as bad for coding as they come... (well, vi excluded... I'm an emacs guy...)

---

### Post by tennvolsmb on 2007-12-04
Well thanks for the replys but you guys still don't have to rude with my choice of editor and sorry i couldn't find the nano syntax highlighting but thanks for putting the link

---

### Post by tennvolsmb on 2007-12-04
Sorry for the constant questions guys but im still confused... I would really like it if someone could break this down for me and be nice about it... Im tired of people hating on me because im new at programming and linux.. remember guys you were new once as well, we have all had problems

---

### Post by LaRoza on 2007-12-04
> **CptPicard said:**
> And why are you using nano as your editor for programming? It's the most basic editor ever, and thus about as bad for coding as they come... (well, vi excluded... I'm an emacs guy...)

[img]http://www.vim.org/images/vim.vialle.love.anim.gif[/img]

Vim is the best.

[http://wiki.linuxhelp.net/index.php/Nano_Syntax_Highlighting](http://wiki.linuxhelp.net/index.php/Nano_Syntax_Highlighting) It may have been given already.

The site I linked to has a complete entry for C and C++, either together or apart.

Just create the file, and follow the instructions.

@OP, I am not hating your choice of editor, the Vim line was for the Emacs user.

---

### Post by tennvolsmb on 2007-12-04
Okay thanks for your response =)

---

### Post by tennvolsmb on 2007-12-04
Okay anyways i'm doing exactly what the Wiki tells me but still no syntax coloring... and i have one more question... does Vim work anything like nano in any way?

---

### Post by LaRoza on 2007-12-04
> **tennvolsmb said:**
> Okay anyways i'm doing exactly what the Wiki tells me but still no syntax coloring... and i have one more question... does Vim work anything like nano in any way?

I don't know about nano, but Vim in very powerful.

For using it for code, install:

```

sudo aptitude install vim-full

```

The Vim wikis, [http://vim.wikia.com/wiki/Main_Page](http://vim.wikia.com/wiki/Main_Page) and [http://www.vi-improved.org/wiki/](http://www.vi-improved.org/wiki/)  

Are a good place to start. Vim may have a higher learning curve, but it is worth it. It is installed in some form on all *nixes and is worth knowing.

---

### Post by CptPicard on 2007-12-04
> **tennvolsmb said:**
>  and i have one more question... does Vim work ... in any way?

No, it doesn't. [Please don't become a vi victim]("http://www.dina.kvl.dk/~abraham/religion/"). 

(Seriously, you'd be happiest using some GUI editor I suppose, unless you absolutely must edit over ssh or something. Check out Kate on KDE and gEdit on Gnome, for starters.)

---

### Post by evymetal on 2007-12-04
vim works great, but don't start it up until you have read how to quit it!!! 

None of it's commands make sense when you first start but after a while you will see why they have been used.

---

### Post by tennvolsmb on 2007-12-04
Hmm, well thanks for the thoughts and suggestions guy's... You've been a big help

---

### Post by DDRFreak21 on 2007-12-06
Sorry you have not been having a good experience with the community so far. I'm personally excited to have you on board the Linux awesomeness!

As far as syntax highlighting goes I was just setting this up for myself.  Check out this page:[ http://wiki.linuxhelp.net/index.php/Nano_Syntax_Highlighting]("http://wiki.linuxhelp.net/index.php/Nano_Syntax_Highlighting").

All I ended up doing was
```

cd ~
nano .nanorc

```

Then copy and paste as many different pieces from the wiki as you want to use in programming.  For example if i wanted HTML sytax I would add in:
```

syntax "HTML" "\.html$"
color blue start="<" end=">"
color red "&[^; ]*;"

```

Hope it helps, happy coding!

---

### Post by bfhicks on 2007-12-06
nano is the basic of most basic text editors. For efficient programming, you have to use the one YOU feel most comfortable with. I think the only way of doing this is to learn a few.

vim, as mentioned, has a HUGE learning curve (especially if you are new to programming all together -- trying to learn this and to learn how to program could be super super tough IMO). 

I thought an easier transition was emacs. Since my current job uses emacs as it ties in with our version control software, I have started to lean a little more to it.

Probably the easiest to get started is to just use gEdit from the gnome side or something. It's super easy, has default syntax highlighting, and that's probably where I would start. Since you are new to programming, this would probably be the best bet.

---

