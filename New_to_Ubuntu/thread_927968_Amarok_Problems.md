---
title: "Amarok Problems"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by susanpenter on 2008-09-23
I am having real problems with Amarok.  It has recognised my ipod and the files already on it - which I though would be the bigger problem - however it won't let me rip my cds.  It will recognise and play them but the option to copy the tracks is greyed out and there is no menu item to rip them.  I ripped one with Rhythmbox music player and it added it into the database and yet when I open Amarok it can't find the album (they both use the same music folder on my external hard disk) and Rhythmbox will play the tracks on my ipod but not copy them from the hard drive to the ipod.

Any ideas anyone of how I can do the whole process with one prog (I hoped it would be Amarok)

Thanks

Susan

---

### Post by LowSky on 2008-09-23
what version iPod? What verision of Ubuntu/Amorok? What database did you set up for Amorok?

Have you tried exaile?

---

### Post by susanpenter on 2008-09-23
Sorry, it is an ipod Classic 80Gb, Ubuntu 8.04 up to date, Amarok 1.4.9.1 (through the package manager) and SQ Lite.

I haven't tried exaile, I'll go and look for it in Synaptic now.

Hope that clarifies

---

### Post by SuperSonic4 on 2008-09-23
I think it is because K3B embeds itself in amarok and it is the former that rips a CD rather than the latter. I think soundjuicer would be a better ripping option for ubuntu ```
sudo apt-get install sound-juicer
```

If Amarok does not spot new music check you have *Scan Recursively* and then *Tools -> Rescan collection* and look then

---

### Post by susanpenter on 2008-09-23
I have checked in Synaptic and I already have Sound Juicer installed although it is not appearing in my applications menu bar.

I have tried Exaile and it won't mount my ipod even with the correct plugin enabled

---

### Post by susanpenter on 2008-09-23
I have now got Sound Juicer working, the problem is that it is rippong in Ogg so I need to use yet another program to transfer this to mp3, maybe if I change to ripping in wav Amarok will read this?

---

### Post by markbuntu on 2008-09-23
If you get the

ubuntu-restricted-extras

package with synaptic you will be able to rip to mp3 with Sound Juicer.

---

