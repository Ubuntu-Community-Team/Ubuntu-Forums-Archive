---
title: "Gnome 3 unable to re-install and menu options are always highlighted"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by andyrew912 on 2012-06-22
I am running v 12.04 of Ubuntu and still quite new with it.

After installing updates my gnome 3 has completely disappeared and I am not able to log into it or reinstall it. This problems began after attempting to install extensions for gnome-shell.

I also have strange things happening with my menu options and on any window when I go to file or edit all of the options appear to be highlighted. This is not specific to the desktop environment as it also shows my name as highlighted on the login menu. 

Had a similar problem with gnome previously but I just reinstalled ubuntu completely. 

I am still very new to Linux so hoping someone can help me!

This is the error I get when attempting to re-install gnome:

andy@andy-Vostro-1400:~$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 gnome-shell : Depends: libgcr-3-1 (>= 3.4.0) but 3.2.2-2ubuntu4 is to be installed
               Depends: gir1.2-gcr-3 but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by drpjkurian on 2012-06-22
Hi
Open a terminal and paste the following command
```
sudo dpkg --configure -a
```
and enter this command followed by the above one
```
sudo apt-get install -f
```
This will clear broken packages.
Then install gnome shell

---

