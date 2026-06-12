---
title: "Packaging newer versions of software and &quot;Apps Available for Download&quot;"
date: 2013-09-27
forum: Packaging and Compiling Programs
---

### Post by ragtag on 2013-09-27
I'm making updated packages of graphics software like Gimp and Krita for Ubuntu 12.04 LTS, and am having some trouble getting them to show correctly in the Dash. The Dash will still show Gimp in Apps Available for Download.

Is there any information on how Ubuntu implements apps available for download, and how, after installing my updated version of Gimp, I can get that to show in the Dash instead. I'm assuming it's a .desktop file somewhere, but I would like to figure out the correct way to do this. I've created a .desktop file for my version of Gimp, but it's not taking over for the other one in the Dash.

Thanks in advance.

---

### Post by ragtag on 2013-09-29
Since I'm not getting any replies, I'm just going to answer this myself. :)

I seems like both the Dash and Software Center look in /usr/share/app-install/desktop for "Apps Available to Download". 

In that directory there are a number of .desktop files with X-AppInstall-Package=packageName

So in my case, where I've been compiling two different versions of Krita (stable and development version), making .deb's and adding them to my little in-house repos, I was still getting the three krita:kde4_krita.desktop files showing up in Dash (no idea why 12.04 has three krita's there, they all install the same package).

So I guess my solution is to remove the .desktops file for krita that are there, and create my own, along with icons, then running:

 sudo update-app-install

There are some more details on it here [here]("https://wiki.edubuntu.org/AddRemoveForDevelopers").

---

### Post by ragtag on 2013-09-29
Just a minor update. "sudo update-app-install" is not available in 12.04, but "sudo update-software-center" works instead. It updates the data shown in the Software Center.

After logging in and out again, what was shown in the Dash was updated too. I would prefer to find a way to force the Dash to update, but I can live with logging in and out. :)

---

