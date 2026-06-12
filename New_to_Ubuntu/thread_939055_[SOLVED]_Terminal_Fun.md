---
title: "[SOLVED] Terminal Fun"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by HellNoire on 2008-10-05
I'm just wondering if there was any way I could have Terminal provide me with a random fortune (yes, that easter egg) every time I open it.

Just for humour and chuckles, I figure it's possible. Thanks. :guitar:

---

### Post by jamesrl on 2008-10-05
edit ~/.bashrc and add the line to the bottom saying

```
fortune
```

THis assumes you have installed fortune.  
```

sudo apt-get install fortunes-mod fortunes-min
```

---

### Post by Elfy on 2008-10-05
Edit your .bashrc and add to the end ```
fortune
```

```
gedit .bashrc
```

Next time you start terminal it should ahve a fortune for you

---

### Post by HellNoire on 2008-10-05
Thanks, that did it, the bashrc edit.

Isn't fortune installed by default on Ubuntu though? I seem to be able to access it even without doing that command.
EDIT: 'that command' being the 'sudo apt-get install fortunes-mod fortunes-min'

---

### Post by Periswell on 2008-10-05
also apt-get moo is funny
-joshua

---

### Post by HellNoire on 2008-10-05
I can agree with you there, Joshua

---

### Post by jamesrl on 2008-10-05
I guess its installed by default on regular ubuntu.   I think i was remembering having to install fortunes (the larger list) which isn't installed by default (as well as fortunes-off, fortunes-spam) at some point.  Or maybe it wasn't present in an earlier ubuntu release.

---

### Post by Periswell on 2008-10-05
have you mooed today hellnoire?

---

### Post by Periswell on 2008-10-05
really you have to see this it is funny! put this in terminal and wait
> telnet towel.blinkenlights.nl
-joshua

---

### Post by HellNoire on 2008-10-05
That's alright Jamesrl, we all learn.

And Periswell, I saw that under Windows last time I used it... half a year ago. 

But let's stop bumping this since it's solved and help the others. After all, Ubuntu's philophosy is 'humanity towards people' so let us live up to it.

---

