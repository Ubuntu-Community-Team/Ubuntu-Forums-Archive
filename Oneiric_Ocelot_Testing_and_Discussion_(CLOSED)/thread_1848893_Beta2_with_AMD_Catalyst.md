---
title: "Beta2 with AMD Catalyst"
date: 2011-09-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Nebuluz on 2011-09-23
Hi all.

I wonder if i somehow can use older catalyst (11.6) with onerirc ocelot. The propertary driver that comes with beta2 and i guess it will stay the same in full release to, has a cpu bug. Its been the same for 11.7 and 11.8 to. I currently use Ubuntu 11.04 with 11.6 and SDK 2.4 and it works great. But ocelot feels alot snippier and i realy want to use it, as i also plan to use it when the full release arrives.

I did try to skip the newest catalyst driver and install 11.6 but with no success. What i've tested is:

1) just run the installer sh ./ati-.........run

and

2) use sh ./ati........run --buildpkg Ubunut/natty etc.

If someone knows how to install the older 11.6 properly with ocelot i would realy like to know.

/Best Regards

---

### Post by kaldor on 2011-09-23
What bugs exist in the latest drivers? Older ones might have graphical issues on GNOME 3.

---

### Post by sumski on 2011-09-23
I really doubt you will be able to install older catalyst releases in OO, cause of the multiarch transition

---

### Post by Nebuluz on 2011-09-23
About bug. I use two of my machines for bitcoin mining (aka intensive calculations on the gpus). And there are  a bug in driver, 11.7 and up which makes cpu to get 100% load, which in turn lower the calculation speed on the gpus. This bug isnt specific to linux as i've test with windows machines to. Driver 11.6 and SDK 2.4 work great. So thats why i try to find a way to use the older drivers :)

And if i dont find a solution to this i will be stuck with 11.04.

---

