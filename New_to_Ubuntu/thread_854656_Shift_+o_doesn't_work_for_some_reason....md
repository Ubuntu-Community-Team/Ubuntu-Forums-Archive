---
title: "Shift +o doesn't work for some reason..."
date: 2008-07-09
forum: New to Ubuntu
---

### Post by maoglone on 2008-07-09
I'm using a compaq c500 notebook and, for some reason or another, the "o" key doesn't work while I'm pushing down the shift key.  I'm a writer, and it's kind of important to have a capital o every once in a while @ the beginning of a sentence.  It seems to work when I employ capslock, though.  

I'm using Hardy, btw.  

Any ideas?  Thanks!

---

### Post by ibuclaw on 2008-07-09
Just out of curiosity, what are the keycode outputs of the characters?

```
for i in 1 2 3; do read -s -n1 ch; printf '%d\n' "'$ch"; done
```
Paste that into a terminal and press the following keys in order:

[LIST]
[*]**o**
[*]**Shift+o**
[*]**CAPSLOCK, o**
[/LIST]
and copy/paste the three lines of output in your next post.

Regards
Iain

---

### Post by maoglone on 2008-07-09
```
maoglone@maoglone-laptop:~$ for i in 1 2 3; do read -s -n1 ch; printf '%d\n' "'$ch"; done
111
79
```

When I keyed in shift+o, nothing happened.  This is really, really weird.  Never seen anything like this w/ a computer before.

---

### Post by ibuclaw on 2008-07-09
Yes, that is very interesting indeed. I've never seen that happen before.
I've just notified some members, and the may find their way here to give their answers.

Just bare with us a min.

Regards
Iain

---

### Post by maoglone on 2008-07-10
Bump-a-doodle-oo.  Still nothing with shift+o.

---

### Post by JoseCervera on 2008-09-09
Hello everybody!
I have a HP Pavilion dv6000 notebook and I have the same problem, but with the "m" key. When I press "shift + m", it doesn't appear anything on the screen.
I'll be grateful if somebody could help me.
Thanks

---

### Post by panhandle on 2008-09-09
See this recent thread:

[http://ubuntuforums.org/showthread.php?t=913639](http://ubuntuforums.org/showthread.php?t=913639)

There have been a few of these lately. Weird.

---

