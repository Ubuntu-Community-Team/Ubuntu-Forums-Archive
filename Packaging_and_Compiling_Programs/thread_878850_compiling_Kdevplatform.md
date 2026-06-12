---
title: "compiling Kdevplatform"
date: 2008-08-03
forum: Packaging and Compiling Programs
---

### Post by gmclachl on 2008-08-03
I am trying to compile kdevelop4 and because of this have to also compile the kdevplatform. 

I am getting an error about Kross::Manager, which I think I have tracked back to the fact I don't have cpptoxml installed, so the pre-generated information may be out of sync. 

Anyway I can't seem to find much reference to cpptoxml and have no real idea how to install it. 


*Edit*
The error I am actually getting is 
/home/gmclachl/kdevplatform/kross/krossplugin.cpp:74: error: &#8216;class Kross::Manager&#8217; has no member named &#8216;setStrictTypesEnabled&#8217;

George

---

### Post by Vorian on 2008-08-03
> **gmclachl said:**
> I am trying to compile kdevelop4 and because of this have to also compile the kdevplatform. 

I am getting an error about Kross::Manager, which I think I have tracked back to the fact I don't have cpptoxml installed, so the pre-generated information may be out of sync. 

Anyway I can't seem to find much reference to cpptoxml and have no real idea how to install it. 


*Edit*
The error I am actually getting is 
/home/gmclachl/kdevplatform/kross/krossplugin.cpp:74: error: &#8216;class Kross::Manager&#8217; has no member named &#8216;setStrictTypesEnabled&#8217;

GeorgeYou'll need the latest builds from kdelibs, kdebase, kdepimlibs, and kdebindings (witch will have the latest cpptoxml) to compile kdevplatform

---

### Post by gmclachl on 2008-08-03
I was afraid of that. Ah well, I might give up on this just now. 

George

---

