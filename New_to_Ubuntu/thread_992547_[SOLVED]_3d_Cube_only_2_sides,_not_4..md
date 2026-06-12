---
title: "[SOLVED] 3d Cube only 2 sides, not 4."
date: 2008-11-24
forum: New to Ubuntu
---

### Post by HemisphereDancer on 2008-11-24
Switched from Windows, had computer guy install only Ubuntu 8.10 on laptop. Love it so far, but...
Q# 1) My 3d cube only has 2 sides and I'd like to have four.

Q# 2) When I get 4 sides back, how do I get a seperate window on each side so I can rotate to diff work areas while on the internet? Can I even do this?

Thanks-

---

### Post by jemate18 on 2008-11-24
> **HemisphereDancer said:**
> Switched from Windows, had computer guy install only Ubuntu 8.10 on laptop. Love it so far, but...
Q# 1) My 3d cube only has 2 sides and I'd like to have four.

Q# 2) When I get 4 sides back, how do I get a seperate window on each side so I can rotate to diff work areas while on the internet? Can I even do this?

Thanks-

You should have 4 work spaces. 
1. Below your screen, lowest right, beside the trash icon, right-click
2. Choose preferences
3. Then set number of workspaces to 4. 

Then do the cube thingy... It should work

---

### Post by HemisphereDancer on 2008-11-24
I wonder if I deleted something? I don't have a trash icon (and would like one. I remember it being there when I picked up the laptop) and I don't have any boxes representing my work spaces.

---

### Post by jemate18 on 2008-11-24
> **HemisphereDancer said:**
> I wonder if I deleted something? I don't have a trash icon (and would like one. I remember it being there when I picked up the laptop) and I don't have any boxes representing my work spaces.

to add workspace 

1. Right click on your bottom panel,, 
2. Click add to panel
3. Find Workspace Switcher
4. Click ADD

to add trash

1. Right click on your bottom panel,, 
2. Click add to panel
3. Find trash
4. Click ADD

---

### Post by fooman on 2008-11-24
you change that setting in the compizconfig settings manager (ccsm).  find it in system > preferences > compizconfig settings manager.

if it is not there,  then you need to install it.  in a terminal, type or copy/paste:

```
sudo apt-get install compizconfig-settings-manager
```

then find it where i described above...open ccsm,  click the general button on the left,  then the general options button on the right > desktop size tab

set the horizontal virtual size to 4

---

### Post by HemisphereDancer on 2008-11-24
That did it! It's been driving me crazy for 30 hours.

Thank You. I'm loving my Ubuntu.

---

### Post by benhur99ph on 2008-11-24
You can try following [Forlong's Compiz Fusion Guide]("http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074").
But this guide is for Compiz Fusion 0.7.4 which is found on Hardy, but it should still give you some idea.

---

### Post by HemisphereDancer on 2008-11-24
Solved. Thanks again everyone!

---

### Post by jemate18 on 2008-11-24
> **HemisphereDancer said:**
> That did it! It's been driving me crazy for 30 hours.

Thank You. I'm loving my Ubuntu.

Which solution SOLVED your problem? Would you mind clicking the THANKS button of the post which solved your problem so that those who will view this thread will see it too. 

Thanks....

---

### Post by jemate18 on 2008-11-24
ooopsss... you already did click the thanks button... Sorry......

---

