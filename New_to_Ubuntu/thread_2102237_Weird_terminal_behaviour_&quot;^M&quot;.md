---
title: "Weird terminal behaviour &quot;^M&quot;"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-01-06
In a terminal, when I type
shift-ctrl-v

The terminal seems to think I've type ^M
I get:

Presario-CQ57-Notebook-PC:~$ ^M
: command not found

---

### Post by coldcritter64 on 2013-01-06
> **Kevin McCready said:**
> In a terminal, when I type
shift-ctrl-v

The terminal seems to think I've type ^M
I get:

Presario-CQ57-Notebook-PC:~$ ^M
: command not found

Actually copy some text and use CTRL+SHIFT+V in terminal, that is the key combo to paste in terminal. You might currrently have "^M" copied into the system "clipboard".

Edit: just saw the lubuntu tag. What terminal app are you using ? I was assuming gnome-terminal above :)

---

### Post by Kevin McCready on 2013-01-06
I had text in the buffer (though I understand there is more than one buffer in linux).

My terminal is 
LXTerminal 0.1.11

---

### Post by coldcritter64 on 2013-01-06
> **Kevin McCready said:**
> ...LXTerminal 0.1.11
Unfamiliar with that terminal sorry, since you did have text in the buffer, I'd quickly check for any key mappings etc for ctrl-shift-v that may have interfered. Good luck.

---

### Post by vasa1 on 2013-01-06
> **coldcritter64 said:**
> Actually copy some text and use CTRL+SHIFT+V in terminal, that is the key combo to paste in terminal. ...
What you wrote works for me with Lubuntu's default terminal which is the same version as OP's. As you suggest, there maybe something done previously (altered keyboard shortcuts?) that conflicts.
Control+shift+v works to paste text (from elsewhere) into the nano editor as well.

---

### Post by coldcritter64 on 2013-01-06
> **vasa1 said:**
> What you wrote works for me with Lubuntu's default terminal which is the same version as OP's. As you suggest, there maybe something done previously (altered keyboard shortcuts?) that conflicts.
Control+shift+v works to paste text (from elsewhere) into the nano editor as well.
Thanks for that confirmation, yes I suspect it maybe a keyboard layout issue or a keyboard shortcut setting altered. Unfortunately I've never really checked into lubuntu, gnome/unity and xfce are my areas of most usage. Cheers.

---

