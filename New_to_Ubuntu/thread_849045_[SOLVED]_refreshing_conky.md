---
title: "[SOLVED] refreshing conky"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-07-04
does anyone know how to refresh conky without restarting

---

### Post by aquavitae on 2008-07-04
What do you mean by 'refresh conky'? If you mean update the display, it does that automatically. If you mean you've changed .conkyrc and you want to see the changes, they you just need to restart conky:
```
killall conky
conky
```

---

### Post by bhadotia on 2008-07-04
What is conky? Its the first time I heard (read) about it.

---

### Post by PatrickMoore on 2008-07-04
> **bhadotia said:**
> What is conky? Its the first time I heard (read) about it.

its a system monitor

heres a screenshot of mine

---

### Post by bhadotia on 2008-07-04
Hey, great desktop! I don't know how you people make AWN look so great - No matter how much I try I always end up being unsatisfied with it.

---

### Post by bhadotia on 2008-07-04
Can you suggest any other AWN like docks in ubuntu.

---

### Post by finer recliner on 2008-07-04
similar to what aquavitae recommended, you have to kill it and start it again to see changes if you modified your .conkyrc. use the command 'pkill conky' and then start it again.

if you start conky explicitly from the terminal i think it remains a child process of the terminal in such a way that when you close the terminal window, conky will be closed too. 2 suggestions to get around this:

1) start conky as a background process:
```
conky &
```

2) press alt+f2 to bring up the "run application" dialog. type conky.

enjoy

---

### Post by akiratheoni on 2008-07-04
> **bhadotia said:**
> Can you suggest any other AWN like docks in ubuntu.

Might be a good idea to start a new thread for that but Kiba Dock and Cairo Dock come to mind. There's more though, obviously.

As for conky, I normally hit alt+f2 and then type "killall conky && conky" without the quotes. The killall conky shuts down conky and conky obviously starts it; the && means only to use the second command if the first one completed successfully.

---

### Post by WorldTripping on 2008-07-04
man conky tells you to use:

killall -SIGUSR1 conky

---

### Post by aquavitae on 2008-07-04
> **finer recliner said:**
> similar to what aquavitae recommended, you have to kill it and start it again to see changes if you modified your .conkyrc. use the command 'pkill conky' and then start it again.

if you start conky explicitly from the terminal i think it remains a child process of the terminal in such a way that when you close the terminal window, conky will be closed too. 2 suggestions to get around this:

1) start conky as a background process:
```
conky &
```

2) press alt+f2 to bring up the "run application" dialog. type conky.

enjoy

Yes, sorry, I forgot the & at the end.

---

