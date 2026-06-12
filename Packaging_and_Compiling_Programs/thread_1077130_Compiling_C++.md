---
title: "Compiling C++"
date: 2009-02-22
forum: Packaging and Compiling Programs
---

### Post by wolfman1221 on 2009-02-22
I am taking a class in unix programming and my teacher recommended that I use ubuntu to compile c++ assignments. However, I do not what to use in ubuntu or how I would go about that, so if anyone could help me I would really appreciate it. Also, I am quite the newbie at this.

---

### Post by cmay on 2009-02-22
first you need to install the build-essential package. it is
 [PHP]sudo apt-get install build-essential[/PHP]
then you compile using the g++ compiler and the teacher must have given instruktions on how to do that. 

there is a programming talk section in the forums and there is also a sticky that explains this .
good luck

---

### Post by Leo Dragonheart on 2009-02-22
I just learned how to do this a couple of days ago....Open a terminal.

Go to folder the file you want to compile is saved in. Once you are there type in these commands.

```
g++ -Wall "Filetocompile.???" -o executable

chmod u+x executable

./executable 
```

please don't ask me to explain those steps I can't but they work...good luck. Oh and yes you have to have build essentials installed first...

---

### Post by gmclachl on 2009-02-22
> **Leo Dragonheart said:**
> I just learned how to do this a couple of days ago....Open a terminal.

Go to folder the file you want to compile is saved in. Once you are there type in these commands.

```
g++ -Wall "Filetocompile.???" -o executable

chmod u+x executable

./executable 
```

please don't ask me to explain those steps I can't but they work...good luck. Oh and yes you have to have build essentials installed first...

If you are using g++ (which you will be) you can miss out

   chmod u+x executable 

You can pass various flags to the compiler. I recommend you have a look at this link. 
[http://ubuntuforums.org/showthread.php?t=689635](http://ubuntuforums.org/showthread.php?t=689635)

George

---

### Post by feelshift on 2009-02-22
Please don't open two threads on the same issue. [http://ubuntuforums.org/showthread.php?t=1077131](http://ubuntuforums.org/showthread.php?t=1077131)

---

### Post by Leo Dragonheart on 2009-02-22
> **gmclachl said:**
> If you are using g++ (which you will be) you can miss out

   chmod u+x executable 

You can pass various flags to the compiler. I recommend you have a look at this link. 
[http://ubuntuforums.org/showthread.php?t=689635](http://ubuntuforums.org/showthread.php?t=689635)

George

Lots of good tips...Thx for the link.

---

