---
title: "Shell Command Listing"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by minuxx on 2008-05-17
Hi there!

This might be a really stupid question but I'd like to know if there is somewhere out there a more or less complete listing of all ubuntu "stock" shell commands with a real short description added to every command. I do realize there are **a lot** of commands but It would be quite handy to have a way of quickly looking a specific command up especially for a absolute beginner.


[ **Disclaimer** ]
*Should this Thread be by all means completely degenerated and moronic the author cant be help responsible neither in part nor in whole.* ;)

---

### Post by amingv on 2008-05-17
Something like this:

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/) <-Very good.

---

### Post by minuxx on 2008-05-17
Oh yeah thats the good stuff!
I owe you ;).

---

### Post by kerry_s on 2008-05-17
you can also copy the commands to a text file and use a alias to show the file when you forget, i did that for a friend when he was starting out.
then in your ~/.bashrc
put something like:

alias com='less ~/file'

you might have to use "more" not sure if "less" is installed on ubuntu
to install less: sudo apt-get install less

more only scrolls down
less you can scroll up and down with the arrow keys, "q" to quit

then you would just type "com" and it will show the commands.

stick to the important commands you'll actually use to keep the list short.

---

### Post by niteshifter on 2008-05-17
Hi,

For a memory-jogger try (in a Terminal):

```
apropos <something>
```

Like "apropos copy" or "apropos compress", etc.

---

### Post by minuxx on 2008-05-17
Brilliant!
Well now we are talking! :)
Especially love that apropos command.
Thank you guys. Much appreciated !

---

### Post by hyper_ch on 2008-05-17
the pdf here contains just about everything I need on a regular base:

[http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/](http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/)

---

