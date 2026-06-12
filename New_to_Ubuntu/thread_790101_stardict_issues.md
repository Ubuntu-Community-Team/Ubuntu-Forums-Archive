---
title: "stardict issues"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by sauravbhaumik on 2008-05-11
Hello friends,
I have recently installed Hardy Heron version and since been having issues with stardict.

I installed stardict of its latest version, which is available from add - remove. But that creates a weird problem; you double-click on a word and the floating window appears but the floating window moves off a distance after 5 seconds or so. That is sometimes troublesome to bear with. 

So I tried to uninstall it ```
sudo apt-get purge stardict-gtk
``` and then install an older version stardict_3.0.1-1_i386.deb (this works absolutely fine in Feisty), but the second attempt was not successful, even though I repeated my endeavour several times. Any suggestion? And by the way, though I don't need, the sound option doesn't work here.

---

### Post by nowshining on 2008-05-11
try turning off 3d effects  ie: compiz and try again.

---

### Post by sauravbhaumik on 2008-05-12
> **nowshining said:**
> try turning off 3d effects  ie: compiz and try again.

I turned off 3d-effect (you mean, the visual effect options in appearance?) at the first boot after install. Any other suggestion? Thanks, anyway.

---

### Post by nowshining on 2008-05-12
i'll try the program myself :)

[http://stardict.sourceforge.net/](http://stardict.sourceforge.net/) - main site

try installing the one from the site for debian here:

[http://downloads.sourceforge.net/stardict/stardict_3.0.1-1_i386.deb](http://downloads.sourceforge.net/stardict/stardict_3.0.1-1_i386.deb)

---

### Post by sauravbhaumik on 2008-05-12
> **nowshining said:**
> i'll try the program myself :)

[http://stardict.sourceforge.net/](http://stardict.sourceforge.net/) - main site

try installing the one from the site for debian here:

[http://downloads.sourceforge.net/stardict/stardict_3.0.1-1_i386.deb](http://downloads.sourceforge.net/stardict/stardict_3.0.1-1_i386.deb)

That didn't help anyway.That had the same problem.

---

### Post by sauravbhaumik on 2008-05-12
> **nowshining said:**
> i'll try the program myself :)

[http://stardict.sourceforge.net/](http://stardict.sourceforge.net/) - main site

try installing the one from the site for debian here:

[http://downloads.sourceforge.net/stardict/stardict_3.0.1-1_i386.deb](http://downloads.sourceforge.net/stardict/stardict_3.0.1-1_i386.deb)

Would it be helpful if I give you this message (error message)?
```
...........
trying to overwrite `/usr/share/locate/ga/LC_MESSAGES/stardict.mo', which is also in package stardict-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)

```

---

### Post by nowshining on 2008-05-13
go to my ubuntu/kubuntu gatherings site to learn how to fix a broken pipe error.

---

### Post by sauravbhaumik on 2008-05-13
> **nowshining said:**
> go to my ubuntu/kubuntu gatherings site to learn how to fix a broken pipe error.

I couldn't find out your article on how to fix a broken pipe error in your website. Could you give me the link, please?

---

### Post by nowshining on 2008-05-13
[http://www.freewebs.com/gutsygibbon/tipsfixeshowtwos.htm#BrokePipe](http://www.freewebs.com/gutsygibbon/tipsfixeshowtwos.htm#BrokePipe)

i just noticed a spacing error in that :) I gotta fix that before I forget

---

### Post by sauravbhaumik on 2008-05-13
> **nowshining said:**
> [http://www.freewebs.com/gutsygibbon/tipsfixeshowtwos.htm#BrokePipe](http://www.freewebs.com/gutsygibbon/tipsfixeshowtwos.htm#BrokePipe)

i just noticed a spacing error in that :) I gotta fix that before I forget

Ohh:(
My installation problem was that the stardict-common package was not removed, which I had to remove from the synaptic. Then I could install the deb file successfully; yet the most woeful thing that happened is that the version I so hardly strove to install turns out a hell lot more buggy than others, and of course, than the one available by default. And by the way, I remember that the stardict website had some of its older versions available for download, but now I can't see any of them! Could you find any of the older versions in their site (I think the older versions might be stabler than the ones I'm muddling with) [http://stardict.sourceforge.net/](http://stardict.sourceforge.net/)

---

### Post by nowshining on 2008-05-14
i have no probs on gutsy - however on my site i fixed the formatting errors when I tried tidying up the site the other day :) messed things all up - not all should be back to normal + much better looking on the tips page..

as for the ol' ver.

look here [http://sourceforge.net/project/showfiles.php?group_id=122858](http://sourceforge.net/project/showfiles.php?group_id=122858)

---

### Post by sauravbhaumik on 2008-05-15
> **nowshining said:**
> i have no probs on gutsy - 


Yes, I didn't find problems in Gutsy, the problem only appears in Hardy.

---

### Post by nowshining on 2008-05-15
anyway thanks for issue :P (j/k) it's quite a nice program and what I was lookin' for  (ie: a non-attched to web dictionary)- the wordnet dictionary is animated :P and it took a bit of getting used to.

---

### Post by sauravbhaumik on 2008-05-16
I think reinstalling stardict_3.0.1-1_i386.deb has at last fixed it; but I can't understand why it showed issues yesterday. Anyway, does an operating system have the power to fix problems on its own (like our body)? I saw something like that in case of xmms many times in the previous versions of ubuntu; actually it didn't show the menus and preferences in the first few days of installation, but it did a bit later!

By the way, please see the problem at [http://ubuntuforums.org/showthread.php?p=4969971#post4969971](http://ubuntuforums.org/showthread.php?p=4969971#post4969971)  I used texmaker in gutsy which integrated kdvi well, but winefish, in hardy, doesn't.

---

