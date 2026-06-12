---
title: "How to find which package conflicts?"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by pudgy parrot on 2008-07-16
I'd like to install Rythmbox on my Xubuntu, but I cant check the box next to it.  I get an error saying that it conflicts with another package, and that I should use synaptic to resolve. 

So how do I do that?  I played around in synaptic for a few minutes, but couldn't determine which package would cause the conflict.

I also cant remove amarok, I tried, thinking that would be the conflict.  The error says that other programs rely on it.

---

### Post by adamogardner on 2008-07-16
go into synaptic and click on what you don't want and hit mark for complete removal. then hit aplly button on top toolbar. voila?  how far can you get in that?

---

### Post by pudgy parrot on 2008-07-16
But how do I know what I dont want?  I dont want to go removing programs all willy nilly.

I guess my real question is "what conflicts with rythmbox?"

---

### Post by adamogardner on 2008-07-16
oh you don't know which package/s have you dump...hmm do you have apt-get?  that will sort things out.

---

### Post by pudgy parrot on 2008-07-16
hmmm, dont see that one in the add/remove applications list.  Is the official name different?

---

### Post by nowshining on 2008-07-16
try sudo apt-get -f install and or audo apt-get install -f

or if all else fails

sudo apt-get clean

to clear ur download cache. :)

---

### Post by Dani Filth on 2008-07-16
apt is the package manager for the *buntu family.

Can you try
> sudo apt-get install rhythmbox

As for removing AmaroK
> sudo apt-get remove amarok

---

### Post by pudgy parrot on 2008-07-16
> **Dani Filth said:**
> apt is the package manager for the *buntu family.

Can you try


As for removing AmaroK

That did it thanks.  My next problem is taht when I start Rhythmbox I get 2 errors stating that plugins (magnatune and jamendo) cannot be activated.  How do I resolve that?

---

### Post by nowshining on 2008-07-17
are these errors on every startup?

---

