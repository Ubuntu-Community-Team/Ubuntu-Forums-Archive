---
title: "Platform independent Python packages"
date: 2009-01-20
forum: Packaging and Compiling Programs
---

### Post by jonny on 2009-01-20
Following some of the how-tos that lurk in the darker corners of the net, I've been trying to build my first ever debian package from a small python program that I've written.  I've successfully built a package that seems to work, but I can't get it to be for the 'all' architecture type.

I've tried moving everything in my rules file from binary-arch into binary-indep - as suggested in the Debian documentation - but to no avail.  There's no reference to i386 in any of the files in my debian folder but dpkg-buildpackage keeps going back to it.

What's the trick that I'm missing?

---

### Post by jonny on 2009-01-20
Sorted.  I must have simply had a dodgy character in one of my files because when I re-pasted them from my crib sheets, a xxx_all.deb file popped out.

After hours of tearing my hair out and scouring the web. Aaaargh!

---

### Post by giuspen on 2009-01-23
I'm also trying to build a simple debian package from my pygtk application but, following the instructions [here]("http://showmedo.com/videos/video?name=linuxJensMakingDeb"), I reach a debian package which creates the directories but nots the files inside.
Can u tell me please if u used a similar procedure and if u found similar problems? Maybe u can give some advice on the correct procedure to follow?
Thanks, Regards.

---

### Post by giuspen on 2009-01-30
Ok I finally was able to create my package and publish it, I advice [this guide]("http://tldp.org/HOWTO/Debian-Binary-Package-Building-HOWTO/") over all tutorials/howtos found in the network.

---

