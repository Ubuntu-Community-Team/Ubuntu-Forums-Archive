---
title: "LiveCD customization problem"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by ralphz on 2008-05-30
Hi

I have fallowed those two howtos to customize my LiveCD with Ubuntu 8.04:

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
[http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd](http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd)

I was able to install additional software and change desktop background - the easy stuff. But I have a hard time figuring out how to customize menus and some other things that I need. 

So my question is how to customize Gnome menus (Aplications, Places, History) from command prompt only? What files I should be looking at any howtos about it?

Ralph

---

### Post by Oldsoldier2003 on 2008-05-30
> **ralphz said:**
> Hi

I have fallowed those two howtos to customize my LiveCD with Ubuntu 8.04:

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
[http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd](http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd)

I was able to install additional software and change desktop background - the easy stuff. But I have a hard time figuring out how to customize menus and some other things that I need. 

So my question is how to customize Gnome menus (Aplications, Places, History) from command prompt only? What files I should be looking at any howtos about it?

Ralph
putting the customizations in /etc/skel before you build the live cd will customize the live cd user. I have a debian installation that I use for making rescue cds and I've found that the easiest way is to set up a "user" and copy all the customizations into /etc/skel before I chroot and build the new cd

---

### Post by ralphz on 2008-05-30
Hi

Thank you for responding. But how do I customize menus?

Lets say I'd like to remove "System" menu form appearing and remove "Add/Remove.." form applications menu.

---

### Post by Oldsoldier2003 on 2008-05-30
> **ralphz said:**
> Hi

Thank you for responding. But how do I customize menus?

Lets say I'd like to remove "System" menu form appearing and remove "Add/Remove.." form applications menu.

My live cd is built using xfce but the idea is the same. Customize the menus and desktops then copy the configuration files from the home directory to /etc/skel. for xfce its ~/.config  copied to /etc/skel/.config

for desktop items ~/Desktop gets copied to /etc/skel/Desktop

---

### Post by ralphz on 2008-05-30
Hi

So I do:

1. I follow the howtos to make Live CD with custom software like I did and it works.

2. I make Live CD like in howtos (squashfs and all that stuff)

3. I boot from CD make any changes to Gnome panels and save home dir somewhere then copy anything thas in it to /etc/skel and build CD again?

Is there a way to do it right away in step 1?

Ralph

---

### Post by Oldsoldier2003 on 2008-05-30
> **ralphz said:**
> Hi

So I do:

1. I follow the howtos to make Live CD with custom software like I did and it works.

2. I make Live CD like in howtos (squashfs and all that stuff)

3. I boot from CD make any changes to Gnome panels and save home dir somewhere then copy anything thas in it to /etc/skel and build CD again?

Is there a way to do it right away in step 1?

Ralph
do it in step one. Depending on what tutorial method you are using depends on how easy its going to be. Personally i build the live cd based on my installation, I don't build a complete installation using deb bootstrap. Its much easier to customize if you dont build it from scratch using debbootstrap!.

A good tutorial is here:
[http://ubuntuforums.org/showthread.php?p=4277073#post4277073](http://ubuntuforums.org/showthread.php?p=4277073#post4277073)

---

### Post by ralphz on 2008-05-30
Hi thanks for the link I'll follow this guide and let you know how it worked.

Ralph

---

