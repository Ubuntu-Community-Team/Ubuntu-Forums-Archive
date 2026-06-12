---
title: "Ubuntu forgets include something important."
date: 2020-07-10
forum: New to Ubuntu
---

### Post by antenac on 2020-07-10
I am working hard to implement GNU/Linux on PCs with Windows's users. So, I have the problem that Ubuntu 20.04 don't include an easy way to make shortcuts or quick access to non executable files and folders.
Windows works very well in this aspect, please take note. Users need versatility, simplicity and an intuitive interface.

---

### Post by Dennis N on 2020-07-11
In Ubuntu 20.04, you can bookmark any folder by right click on the folder's tile in the path at the top of Files. A drop down menu appears that has 'add to bookmarks'. See screenshot. Bookmarks appear in the left-side pane of Files. Those give you one-click 'quick access'.

---

### Post by monkeybrain20122 on 2020-07-11
> **antenac said:**
>  Users need versatility, simplicity and an intuitive interface.

My two cents: If you want versatility, simplicity and an intuitive interface don't use gnome shell. Install another DE or find another flavour. Gnome is moving in the opposite direction of those qualities, it gets more frustrating to use and weird with each new release. IMHO it is unusable for normal users without a bunch of hacks in the form of often poorly maintained addons. Gnome developers think that these addons are rude interference with their vision so they don't care about backward compatibility or a stable API, many addons bite the dust whenever a new version of gnome shell is released. The internet is littered with abandoned gnome shell addons.

If you are setting up gnome shell for new users (whether Windows user or not) don't forget to create an empty text file in ~/Templates, otherwise the right click option of "create new document" will not show up. Gnome developers think that it is a brilliant idea to make user go through this unintuitive step to achieve a simple thing that users of other DEs and OSes take for granted. They said it is part of some grand design vision.

I am using unity on standard Ubuntu20.04 (sudo apt install ubuntu-unity-desktop, choose lightdm as default at pop up, logout and login, then remove gnome shell that's it, I also use nemo instead of nautilus as my file manager) I can display all recent files and folders with the dash with a keyboard stroke. I am setting up Kubuntu 20.04 for a friend who wants a more Windows like interface, Mint is another possibility for users who want a slick but Windows like layout (or Ubuntu with Cinnamon which is basically the same thing)

---

### Post by monkeybrain20122 on 2020-07-11
Default Ubuntu 20.04 does have some important tools missing, e.g  net-tools. It is frustrating that you cannot even run ifconfig to  diagnose your wifi and you need wifi to install it! (not all of us have  access to wired connection, I share internet and the modem is upstairs  with separate entrance), or when you try to locate a file and find out  you have to install mlocate. 

I never had to install these myself in previous Ubuntu releases. What is going through their minds?

---

### Post by Impavidus on 2020-07-11
Intuitive is subjective. What someone with years of Windows experience considers intuitive may be very counter-intuitive for someone else. Ubuntu isn't Windows and doesn't try to be, so to a long-term Windows user it will sometimes appear non-intuitive.

BTW, on my Xubuntu system, when I right-click on my desktop and go to "create document", it tells me "no templates installed", but does give me the option to create an empty file. I've never used that. I've no use for empty files. But if you put the file manager centre-stage in your workflow, it may be useful.

---

### Post by mastablasta on 2020-07-11
use Kubuntu with KDE for "every setting in GUI" approach.
Xubuntu (with XFCE) is also very easy to configure.
Cinnamon is next in line for classic desktop usage.

---

### Post by antenac on 2020-07-11
> **Impavidus said:**
> Intuitive is subjective. What someone with years of Windows experience considers intuitive may be very counter-intuitive for someone else. Ubuntu isn't Windows and doesn't try to be, so to a long-term Windows user it will sometimes appear non-intuitive.

I am talking about one specific functionality of Windows 10 menu. You can set up this menu as you want. Ironic thing, doesn't it? MS started to do that things because GNU/Linux give personalitation options. And now, user's have to adapt to Ubuntu. That's crazy. 

> **Impavidus said:**
> But if you put the file manager centre-stage in your workflow, it may be useful.

Again, what if I want the possibility?. I am working for introduce GNU/Linux in society, and I don't feel supported by them at all.

---

### Post by antenac on 2020-07-11
> **monkeybrain20122 said:**
> My two cents: If you want versatility, simplicity and an intuitive interface don't use gnome shell.
Thanxs a lot. 
It is very sad to see how Ubuntu is turning to become in Apple philosofie.
With the snap store I think I lost at least, ten hours, It is really slow and inefficient.
I hope Gnome Desktop start to think in user's neededs more than a clean estetic.

---

### Post by antenac on 2020-07-11
> **Dennis N said:**
> In Ubuntu 20.04, you can bookmark any folder by right click on the folder's tile in the path at the top of Files. A drop down menu appears that has 'add to bookmarks'. See screenshot. Bookmarks appear in the left-side pane of Files. Those give you one-click 'quick access'.

Thanxs. I know this methods, but it is not what I looking for,

---

### Post by antenac on 2020-07-12
> **mastablasta said:**
> use Kubuntu with KDE for "every setting in GUI" approach.
Xubuntu (with XFCE) is also very easy to configure.
Cinnamon is next in line for classic desktop usage.


When Richard Stallman said that Ubuntu was a Spyware, the answer was, something like "the goal of this change and others to come is to unify searches for user convenience."

---

### Post by antenac on 2020-07-12
Thanks to all for answer.


I gonna try with Gnome-pie and/or Gnome-do. It is not the ideal, but may be it results at least funy and friendly for Windows users.

---

### Post by ActionParsnip on 2020-07-12
You don't have to use the Gnome desktop. It's not mandatory. Snuff around for a solution. KDE may do what you need, or LXDE, or an application you can run in those....

---

### Post by antenac on 2020-07-13
Well, I have to say it was easy achieve my goal from the Files settings. I just had to select on Behavior option, symbolic links.
Before this discovery, I proved with Gnome-pie and it was great. I recomend it. So, Gnome keeps in race :arrow:
Thanks to all again.

---

