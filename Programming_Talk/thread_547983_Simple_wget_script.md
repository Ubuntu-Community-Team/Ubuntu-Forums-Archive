---
title: "Simple wget script"
date: 2007-09-10
forum: Programming Talk
---

### Post by Kingsley on 2007-09-10
I have a big list of the links to images in my Photobucket that I want to download all at once to my hard drive. Can any of you help me make a script that utilizes wget?

---

### Post by CptPicard on 2007-09-10
cat yourlist.txt | xargs wget

---

### Post by Kingsley on 2007-09-10
Nevermind, I read the wget manual and figured out something else :D. All I had to do was wget -i /home/king/listofmyurls.

---

### Post by CptPicard on 2007-09-10
Yeah, well, rtfm sometimes works.. ;)

---

### Post by Kingsley on 2007-09-10
> **CptPicard said:**
> Yeah, well, rtfm sometimes works.. ;)
Yeah, thanks. I'll try out your solution for another part of my photobucket that I want to download.

---

### Post by CptPicard on 2007-09-10
Also if you're grabbing parts of the site, don't forget that wget can do recursive fetching with -r. I use it to get local copies of good po^H^H NO CARRIER

---

