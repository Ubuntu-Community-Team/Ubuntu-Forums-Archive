---
title: "firefox 2 and firefox 3"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-08-27
is it possible to have both ff2 and ff3?if yes,how?i use ubuntu8.04.

---

### Post by knattlhuber on 2008-08-27
> **stonecoldjha said:**
> is it possible to have both ff2 and ff3?if yes,how?i use ubuntu8.04.

I had them both on my machine until this morning when I moved to FF3. I can't remember exactly how I did it way back then... How about simply installing the package firefox-2 with Synaptic?

---

### Post by habtool on 2008-08-27
If you install firefox 2 from repo you should be all set.

---

### Post by billgoldberg on 2008-08-27
> **stonecoldjha said:**
> is it possible to have both ff2 and ff3?if yes,how?i use ubuntu8.04.

Firefox 3.0.1 is the standard one in Ubuntu 8.04.1

Firefox 2 is also in the ubuntu repositories.

Search for it in add/remove or synaptic.

---

### Post by aysiu on 2008-08-27
Install *firefox* and *firefox-2* and you should be set.

You'll need the Universe repositories enabled to install Firefox 2, though.

---

### Post by elmoosecapitan on 2008-08-27
I have run into this problem before on XP (never tried it on Ubuntu), but if you have multiple releases of FF both (or all versions) will start accessing common and unique folders at the same time, ultimately causing file corruptions in said folders. When FF 3.0.x-beta first came out, I was running FF 2.5.y at the same time and the two started to interfere with one another. I was able to import all my FF 2.5 tabs into FF 3-beta, but when I began customizing my FF 3, I lost all my FF 2.5 data; it became inaccessible. When I removed FF 3, it took all of my FF 2.5 information along for the ride.

This was with 3-beta and on XP, it may be completely different now. Just be careful!

cheers

---

### Post by alienexplorers on 2008-08-27
If you are going to run both firefox2 and firefox3 it is best to set up seperate profiles in the .mozilla folder.  This way neither interferes with the other to start the firefoxes you would start one as:
> firefox -P "profilename"
you would also do this with the second one.

---

### Post by stonecoldjha on 2008-08-28
i am sorry,i did not get that.how do i do that?

---

### Post by knattlhuber on 2008-08-29
> **stonecoldjha said:**
> i am sorry,i did not get that.how do i do that?

You should have a profile for Firefox 3 in ~/.mozilla/firefox. It's a folder with some letter/number sequence ending in '.default'.
Make a copy of that folder and rename it. This will be your FF2 profile now.
Then create shortcuts on your panel for FF2 and FF3.

To start FF2, use
```
firefox-2 -P "profilename for FF2"
```

To start FF3, use
```
firefox -P "profilename for FF3"
```

If you use the same profile for both, you may run into trouble.

---

