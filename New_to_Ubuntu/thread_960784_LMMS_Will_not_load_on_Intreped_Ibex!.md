---
title: "LMMS Will not load on Intreped Ibex!"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by xnerdx on 2008-10-27
Okay, here is the problem! I compiled LMMS from source of 0.4.0-rc3. I compiled it in Cmake and then ran the make(install) commands. Now it is installed in full, I went into the application menu and attempted to load up the program, it shows me the little smiling music note with headphones that says LMMS, thats it. It has been sitting there for about 5 minutes now and hasn't budged :). Any idea why?

---

### Post by OutOfReach on 2008-10-27
Goto a terminal and launch lmms from there. (Hint: Type in lmms)
Check the terminal output and post back here.

---

### Post by xnerdx on 2008-10-27
Fast reply, I thank you for that, here is the output:
```
michael@michael-laptop:~$ lmms
Notice: could not set realtime priority.

```

---

### Post by OutOfReach on 2008-10-27
Odd, that has always happened to me when launching so that shouldn't be the problem.

Can you check in the System Monitor if it's taking up a lot of CPU/Mem?

---

### Post by xnerdx on 2008-10-27
Well I checked and at first it was reporting 80% CPU but then it slowly went down to 50% after about 30 seconds, the memory is at about 100MB and this all is fluctuating! I don't know it seems like I have enough CPU and memory, I would assume it to be so.

---

### Post by OutOfReach on 2008-10-27
How much memory do you have?
Did you receive any errors while compiling lmms?

Maybe you should wait until the final release of LMMS is out. It shouldn't be too long off.

---

### Post by xnerdx on 2008-10-27
No errors that I know of hmmm... I have 2 GB's of RAM :) lol. I might try to compile another version thanks for the help :)

---

### Post by OutOfReach on 2008-10-27
Well, in that case It might be a bug withing LMMS itself. I don't currently have rc3 installed but that may be the case. As I said, it might be better to wait until 4.0 final is released.

---

### Post by xnerdx on 2008-10-27
Yeah I have never used LMMS so what I did was autoremoved the package and went and got the 0.3.2 deb package :)

---

### Post by xnerdx on 2008-10-27
Yeah installed it on 0.3.2 and runs fine :)

---

### Post by neu2buntu on 2008-12-24
i would try compiling the latest version on top of 0.3.2 ,i think you had to have this already installed before upgrading to 0.4  ..... i see this is an old post y6ou may already have done this by now

---

### Post by Patrick793 on 2008-12-24
Well, this thread got bumped up but this post may be helpful for people who want LMMS on Intrepid.
Do this.

```
gksudo gedit /etc/apt/sources.list
```
Add this to the end
```
## Toby's PPA
deb http://ppa.launchpad.net/tobydox/ubuntu intrepid main
deb-src http://ppa.launchpad.net/tobydox/ubuntu intrepid main
```
Save the file, update the repositories.
```
sudo apt-get update
```
Time to install lmms.
```
sudo apt-get install lmms-common lmms lmms-extras
```

---

### Post by neu2buntu on 2009-01-01
i installed it already from source ,but your method is easier tried on another computer!!! so for newcomers to ubuntu this method is far better!!!!

---

