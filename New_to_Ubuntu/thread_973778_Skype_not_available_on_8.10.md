---
title: "Skype not available on 8.10"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Matrix1 on 2008-11-07
Skype is not available on 8.10.  Do you know how I get skype or I have to use WINE?
Thanks.

---

### Post by Yoke &amp; Chung on 2008-11-07
Don't think you need to run it under WINE. I have seen Ubuntu screenshots with Skype on it.

---

### Post by patrickballeux on 2008-11-07
Download from Skype site...

They already have Linux version...

---

### Post by kostkon on 2008-11-07
> **Matrix1 said:**
> Skype is not available on 8.10.  Do you know how I get skype or I have to use WINE?
Thanks.
What do you mean? You can just download it from Skype's website. It offers a deb file. Download it, double-click on it to install it. 

Alternatively, you can install it from the [*Medibuntu* repo]("http://medibuntu.org/") (you'll have to add this repo to your software sources list and then use Synaptic to install it).

---

### Post by Matrix1 on 2008-11-07
> **kostkon said:**
> What do you mean? You can just download it from Skype's website. It offers a deb file. Download it, double-click on it to install it. 

Alternatively, you can install it from the [*Medibuntu* repo]("http://medibuntu.org/") (you'll have to add this repo to your software sources list and then use Synaptic to install it).

Skype was available in 8.4 and it was under "Applications/Internet", but not available in 8.10.  I tried to install from synaptic package manager but not available there also.

I didn't know it was available for Ubuntu from Skype.com.  

I just downloaded and installed...Thanks a lot.

---

### Post by lisati on 2008-11-07
I downloaded Skype from the Skype website, and the Ubuntu verdsion works well with the copy of Xubuntu 8.10 on my day-to-day laptop.
It can be found here: [http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

---

### Post by hyper_ch on 2008-11-07
Use the Medibuntu site to install skype.

---

### Post by jetpeach on 2008-11-07
See the intructions here to add Medibuntu (and a description of Mediubuntu) here:
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

actually, just two commands two ad Medibuntu:
```
sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
```
then, if you want to allow authentication
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
and accept the package (then you won't be bugged with warning about authentication)

now, with that repository added and taken care of just
```
sudo apt-get install skype
```
should download/install skype for you!

---

### Post by B34ST1Y on 2008-11-07
> **Matrix1 said:**
> Skype is not available on 8.10.  Do you know how I get skype or I have to use WINE?
Thanks.

pretty sure I'm running skype just fine. Try downloading it straight off their website. I'm running 8.10 right now, with no special configurations...it installed like a normal program :)

---

### Post by ww711 on 2008-11-07
As other have mentioned, it's available from their site and since there is a deb file installer; it is straightforward to install and to get running.

---

### Post by hyper_ch on 2008-11-07
> **ww711 said:**
> it is straightforward to install and to get running.
I disagree :) try to do that on 64bit ;) my recommendation is still to use medibuntu.

---

### Post by Soriano on 2008-11-07
If you want skype just add this into your repositories.  

```
deb http://download.skype.com/linux/repos/debian/ stable non-free
```

That way you'll get any updates that skype pushes out and it will also add skype to the Synaptic Packet Manager.

Here is a link:

[Skype install methods]("https://help.ubuntu.com/community/Skype")

Here is a link about repositories in case you want to learn more:

[Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by hyper_ch on 2008-11-07
> **Soriano said:**
> If you want skype just add this into your repositories.  

```
deb http://download.skype.com/linux/repos/debian/ stable non-free
```


yet again this only works for 32-bit.

---

### Post by Soriano on 2008-11-07
This is true............:)

---

### Post by Soriano on 2008-11-07
I don't have a 64-bit machine but it appears that it works according to this page:

[64 Bit Skype]("http://ubuntuforums.org/showthread.php?t=432295")

There is a link to a deb file for amd-64 under the Intrepid Header.  If it works for anyone I'd love to know!

---

### Post by hyper_ch on 2008-11-07
or just add medibuntu ;) 64-bit support, webcam support...

---

