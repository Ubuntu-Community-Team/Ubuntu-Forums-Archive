---
title: "APTonCD package list is blank"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-05-22
Basically I cleaned out all my installed packages and so I thought I would create an updated aptoncd iso.

When I ran aptoncd, it said 1.2gb. This seemed a bit excessive, upon looking through the list I found that a LOT of the packages were packages I had deleted. 

Reading up a little more I came across the fact that aptoncd basically takes a list of packages from the directory: /var/cache/apt/archives

So i used sudo apt-get clean to clean out the directory.

Now (ofcourse) there are no packages in aptoncd. How can I sort this out?

---

### Post by MaindotC on 2008-05-22
I'd never heard of aptoncd until now.  Looks like an easy way to create a backup image of my current installation in case I want to re-install.  You get a star for that :)

---

### Post by abhiroopb on 2008-05-22
hmmmm...Well at least I helped you out! But be careful when creating an iso, as it sometimes takes packages that have been uninstalled! So take a cursory look through the list!

---

### Post by MaindotC on 2008-05-22
I'm trying to re-create your issue.  I did the apt-get clean as well, so if aptoncd uses that /var/cache/apt/archives directory I'm just trying to find a way to re-populate it.  I did man apt-cache and there is an --installed option but I'm not sure how to get it to show.

---

### Post by sayakb on 2008-05-22
Well, I don't use AptOnCD.. plus, if you already have cleared out the /var/cache/apt/archives, you might not have anything left for the AptonCD to burn.. I generally copy all my packages after a clean install (which ofcourse, do not include upgrades) and later, I just browse to the folder and do:
```
sudo dpkg-i *.deb
```

---

### Post by abhiroopb on 2008-05-22
Hmmm thanks for the thoughts.

Basically the cache folder was taking up about 1.2gb of space and from whatever I read it wasn't exactly necessary and so I thought I'd recover the space. Also I didn't want to go manually through aptoncd deleting the packages I didn't want. So, I thought this would work!

That seems like a easy idea and this way you have a clean listing of all your packages. Where are they located?

I think Innovations menthod is the way to go as it doesn't require any unneccesary installs.

EDIT: just found that the location of all the deb files IS the same cache folder. So is there anyway to rebuild all of them?

---

