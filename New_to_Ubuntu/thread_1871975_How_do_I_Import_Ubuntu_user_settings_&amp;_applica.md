---
title: "How do I Import Ubuntu user settings &amp; applications into Xubuntu"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by williamgunn on 2011-10-29
I used to run Ubuntu with Gnome and I thought I would try the upgrade to 11.10. The upgrade left me unable to get to a desktop or even a terminal in recovery mode. On someone's advice I decided to try installing xubuntu over the top, which went just fine except that during the install process, it said there was a problem restoring my applications. I was then prompted to create a new user, which I did, and as expected, it was a completely fresh install. However, ls /home shows both william (the new user) and williamgunn (the old user, with all my files and data intact. I like xubuntu & xfce and I think I'll stay here, but ..

Is there some easy way to restore all the applications I used to have installed? What would happen if I copied the contents of /home/williamgunn/ into /home/william?

Thanks for any help with this n00b question.

---

### Post by mike555 on 2011-10-29
You probably should only copy things like .Thunderbird , .Mozilla and your pictures, music & documents .
   copying the whole folder might confuse the new operating system.

 You should be careful installing apps , they might drag in Gnome stuff and mess things up........ try the apps that come with Xubuntu they might surprise you.

---

### Post by williamgunn on 2011-10-30
Thanks, Mike. I was more thinking about stuff like Dropbox and Synergy. Since I installed everything through the updates manager, I was hoping that I could copy the repositories over and do something like apt-get update based on my old information and update from there.

Any ideas?

---

### Post by mike555 on 2011-10-30
Just install Dropbox ,then sign on with your user name and password, it will update for you (although Thunar doesn't show the animations )....         
   be careful copying repositories some might be only for Gnome not xfce.

---

### Post by williamgunn on 2011-10-30
Thanks again, Mike. How would I tell if a repository is for Gnome and not Xfce? Where would I find the repositories to copy them?

I realize that there's differences between Unity & Gnome & Xfce, but the underlying system isn't that different & there is a migration process, because the automatic installer tried to carry it out. So maybe I'm just not asking the right questions.

Is there some way to register the applications that I had installed via the update manager in my old ubuntu install with the update manager in xubuntu, so that I could then just run the updater and it would fetch the correct files & dependencies for my current install?

---

### Post by mike555 on 2011-11-01
If the PPA's program is a program that isn't installed by default in Xubuntu ,just open package manager and find the program ,mark to install but before installing check the things it will install .......... if it installs a lot of Gnome stuff or worse KDE stuff you might not want to install it ,so unmark it.
   better to use only fxce stuff if you can.

---

### Post by alco75 on 2011-11-01
I found [this]("http://www.psychocats.net/ubuntu/purexfce") really useful after upgrading Ubuntu Natty to Xubuntu Oneiric.

---

### Post by williamgunn on 2011-11-02
> **mike555 said:**
> If the PPA's program is a program that isn't installed by default in Xubuntu ,just open package manager and find the program ,mark to install but before installing check the things it will install .......... if it installs a lot of Gnome stuff or worse KDE stuff you might not want to install it ,so unmark it.
   better to use only fxce stuff if you can.

So the problem is that I don't see anything in the package manager. I had added several PPAs for applications and none of that is showing up in package manager.

---

