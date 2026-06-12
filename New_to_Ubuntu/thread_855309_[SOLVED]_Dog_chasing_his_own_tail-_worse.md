---
title: "[SOLVED] Dog chasing his own tail- worse"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by carrarin on 2008-07-10
i have a package - g++-4.2 - that has libstdc++6-4.2 as a dependancy. but g++-4.2 is a dependancy of libstdc++6-4.2. 

Now do you understand the title of the post. :)

This probrlem makes me angry!! :mad: ](*,):twisted::evil::biggrin:
Me hulk, me SMASH!! ARCGGGGG
How do i solve this?

---

### Post by SkonesMickLoud on 2008-07-10
> **carrarin said:**
> i have a package - g++-4.2 - that has libstdc++6-4.2 as a dependancy. but g++-4.2 is a dependancy of libstdc++6-4.2. 

Now do you understand the title of the post. :)

This probrlem makes me angry!! :mad: ](*,):twisted::evil::biggrin:
Me hulk, me SMASH!! ARCGGGGG
How do i solve this?

Try:

```
sudo aptitude update && sudo aptitude install g++-4.2 libstdc++6-4.2
```

---

### Post by ET! on 2008-07-10
or download the two packages from the net(not through synaptic) and install it

---

### Post by carrarin on 2008-07-10
i got the packs from the net. i dclick on one it cant install untill the other is installed .

---

### Post by SkonesMickLoud on 2008-07-10
Aptitude and/or apt-get will download all of the needed dependencies for you.

---

### Post by carrarin on 2008-07-10
dont have the internet, geting close to dragging my comp to the library and hooking up there. untilll then what should i do.

---

### Post by carrarin on 2008-07-10
bump

---

### Post by sisco311 on 2008-07-10
copy the packages in the /var/cache/apt/archives
folder and install them with apt-get.

---

### Post by carrarin on 2008-07-10
i try that thank you

---

### Post by YaroMan86 on 2008-07-10
I could be wrong, but you could type in the following and get everything you need:

```

sudo apt-get install build-essential

```

That would install both g++ and the standard headers.

---

### Post by carrarin on 2008-07-10
dont have internet, so cant do that. thanks anyways.

---

### Post by Canis familiaris on 2008-07-10
Take them to a new folder:
Change to that foldet (using cd)

```
sudo dpkg -i --force-depends *.deb
```

```
sudo apt-get install -f
```

And the dog will stop chasing its tail. ;)


I would however recommend.
If you have the Ubuntu install CD.
Insert the CD.

```
sudo apt-cdrom add
```

```
sudo apt-get install build-essential
```

It will install all essential the packages with only requiring the CD, not internet.

---

