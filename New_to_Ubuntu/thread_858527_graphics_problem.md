---
title: "graphics problem"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by zamadatix on 2008-07-13
i just got open city and it keeps flashing black n a pattern over the screen. as far as i know my graphics card worked and i have no driver problems in the top bar. i am able to run sim city 4 in windows and some other games, im not saying my graphics cards the best but it has always played games before. any ideas other than my graphics cards to old which i dont think it is?

---

### Post by ChameleonDave on 2008-07-13
Run the following commands in the terminal and post the output here, in order to give us an idea of your hardware.

```

sudo lshw -sanitize
cat /etc/lsb-release
uname -a

```*Please* use the "#" button in the post editor to put [noparse]```
...
```[/noparse] tags around the output to make it legible.

---

### Post by kk0sse54 on 2008-07-13
Try disabling compiz and all it's special effects by typing in the terminal ```
metacity --replace
```. In the past that has been a big problem for me when trying to run any 3-D program with compiz on.

---

### Post by ChameleonDave on 2008-07-13
You should also give us a clue as to what "open city" might mean.

You could link to its official site.

---

### Post by kk0sse54 on 2008-07-13
> **ChameleonDave said:**
> You should also give us a clue as to what "open city" might mean.

You could link to its official site.

I think that it's a RTS game in the repo's

---

### Post by ChameleonDave on 2008-07-13
> **C!oud said:**
> I think that it's a RTS game in the repo's
Ah, my mistake then, if it's in the repos.

I searched for it on the Web, but I should have guessed that the OP got the name a little wrong.  (It's OpenCity.)

I'm now installing it with *sudo apt-get install opencity* to see.

P.S. It works fine for me with Compiz, though that may be the original poster's problem.  It's a very low-graphics game.  Waiting for him to post information.

---

