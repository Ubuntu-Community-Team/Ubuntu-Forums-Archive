---
title: "Ubuntu Software Center stuck  &quot;in progress&quot;"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by zikuskate on 2011-12-29
Hi , pleaase I just installed ubuntu yesterday , I dont know much about it but I have a problem with the software center , it gets stuck in the beginin , it doesnt keep progressing . I am at the university , I dont if it s because of the proxy configuration  because I already configured it and I can surf the net without a problem.

---

### Post by oldos2er on 2011-12-29
Post moved to its own thread.

---

### Post by jjex22 on 2011-12-29
Hi there! welcome to the forums, sorry to hear you're having difficulties!

First, lets check out this proxy config - best way is to see if you can fetch your package lists, a really simple way to do this is open a terminal (ctrl+alt+T) and type

```

sudo apt-cache search kde

```

the "kde" part is just a search term guaranteed to generate hundreds of results. The desired effect is that it will spew out hundreds of packages and descriptions about them. If not we know the problem is most likely with the connection to the internet :)

---

### Post by cortman on 2011-12-29
Welcome to the forums!

Open a terminal by pressing Control+Alt+t and copy/paste the following code in at the prompt.

```
sudo apt-get update
```

and paste the output here to make sure the repositories are all up-to-date.

---

