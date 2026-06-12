---
title: "Lubuntu - biggest gripe. PCManFM bad. Dolphin good."
date: 2012-08-09
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-08-09
My system is Ubuntu 11.10. Lubuntu's native file manager PCManFM 0.9.9 is soooo slow. I've given up using it. Whenever I want to open a file, other than from CLI, I open the Dolphin file manager instead.

I NEVER try to open a file from within an application because PCManFM takes ages to work and I don't seem to be able to make Dolphin the default from within an application. Maybe Dolphin is not designed that way.

I run lubuntu because I have a low spec system. Any help would be greatly appreciated.

---

### Post by vasa1 on 2012-08-09
> **Kevin McCready said:**
> My system is Ubuntu 11.10. Lubuntu's native file manager PCManFM 0.9.9 is soooo slow. I've given up using it. Whenever I want to open a file, other than from CLI, I open the Dolphin file manager instead.

I NEVER try to open a file from within an application because PCManFM takes ages to work and I don't seem to be able to make Dolphin the default from within an application. Maybe Dolphin is not designed that way.

I run lubuntu because I have **a low spec system**. Any help would be greatly appreciated.
Interesting!
Anyway, FWIW, caveat emptor, and whatever else applies: [http://askubuntu.com/questions/84929/how-to-set-up-dolphin-as-default-file-manager](http://askubuntu.com/questions/84929/how-to-set-up-dolphin-as-default-file-manager)

---

### Post by Kevin McCready on 2012-08-10
what would be the next choice then for a lightweight system with a fast filemanager (which I thought was one of the strengths of linux)?

---

### Post by Kalanac on 2012-08-10
xubuntu?  That uses XFCE and I believe XFCE's default file manager is Thunar.  I used it many moons ago and it seemed pretty sound, not sure how it will run on a low end system, but XFCE is considered a lightweight desktop environment, so you might have good results :)

---

### Post by vasa1 on 2012-08-10
> **Kevin McCready said:**
> what would be the next choice then for a lightweight system with a fast filemanager (which I thought was one of the strengths of linux)?

Well, it's going to be difficult to suggest something. You're having problems with what most people find a very light FM which is why lubuntu uses it.

---

### Post by Elfy on 2012-08-10
Nothing to stop you installing thunar in lubuntu.

I'd wonder though if there is a problem causing pcmanfm to act like it does.

---

### Post by Peripheral Visionary on 2012-08-10
> **Elfy said:**
> Nothing to stop you installing thunar in lubuntu.

I'd wonder though if there is a problem causing pcmanfm to act like it does.

Indeed. I always install PCManFM in Xubuntu because I love PCManFM and find it a lot quicker and easier on my computer than Thunar (the Xfce file manager and default in Xubuntu).

I'd be looking at purging and reinstalling PCManFM if I were you. Seems like something's out of whack with that app *on your computer*, since it's awesome just about everywhere else.

---

### Post by Rodney9 on 2012-08-10
[http://www.linuxlinks.com/article/20081224191928555/FileManagers.html](http://www.linuxlinks.com/article/20081224191928555/FileManagers.html)

---

### Post by Kevin McCready on 2012-08-10
Thanks everyone. I don't know if I can uninstall the reinstall PCManFM because it is an essential part of the system. I thought about that route before but was told it would be very risky.

The other file managers are going to leave me with the same problem - that they won't be the default file manager which is automatically used by programs when you open files from within them. Unless there is an easy way to make them the default file manager (the link above showed it was not feasible with Dolphin for example).

My Documents take up about 25GiB 56,000 files in 2000 sub-folders. Even doing a ls -tl in a terminal makes the system run hot.

---

### Post by Rex Bouwense on 2012-08-10
Try restarting PCMan

```
  pcmanfm --desktop --profile=LXDE
```.

---

