---
title: "How does this Mythbuntu thing work?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by jasontu on 2008-06-10
One last newb question for the hour...

I am looking to transfer some VHS tapes to DVD.  Would Mythbuntu be a good tool for that?  What is it exactly?  Do/can I run it within Ubuntu or does it have to be its own separate partition and thing?

What would be the best video capture card for it?  Am I totally barking up the wrong tree here?

Thanks!

---

### Post by jbrown96 on 2008-06-10
Mythbuntu would be a good choice. Hook your VCR up via coaxial to a PVR card on the box and you should be set to record. 
Mythbuntu is basically an awesome mediacenter pc. It can record TV shows (you need to have a PVR card), and all kinds of other cool stuff. This would probably be the easiest way to go about it. There are tons of good guides out there, so just search for one on how to set it up and the hardware to buy.

---

### Post by jasontu on 2008-06-11
Does it need its own partition?

Where would be a good place to search for guides?

Thank you

---

### Post by Duck2006 on 2008-06-11
Try this search engine.

[http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

---

### Post by OffAxis on 2008-06-11
> Does it need its own partition?
No, it's not necessary (but you can if you want). It's a metapackage (with mythtv as the primary component).
You can install it via synaptic or with
```
sudo aptitude install mythbuntu
```

think of it as another desktop, with super-media capabilities.

HOWEVER, if all you're doing is transferring VHS tapes over, you can just do a capture off a TV capture card without installing all the overhead.
You can view an incoming stream with
```
mplayer /dev/video0
```

where video0 is your capture card.
And you can do the capture with
```
cat /dev/video0 > file.mpg
```


The Hauppaugge PVR-150 is probably the most widely used card for media centers. 
If you get one, make sure it actually IS a 150 (hauppaugge packaged a different card in some of the 150 boxes, one that doesn't work with linux. Look at the mythtv.org wiki for more info. [http://mythtv.org/wiki/index.php/Main_Page]("http://mythtv.org/wiki/index.php/Main_Page"))

---

