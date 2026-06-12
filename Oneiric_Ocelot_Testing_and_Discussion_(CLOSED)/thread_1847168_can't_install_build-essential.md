---
title: "can't install build-essential"
date: 2011-09-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Darngood on 2011-09-20
I have just installed ubuntu 11.10 beta but had an unexpected surprise!:
sudo apt-get install build-essential

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 build-essential : Depends: g++ (>= 4:4.4.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

What should I do ?
PS:
Linux Inspirion 3.0.0-11-generic #18-Ubuntu SMP Tue Sep 13 23:38:01 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by josephmills on 2011-09-20
> **Darngood said:**
> I have just installed ubuntu 11.10 beta but had an unexpected surprise!:
sudo apt-get install build-essential

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 build-essential : Depends: g++ (>= 4:4.4.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

What should I do ?
PS:
Linux Inspirion 3.0.0-11-generic #18-Ubuntu SMP Tue Sep 13 23:38:01 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

as you know it is still in beta testing so there are going to be things like this . but it looks like g++ needs to be installed apt is the package manager. so It should not do this. but it is try to install g++ then the headers nothing try sudo apt-get -y install

---

### Post by Darngood on 2011-09-20
> **josephmills said:**
> as you know it is still in beta testing so there are going to be things like this . but it looks like g++ needs to be installed apt is the package manager. so It should not do this. but it is try to install g++ then the headers nothing try sudo apt-get -y install
None of this work. I'll just reinstall ubuntu 11.04 again if I can't find a solution soon.

---

### Post by jerrrys on 2011-09-20
I just downloaded it using Main Server U.S.

---

### Post by josephmills on 2011-09-20
I also have it with kubuntu 11.10 you should 100% report this. 
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by mdhollis on 2011-09-20
> **jerrrys said:**
> I just downloaded it using Main Server U.S.

Me too.  Downloaded and installed ok.

---

### Post by Darngood on 2011-09-20
> **jerrrys said:**
> I just downloaded it using Main Server U.S.

I switched to the main server and it works, thank you.

---

