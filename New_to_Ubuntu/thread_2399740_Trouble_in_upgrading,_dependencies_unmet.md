---
title: "Trouble in upgrading, dependencies unmet??"
date: 2018-08-29
forum: New to Ubuntu
---

### Post by adityatripathi on 2018-08-29
I try sudo apt-get upgrade and get the following on my ubuntu 16.04 LTS Xenial. Please note I use a proxy server and an institute repository. Please help me out as i am new to linux.  

```
sunil@sunil-Precision-Tower-3620:~$ sudo apt-get upgrade
[sudo] password for sunil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 cpp-5 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 g++-5 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
         Depends: gcc-5 (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 gcc-5 : Depends: cpp-5 (= 5.4.0-6ubuntu1~16.04.10) but 5.4.0-6ubuntu1~16.04.4 is installed
         Depends: libcc1-0 (>= 5.4.0-6ubuntu1~16.04.10) but 5.4.0-6ubuntu1~16.04.4 is installed
         Depends: libgcc-5-dev (= 5.4.0-6ubuntu1~16.04.10) but 5.4.0-6ubuntu1~16.04.4 is installed
 gfortran-4.8 : Depends: gcc-4.8-base (= 4.8.4-2ubuntu1~14.04.4) but it is not installed
                Depends: gcc-4.8 (= 4.8.4-2ubuntu1~14.04.4) but it is not installed
                Depends: libgfortran-4.8-dev (= 4.8.4-2ubuntu1~14.04.4) but it is not installed
                Depends: libcloog-isl4 (>= 0.17) but it is not installed
                Depends: libisl10 (>= 0.10) but it is not installable
 gfortran-5 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.5) but 5.4.0-6ubuntu1~16.04.10 is installed
              Depends: gcc-5 (= 5.4.0-6ubuntu1~16.04.5) but 5.4.0-6ubuntu1~16.04.10 is installed
              Depends: libgfortran-5-dev (= 5.4.0-6ubuntu1~16.04.5) but it is not installed
 libasan2 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libatomic1 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libcc1-0 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libcilkrts5 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libgcc-5-dev : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libgomp1 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libitm1 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 liblsan0 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libmpx0 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libquadmath0 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libstdc++-5-dev : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libstdc++6 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libtsan0 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libubsan0 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
E: Unmet dependencies. Try using -f.
```

---

### Post by adityatripathi on 2018-08-29
I get the following while i try to install gfortran, please help.

```
sunil@sunil-Precision-Tower-3620:~$ sudo apt-get install gfortran
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gfortran is already the newest version (4:5.3.1-1ubuntu1).
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cpp-5 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is to be installed
 g++-5 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is to be installed
         Depends: gcc-5 (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is to be installed
 gcc-5 : Depends: cpp-5 (= 5.4.0-6ubuntu1~16.04.10) but 5.4.0-6ubuntu1~16.04.4 is to be installed
         Depends: libcc1-0 (>= 5.4.0-6ubuntu1~16.04.10) but 5.4.0-6ubuntu1~16.04.4 is to be installed
         Depends: libgcc-5-dev (= 5.4.0-6ubuntu1~16.04.10) but 5.4.0-6ubuntu1~16.04.4 is to be installed
 gfortran-4.8 : Depends: gcc-4.8-base (= 4.8.4-2ubuntu1~14.04.4) but it is not going to be installed
                Depends: gcc-4.8 (= 4.8.4-2ubuntu1~14.04.4) but it is not going to be installed
                Depends: libgfortran-4.8-dev (= 4.8.4-2ubuntu1~14.04.4) but it is not going to be installed
                Depends: libcloog-isl4 (>= 0.17) but it is not going to be installed
                Depends: libisl10 (>= 0.10) but it is not installable
 gfortran-5 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.5) but 5.4.0-6ubuntu1~16.04.10 is to be installed
              Depends: gcc-5 (= 5.4.0-6ubuntu1~16.04.5) but 5.4.0-6ubuntu1~16.04.10 is to be installed
              Depends: libgfortran-5-dev (= 5.4.0-6ubuntu1~16.04.5) but it is not going to be installed
 libasan2 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is to be installed
 libatomic1 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is to be installed
 libcc1-0 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is to be installed
 libcilkrts5 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is to be installed
 libgcc-5-dev : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is to be installed
 libgomp1 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is to be installed
 libitm1 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is to be installed
 liblsan0 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is to be installed
 libmpx0 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is to be installed
 libquadmath0 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is to be installed
 libstdc++-5-dev : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is to be installed
 libstdc++6 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is to be installed
 libtsan0 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is to be installed
 libubsan0 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

This is something similar to what we get while trying to upgrade ubuntu 

```
[sudo] password for sunil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 cpp-5 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 g++-5 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
         Depends: gcc-5 (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 gcc-5 : Depends: cpp-5 (= 5.4.0-6ubuntu1~16.04.10) but 5.4.0-6ubuntu1~16.04.4 is installed
         Depends: libcc1-0 (>= 5.4.0-6ubuntu1~16.04.10) but 5.4.0-6ubuntu1~16.04.4 is installed
         Depends: libgcc-5-dev (= 5.4.0-6ubuntu1~16.04.10) but 5.4.0-6ubuntu1~16.04.4 is installed
 gfortran-4.8 : Depends: gcc-4.8-base (= 4.8.4-2ubuntu1~14.04.4) but it is not installed
                Depends: gcc-4.8 (= 4.8.4-2ubuntu1~14.04.4) but it is not installed
                Depends: libgfortran-4.8-dev (= 4.8.4-2ubuntu1~14.04.4) but it is not installed
                Depends: libcloog-isl4 (>= 0.17) but it is not installed
                Depends: libisl10 (>= 0.10) but it is not installable
 gfortran-5 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.5) but 5.4.0-6ubuntu1~16.04.10 is installed
              Depends: gcc-5 (= 5.4.0-6ubuntu1~16.04.5) but 5.4.0-6ubuntu1~16.04.10 is installed
              Depends: libgfortran-5-dev (= 5.4.0-6ubuntu1~16.04.5) but it is not installed
 libasan2 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libatomic1 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libcc1-0 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libcilkrts5 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libgcc-5-dev : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libgomp1 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libitm1 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 liblsan0 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libmpx0 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libquadmath0 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libstdc++-5-dev : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libstdc++6 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libtsan0 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
 libubsan0 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.10 is installed
E: Unmet dependencies. Try using -f.
```

---

### Post by Claus7 on 2018-08-29
Hello,

> **adityatripathi said:**
> **I get the following while i try to install gfortran, please help.**

You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cpp-5 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~**16.04.4**) but 5.4.0-6ubuntu1~16.04.10 is to be installed
 gfortran-4.8 : Depends: gcc-4.8-base (= 4.8.4-2ubuntu1~**14.04.4**) but it is not installed
 

it seems that you have upgraded your system somehow, yet the upgrade process had some issues. You could try to run:
sudo apt-get -f install

as the message you are getting in order to solve your issues. 

Regards!

---

### Post by kc1di on 2018-08-29
did you try what it told you to try?
```
apt install -f
```

---

### Post by coffeecat on 2018-08-29
@adityatripathi, I've merged your two threads. Although you are experiencing two problems, it looks as though they have the same underlying cause. I'm sure they can be solved together.

Also - I've enclosed your terminal output between BBCode code tags for clarity and to preserve columnar formatting. Please use code tags for terminal output, contents of config files, and any other code. There is a link in my sig that tells you how to use forum code tags.

---

### Post by Impavidus on 2018-08-29
It appears you have outdated versions of some packages, conflicting with the newer version of other packages. First refresh the memory of your package manager:```
sudo apt update
```Then try to fix it with```
sudo apt-get install -f
```If that tries to remove a lot of stuff, abort it.

If the problem persists, run```
apt-cache policy cpp-5 g++-5 libcc1-0 libgcc5-dev
```I'm not going to check every conflicting package, as there's probably a single cause for all conflicts.

---

