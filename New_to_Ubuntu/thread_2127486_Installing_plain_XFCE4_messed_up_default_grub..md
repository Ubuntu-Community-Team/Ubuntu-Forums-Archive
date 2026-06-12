---
title: "Installing plain XFCE4 messed up default grub."
date: 2013-03-20
forum: New to Ubuntu
---

### Post by c2tarun on 2013-03-20
Hi friends,

I installed plain-vanilla xfce4 package on my ubuntu 12.04. I know many will advice me to install xubuntu-desktop instead of xfce4 but frankly, I don't know why, plain xfce4 on ubuntu 12.04 is lot faster than Xubuntu and lot lot faster then xubuntu-desktop on Ubuntu.

Anyway my problem is that xfce4 while installation somehow messed my grub. I don't know why but now I see a backgroud in my grub menu and it is slow now. I tried to boot from liveCD and then mount my root partition to a point and did a grub-install in that partition. But nothing happened.

Here is the screenshot of my new boot screen:
[ATTACH=CONFIG]240370[/ATTACH]

Can anyone please help me restoring my old grub?

---

### Post by Frogs Hair on 2013-03-20
I don't think I can help but I have installed XFCE4 on 12.04 and 12.10 and seen no change in grub.  The XFCE4 Session is much lighter than the Xubuntu  desktop  which includes artwork for GDM ,but  not grub as far as I know.

---

### Post by Lemuriano on 2013-03-20
If you have another desktop install like unity. Login to that desktop and from the terminal reintall grub.

> sudo grub-install /dev/sda && sudo update-grub

Make sure the sda is the correct one, otherwise make the correction. 

Regards

---

### Post by c2tarun on 2013-03-21
> **Lemuriano said:**
> If you have another desktop install like unity. Login to that desktop and from the terminal reintall grub.



Make sure the sda is the correct one, otherwise make the correction. 

Regards

Ok, I'll do this today. I am just confirming.
I have Unity, I'll login in unity and then I'll run following command:

```
sudo grub-install /dev/sda1
```

sda1 because my primary Ubuntu is installed in sda1 only.

---

### Post by Krytarik on 2013-03-21
First, there is **absolutely no need to reinstall Grub**, and it wouldn't help either, as your Grub is generally working just fine, it's just about its appearance; and btw, to answer your last question:
> **Reinstalling GRUB 2 from a Working System**

If Ubuntu is operating normally, boot into the working installation and run the following command from a terminal.  

[INDENT]***X*** is the *drive* (letter) on which you want GRUB to write the boot information. Normally users should **not**  include a partition number, which would produce an error message as the  command would attempt to write the information to a partition.  
```
sudo grub-install /dev/sdX  # Example: sudo grub-install /dev/sda
```[/INDENT]
This  will rewrite the MBR information to point to the current installation  and rewrite some GRUB 2 files (which are already working).

Source: [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System)

Now, **in short**, to get your Grub appearance back to what is the default under Ubuntu, just run these commands:
```
sudo update-alternatives --remove-all desktop-grub
sudo update-grub
```

**Background:** Installing the metapackage "[xfce4]("http://packages.ubuntu.com/precise/xfce4")", as a matter of dependency (recommend), pulled in the package "[desktop-base]("http://packages.ubuntu.com/precise/desktop-base")", which among other stuff, also includes a couple of background images for Grub, installed into the 'alternatives' system with these 'postinst' commands:
```
    # Alternatives for grub
    update-alternatives --install \
        /usr/share/images/desktop-base/desktop-grub.png \
        desktop-grub \
        /usr/share/images/desktop-base/spacefun-grub.png 15

    update-alternatives --install \
        /usr/share/images/desktop-base/desktop-grub.png \
        desktop-grub \
        /usr/share/images/desktop-base/spacefun-grub-widescreen.png 14

    update-alternatives --install \
        /usr/share/images/desktop-base/desktop-grub.png \
        desktop-grub \
        /usr/share/images/desktop-base/moreblue-orbit-grub.png 10
```
Since by default, the 'alternatives' group "desktop-grub" doesn't exist on a current Ubuntu installation, we can just happily remove the entire group, as opposed to removing the added alternatives one by one from the group.

Manpage of "update-alternatives", for further reference:

[http://manpages.ubuntu.com/manpages/precise/en/man8/update-alternatives.8.html](http://manpages.ubuntu.com/manpages/precise/en/man8/update-alternatives.8.html)

Regards.

---

### Post by grahammechanical on 2013-03-21
If you run the command ```
sudo update-grub
``` you may see that it is finding a image file in /boot/grub. Remove that image file from /boot/grub and then run ```
sudo update-grub
```

Regards.

---

### Post by c2tarun on 2013-03-21
> **Krytarik said:**
> First, there is **absolutely no need to reinstall Grub**, and it wouldn't help either, as your Grub is generally working just fine, it's just about its appearance; and btw, to answer your last question:

Source: [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System)

Now, **in short**, to get your Grub appearance back to what is the default under Ubuntu, just run these commands:
```
sudo update-alternatives --remove-all desktop-grub
sudo update-grub
```

**Background:** Installing the metapackage "[xfce4]("http://packages.ubuntu.com/precise/xfce4")", as a matter of dependency (recommend), pulled in the package "[desktop-base]("http://packages.ubuntu.com/precise/desktop-base")", which among other stuff, also includes a couple of background images for Grub, installed into the 'alternatives' system with these 'postinst' commands:
```
    # Alternatives for grub
    update-alternatives --install \
        /usr/share/images/desktop-base/desktop-grub.png \
        desktop-grub \
        /usr/share/images/desktop-base/spacefun-grub.png 15

    update-alternatives --install \
        /usr/share/images/desktop-base/desktop-grub.png \
        desktop-grub \
        /usr/share/images/desktop-base/spacefun-grub-widescreen.png 14

    update-alternatives --install \
        /usr/share/images/desktop-base/desktop-grub.png \
        desktop-grub \
        /usr/share/images/desktop-base/moreblue-orbit-grub.png 10
```
Since by default, the 'alternatives' group "desktop-grub" doesn't exist on a current Ubuntu installation, we can just happily remove the entire group, as opposed to removing the added alternatives one by one from the group.

Manpage of "update-alternatives", for further reference:

[http://manpages.ubuntu.com/manpages/precise/en/man8/update-alternatives.8.html](http://manpages.ubuntu.com/manpages/precise/en/man8/update-alternatives.8.html)

Regards.

Thanks for such a detail reply and awesome explanation.

> **grahammechanical said:**
> If you run the command ```
sudo update-grub
``` you may see that it is finding a image file in /boot/grub. Remove that image file from /boot/grub and then run ```
sudo update-grub
```

Regards.

Thanks to you too for simple solution.

I did some googling and on the background information provided by Krytarik I actually understand now that what had happened. I'll try removing alternatives link and then update-grub. If it worked, I'll mark thread as solved.

---

