---
title: "How to get rid of older versions of linux kernel in the grub menu?"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by Christopher on 2011-12-19
**  How do i get rid of older versions of linux kernels in the grub menu?   I'm using Ubuntu 10.04 LTS     **

---

### Post by Christopher on 2011-12-19
> **Christopher said:**
> **  How do i get rid of older versions of linux kernels in the grub menu?   I'm using Ubuntu 10.04 LTS     **


Ok i think i found a solution to my question, IF anyone has another way of doing this please feel free to post it. Thanks. Chris




[http://ubuntu-install.blogspot.com/2011/06/remove-obsolete-ubuntu-kernels.html](http://ubuntu-install.blogspot.com/2011/06/remove-obsolete-ubuntu-kernels.html)

---

### Post by Christopher on 2011-12-19
> **Christopher said:**
> Ok i think i found a solution to my question, IF anyone has another way of doing this please feel free to post it. Thanks. Chris




[http://ubuntu-install.blogspot.com/2011/06/remove-obsolete-ubuntu-kernels.html](http://ubuntu-install.blogspot.com/2011/06/remove-obsolete-ubuntu-kernels.html)




[http://www.youtube.com/watch?feature=player_embedded&v=9FYW2nGv4gs]("http://www.youtube.com/watch?feature=player_embedded&v=9FYW2nGv4gs")

---

### Post by lechien73 on 2011-12-19
You can download Ubuntu Tweak ([http://www.ubuntu-tweak.com](http://www.ubuntu-tweak.com)), then click on **Janitor**, select **Old Kernel** and check the kernels you wish to remove.

Then open a terminal window and type:

```
sudo update-grub
```

To refresh the menu.

---

### Post by Lars Noodén on 2011-12-19
You can see which ones you have installed using [dpkg](http://manpages.ubuntu.com/manpages/oneiric/en/man1/dpkg.1.html)

```

dpkg --get-selections linux-image-*

```

Then the extras can be uninstalled with [apt-get](http://manpages.ubuntu.com/manpages/oneiric/en/man8/apt-get.8.html)

---

### Post by Christopher on 2011-12-19
> **lechien73 said:**
> You can download Ubuntu Tweak ([http://www.ubuntu-tweak.com](http://www.ubuntu-tweak.com)), then click on **Janitor**, select **Old Kernel** and check the kernels you wish to remove.

Then open a terminal window and type:

```
sudo update-grub
```

To refresh the menu.


Awesome thank you.

---

### Post by grahammechanical on 2011-12-19
Removing old kernels is one way to do it but is there a way of hiding the old ones until you remove them? Yes.

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

Grub Customizer works great and does other things as well that you might find useful.

Regards.

---

### Post by philinux on 2011-12-19
> **Christopher said:**
> How do i get rid of older versions of linux kernels in the grub menu?   I'm using Ubuntu 10.04 LTS 

Personally I like this. See step 5 for the dry run and then do it for real.
 [http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

