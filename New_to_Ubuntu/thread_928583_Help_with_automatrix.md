---
title: "Help with automatrix"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by KatanaMonk on 2008-09-24
Im trying to open a .rar archeive, and It seems that unrar-free wont work right, so I did a bit of digging and came up with automatrix. However, I used some online guides for installing automatrix, but it says something about the website not being found.  I then go to [www.automatrix.com](www.automatrix.com), and find out it has a new host or whatever.  My problem, I need to open a rar archeive and don't know how to on ubuntu.

---

### Post by Paqman on 2008-09-24
Automatix is an old obsolete piece of software designed to deal with some of the shortcomings of older versions of Ubuntu. It's not needed (and in fact, is strongly advised against) on recent versions.

Most of the things Automatix did (such as install an unrar tool) can be achieved by installing a single package: [ubuntu-restricted-extras](apt:ubuntu-restricted-extras) (click to install)

---

### Post by KatanaMonk on 2008-09-24
Thank you, but how do I get to it using the terminal?

---

### Post by kpkeerthi on 2008-09-24
> **KatanaMonk said:**
> Thank you, but how do I get to it using the terminal?

Enter this command:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by KatanaMonk on 2008-09-24
Im going to assume that the below code is a problem?
```


E: Type '“deb' is not known on line 35 in source list /etc/apt/sources.list
E: The list of sources could not be read.

```

---

### Post by mevets on 2008-09-24
You might have been messing around with your /etc/apt/sources.list. You might only need to refresh your list:
```

sudo apt-get update

```
Or edit that file and fixed or remove the line you were messing with:
```

sudo gedit /etc/apt/sources.list

```

---

### Post by Paqman on 2008-09-24
> **mevets said:**
> 
```

sudo gedit /etc/apt/sources.list

```

Small point; you should actually use gksu for GUI apps like gedit, instead of sudo. So:
```

gksu gedit /etc/apt/sources.list

```

---

### Post by KatanaMonk on 2008-09-24
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ubuntu-restricted-extras

```

I think there is a problem

---

### Post by Paqman on 2008-09-24
> **KatanaMonk said:**
> ```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ubuntu-restricted-extras

```

I think there is a problem

Do you have the multiverse repo enabled? Go to System > Admin > Software sources, make sure it's checked then try again with:
```

sudo apt-get update && sudo apt-get install ubuntu-restricted-extras

```

---

### Post by KatanaMonk on 2008-09-24
I don't understand, do you mean in the root filesystem?

---

### Post by Bölvaður on 2008-09-24
no, he is refering to broaden what you can see in synaptic or apt-get.
read his instructions carefully, I think they are clear when you do them step by step and read slowly.

*added*
he is talking about the gnome pannel (the thing on top of the screen)

---

### Post by KatanaMonk on 2008-09-24
> Do you have the multiverse repo enabled? Go to System > Admin > Software sources, make sure it's checked then try again with:

I don't see the "Software sources", would it have anything to do with my computer running dapper drake?

---

### Post by Kevbert on 2008-09-24
Check what software sources you have enabled.  Go to System - Administration - Software Sources and check that all four boxes under the Ubuntu Software Tab are ticked, then click on Close. Now go to System - Administration - Synaptic Package Manager and click on Search.  Enter ubuntu-restricted extras in the Search box and click on Search.  The package should be displayed.  Now right-click on the box next to your package, select Mark for Installation and then click on Apply.  If this fails please post back.

---

### Post by Bölvaður on 2008-09-24
perhaps it is different in dapper drake.
You can access that program also from within Synaptic.

open synaptic and find.

Settings &#8594; Repositories.

That is the Software Sources we have been talking about.
There you can check in evey box except the cd one, Multiverse one is a requirement.

---

### Post by philinux on 2008-09-24
Is there a reason you're sticking with Dapper. There is a direct upgrade path to Hardy, which is also a LTS release. 

What are your pc specs?

---

### Post by Sef on 2008-09-24
>      Quote:
                                                                      Originally Posted by **mevets**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5846276#post5846276")                 
                 [I]     Code:
     sudo gedit /etc/apt/sources.list 
[/I]
                                 
Small point; you should actually use gksu for GUI apps like gedit, instead of sudo. So:
     Code:
     gksu gedit /etc/apt/sources.list 

Actually the correct code is

```
gksudo gedit /etc/apt/sources.list
```Once gedit opens here's how to find the line easier:

Edit > Preferences > View > check the box below Line Numbering

then once you find the line comment it out.   To comment it out, put a # before it.

Note: When using a graphical appliation in root, you need either gksudo for Ubuntu and Xubuntu or  kdesu for Kubuntu.  For terminal applications in root, sudo is used for all three.

---

### Post by Paqman on 2008-09-24
> **KatanaMonk said:**
>  would it have anything to do with my computer running dapper drake?

Yes, it would. Dapper is a very old version, and doesn't seem to have ubuntu-restricted-extras in it's repos.

Just grab [unrar](apt:unrar) on it's own and you should be alright.

---

### Post by AndyCooll on 2008-09-24
Also there are two versions of unrar. The unrar-free is as it implies completely "free", however it doesn't open all rar files. If that's what you'll be needing you'll want plain unrar.

:cool:

---

### Post by KatanaMonk on 2008-09-24
I started the update before I left for school, It will update to hardy heron.

---

### Post by KatanaMonk on 2008-09-24
> **Paqman said:**
> Do you have the multiverse repo enabled? Go to System > Admin > Software sources, make sure it's checked then try again with:
```

sudo apt-get update && sudo apt-get install ubuntu-restricted-extras

```

After I got home, it finished the intallation of hardy heron, and now it works thanks.

---

### Post by billgoldberg on 2008-09-24
> **KatanaMonk said:**
> Im trying to open a .rar archeive, and It seems that unrar-free wont work right, so I did a bit of digging and came up with automatrix. However, I used some online guides for installing automatrix, but it says something about the website not being found.  I then go to [www.automatrix.com](www.automatrix.com), and find out it has a new host or whatever.  My problem, I need to open a rar archeive and don't know how to on ubuntu.

Install 

```
p7zip-full
```

In the rare case it shouldn't be able to unrar the archive, use winrar in wine. It works great.

---

### Post by crjackson on 2008-09-24
ignore this post.

---

