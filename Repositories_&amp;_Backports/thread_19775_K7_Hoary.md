---
title: "K7 Hoary"
date: 2005-03-13
forum: Repositories &amp; Backports
---

### Post by marcadams on 2005-03-13
Hello

I have just installed Hoary preview - everything went very smooth. WELL DONE !

One the first things I'd like to do is switch from a 386 to a K7 system. Could someone please tell me which packages I can install to achieve this?



Many thanks
Marc

---

### Post by Yukonjack on 2005-03-13
sudo apt-get install linux-k7

---

### Post by marcadams on 2005-03-13
There are also other k7 modules E,g, linux-image-k7, linux-restricted-modules-k7 etc which seem to have a 386 installed equivalent.

Should these also be installed, or is the linux-k7 module sufficient?

(NB my system currently has two different versions of both 386 restricted modules, and 386 linux image modules installed. Is this necessary for the K7 system as well??)

Thanks
Marc

---

### Post by Yukonjack on 2005-03-14
Should work fine for you, works for me once install do a reboot and
sudo apt-get update
sudo apt-get upgrade 
I've done this in Warty and Hoary with no problems.

---

### Post by acascianelli on 2005-03-16
the dependancies with linux-k7 are automatically resolved if you use synaptic.

---

### Post by marcadams on 2005-03-17
thanks - it's just that I remembered some 386 packages being left installed after I had installed the linux-k7 module (when I did the same on Warty).

But I suppose, even if the 386 packages are installed, that does not mean they are actually being used?

Is this true?

Anyhow, I shall make the change tonight.....


Cheers
Marc

---

