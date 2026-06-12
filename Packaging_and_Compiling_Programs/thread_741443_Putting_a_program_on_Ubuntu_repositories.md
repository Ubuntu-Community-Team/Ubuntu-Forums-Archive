---
title: "Putting a program on Ubuntu repositories"
date: 2008-03-31
forum: Packaging and Compiling Programs
---

### Post by quandary on 2008-03-31
Hi!

I've written an aimbot for Quake3 & Urban Terror, which works on Linux, Unix, Windows and Mac - OS X.

I've so far already distributed it, and it works perfectly.

I put the aimbot under GPL, and Quake3 is so, too.

Now the question:
1. Is it allowed to add an aimbot to some Ubuntu repository, so a Ubuntu user would only have to type: apt-get install urthack-0.1

2. If yes, what would be the formal procedure?

3. Would I need to make a dpkg-package, and if yes how?

---

### Post by Zugzwang on 2008-04-01
> **quandary said:**
> 
I put the aimbot under GPL, and Quake3 is so, too.

I doubt that Quake3 has a GPL licence. I guess it is just the source that's now free software. The rest normally isn't released this way.

See the stickies on how to make packages. There is also a link to [https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages]("https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages") stating how to get your package included.

---

### Post by quandary on 2008-04-01
> **Zugzwang said:**
> I doubt that Quake3 has a GPL licence. I guess it is just the source that's now free software. The rest normally isn't released this way.

See the stickies on how to make packages. There is also a link to [https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages]("https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages") stating how to get your package included.

Yes of course I'm talking about the source. I'm not interested in the non-GPL PAK files from quake, i don't need 'em ;-)

---

