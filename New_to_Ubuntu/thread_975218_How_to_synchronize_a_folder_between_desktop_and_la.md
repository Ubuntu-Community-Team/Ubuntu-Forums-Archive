---
title: "How to synchronize a folder between desktop and laptop?"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by legolas_w on 2008-11-08
Hi
Thank you for reading my post
I have some folder sin my desktop computer which I need to keep them synchronized with the same set of folders in my laptop.

I usually do some work in the office and should continue them in home, so before I go to work I should synchronize the folders and when I come back from office i should perform the synchronization again.



Thanks.

---

### Post by Ahunt on 2008-11-08
We have two Unbuntu PCs and keep all our files synchronized between them for back-up and so that they can be worked on on either PC.

Our method may not be what you are looking for however as we manually sych them by copying the most recently edited files or folders from one PC to a USB drive and then move it to the other PC and copy them there to overwrite the old files. 

It does work, is simple and keeps both PCs otherwise isolated from each other for security.

---

### Post by bodhi.zazen on 2008-11-08
IMO the best option is rsync

---

### Post by kaptengu on 2008-11-08
You might want to take a look at Unison.
```
sudo apt-get install unison-gtk
```

---

### Post by mapes12 on 2008-11-09
A simple way to connect up your laptop and desktop is to use openssh.Have a look at SpaceTeddy's post: [http://ubuntuforums.org/showthread.php?t=79330](http://ubuntuforums.org/showthread.php?t=79330)

Then simply copy over the folders from one machine to the other or use a backup routine: [http://theaddicted.wordpress.com/2008/05/12/how-to-backup-ubuntu/](http://theaddicted.wordpress.com/2008/05/12/how-to-backup-ubuntu/)

---

### Post by roger_1960 on 2008-11-09
Hi

Have a look at [www.getdropbox.com](www.getdropbox.com)  This app is really really good and works across the web and across windows, Mac and linux machines.  And its free!

---

### Post by hyper_ch on 2008-11-09
you should use sshfs to mount the folder from the desktop on the laptop at work... then you'd only have one folder.

---

### Post by Rocko262c on 2008-11-14
Can this program duplicate filenames given in Japanese or other such launguages?

---

### Post by Vadi on 2008-11-14
I'd recommend Dropbox also

---

