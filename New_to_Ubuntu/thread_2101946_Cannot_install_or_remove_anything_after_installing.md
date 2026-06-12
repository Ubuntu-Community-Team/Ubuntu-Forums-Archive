---
title: "Cannot install or remove anything after installing ia32-libs"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by ahmetaa on 2013-01-05
I have Ubuntu 12-10 64 bit
After installing  ia32-libs in my x86-64 system, whole package system seems to be broken and no matter what I tried I cannot install or remove anything

This is what I get for example:

```
>sudo apt-get install audacity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 audacity : Depends: audacity-data (= 2.0.1-1) but it is not going to be installed
            Depends: libflac++6 (>= 1.2.1) but it is not going to be installed
            Depends: libid3tag0 (>= 0.15.1b) but it is not going to be installed
            Depends: libportsmf0 but it is not going to be installed
            Depends: libsbsms10 but it is not going to be installed
            Depends: libvamp-hostsdk3 but it is not going to be installed
            Depends: libwxbase2.8-0 (>= 2.8.12.1) but it is not going to be installed
            Depends: libwxgtk2.8-0 (>= 2.8.12.1) but it is not going to be installed
 bluez-alsa:i386 : Depends: libasound2:i386 (>= 1.0.16) but it is not going to be installed
 ia32-libs-multiarch:i386 : Depends: libasound2:i386 but it is not going to be installed
 libasound2-plugins:i386 : Depends: libasound2:i386 (>= 1.0.25) but it is not going to be installed
 libcanberra0:i386 : Depends: libasound2:i386 (>= 1.0.16) but it is not going to be installed
 libesd0:i386 : Depends: libasound2:i386 (>= 1.0.16) but it is not going to be installed
 libsdl1.2debian:i386 : Depends: libasound2:i386 (>= 1.0.16) but it is not going to be installed
 libvisual-0.4-plugins:i386 : Depends: libasound2:i386 (>= 1.0.16) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```


Before, for some reason I installed bluez-alsa stuff from a repository. I am guessing that caused all this mess. 
I tried following suggesstions in many places (for example ppa-purge)but nothing worked. I am in the verge of re-installing the whole thing but I will hate to do that.

any suggesstions?

---

### Post by Bashing-om on 2013-01-05
ahmetaa; Hi !

Have you tried what the out puts recommend ?
```
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```Post back with any errors from the above.
[INDENT][INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by NikTh on 2013-01-06
Hi, 
sometimes dpkg gets confused with 32bit packages on 64bit system. 
Lets see if this is your situation 
Apply the command below ```
dpkg --print-foreign-architectures
```if above command does not show any output then try 
```
sudo dpkg --add-architecture i386
```and
```
sudo apt-get install -f
sudo apt-get update ; sudo apt-get dist-upgrade
```If problem not solved the full output of above commands required for debugging.
Thanks

---

### Post by ahmetaa on 2013-01-06
> **NikTh said:**
> Hi, 
sometimes dpkg gets confused with 32bit packages on 64bit system. 
Lets see if this is your situation 
Apply the command below ```
dpkg --print-foreign-architectures
```if above command does not show any output then try 
```
sudo dpkg --add-architecture i386
```and
```
sudo apt-get install -f
sudo apt-get update ; sudo apt-get dist-upgrade
```If problem not solved the full output of above commands required for debugging.
Thanks

Nikth, you saved my sanity. Thank you so much it worked like a charm!!

---

### Post by NikTh on 2013-01-06
Hi , 
sorry for the misspelled command , but you understood it I guess. 

Please correct the quote if you want , I already corrected the command

Thanks and glad we solved it

---

