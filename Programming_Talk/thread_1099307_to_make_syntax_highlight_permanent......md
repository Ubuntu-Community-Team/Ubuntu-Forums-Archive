---
title: "to make syntax highlight permanent....."
date: 2009-03-18
forum: Programming Talk
---

### Post by abhilashm86 on 2009-03-18
i use vim editor to write programs, so i need to always type :syntax on to to get highlight on. so i just browsed ~/.vi but din't find anything to alter,
how to permanently add syntax on?

---

### Post by sujoy on 2009-03-18
add
```
syntax on
```
in the config file

---

### Post by grepgav on 2009-03-18
> **sujoy said:**
> add
```
syntax on
```
in the config file

In case you are not familiar, the config file should be .vimrc (create it if need be)

---

### Post by geirha on 2009-03-18
Either edit /etc/vim/vimrc (to change settings for all users), or copy it to ~/.vimrc then edit it. The file has comments explaining what this and that option do ...

---

### Post by abhilashm86 on 2009-03-18
> **geirha said:**
> Either edit /etc/vim/vimrc (to change settings for all users), or copy it to ~/.vimrc then edit it. The file has comments explaining what this and that option do ...

yea it just worked fine :) i was initially lost searching in vi files.........

---

### Post by ArsalHero on 2012-12-15
> **grepgav said:**
> In case you are not familiar, the config file should be .vimrc (create it if need be)
Thanks that was helpful to me as I was looking the name of the vi editor config file. ;)

---

### Post by overdrank on 2012-12-15
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

