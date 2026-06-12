---
title: "[SOLVED] help!!"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by ayeshap on 2008-06-16
i am absolutely new to this ubuntu system and i tried to install windows instead but its not working. anyways i was trying to download limewire for ubuntu but it didnt work and now i'm trying to open my synaptic package manager but a message keeps coming up saying :

An error occured.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i have no idea wat this means..plz help.

---

### Post by tamoneya on 2008-06-16
open up terminal(applications -> accessories -> terminal) and type ```
sudo dpkg --configure -a
```

Also you will get better help if you choose a more descriptive title.  It helps the other forum members. I would have named it "E: dpkg was interrupted" or  "'dpkg --configure -a'??"

---

### Post by alienexplorers on 2008-06-16
run this in terminal > sudo dpkg --configure -a

---

### Post by iaculallad on 2008-06-16
> **ayeshap said:**
> i am absolutely new to this ubuntu system and i tried to install windows instead but its not working. anyways i was trying to download limewire for ubuntu but it didnt work and now i'm trying to open my synaptic package manager but a message keeps coming up saying :

An error occured.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i have no idea wat this means..plz help.

Open your terminal and issue the command below (as what is stated):

```
sudo dpkg --configure -a
```

---

### Post by Corrupt3d on 2008-06-16
Open up a terminal,
Apps>Acessories>Terminal & then type in:

sudo dpkg --configure -a

it will prompt you to enter you password, input it and press enter.

---

### Post by steveneddy on 2008-06-16
Have you tried

```

sudo dpkg --configure -a

```

??

---

### Post by ayeshap on 2008-06-17
thanks a lot..i didnt know wat i should've put at as my heading since i dont even know wat dpkg is..this system is very hard to get used to since i know nothing about computers. i ordered a laptop from dell and i didnt read the small print that the reason this laptop was cheap was because it contained ubuntu and not windows so now i'm stuck with it i guess

---

### Post by hyper_ch on 2008-06-17
it is adviced to use a descriptive thread title that refelcts the content of the post/problem/inquiry instead of using a generic title like "noob here" or "help needed".

---

### Post by kesman on 2008-06-17
> **ayeshap said:**
> thanks a lot..i didnt know wat i should've put at as my heading since i dont even know wat dpkg is..this system is very hard to get used to since i know nothing about computers. i ordered a laptop from dell and i didnt read the small print that the reason this laptop was cheap was because it contained ubuntu and not windows so now i'm stuck with it i guess

If ubuntu is preinstalled and working, stick to it and learn it, you'll benefit a lot!

Did running the given command solve your problem?

---

### Post by ayeshap on 2008-06-17
yes i'm now able to get into the synaptic package manager. however when i open it a msg  comes up saying i have a broken package which is sun-java6-bin.when i go to completely remove it an error msg comes up saying that the package is in a very bad inconsistent state- you should reinstall it before attempting a removal
E: Sub-process /usr/bin/dpkg returned an error code.

i have a feeling it might have to do with the fact that i placed the limewire thing i was downloading into the bin and deleted it last night. now i dont know wat to do and i wanna download frostwire but a status comes up saying

ERROR: Failed to satisfy all dependencies (broken cache)

i have no idea what all that means...i hope i didnt mess up my laptop.

---

### Post by kesman on 2008-06-17
open up terminal and run the following:
```

sudo apt-get update
sudo apt-get install --reinstall sun-java6-bin

```
if this doesn't work, try
```

sudo apt-get purge sun-java6-bin
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get install sun-java6-bin

```

---

### Post by bumanie on 2008-06-17
Go to synaptic and type java6-bin into search. Click on the green square and choose "mark for reinstallation" - it will be reinstalled from the repository and should be like new again. Then you should be able to install frostwire and get it working.

---

### Post by ayeshap on 2008-06-17
neither of those things worked..when i type those codes into the terminal and then i go back to synaptic the same msg broken package msg coming up.when i type java6-bin into search, a red square, not a green square comes up.
maybe its because i emptied my trash last night??

---

### Post by Sef on 2008-06-17
Go back into synaptic and do this:

Edit > Fix Broken Packages > follow the directions to fix

---

### Post by bumanie on 2008-06-17
What kesman has put should work. May be there is more wrong with the file system than a mucked up java6. Do you have separate /home partition or is /home within /? If you have a separate /home partition, it may be best to reinstall ubuntu to / If not may be you will have to save any important data in /home and reinstall from scratch, in which case it would be best to manually format and make a separate / and /home as well as the mandatory swap partition. I have to go to work now. Good luck.

---

### Post by ayeshap on 2008-06-17
oh i did what kesman said to do again. i didnt know i was supposed to go back to synaptic after that and reinstall it.*blush* i worked tho...thanks a lot everyone!

this'll take some getting used to...

---

### Post by sailor2001 on 2008-06-17
you may want to consider using AMULE rather than limewire. Your downloaded pks from there are in PLACES/HOME ..ctrl/h to see folder.. Also when going back into synaptic, RELOAD to get all your pkgs updated.  Learn ubuntu, it is actually quite easy and have a lot of computer fun.

---

### Post by tamoneya on 2008-06-17
another nice limewire alternative is frostwire: [http://www.frostwire.com/](http://www.frostwire.com/)

---

