---
title: "Ubuntu lock down"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by ibizatunes on 2008-05-21
Hello, 
A friend of mine is looking to set up a small network of about 8 PC, basically he want them almost dum terminal,

They JUST need internet, office, to open pdf’s, - THAT IT!

Looking at it, if he goes down the Microsoft route it will cost about £800 in licences etc

Quick few questions
He need to remove basically any application that does need to be on there, ie games, evolution, totem, etc etc

Users can’t change the desktop background
User can’t delete the menu bar, or change it!
Users can’t install
Basically user can’t do anything extra there not meant too!

Can this be done easily?

---

### Post by bluefrog on 2008-05-21
yes. (pessulus, sabayon, gconf-editor)

But you'd better use the 800 pounds in hiring someone who will set up the network, do the restriction as needed and do user's training.
(If you find the right guy/company, it will surely cost less than £800 and with the difference, you could even get a 6 month assistance plan)

---

### Post by jimv on 2008-05-21
Yes, all that can be done.  Don't know precisely how, but I think most of the privilege stuff is in the Users and Groups control panel and the Permissions tab on file/folder property windows.

He can remove all the extra programs using the Synaptic package manager.

---

### Post by Xiong Chiamiov on 2008-05-21
I don't have much (read any) experience with limited accounts in *buntu (and I don't use GNOME), but many of those things should be easily done by simply not giving users access to an account with root priviledges.  For things like the background and other things configured in the ~/.gnome2 directory, I *think* you could change the ownership of that folder to root, and deny write access (though give read) to others.  Don't take that for sure, though.

---

### Post by N.N. on 2008-05-21
Forum member elianthony has set up a very limited Ubuntu installation on a computer in the public library where he works. He has documented some of the steps he took to lock down the computer in the following guide: [http://ubuntuforums.org/showthread.php?t=707688](http://ubuntuforums.org/showthread.php?t=707688).

Removing applications should be as simple as using Synaptic, Add/remove, or, preferably, issuing aptitude from the command line. When removing programs such as evolution, totem, and so on, the package manager will alert you that it will remove the ubuntu-desktop and/or ubuntu-standard packages. It is perfectly safe to do so, cf. the following discussion: [http://ubuntuforums.org/archive/index.php/t-378140.html](http://ubuntuforums.org/archive/index.php/t-378140.html).

Be aware, though, that there seems to be a bug with the process of removing evolution. Several users have experienced that it breaks gnome-panel. If you experience that, simply re-install gnome-panel.

---

### Post by ibizatunes on 2008-05-21
Thanks NN, i think that example of lockdown in just want i needed to show him, 
Thanks for your help everyone!!

---

