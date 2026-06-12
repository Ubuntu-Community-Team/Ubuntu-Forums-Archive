---
title: "when creating .iso of svcd it copied 600k then stops with no error"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by stinger30au on 2008-05-30
i have a svcd disc i made and im trying to make an .iso file from it.
i have used Brasero to create an image of it to hda and it says it is copying and the cd light flashes for a while and it says it has finished. when i check the file it is only 600k long.

i have also installed the cd in to the drive and let ubuntu mount it and then right click on it and click on copy cd. i can then tel it to make a .iso file and tell it to save the the hard drive and  agian with the same results.

i have tried using k3b to create the iso, but it fails as it says it wont handle data tracks. 

any ideas????

---

### Post by Mentem on 2008-05-30
When I have trouble with this kinds of things, I usually just copy everything from the cd to my harddrive and then make an iso from the contents of the folder where I copied them into. 

It seems to be quite a bit more error proof, as burning "in the fly" is quite dependant on the read buffer.

---

### Post by Efros on 2008-05-30
I think this is something to do with the structure of an SVCD, I think they use multiple sessions, [http://osdir.com/ml/video.mjpeg.devel/2004-06/msg00024.html]("http://osdir.com/ml/video.mjpeg.devel/2004-06/msg00024.html")

---

