---
title: "compiz plugin problem."
date: 2008-10-15
forum: New to Ubuntu
---

### Post by LeftNut on 2008-10-15
Hi guys i followed these instructions:
> **Locutus_of_Borg said:**
> for the latest compiz packages, you are probably going to have to compile them yourself.

you can get the source codes though git

first install git
```
sudo apt-get install git
```

also make sure you have necessary headers and such
```
sudo apt-get install linux-headers-'uname -r' build-essential
```

now get the source compile and install
```
wget http://www.xs4all.nl/~mgj1/downloads/compiz-git-newest.tar.gz
tar xzf compiz-git-newest.tar.gz
cd compiz-git
./compiz-git install
```

I followed these directions and it installed. But now when i try and goto compizconfig-settings its wont load and when i click fusion-icon it wont load either.

Any help to fix this error would be greatly appreciated since i've reinstalled hardy 3 times in the past 2 days and i'm really trying to avoid doing that again. =[

Thank you very much,
Gary

---

### Post by eternalnewbee on 2008-10-15
Have you enabled your hardware driver in Main Menu > System > Hardware Drivers?

---

### Post by LeftNut on 2008-10-15
> **eternalnewbee said:**
> Have you enabled your hardware driver in Main Menu > System > Hardware Drivers?

ya everything was working fine till i tried adding the plugins =\

thanks for the reply. if anyone else has some ideas on how i can get them to work i would greatly appreciate it.

Thank you,
Gary

---

### Post by SunnyRabbiera on 2008-10-15
Well maybe you should not be trying out the latest version of compiz, sometimes its just best to stick with what you have as latest doesnt always mean greatest.

---

### Post by LeftNut on 2008-10-15
> **SunnyRabbiera said:**
> Well maybe you should not be trying out the latest version of compiz, sometimes its just best to stick with what you have as latest doesnt always mean greatest.

1)i didnt update the version i just added plugins. 2) i got the compiz config to open but when i enable the plugins i added the box checks and the box unchecks 1 sec later. If anyone can link to a page to fix this or has information to get these to work i would greatly appreciate it. 

Thank you,
Gary

---

### Post by SunnyRabbiera on 2008-10-15
> **LeftNut said:**
> 1)i didnt update the version i just added plugins. 2) i got the compiz config to open but when i enable the plugins i added the box checks and the box unchecks 1 sec later. If anyone can link to a page to fix this or has information to get these to work i would greatly appreciate it. 

Thank you,
Gary

well I know that certain plugins wont work on certain versions of compiz

---

### Post by Gazneth on 2008-10-15
Some parts of compiz are still quite experimental, especially anything you would have to install with git. Unless you just have to have that certain effect, you might save yourself some headaches by staying away from these plugins. I understand your desire for this I am running Intrepid Beta myself, just choose your battles wisely. Also if you post in the Desktop effects section you may get more knowledgeable help than in the beginner forum.

---

### Post by eternalnewbee on 2008-10-15
Final solution: Reinstall again.
We learn to walk in the world of Ubuntu through ttrial and error.

---

### Post by LeftNut on 2008-10-15
> **eternalnewbee said:**
> Final solution: Reinstall again.
We learn to walk in the world of Ubuntu through ttrial and error.

bah sick of formatting this partion already lol. if anyone knows a way to unistall compiz-git and all the plugins with the information i provided with the first post it would be love it.

Thank you,
Gary

---

### Post by eternalnewbee on 2008-10-15
Not reinstalling the whole system!!!
Just compiz.

---

### Post by eternalnewbee on 2008-10-15
sudo apt-get remove compiz compiz-core compiz-dev compiz-bcop compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-kde emerald libcompizconfig-0 python-compiz --purge

This will uninstall it.

---

### Post by LeftNut on 2008-10-15
> **eternalnewbee said:**
> sudo apt-get remove compiz compiz-core compiz-dev compiz-bcop compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-kde emerald libcompizconfig-0 python-compiz --purge

This wiil uninstall it.

One question if i install compiz through the synaptic manager which is the newist version i think can i use emerald with that version?

Thank you,
Gary

---

### Post by eternalnewbee on 2008-10-15
You can install Emerald via Synaptic, too.

---

### Post by eternalnewbee on 2008-10-15
Of course you can

---

### Post by LeftNut on 2008-10-15
> **eternalnewbee said:**
> Of course you can

thank you for all the help

---

### Post by eternalnewbee on 2008-10-15
You're welcome LeftNut

---

