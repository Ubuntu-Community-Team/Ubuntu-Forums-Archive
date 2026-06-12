---
title: "declutter and speed ubuntu up"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by hazman on 2008-06-10
how do i declutter ubuntu. thing is i been playing about with all the different flavours of ubuntu [kubuntu & xubuntu] and when i got back to ubuntu i am left with alot of applications and other stuff and any way of speeding ubuntu up i.e booting up ect

---

### Post by wolfen69 on 2008-06-10
```
sudo apt-get clean
```
```
sudo apt-get autoremove
```these 2 things are basically all you can do to "clean up" ubuntu. you could also prevent apps from starting upon boot, to save memory.

---

### Post by alienexplorers on 2008-06-10
You can also try running deborphan to remove any orphaned libraries.

---

### Post by hazman on 2008-06-10
i used synaptic to download deborphan,but carn't find it to use it

---

### Post by azurepancake on 2008-06-10
Now simply open up a terminal session, type deborphan and hit enter.

It will display a list of packages that have been orphaned. Simply use..

```

sudo apt-get remove <package name>

```

..for each library you want to remove.

More information [http://www.debian-administration.org/articles/134](http://www.debian-administration.org/articles/134)

Hope this helps.

---

### Post by oldos2er on 2008-06-10
> **hazman said:**
> i used synaptic to download deborphan,but carn't find it to use it

 Type "deborphan" in a terminal.

---

### Post by bodhi.zazen on 2008-06-10
I think this link may help :

[http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

---

### Post by markbuntu on 2008-06-10
You can also use bum, the Boot Up Manager to speed up the boot process. You can stop all the stuff you don't need from being loaded at boot.

---

### Post by FakeOutdoorsman on 2008-06-10
I recommend K.Mandla's [Howto: Set up Hardy for speed]("http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/").  Another option is to get the alternate Ubuntu install disc and install a command-line only system and build up from there.  This let's you install only what you want.  You'll really see a difference in speed.  I do this for all of my Ubuntu installs.

---

### Post by Bubba64 on 2008-06-10
> **wolfen69 said:**
> ```
sudo apt-get clean
```
```
sudo apt-get autoremove
```these 2 things are basically all you can do to "clean up" ubuntu. you could also prevent apps from starting upon boot, to save memory.

These are two I use after every download except that I run 
sudo apt-get autoclean, they may be the same but I don't think so.
Powertop is also a good program for getting the cpu down

---

