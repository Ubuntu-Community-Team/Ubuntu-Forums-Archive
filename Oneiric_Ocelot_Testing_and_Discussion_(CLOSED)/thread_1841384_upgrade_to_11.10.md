---
title: "upgrade to 11.10"
date: 2011-09-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by shubham1 on 2011-09-09
i wnt to upgrade to 11.10 will my software be there will there be a problem will i will get new preinstalled software will my ram support it 2gb will ubuntu one which is not working work

---

### Post by howefield on 2011-09-09
Thread moved to the development release forum "*Ubuntu +1 (Oneiric Ocelot)*"

---

### Post by 2F4U on 2011-09-09
Since 11.10 is currently in beta stage, it is likely that you will experience problems and that not all software works as you may expect.

---

### Post by shubham1 on 2011-09-10
> **2F4U said:**
> Since 11.10 is currently in beta stage, it is likely that you will experience problems and that not all software works as you may expect.
how to upgrade i have used apt-get update should i now use apt-get upgrade

---

### Post by shubham1 on 2011-09-10
after upgrading  an swicth back to 11.04

---

### Post by wgarcia on 2011-09-10
> **shubham1 said:**
> how to upgrade i have used apt-get update should i now use apt-get upgrade

This just upgrades your system to the last versions of the packages of the release installed in your system, to upgrade to a new distribution version you have to use 

```
update-manager -d
```

But as you were told in previous messages it is very likely that, being at Beta 1 stage of the new 11.10 version, you may get upgrade problems and/or breakage in packages, not advisable for "production" systems.

---

### Post by RomeReactor on 2011-09-10
> **shubham1 said:**
> after upgrading  an swicth back to 11.04

Once you upgrade to 11.10 you won't be able to revert the system to 11.04, other than a complete reinstall.

---

### Post by grahammechanical on 2011-09-10
You should create a new partition and install 11.10 beta 1 (in fact any development release) into the new partition. Then you can test out to see if you can set the system up the way you want to before upgrading your working Ubuntu.

I can tell you this:

1) In 11.10 beta 1 I have two Ubuntu One icons. I have not tried connecting to my account. But if Ubuntu One is not working for you in 11.04, then I suggest that it will not work in 11.10 beta. Find out why Ubuntu One is not working for you in 11.04. It works for me. Why is it not working for you?

2) Libreoffice Writer has a modified Find and Replace function. so, Libreoffice might be a later version than the one in 11.04.

3) The Ubuntu software Centre has a new look and gives an option to put an icon on the Launcher.

4) Many of the system settings utilities have been redesigned to be simpler.

5) A lot of the usual utilities are not yet available.

Regards.

---

### Post by shubham1 on 2011-09-10
The Ubuntu software Centre has a new look and gives an option to put an icon on the Launcher.
ubuntu software center always provide an option to put a icon on launcher

---

### Post by shubham1 on 2011-09-10
did it souits you

---

### Post by DogMatix on 2011-09-10
I have 11.10 and Ubuntu One is working fine. The only real problem I came across was the software centre is quite unstable, which is well documented in Launchpad bugs, and I had an issue with wireless because of acer-wmi. Otherwise its been pretty much O.K.

---

### Post by shubham1 on 2011-09-11
> **DogMatix said:**
> I have 11.10 and Ubuntu One is working fine. The only real problem I came across was the software centre is quite unstable, which is well documented in Launchpad bugs, and I had an issue with wireless because of acer-wmi. Otherwise its been pretty much O.K.
i dont want the one more problem of making other partion should i upgrade any serius problem.
buttt
i want to completely reinstall i want to reomove my current ubuntu it has thousands of problem and the problem is caused a the time of installation.should id onwload it from net.

---

### Post by eentonig on 2011-09-11
> **shubham1 said:**
> how to upgrade i have used apt-get update should i now use apt-get upgrade

Considering you don't know the difference between apt-get update en apt-get upgrade, I doubt if it's wise for you to upgrade to a development release which hasn't been launched yet. 


Give it another month for the final release to be launched.

---

### Post by shubham1 on 2011-09-11
> **eentonig said:**
> Considering you don't know the difference between apt-get update en apt-get upgrade, I doubt if it's wise for you to upgrade to a development release which hasn't been launched yet. 


Give it another month for the final release to be launched.
so i should wait
i want to completely reinstall i want to reomove my current ubuntu it  has thousands of problem and the problem is caused a the time of  installation.should id onwload it from net.

---

### Post by RomeReactor on 2011-09-11
> **eentonig said:**
> Considering you don't know the difference between apt-get update en apt-get upgrade, I doubt if it's wise for you to upgrade to a development release which hasn't been launched yet. 


Give it another month for the final release to be launched.

I think shubham1 understands what apt-get update and apt-get upgrade do, he was just asking if that is the way to perform the distribution upgrade; also, the correct method was explained last page.

shubham1: if you decide to upgrade bear in mind that while you have problems in 11.04, you're likely to encounter bugs in 11.10 as well.

---

### Post by shubham1 on 2011-09-11
> **RomeReactor said:**
> I think shubham1 understands what apt-get update and apt-get upgrade do, he was just asking if that is the way to perform the distribution upgrade; also, the correct method was explained last page.

shubham1: if you decide to upgrade bear in mind that while you have problems in 11.04, you're likely to encounter bugs in 11.10 as well.
i want to reomve completely 11.04 i will wait for the final to launched and remove the current and install the 11.10

---

