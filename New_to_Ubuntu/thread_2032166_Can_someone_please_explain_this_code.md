---
title: "Can someone please explain this code?"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by vasa1 on 2012-07-23
```
sudo su
xhost +SI:localuser:lightdm
sudo su lightdm -s /bin/bash
gsettings set com.canonical.unity-greeter background '/usr/share/backgrounds/awesome_.png'
exit
```
I came across it [here]("http://askubuntu.com/questions/72620/how-do-i-remove-the-dots-from-the-lightdm-greeter/121620#121620") which linked to[this]("http://ubuntuforums.org/showpost.php?p=11840170&postcount=25")
I haven't used **sudo su** before and most of the rest of the code seems complicated as well.

---

### Post by Kopkins on 2012-07-23
Using ```
sudo su
``` Uses root priviledges (sudo) to switch users (su) and without another argument it defaults to the superuser (root). If I needed to access files that only a user "smith" has access to I would use: ```
su smith
``` But I would need smith's password. In your case, using just "su" would work too, if you knew the root password. This effect, acting as another user, lasts until you issue the command: exit, or you close the terminal.

I'm not sure what xhost does, but is probably doing somethign related to the lightdm user.

"sudo su lightdm" switches to the user lightdm, and sets the default shell to bash. 

The gsettings line looks like it is just changing the background of the login screen. 

There should be another exit at the end. With just one exit you leave open a terminal logged in as root.

Kopkins

---

### Post by mapes12 on 2012-07-23
If you're looking to remove the white dots from the log in screen I followed this and it worked:-

[http://www.noobslab.com/2012/05/remove-white-dots-from-login-screen-of.html](http://www.noobslab.com/2012/05/remove-white-dots-from-login-screen-of.html)

The Terminal commands look the same.

---

### Post by Frogs Hair on 2012-07-23
xhost - the server access control program for X. The xhost program is used to add and delete host (computer) names or user names to the list of machines and users that are allowed to make connections to the X server. This provides a rudimentary form of privacy control and security.

---

### Post by vasa1 on 2012-07-23
Thank You, Kopkins, mapes12 & Frogs Hair :)

Marking it Solved

---

