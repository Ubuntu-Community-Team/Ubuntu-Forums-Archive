---
title: "Open office not in desktop user start menu."
date: 2015-07-26
forum: New to Ubuntu
---

### Post by Travis_Haynie on 2015-07-26
Please direct me to the right spot if already answered.

I am building a small computer lab at the school I work at. I am fairly novice to Linux and need some assistance. I have installed Lubuntu onto 10 Pentium D machines with 2gb memory. it runs great. Ive installed open office, and it runs fine, and is in the start menu. All of this I did with an admin account. I created a desktop user account as I don't want students using the machine as Admin. 

When I log in as the user account, Open Office is not in the menu. How do I get it in the start menu?

~Travis

---

### Post by Bucky Ball on 2015-07-26
Welcome. I imagine you would need to add the users to the appropriate group. I could be wrong and not sure of the group, but it bumps your thread and gives you a clue. Good luck. :)

(You don't mean you installed OO as root, do you? You just logged in as the original user then installed?)

---

### Post by ajgreeny on 2015-07-26
There is a lubuntu menu editor available, though I am not sure if it is in the standard repos. Search around a bit and you may find it. That should allow you to add OOo to the menu.

However, like Bucky Ball I am confused about your installation process of open office. It should appear in the menunif you installed from the repos normally.

I've just found the menu-editor which I used to use at [http://lxmed.sourceforge.net/](http://lxmed.sourceforge.net/)

---

### Post by Travis_Haynie on 2015-07-26
I dont think I did it as root. When I install Lubuntu, it asks to create the compute rname, name and password. This created a "custom" user, which I went and changed to administrator in the users and groups utility.  I don't think that is root. I downloaded OpenOffice (OO?) and unzipped. I used dpkg from the command line while logged in as that user. OO appears in the Office menu in the start menu.

I created an additional user, and assigned it as a desktop user. I logged out as that admin user, and logged in as the new desktop user. While logged in as the desktop user, the OO stuff is not in the start menu.

In Windows, you have the ability to install an app for just one user, or all users. I don't have that option in Lubuntu so how do I get the OO to appear in the desktop user start menu?

I will look for some kind of menu editor. 

~T

---

### Post by ajgreeny on 2015-07-26
As you installed from the archive of .debs downloaded from OOo using dpkg I think you may have to create your own .desktop files similar to this for libreoffice
```

[Desktop Entry]
Version=1.0
Type=Application
Name=OOo Writer
Comment=Office Suite
Categories=Office;
Exec=[COLOR="#FF0000"]execfile-for-openoffice[/COLOR] %U
Icon=[COLOR="#FF0000"]path to OOo-icon[/COLOR]
Terminal=false
StartupNotify=false

```
I do not remember what the exec is actually called or what the icon file is so you will need to find that yourself but I think you will probably find all the applications installed in /opt, though my memory may be playing tricks.

The simpler alternative, of course, is to remove OOo and use libreoffice instead, which you can install from the repos in the usual way.  Perhaps you have a reason for using OOo rather than LO?

---

### Post by Dennis N on 2015-07-26
Check to be sure the Open Office .desktop file is located in /usr/share/applications. That is necessary for it to be globally available to all users, and in everyone's menu.

---

### Post by ajgreeny on 2015-07-26
Just a thought; when I used the OOo archive downloaded a long, long time ago, I think there were two subfolders in the archive, one called **deb** for the main parts of the suite, and a second called something like **desktop-integration** which had another package to install that gave integration into the menu, etc, etc.

Have another look at what you downloaded and see if that is still so.

---

### Post by sandyd on 2015-07-26
> **ajgreeny said:**
> <snip>
The simpler alternative, of course, is to remove OOo and use libreoffice instead, which you can install from the repos in the usual way.  Perhaps you have a reason for using OOo rather than LO?

+1 to this.

Libreoffice gets regular updates and security updates from the default Ubuntu repositories.

---

### Post by Travis_Haynie on 2015-07-26
Ill look at Libre Office tomorrow, and give that a shot...

---

### Post by Bucky Ball on 2015-07-26
Remove all trace of OpenOffice before installing Libreoffice (they are pretty much identical, by the way, Libreoffice is a branch of OO and is the default for other flavours of Ubuntu - OO used to be). They do not play together. If you already have LO installed, that could explain why you are having so much trouble installing OO.

---

### Post by Geoffrey_Arndt on 2015-07-27
ALso, when doing an install, if my memory serves me right, there is no need to add a "custom" user, and then assign whatever rights.    The "first" user added to a "buntu-based" system is by default placed in the sudoer group, and is the admin for the device.    Other users added are by default "non-admin" or just plain users.    It will be cleaner to fully purge OO as others have said, before installing LibreOffice from the Lubuntu Software Center (or by using something like Synaptic which should work better on Lubuntu anyway).

---

### Post by Melodie on 2015-07-27
> **Travis_Haynie said:**
> In Windows, you have the ability to install an app for just one user, or all users. I don't have that option in Lubuntu so how do I get the OO to appear in the desktop user start menu?

Hello,

I might have not understood well but I think I understood you used the administration (aka root) account in a normal/classic graphical environment : is that so? If it is so, it is a BIG NO NO.

In Windows you have one way, which looks like an open castle with everything wide opened, even when you are away for the evening. In GNU/Linux it's the other way around:
This is where you have to get concentrated on how it is different:

In Ubuntu Linux, you are lucky as you have one password only : the one for the user, which allows gaining administration (aka root) privilege when needed.[¹]

So you need to create a user account first. The first user created can gain privilege (via sudo for commands in the terminal, and with pkexec when there are windows raising to ask for your password, but there you don't see the pkexec process directly, it's under in the system). Users created after the first one don't get admin privilege as the default. Only the first user created can provide more rights and permissions to the second and following users.

Let us know if you can perform a normal install, with a normal first user, and access to a normal user session, then use the Synaptic package manager to install Libreoffice (same as OpenOffice.org, but available in the repositories).

Do you know about the repositories? If you don't, we probably need to point you to the right documentation, this is a very important component to know about in the GNU/Linux world.

Here is a full book, in English, based on the Trusty version. There is not much difference with the 15.04, so you can use this one:
[http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/14.04e2/en_US/screen/Getting%20Started%20with%20Ubuntu%2014.04%20-%20Second%20edition.pdf](http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/14.04e2/en_US/screen/Getting%20Started%20with%20Ubuntu%2014.04%20-%20Second%20edition.pdf)

if you want other versions, just choose from this page:
[http://ubuntu-manual.org/downloads](http://ubuntu-manual.org/downloads)

[¹] (in some other distros you get to have two, one for the user and one for the admin(=root))

---

