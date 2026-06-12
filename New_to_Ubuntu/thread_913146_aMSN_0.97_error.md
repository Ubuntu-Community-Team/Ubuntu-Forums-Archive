---
title: "aMSN 0.97 error"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Linux_noob616 on 2008-09-07
I just installed aMSN through the new autopackage system they have. But i keep getting an error every time i try to open it saying 
> "Loading TkCximage failed. This module is needed to run aMSN. Please complile aMSN first, instructions on how to compile are located in the file INSTALL"

so my questions is how do i. 
A.) fix this?
Or
B.) remove this aMSN and compile it from source?

---

### Post by billgoldberg on 2008-09-07
> **Linux_noob616 said:**
> I just installed aMSN through the new autopackage system they have. But i keep getting an error every time i try to open it saying 


so my questions is how do i. 
A.) fix this?
Or
B.) remove this aMSN and compile it from source?

I'm not sure what autopackage system you are referring to as I don't use aMSN (don't like how it looks).

Does it come up when you search for it in synaptic (system -> administration -> synaptic package manager)?

Remove it completely from there.

Is there a reason you don't install the one from the Ubuntu repo's (you can do that from synaptic)?

--

Note alternatives for aMSN: emesene, galaxium, ...

---

### Post by Linux_noob616 on 2008-09-07
Cause it's an older version. And it's something on their site. it's pretty much a graphical installer for it.

Said something about "3rd party application manager" to remove it, But i can't find it anywhere. I'm new to the major workings of Ubuntu.

---

### Post by Zalbor on 2008-09-07
The reason not to install the one in the ubuntu repos is that it's too old.
I don't know about autopackage, sorry. But try removing it (however it's done) and downloading the lastest version in a .deb file from getdeb.net.

---

### Post by billgoldberg on 2008-09-07
If you install the package provided here:

[http://www.getdeb.net/app/aMSN](http://www.getdeb.net/app/aMSN)

does that work?

Double click to install the file.

---

### Post by Linux_noob616 on 2008-09-07
thats not the one i got, though it is the right version, I need to remove the other one before i can install this one don't i?

---

### Post by billgoldberg on 2008-09-07
> **Linux_noob616 said:**
> thats not the one i got, though it is the right version, I need to remove the other one before i can install this one don't i?

Yes.

(completely remove it so no traces are left of it on the system).

---

### Post by Linux_noob616 on 2008-09-07
hey it worked. Thanks a lot.

---

### Post by Bölvaður on 2008-09-07
no do not get it from getdeb.

go to the [amsn website ]("http://www.amsn-project.net/") and download the .deb from there, it is the latest one, and has 100% not been fiddled with by 3rd party.

Before you do that, you should go to Add/Remove and untick amsn and press apply for the uninstall to happen (Im guessing you used that in the first place so it should work with uninstalling it also)

or you can try this command:```
sudo apt-get purge amsn
```

---

### Post by Linux_noob616 on 2008-09-07
There isn't a .deb from the amsn site, only .package (what i used) and .tar.bz

---

### Post by Bölvaður on 2008-09-07
ah you are almost correct, the ubuntu one has been shut down, but debian one is still up... well everything worked out eventually any way :)

---

### Post by Linux_noob616 on 2008-09-07
Alright, i'll remember that, Thanks alot for your help

---

