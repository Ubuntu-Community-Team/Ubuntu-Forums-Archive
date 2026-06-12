---
title: "PCspim installation on ubuntu 7.10"
date: 2007-11-01
forum: Packaging and Compiling Programs
---

### Post by nima352000 on 2007-11-01
hi , i have problem installing pcspim on ubuntu 7.10 , im taking this digital system class and i have to do some assembly programming and they use PC-spim , i have pc spim on my windows ( dual booting with ubuntu) i was wondering to see if i can have pcspim on ubuntu as well ! if so how can i install it ? i am new to linux and i dont know how to install software on linux :| there is no .exe file in the packages :(

---

### Post by jorge.py on 2007-11-09
Hi!!.. you can install the windows version of PCSpim in Ubuntu with wine.

Follow this steps in terminal:

1. Install Wine

```
sudo apt-get install wine
```

2. Download [http://www.cs.wisc.edu/~larus/SPIM/pcspim_src.zip](http://www.cs.wisc.edu/~larus/SPIM/pcspim_src.zip) and put in your home directory, them:

```
unzip pcspim.zip
```

3. Install with wine:

```
cd Release
msiexec /i Setup.msi
```

If the instalation was ok, you must have a icon in your Desktop..

I hope this help you..

---

### Post by nima352000 on 2007-11-11
unzip:  cannot find or open pcspim.zip, pcspim.zip.zip or pcspim.zip.ZIP.
any time i try to install any program i get a following error

---

### Post by jorge.py on 2007-12-03
make sure that you are in the right directory when unzip, or use the complete path of the file, for example:

```
unzip /home/youruser/pcspim.zip
```

---

### Post by nima352000 on 2007-12-05
well i was able to unzip it but it gave me a error while installation , i kind of give up on this thing . semester is over and i had to use pcspim with Windows :)

---

### Post by iceninja86 on 2008-09-04
Thank you so much for your instruction on how to make PCSpim work on wine. I tried installing Xspim but it wasn't that good. I almost gave up installing it into wine until i found this thread. Finally I don't have to switch to windows to use PCSpim. Again Thankyou :)

---

### Post by jijacob on 2008-10-23
spim 7.1 is currently in the multiverse repositories.  So once you have them enabled, simply type:

```
sudo apt-get update
```

and then

```
sudo apt-get install spim
```

No need to compile, run in wine, or *any* of that nonsense.

---

### Post by jlucasps on 2009-04-10
Thanks jijacob,

it's works fine.

---

