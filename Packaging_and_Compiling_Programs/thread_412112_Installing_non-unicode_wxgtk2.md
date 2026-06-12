---
title: "Installing non-unicode wxgtk2"
date: 2007-04-17
forum: Packaging and Compiling Programs
---

### Post by simplyw00x on 2007-04-17
Rigs of Rods requires non-unicode versions of the wxgtk2 libs - how can I install these on Feisty? Can I ebuild all the packages? Is there and easier way? Can I install unicode and non-unicode versions alongside each other?

---

### Post by rcatman on 2007-06-19
I wish I knew too. I've been trying for about an hour to get the non-unicode versions.

---

### Post by rcatman on 2007-06-19
I successfully got Rigs of Rods up and running last night.

To install the non-unicode wxgtk2 you download the source code and compile it yourself.

Download the source code from [http://www.wxwidgets.org/](http://www.wxwidgets.org/)

RoR requires wxWidgets 2.6.4 wxGTK. Download it here: [http://prdownloads.sourceforge.net/wxwindows/wxGTK-2.6.4.tar.gz]("http://prdownloads.sourceforge.net/wxwindows/wxGTK-2.6.4.tar.gz")

Follow the directions in the README.LINUX file. 

After compiling there's a couple new directories. I copied the contents of the new lib folder into my /usr/lib folder. 

Rigs of Rods started right up. It's a bit slow on the lowest setting on my computer. I run a 1.7ghz AMD Athlon XP and a GeForce 3 Ti 200. It's a bit outdated but I'm sure a newer computer would run this great.

---

