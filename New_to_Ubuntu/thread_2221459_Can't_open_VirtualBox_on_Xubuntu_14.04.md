---
title: "Can't open VirtualBox on Xubuntu 14.04"
date: 2014-05-02
forum: New to Ubuntu
---

### Post by mauricio7 on 2014-05-02
I'm running **Xubuntu 14.04**, and I can't open **VirtualBox 4.3**.

I installed VirtualBox from Software Center. I have icon in my menu under System category, but when I click the icon nothing happens.
After removing it, I tried the procedure from this blog [http://www.n00bsonubuntu.net/content/install-virtualbox-ubuntu-14-04/](http://www.n00bsonubuntu.net/content/install-virtualbox-ubuntu-14-04/) . Virtualbox gets installed but again when I want to run it nothing happens.

Is it happening to anyone else? Am I missing something obvious?

Thanks for help...

---

### Post by mauricio7 on 2014-05-02
Solved it!

Besides not being able to open VirtualBox, I also had problem with opening Software Ceneter. Both problems were fixed by reinstalling** libgl1-mesa-glx** .

Code:
> 
sudo apt-get install --reinstall libgl1-mesa-glx


---

