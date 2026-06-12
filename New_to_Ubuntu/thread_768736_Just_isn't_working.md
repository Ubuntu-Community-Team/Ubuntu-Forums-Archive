---
title: "Just isn't working"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by falonyn on 2008-04-26
Having a lot of issues here with this installation of Kubuntu. i installed Kubuntu 7.10 Gutsy Gibbon on my brother's desktop PC and then upgraded to Hardy Heron. Everything seemed to be fine, but I have had major issues with getting compizfusion to work. I have a thread about this problem already, however now I am experiencing something far more critical. Every time I try to install anything through the package manager or add/remove I get this . . . 

*There was an error committing changes. Possibly there was a problem downloading packages or the commit would break packages.*


What is going on? Please, someone help. This is the first time seriously working with Kubuntu, and I have never run into problems like this with Ubuntu. The only reason I switched him to Kubuntu is that there were some issues with his Ubuntu installation. Things like it randomly crashing, it logging him off when he tried to minimize a window.

He was told that some of those issues could be caused by Ubuntu not having an integrated GUI while Kubuntu does. I think he will really like Kubuntu, but some of these problems are enough to make him just want to switch back to Windows XP MCE.

---

### Post by Michael.Godawski on 2008-04-26
When did the installation start? Any hints?

I am not the expert concerning Kubuntu, but did you have added some additional sources to the sources list?

What happens if you run:

```
sudo apt-get update
sudo apt-get upgrade
sudo dpkg --configure -a
```

---

### Post by falonyn on 2008-04-26
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.

I installed yesterday with a copy of 7.10. I was downloading 8.04, but he didn't want to wait and said he would just upgrade it.



. . . I ran 'sudo apt-get -f install' 

and completed that install and now it seems I can install through the package manager. I hope now I can fix the issue with compizfusion. I have an eVGA nVidia Geforce 6600GT AGP 8x 128mb GDDR2 graphics card. I currently have the 'legacy' drivers installed, but was thinking about switching them to the regular ones. Would this be a good idea?

---

