---
title: "[SOLVED] Cannot play DVD's"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-06-27
Pretty simple: if I put in a DVD, Totem Movie Player opens up and the DVD file appears on my desktop.  After Totem opens, though, an error message pops up saying "An error occured.  Could not read from resource".

What do I have to do to be able to play a DVD?

---

### Post by Hospadar on 2008-06-27
Probably, you need to install libdvdcss2, which is what let's you read copy-protected dvds (i.e. all commercial dvds).  Due to licensing issues, it's not available in the mainstream repos, but you can get it easily from medibuntu.  If you google medibuntu it'll take you to their site where they have good instructions on howto install their repositories.

Once you have their repositories installed, install libdvdcss2 either from synaptic or by ```
sudo apt-get install libdvdcss2
```

Also I think you might need another package called libdvdread (or something like that?) once you have the medibuntu repos working, if installing libdvdcss2 doesn't get you working, try searching synaptic by name for "dvd" and see if you can find libdvdread or something that appears to give you the functionality you want.

Also note that mplayer and vlc can play dvds just fine if you prefer them or if you just can't get totem working.

---

### Post by ConMan318 on 2008-06-27
Beautiful, worked perfectly.  Thank you very much.

---

### Post by swoody on 2008-06-28
> **Hospadar said:**
> Probably, you need to install libdvdcss2, which is what let's you read copy-protected dvds (i.e. all commercial dvds).  Due to licensing issues, it's not available in the mainstream repos, but you can get it easily from medibuntu.  If you google medibuntu it'll take you to their site where they have good instructions on howto install their repositories.

Once you have their repositories installed, install libdvdcss2 either from synaptic or by ```
sudo apt-get install libdvdcss2
```

Also I think you might need another package called libdvdread (or something like that?) once you have the medibuntu repos working, if installing libdvdcss2 doesn't get you working, try searching synaptic by name for "dvd" and see if you can find libdvdread or something that appears to give you the functionality you want.

Also note that mplayer and vlc can play dvds just fine if you prefer them or if you just can't get totem working.

Thank you so much! I've been troubled with getting my dvds to play, and I love how you put it out there in such easy terms.

---

### Post by rainwalker on 2008-06-28
Doesn't ubuntu-restricted-extras install libdvdcss2?

---

### Post by Pjotr123 on 2008-06-28
> **rainwalker said:**
> Doesn't ubuntu-restricted-extras install libdvdcss2?

No.  :-)

You need Medibuntu for that:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by uzzo2 on 2008-06-29
> **Pjotr123 said:**
> No.  :-)

You need Medibuntu for that:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)
i'm having the same problem, performed the task from the link provided and am still getting an error "could not read from resource".

---

### Post by frbe0101 on 2008-06-29
This is the error I get when I try to install that patch. 

```
sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
```

---

