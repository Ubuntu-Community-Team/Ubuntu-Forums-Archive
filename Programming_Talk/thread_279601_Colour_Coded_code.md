---
title: "Colour Coded code"
date: 2006-10-18
forum: Programming Talk
---

### Post by Dimitar on 2006-10-18
Hey everyone,
Just messing around with some code when something hit me in the face: my code isnt colour coded. I use Vim as my editor and if your not sure what im talking about its when you type in int and it changes colour, or when you type in if it also changes colour, now this isnt a huge deal but it does help alot, does anyone know how i can set this up? is there a package that will do this for me?

---

### Post by amo-ej1 on 2006-10-18
in vim type:

":syntax on"

(in command mode)


and to make it permanent open /etc/vim/vimrc and search for

```

" Vim5 and later versions support syntax highlighting. Uncommenting the next
" line enables syntax highlighting by default.
"syntax on

```

And uncomment 'syntax on'

---

### Post by Anonii on 2006-10-18
I guess that you mean syntax highlighting.
I dont really know how to enable that to Vim, since I use Emacs (rarely, but when I need a full featured editor, Emacs will do it.)

But I think that this will help you:
[http://www.eecs.harvard.edu/~cduan/technical/vi/vi-4.shtml](http://www.eecs.harvard.edu/~cduan/technical/vi/vi-4.shtml)

Good luck!

---

### Post by Ramses de Norre on 2006-10-18
Vim needs to know what code your typing, if you create a new file you need to add the extension correctly (file.sh, file.java, file.c).
When you open a file without extension that has been made before it will recognize the mime type (but not on new files).

When that isn't the problem: check your ~/.vimrc and make sure there is a line ```
 syntax on
``` in there.

With these two things it should work.

---

### Post by dancavs on 2006-10-18
in vim the command

```
:syntax on
```

should do the trick

---

### Post by Dimitar on 2006-10-18
big thanks guys, works fine now. one more thing, i cant seem to run any files, it just says unrecognized command, any help?

Edit: and by run any files, i mean programs ive written.

---

### Post by amo-ej1 on 2006-10-18
have you appended the ./ before the binary name ?

```

gcc -o outFile sourcefile.c
./outFile

```

---

### Post by Dimitar on 2006-10-18
hahahah! oh man do i feel stupid. cant believe i forgot ./ thanks alot hey.

---

### Post by JonahRowley on 2006-10-22
Just a note to people using edgy.  It seems vim was split into two packages.  You have to install the vim package, I somehow had vim-minimal installed, and it doesn't do syntax highlighting at all.

---

### Post by nathanbriggs on 2007-04-25
have to apt-get install vim-full to get syntax or use synaptic package

---

