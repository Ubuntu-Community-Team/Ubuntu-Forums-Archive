---
title: "Tunes"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Ryzekiel on 2008-11-12
How in god's name can I play my music library on ubuntu? My itunes library is on the windows partition. I tried installing itunes in wine (failed), amarok (didn't want to access the windows partition),  and finally songbird, which accessed my library, but doesn't want to play .m4a's. So, I tried to follow the instructions provided by songbird that would allow me to play these files: install gnonlin. So I tried to install that, but I need to install glib >= 2.6. And to install that I have to install pgkconfig which recommends that I have make v3.75, etc, etc. you can see where this is going...

I hadn't used any linux distribution before, so I got pretty little lost. does anyone out there have a recommendation for how to play my tunes on this machine?

---

### Post by sydbat on 2008-11-12
First you need to install the NTFS configuration tool (in System > Administration > Synaptic Package Manager) and run it. It should allow you to access your NTFS partitions. It will show up in Applications > System Tools menu.

You may also need ntfs-3g for read/write support.

From there, you should be able to access your NTFS drives and Amarok should be able to create a DB for your tunes.

---

### Post by chrisod on 2008-11-12
If they are encrypted .m4a files nothing on Linux will play them. You'll need to export the entire library to MP3 or OGG.

---

### Post by Paqman on 2008-11-12
> **Ryzekiel said:**
> My itunes library is

...probably locked with DRM (unless you paid extra for the tunes that are DRM-free)

**sydbat**: Ubuntu has had read/write for NTFS by default for a while now.

---

### Post by sydbat on 2008-11-12
> **Paqman said:**
> ...probably locked with DRM (unless you paid extra for the tunes that are DRM-free)

**sydbat**: Ubuntu has had read/write for NTFS by default for a while now.

I figured that...but just in case it had not been installed...I have found that sometimes things that should be installed are not...not sure why.

---

### Post by PierreDeKat on 2008-11-12
Yeah, my daughter had some trouble with her itunes/ipod after a computer crash. 

And supposedly the Apple mothership was keeping track of what music she had licensed, but no such luck. So she ended up losing something like $200 worth of music licenses.

No biggie. 

I just got her started with Audacity on Ubuntu and encouraged her to help herself to $200 worth of music from wherever she could scrounge it off the internet.

I thought that was fair.

---

