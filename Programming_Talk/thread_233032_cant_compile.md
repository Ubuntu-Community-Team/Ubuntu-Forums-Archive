---
title: "cant compile"
date: 2006-08-09
forum: Programming Talk
---

### Post by ubunting on 2006-08-09
I am new to linux, I downloaded a few compilers for c/C++ but i cant make any of them to work, i get the error "cant find make" is it because those are for kde only and im using gnome, or is it something else i'm missing...

thank you

---

### Post by Revert on 2006-08-09
If you apt-get install build-essential, it should pull in the compilers and everything else you need.

---

### Post by ubunting on 2006-08-09
im sorry, but i've been with linux for less than a week, what is the exact command to do that?

thank you

---

### Post by Engnome on 2006-08-09
> im sorry, but i've been with linux for less than a week, what is the exact command to do that?

> **Revert said:**
>  ...apt-get install build-essential...

asdf

---

### Post by X.Cyclop on 2006-08-09
```
sudo apt-get install build-essential
```

;)

---

### Post by Christmas on 2006-08-10
It's
```
sudo apt-get install build-essential
```
Be sure to enable the needed repositories, you can do it through Synaptic or manually editing the /etc/apt/sources.list file. Details [here](https://help.ubuntu.com/community/Repositories/Ubuntu), or [here](http://www.psychocats.net/ubuntu/sources.php) and also [here](http://monkeyblog.org/ubuntu/installing.html).

---

### Post by Engnome on 2006-08-10
Some would recommend aptitude instead.

```
sudo aptitude install build-essential
```

---

