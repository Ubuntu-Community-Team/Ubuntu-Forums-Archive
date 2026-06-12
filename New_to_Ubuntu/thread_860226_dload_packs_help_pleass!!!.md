---
title: "dload packs help pleass!!!"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by carrarin on 2008-07-15
so i have a live cd in a comp hooked up to the internet. how do i dload build essential with synaptic while haveing the dependancies. 

i tried marking it for installation, and looking in /var/cache/apt
nothing is there
what do i do ?

---

### Post by Het Irv on 2008-07-15
If you open the terminal (Applications -> Accessories -> Terminal)  You can use ```
sudo apt-get install build-essential
```

---

### Post by carrarin on 2008-07-15
this wont be installed on the computer, th hard drive will it. Im at school,. i dont think they would appreciate someone messing up their comps

i typed in what you said, nad the comp replied

After this op, 34 mb of disk space will be used. DO you want to continue. ?

---

### Post by bhadotia on 2008-07-15
> **carrarin said:**
> this wont be installed on the computer, th hard drive will it. Im at school,. i dont think they would appreciate someone messing up their comps
Nope!

---

### Post by Het Irv on 2008-07-15
Live CD doesn't write to the Hard Drive, unless you specifically tell it to.  It doesn't even mount the Drive on boot, you have to manually mount it.

That and Synaptic is just a GUI for apt-get, its basically the same thing.

---

### Post by carrarin on 2008-07-15
will the packs be at var/cache/apt
i wanna port them to my comp at home

i looked there, and cant finds them. where did they go!!!

---

### Post by carrarin on 2008-07-15
bump

---

### Post by Het Irv on 2008-07-15
If you want to move it to another computer, try downloading the file from here:

[http://packages.ubuntu.com/hardy/build-essential](http://packages.ubuntu.com/hardy/build-essential)

Also, everyone here is volunteer, please don't bump your own thread after only 4 min.

---

### Post by damis648 on 2008-07-15
You have to continue to download it. When it warms about disk space, install it. Continue. It will just download it and save it on the ramdisk and it will be cached there. Try looking to it in the cache after installing it.

---

### Post by carrarin on 2008-07-15
bcause then i have have to dload all the dependancies, and that is tough. i was hoping that syanptic would dload all the depends without installing them


i looked in cache and i dont see my debs

---

### Post by carrarin on 2008-07-15
bumpo

---

### Post by Het Irv on 2008-07-15
Again please do not bump your own thread.  Second, You have been given answers to your questions, although some require some work.  If you need more help please post exactly what you are trying to do and why the posted responses will not work.

---

### Post by carrarin on 2008-07-15
sorry about the bump. 

i was on the live cd. i went into the terminal and typed
sudo apt-get install build-essentials 
i installed everything. great. 
where did build-essential go, and where did all the dependancies go too.

thats all im asking [-o<

---

### Post by carrarin on 2008-07-15
this was postedbefore 

"It will just download it and save it on the ramdisk and it will be cached there. Try looking to it in the cache after installing it."

Where exactly is the ramdisk. i need like a path name

---

### Post by Het Irv on 2008-07-15
/var/cache/apt/archives

It should be in there.

---

### Post by carrarin on 2008-07-15
does this just dload the dependancies before dloading the actual package

---

### Post by Het Irv on 2008-07-15
Any packages you have downloaded though apt (dependcies and all) will be in there.

---

### Post by carrarin on 2008-07-15
i marked build-essential for upgrade, then i click apply, checked off the dload packages only. hit install. it installed

looked in var/cache/apt/ found only three packages:

- cpp-4.1_4.1.2-21ubuntu1_i386.deb
- gcc-4.1-base_4.1.2-21ubuntu1_i386.deb
- gcc-4.1_4.1.2-21ubuntu1_i386.deb 

but no build essential package? so where is it. whats going on

---

### Post by Het Irv on 2008-07-15
there is no actual build-essential package, its just a dummy package that represents a few packages, those packages is what you are looking for.


DOH! Build Essential is on the Live CD, Boot to your Ubuntu Install and insert the CD, somewhere on there (in the packages folder I think) is the build Essential package.

---

