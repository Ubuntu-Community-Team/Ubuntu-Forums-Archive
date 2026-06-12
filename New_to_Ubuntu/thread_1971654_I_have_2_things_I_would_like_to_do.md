---
title: "I have 2 things I would like to do"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by dmobley88 on 2012-05-02
The first thing I would like to do is - to install wanda the fish in ubuntu 12.04. 


The second thing I would like to do is - to change the predefined "Username" text and "Password" text at the login screen.

I have the Guest account disabled.
I have disabled the users list.
I have turned off the automatic wallpaper transitioning.
I have set a seperate wallpaper for the login screen.
Now my login screen has me enter username AND password. This is fine... 

What I'm trying to do is change the text in the text box from [Username] to something of my choosing. same with [Password]. if anyone can help with this, I would be most grateful. Thank you for your time and consideration. Have a wonderful day. :)

---

### Post by kostkon on 2012-05-02
> **dmobley88 said:**
> The first thing I would like to do is - to install wanda the fish in ubuntu 12.04.
Check [here]("http://www.omgubuntu.co.uk/2011/11/catch-of-the-day-wanda-the-fish-indicator-applet/"). Just add the PPA in your software sources list (instructions on how to add it can be found on the [PPA's page]("https://launchpad.net/~dylanmccall/+archive/indicator-fish"), for example), or download the deb file directly. For 12.04, the files are:
[32bit]("https://launchpad.net/~dylanmccall/+archive/indicator-fish/+files/indicator-fish_1.08-0~19~precise1_i386.deb")
[64bit]("https://launchpad.net/~dylanmccall/+archive/indicator-fish/+files/indicator-fish_1.08-0~19~precise1_amd64.deb")

---

### Post by billyseth on 2012-05-02
I'm sure all the text strings are hidden deep in some language pack files, I think it would be very difficult to change those

---

### Post by dmobley88 on 2012-05-14
> **billyseth said:**
> I'm sure all the text strings are hidden deep in some language pack files, I think it would be very difficult to change those

I was able to download the unitygreeter .tar.gz file, and un-pack it. 
I then went into unitygreeter.vala file

I changed both username strings in quoted text
I changed both password strings in quotes
I then re-packaged the unity greeter
I installed unity-greeter.deb

it works. :)

---

### Post by dmobley88 on 2012-05-14
> **kostkon said:**
> Check [here]("http://www.omgubuntu.co.uk/2011/11/catch-of-the-day-wanda-the-fish-indicator-applet/"). Just add the PPA in your software sources list (instructions on how to add it can be found on the [PPA's page]("https://launchpad.net/%7Edylanmccall/+archive/indicator-fish"), for example), or download the deb file directly. For 12.04, the files are:
[32bit]("https://launchpad.net/%7Edylanmccall/+archive/indicator-fish/+files/indicator-fish_1.08-0%7E19%7Eprecise1_i386.deb")
[64bit]("https://launchpad.net/%7Edylanmccall/+archive/indicator-fish/+files/indicator-fish_1.08-0%7E19%7Eprecise1_amd64.deb")


Thank you so much.... I missed wanda. :)

---

### Post by mörgæs on 2012-05-14
Good, please mark the thread 'solved'.

---

### Post by dmobley88 on 2012-05-15
interesting you should ask that in your "Signiture" because, well... ubuntu is the first distro of linux I have ever used.... I have used BT and have it installed, but I barely use it....

---

### Post by mörgæs on 2012-05-15
Then a nice surprise is awaiting you, when you try the other Buntus :-)

A thread is marked solved using 'thread tools' in the top right corner.

---

### Post by Face-Ache on 2012-05-15
> **mörgæs said:**
> Then a nice surprise is awaiting you, when you try the other Buntus :-)

Why? I'm curious to know!  :)

Ubuntu 11.10. Fedora 15 and OpenSUSE were distros included with a PC magazine disc that i bought recently, and i went with Ubuntu because the magazine said it was the easiest to install, and had better hardware support in terms of drivers straight 'out of the box'.

I've thought about Kubuntu and Xubuntu, but i'm quite happy with Ubuntu - what are these nice surprises you speak of?

---

### Post by mörgæs on 2012-05-16
Hardware support is the same for all members of the Buntu family. The difference is the desktop environment.

It's all a matter of taste - you can see some samples at Youtube. I'm just encouraging people to try more than one solution.

---

### Post by Face-Ache on 2012-05-16
So they have quite different desktops? That's cool, i might try a couple out, maybe in VirtualBox or USB installs, see if i like any more than Ubuntu  :)

Thanks!

---

### Post by dmobley88 on 2012-05-16
> **Face-Ache said:**
> So they have quite different desktops? That's cool, i might try a couple out, maybe in VirtualBox or USB installs, see if i like any more than Ubuntu  :)

Thanks!

launch a terminal

type sudo apt-get install lxde 

or type sudo apt-get install kde

or type sudo apt-get install gnome

....

---

