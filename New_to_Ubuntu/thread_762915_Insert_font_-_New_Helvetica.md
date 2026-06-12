---
title: "Insert font - New Helvetica"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Ohwii on 2008-04-22
Hi Guys

I have a very simple problem I just want to add the attached font 

I  copied in ```
.fonts 
```

and then typed in the terminal 

```
sudo fc-cache -f
```

but it doesn't work 

Tanks in advance

Oh wii

---

### Post by Superkoop on 2008-04-22
Open up Nautilus and in the location space put: fonts:///

And then just copy over your .PFB files. 
That will add the fonts for you =)

(if this isn't your problem, sorry :P)

---

### Post by PinkFloyd102489 on 2008-04-22
Anytime Ive added a font, I just copied it to the ~/.fonts/ dir and it worked immediately. I think it may be because it needs to be plural.

---

### Post by Ohwii on 2008-04-22
thanks for the answers, but it still does not work. 
:(

PS tried both

---

### Post by Superkoop on 2008-04-22
You are just copying the .PFB file over right? Nothing else, right?

---

### Post by Ohwii on 2008-04-22
Yes I am only using the .pfb files

---

