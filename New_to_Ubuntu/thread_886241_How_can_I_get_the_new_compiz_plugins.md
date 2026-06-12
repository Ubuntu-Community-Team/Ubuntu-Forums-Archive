---
title: "How can I get the new compiz plugins?"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by Rukaru on 2008-08-10
They aren't even that new, but I don't have them.  I have the latest Ubuntu (Hardy) and it's up to date.  I'm looking for the snow plugin and the flying windows plug in in particular. 

I also have an unrelated question here.  Is there some way to get a sort of sound machine for the computer, but with more sounds than a normal sound machine.  I'm looking for sounds (and music I suppose) that will make you feel like you're in another world.  Stuff like this helps me with my creative writing :)

EDIT: please keep in mind that I am very new to ubuntu, so I will not recognize a lot of terms.

EDIT 2: Oh and I have the settings manager and compiz all set up.

---

### Post by Locutus_of_Borg on 2008-08-10
for the latest compiz packages, you are probably going to have to compile them yourself.

you can get the source codes though git

first install git
```
sudo apt-get install git
```

also make sure you have necessary headers and such
```
sudo apt-get install linux-headers-'uname -r' build-essential
```

now get the source compile and install
```
wget http://www.xs4all.nl/~mgj1/downloads/compiz-git-newest.tar.gz
tar xzf compiz-git-newest.tar.gz
cd compiz-git
./compiz-git install
```

---

### Post by eightmillion on 2008-08-10
That first command should actually be **sudo apt-get install git-core**

---

### Post by Locutus_of_Borg on 2008-08-11
oh, i dont know what apt calls their packages these days...

---

### Post by eightmillion on 2008-08-11
Yeah, you'd expect git to be just git, but it's actually GNU interactive tools. :)

---

### Post by rocklee on 2008-08-19
When I do the installation it always prompts me for the CD which I don't have.

Is there a way to install without using the CD? (like the usual deb or package manager way).

---

### Post by LeftNut on 2008-10-15
> **Locutus_of_Borg said:**
> for the latest compiz packages, you are probably going to have to compile them yourself.

you can get the source codes though git

first install git
```
sudo apt-get install git
```

also make sure you have necessary headers and such
```
sudo apt-get install linux-headers-'uname -r' build-essential
```

now get the source compile and install
```
wget http://www.xs4all.nl/~mgj1/downloads/compiz-git-newest.tar.gz
tar xzf compiz-git-newest.tar.gz
cd compiz-git
./compiz-git install
```

Alright i followed these directions and it installed. But now when i try and goto compizconfig-settings its wont load and when i click fusion-icon it wont load either.

any help would be greatly appreciated,
Gary

---

