---
title: "pdf viewer with good search feature"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by amyst on 2008-05-16
Do you know a good open source pdf reader that has a good search functionality? I'm using Evince currently, which can search a text string only sequentially through a document and can't search djvu. I am looking for a pdf viewer which can display ALL the matching strings in the document, so I can jump through the documents instead of having to go through the matching strings sequentially (like adobe reader).

---

### Post by dstin1 on 2008-05-16
Adobe does have a linux version it is in RPM format so I think you will have to use alien to install it. 

You could also search synaptic I am sure you will find somthing other than what is installed by default.

---

### Post by gg234 on 2008-05-16
try this application

sudo aptitude install evince

---

### Post by nirpius on 2008-05-16
> **gg234 said:**
> try this application

sudo aptitude install evince

I think this user's already using Evince (check post one)

---

### Post by Oldsoldier2003 on 2008-05-16
> **dstin1 said:**
> Adobe does have a linux version it is in RPM format so I think you will have to use alien to install it. 

You could also search synaptic I am sure you will find somthing other than what is installed by default.

Why would you ever want to use a rpm to install adobe reader? Using alien should always be a last resort because it can wreck your Ubuntu install.

---

### Post by amyst on 2008-05-16
> **Oldsoldier2003 said:**
> Why would you ever want to use a rpm to install adobe reader? Using alien should always be a last resort because it can wreck your Ubuntu install.

Thanks for the tip. I've been looking for an open source reader b/c I heard adobe reader occupy too much ram? What would be the proper way of installing adobe reader on Ubuntu? 

Alternatively, how can I perform efficient search of a string text in 900 page documents? The sequential search is rather slow.

---

### Post by Oldsoldier2003 on 2008-05-16
[http://www.adobe.com/products/acrobat/readstep2_allversions.html](http://www.adobe.com/products/acrobat/readstep2_allversions.html) get the .deb or the one of the tar versions. If you get the .deb you can just doubleclick it to install

---

### Post by amyst on 2008-05-16
Thanks everyone. I downloaded and installed adobe reader 8.0, with a very unfortunate side effect. Opening pdf document in firefox will default to adobe reader, instead of evince. How do I fix this?

I like evince except searching through 900 page documents.

---

### Post by Swatfoot on 2008-05-16
Go to edit -> prefrences--> applications in firefox should think you can choose default application for pdf there. just a guess im new to firefox

---

### Post by amyst on 2008-05-16
What I did was going to firefox -> edit -> preference -> content -> File Types. It produces a pop-up window which I am almost certain existed in an [COLOR="Red"]entirely different form[/COLOR] just an hour ago, while I was struggling with that annoying yellow-star icon next to the system clock). 

I'm going to install a.r. on a Hardy machine that I have, now I uninstalled it from Gutsy. 

About uninstall. I installed the a.r.8.1.2.deb from Adobe website, and the package appeared to have [COLOR="Red"]added itself [/COLOR]to Synaptics's list of packages under the name acro...-en. There was no UNINSTALL file. I uninstalled acro...-en in Synaptics, and the package removed itself from the list.

Very strange.

---

