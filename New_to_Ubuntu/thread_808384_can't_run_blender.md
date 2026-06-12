---
title: "can't run blender"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by ciclopropano on 2008-05-26
If you download blender from the website you're supposed to be able to run it without doing any installation. I wasnt able to run it so I installed it by typing *apt get blender.*.. in a terminal. but now I want to install an optimized version and I have the same problem as in the beginning. how can I get it to run? I double click on the executable and nothing happens.
Im using xubuntu hardy heron at 64bits

---

### Post by xenocide13 on 2008-05-26
do you have your video card drivers up to date? it requires the openGL rendering

---

### Post by ciclopropano on 2008-05-26
I know, I can run the blender I got from synaptic. the problem is with the blender I downloaded from a website

---

### Post by xenocide13 on 2008-05-26
have you right clicked on the executable and checked the allow to be exacutable box?

---

### Post by ciclopropano on 2008-05-26
yeah, its checked

---

### Post by xenocide13 on 2008-05-26
I have no other ideas then 

sorry i couldnt help more

good luck

---

### Post by Prospero2006 on 2008-05-26
First, please post a link to the download you are using.

Second, open up a shell, cd to the directory with the executable, and 
type
```

 ./blender

```


The output it provides will help us out. 
On 64 bit arch, you may need to compile it. 
I'm about to do that myself actually. 

(Take a look at the link in my signature for my blender tutorials.)

---

### Post by Prospero2006 on 2008-05-26
Ok, here is the link I used for getting 2.46 to run on my 64 bit arch.

[http://mirror.cs.umn.edu/blender.org/release/Blender2.46/blender-2.46-linux-glibc236-py25-x86_64.tar.bz2](http://mirror.cs.umn.edu/blender.org/release/Blender2.46/blender-2.46-linux-glibc236-py25-x86_64.tar.bz2)

Once downloaded I typed 
```

bunzip2 blender-2.46-linux-glibc236-py25-x86_64.tar.bz2
tar -xvf blender-2.46-linux-glibc236-py25-x86_64.tar.bz2
cd blender-2.46-linux-glibc236-py25-x86_64.tar.bz2
./blender

```

Once again, that's the 64 bit version. 

[http://linuxclassroom.com](http://linuxclassroom.com)

---

### Post by ciclopropano on 2008-05-26
whoooa I got it now! thank you!:popcorn:

---

