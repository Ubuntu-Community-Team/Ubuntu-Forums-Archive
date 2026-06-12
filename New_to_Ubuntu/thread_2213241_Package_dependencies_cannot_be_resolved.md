---
title: "Package dependencies cannot be resolved"
date: 2014-03-25
forum: New to Ubuntu
---

### Post by DefibCT on 2014-03-25
Hello Folks

Im running the 12.04 LTS version as when I use the latest, my PC shuts down randomly.

Each time I install an app from the USC i get the error Package dependencies cannot be resolved 

Any ideas?

---

### Post by gifford on 2014-03-25
Can you provide some information on your PC?
Also, do you have synaptic package manager installed? If not, install as it will help determine and hopefully fix the dependency problems.

---

### Post by newb85 on 2014-03-25
Open a terminal and paste the following.
```
sudo apt-get -f upgrade
```

Copy the results back to this thread.

---

### Post by DefibCT on 2014-03-26
What I did was change from the ZA server to the US server and no errors. :)

---

### Post by slickymaster on 2014-03-26
Can you please do what newb85 suggested you to, and past the output of```
sudo apt-get -f upgrade
```so we can have a better idea of what might be causing it.

---

