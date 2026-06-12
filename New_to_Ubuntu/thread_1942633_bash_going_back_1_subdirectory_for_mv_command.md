---
title: "bash: going back 1 subdirectory for mv command"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by mferarri on 2012-03-18
hi ubuntuforums,

if i want to move pictures from 
'home/user/pics/animals/downloaded/google_images/mammals/scary/' to 'home/user/pics/animals/downloaded/google_images/mammals/' (back 1 subdirectory)is there a shorter way to do it than: ```
mv foo.jpg home/user/pics/animals/downloaded/google_images/mammals/
```

this is an example for something similar that im doing btw.:)

---

### Post by zombifier25 on 2012-03-18
In the command line, .. stands for the parent directory, so your code could be rewritten as this:
```
mv foo.jpg ..
```

---

### Post by mferarri on 2012-03-18
> **zombifier25 said:**
> In the command line, .. stands for the parent directory, so your code could be rewritten as this:
```
mv foo.jpg ..
```

D'OH! Why didn't i think of that!!!! thanks! You're a superstar!:KS

---

