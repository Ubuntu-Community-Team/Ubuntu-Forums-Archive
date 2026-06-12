---
title: "compiling cpp files"
date: 2007-04-02
forum: Programming Talk
---

### Post by wacind on 2007-04-02
Hi 

I initially posted this in the absolute beginner talk but realized this section may be more appropriate. I apologize for that and mods may please remove the thread in the beginner section.


I am having some trouble compiling c++ files

I have used

**sudo aptitude install build-essential**, which gave me the following error:
> 
 libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20.4) but 2.4-1ubuntu12 is installed.

I have also tried **apt-get install build-essential** as well as **synaptic** both of which gave me the following error


> build-essential:
Depends: libc6-dev but it is not going to be installed or
libc-dev
Depends: g++ but it is not going to be installed
i have tried **apt-get -f install **and also the **apt-get update**

i have been searching for quite a while now but couldnt find anything to help me out
i don't know if i have problems with my repositories

thanks
wacind

---

### Post by Majorix on 2007-04-02
Install libc6 manually:

```
sudo apt-get install libc6
```

Then try installing the build-essential again.

---

### Post by wacind on 2007-04-02
thanks for the quick reply.

however that did not help, i still get the same errors and on trying g++ i get 
[B]bash: g++: command not found
[/B]

---

### Post by hod139 on 2007-04-02
Try
```
sudo aptitude install build-essential
```aptitude is smarter than apt and may be able to resolve the dependencies.

**Edit:**  Sorry, I'm an idiot and didn't see that you already tried using aptitude.

---

### Post by wacind on 2007-04-02
yep i tried that earlier and got the following dependency error
> libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20.4) but 2.4-1ubuntu12 is installed.

and I tried removing and reinstalling using Aptitude but i still can't get it working

---

### Post by hod139 on 2007-04-02
You can try downgrading  your version of libc currently installed. Using synaptic you can right-click, select properties, and select version tab.  Hopefully there will be an older version available to attempt a downgrade.

---

### Post by Rui Pais on 2007-04-02
hi,
yours it's a strange problem...
your system requires libc6 for dapper but you got libc6 for edgy. 
Seems that you have a mixed distro. Usually thats not a great problem... but with lic6 *IS*. 
You can not play around with that (you can not uninstall it without bork the system... :(

What exactly you got, dapper or edgy? If it's dapper (seems to be) do you have any edgy references on your sources.list?

---

### Post by wacind on 2007-04-02
hi 

Thanks for all your replies. i figured the problem was something to do with my repositories so i upgraded the repository list and it finally installed and everything seems to be working now

thanks again
wacind

---

