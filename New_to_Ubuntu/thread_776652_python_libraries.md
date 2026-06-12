---
title: "python libraries"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by henok on 2008-04-30
I was just testing out some python codes to manipulate images and run into a couple of problems. 

I first had the following error: 
```
ImportError: No module named Image
```

which I fixed by: 

```
sudo apt-get install python-imaging
```

then I had the following error: 

```
ImportError: No module named exif
```

I couldn't install the exif library like I did the imaging so I downloaded ```
python-exif-1.0.2-3.fc6.noarch.rpm
``` from the fedora project, converted it to a dpkg using alien and installed it using ```
dpkg -i python-exif_1.0.2-3.fc6_all.deb
```. When I searched for the file exif.py using find, the only copy was in ```
/usr/share/hplip/base/exif.py
``` even then, ```
import exif
``` returns the "No module name exif" error.  

My question is: is there some secret to installing python libraries?

---

### Post by thehada on 2008-06-22
It could be that the author of the application is talking about EXIF.py with you can download from SourceForge.net just put in "EXIF.py" in Google and you will find the download source.

That solved it for me but we could of course be talking about different things..
Hope that helps..

---

