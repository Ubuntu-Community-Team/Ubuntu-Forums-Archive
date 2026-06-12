---
title: "Mounting .img files"
date: 2006-06-29
forum: Outdated Tutorials &amp; Tips
---

### Post by PoisoN2003 on 2006-06-29
This is my first tutorial, this tutorial will teach u how to mount .IMG files.

First u need to have these things
a rpm version of ccd2iso u can get it here
```
wget http://rarewares.org/debian/packages/unstable/ccd2iso_0.2-0.1_i386.deb
```


Now that we have those things we can start

Lets install we do
```
sudo dpkg -i ccd2iso-0.2-1.i386.deb
```

Now we are going to convert the img to iso using this application

```
sudo ccd2iso /place/of/the/img.img /place/of/the/wanna/be/iso.iso
```

Please tell me if im missing anything 
I added that link provided by same

After some testing this i realized that when i try to open the iso i get it gives me an error im trying to figure out how to fix that but if someone else knows ill be glad to fix my tutorial

What does work well is running UltraISO on cedega u can get the trial of their site and when u run it with cedega i noticed that the trial is the same thing as the full version so u can convert any size file to iso (bin,img,ccd,anything)

---

### Post by Sam on 2006-06-30
Use [this package](http://rarewares.org/debian/packages/unstable/ccd2iso_0.2-0.1_i386.deb) instead, this one works (although it's an older version).

---

### Post by PoisoN2003 on 2006-06-30
thx i added that file

---

### Post by Norberg on 2006-07-24
It is easier to just rename the file from filname.img to filname.iso and it works grate.

---

### Post by dethree on 2006-07-29
okae, I installed the program from the link, try to convert .img file with ```
sudo ccd2iso file.img file.iso
``` I get 'Segmentation fault', I have no idea why it says that.

---

### Post by ykram on 2006-07-29
Can be done easily from command line and browsable if permissions are set:

mount -o loop -t iso9660 filename.iso /mnt/iso

---

### Post by fakie_flip on 2007-04-15
Grab the newest ccd2iso from here.
[http://packages.debian.org/unstable/otherosfs/ccd2iso](http://packages.debian.org/unstable/otherosfs/ccd2iso)

---

### Post by ifraser on 2010-03-15
Thanks for updated link

---

### Post by krychek on 2011-03-17
Here it is:

[http://www.ubuntugeek.com/ccd2iso-convert-clonecd-disc-image-img-format-to-standard-iso-iso.html](http://www.ubuntugeek.com/ccd2iso-convert-clonecd-disc-image-img-format-to-standard-iso-iso.html)

---

