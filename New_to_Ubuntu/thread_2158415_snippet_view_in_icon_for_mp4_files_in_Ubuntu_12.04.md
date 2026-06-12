---
title: "snippet view in icon for mp4 files in Ubuntu 12.04 LTS."
date: 2013-06-28
forum: New to Ubuntu
---

### Post by ask_ on 2013-06-28
Hello , 

I have Ubuntu 12.04 LTS on one of my machines. I also have Lubuntu 13.04 on another system. In Lubuntu 13.04 , the icons for media files display a snippet from the media file , i.e it is one of a snapshot of the media content (I don't know the exact term for this hence using description , pardon me for the same).

Now in Ubuntu 12.04 , the mp4 file icons are displayed as a movie reel (which I guess is archetypal). Is there a way I can make these files display the icon as snippet/snapshot (or is that a feature exclusive for 13.04 onwards)? 
Note , that .mov file icons in Ubuntu 12.04 are in the 'snippet' view. So it's an issue with files other than .mov .


In Lubuntu , the default media player is GNome media player. While in Ubuntu 12.04 it is Movie Player. And currently , it doesn't have all codecs installed so I use the media files with VLC. Is it an issue of the default media player ?

Thanks.

---

### Post by Krytarik on 2013-06-29
> **ask_ said:**
> And currently , it doesn't have all codecs installed...
It's that - just make sure the metapackage "ubuntu-restricted-extras" is installed, and you should be good:
```
sudo apt-get install ubuntu-restricted-extras
```
Regards.

---

### Post by ask_ on 2013-07-12
> **Krytarik said:**
> It's that - just make sure the metapackage "ubuntu-restricted-extras" is installed, and you should be good:
```
sudo apt-get install ubuntu-restricted-extras
```
Regards.
Hey thanks , did just as you told and it the icons look like real gems now. Thanks.

---

