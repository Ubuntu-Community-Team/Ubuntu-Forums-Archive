---
title: "Ubuntu Privacy?"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by ofb on 2008-06-28
So how do you really wipe or limit cache of previously accessed documents in Ubuntu?

With Windows, of all things, this was simple. Either TweakUI or O'Reilly's Utilities had a Paranoia panel that you could use to clear caches on exit. After a couple of years with Ubuntu, I'm bemused that I haven't found the equivalent for Linux.

I've got my browsers set to flush, and have diabled ~/.recently-used.xbel, but this seems to be only the tip of the iceberg. For example, ~/.kde/share/apps/kpdf has xml files for every PDF I've opened since I've started.

I'll guess the problem is we have so many apps, Gnome/KDE/indie, that there are nearly as many caches. But still I'd have thought Linux of all OSs would have a way for dealing with this. Or at least a fellow paranoid would have made a list of all possible caches you might have, and how they can be configured.

Ideally I'd like to just limit 'recent document' lists to a number like the last ten, or a date like the last 90 days. Second choice would be flushing all lists on logout,  but failing those options I'll accept just disabling the function entirely.


And if there really isn't documentation or software for how to do this, maybe we should start it. This thread could become a complilation of known caches and how to configure them, forming the basis for a Sticky and then a Community Doc.

---

### Post by Pjotr123 on 2008-06-28
Well, perhaps there's no real need for that in Linux: the consistent rights structure prevents snooping in other user accounts. Except for the almighty root, of course.  :-)

Anyway, in the preferences of Firefox you can make F. flush everything at shutdown.

---

### Post by nowshining on 2008-06-29
hmmm there prob. are many ways - u can set the permissions of the ~/.kde/share/apps/kpdf folder to root and only read by root, etc.. after removing those files from the folder and of course any other folders that way so it - the program can't write to it in ur home folder. :)

and thanks for the kpdf folder heads up - i didn't know about that one. :D

---

### Post by hyper_ch on 2008-06-29
those wipings in Windows won't wipe it all anyway.

Now what are you afraid of? Basically using different user accounts for different users should "protect" you from others snooping what you had open etc.

However if you truly want to be safe against thrid parties, then you'd have to use encryption.

---

### Post by brian_p on 2008-06-29
> **ofb said:**
>  But still I'd have thought Linux of all OSs would have a way for dealing with this. Or at least a fellow paranoid would have made a list of all possible caches you might have, and how they can be configured.

Soft link all caches to /dev/null.

---

### Post by nowshining on 2008-06-29
brian how would one do that?

---

### Post by brian_p on 2008-06-29
> **nowshining said:**
> brian how would one do that?

On my box:

```
rm  ~/.mozilla/firefox/gaqvyftd.default/Cache
```

```
ln -s /dev/null ~/.mozilla/firefox/gaqvyftd.default/Cache

```

---

### Post by nowshining on 2008-06-29
ah thanks brian :)

---

### Post by hyper_ch on 2008-06-29
whom do you want to secure it against?

---

### Post by egalvan on 2008-06-29
> **brian_p said:**
> On my box:

```
rm  ~/.mozilla/firefox/gaqvyftd.default/Cache
```

```
ln -s /dev/null ~/.mozilla/firefox/gaqvyftd.default/Cache

```

Newbie question... does this make the caches dissapear ? Does this slow down browsing?

Thank you.

---

### Post by brian_p on 2008-06-29
> **egalvan said:**
> Newbie question... does this make the caches dissapear ?

The cache is there but anything put into it disappears into the black hole of /dev/null.

> Does this slow down browsing?

Quite possibly. Repeated page viewings have to fetched from the web again. It's not something I'm advocating or which I do myself, but it does give it's a possible technique for people who get unduly worried about privacy.

---

### Post by ofb on 2008-07-01
Sorry, I've been tied up with hardware trouble. The summer heat took a drive down.

Agreed: the only way to completely 'safe' is to take a belt-sander to the harddrive platter. As a generalist thread it would probably be good to outline what different levels/methods of security actually achieve.

For myself I'm only interested in wiping or limiting document history in Ubuntu. By asking "how do you really wipe or limit cache?", I should have been much more clear that by 'really' I meant only "What's the intended method / I can't believe I haven't found this yet", not some sort of Ultimate Removal. Sorry.

I quite agree that this is only a layer of privacy, like a locked door, and that if the ninjas want to get you, either of those is inadequate.

---

### Post by Inxsible on 2008-07-01
If you want privacy...you gotta encrypt like hyper suggested. TrueCrypt is what most linux users use, IMO

---

