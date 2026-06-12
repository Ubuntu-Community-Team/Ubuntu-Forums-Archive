---
title: "ruby poo..."
date: 2005-12-30
forum: Programming Talk
---

### Post by unionjak on 2005-12-30
hello,
Has anyone else hed major grief getting ruby to play, or is it me ?
If i type ruby -v i get all the correct v numbers, but if i type ruby nothing at all happens. The curser moves down, you input but get nothing back...what have i done wrong ?
I have followed manual installation, and syaptic`s as well but no joy....boo hoo.

---

### Post by thumper on 2005-12-30
I don't think that ruby has an interactive interpreter like python.

Try making a script with ```
#! /usr/bin/env ruby
```

---

### Post by j-a-p on 2005-12-30
You could need to try..
```
irb --simple-prompt
```

or ruby, then enter your program then press CTRL+D.

I'm just starting to look at it myself.  Looks good.  I'd like some info on which way to go for GUI app development in Ruby though.

---

### Post by mostwanted on 2005-12-30
[QUOTE=unionjak]hello,
Has anyone else hed major grief getting ruby to play, or is it me ?
If i type ruby -v i get all the correct v numbers, but if i type ruby nothing at all happens. The curser moves down, you input but get nothing back...what have i done wrong ?
I have followed manual installation, and syaptic`s as well but no joy....boo hoo.[/QUOTE]

You need to press ctrl + d to exit the interpreter and run whatever you've written. Example:

```

$ ruby
p *(1..10)

```

(press ctrl + d)

```

1
2
3
4
5
6
7
8
9
10

```

If you want something more like the Python prompt you can try out Ruby [online]("http://tryruby.hobix.com/").

And Ruby is not poo. Don't blame the program for your own lack of know-how ;)

---

### Post by aljones15 on 2006-02-09
you're looking IRB which is the interactive ruby interpreter.
ubuntu's default ruby install installs irb with the version number.
hence if you have ruby 1.8 it's irb1.8
and then it runs. same for the other version numbers I beleive.

peace,
A

---

