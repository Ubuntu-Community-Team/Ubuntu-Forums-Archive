---
title: "[SOLVED] How do I identify a given ubuntu release from a shell script?"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by qsr.nrwn on 2008-05-24
:confused: Perhaps is a noob question, but I'm working on a bash script that needs to retrieve the ubuntu release in a non-ambiguous manner, such as Warty Warhog, Breezy Badger, D(i)apper Drake, or just retrieve the release number as 4.10, 6.10 ....

Any hint/answer is welcome

---

### Post by amingv on 2008-05-24
Try
```
export CODENAME=$(lsb_release -sc)
echo $CODENAME

```

or

```
export RELEASE=$(lsb_release -sr)
echo $RELEASE

```

---

### Post by qsr.nrwn on 2008-05-24
Is lsb_release accesible from CLI?, I'm not assuming that the target computer has PHP installed on it

Thanks in advance

---

### Post by amingv on 2008-05-24
> **qsr.nrwn said:**
> Is lsb_release accesible from CLI?, I'm not assuming that the target computer has PHP installed on it

Thanks in advance

Yes, the "PHP Code" it's just a misleadingly named code tag (so to say), what's in there it's actually shell commands (No PHP or anything else involved).
But you can just open a shell and confirm it if you don't believe me :).

EDIT:
Better like that ^^^^^?

---

### Post by qsr.nrwn on 2008-05-24
Thank you for your hint

You can retrieve some info regarding the release simply typing:
```

cat /etc/lsb-release 

```
and it will print something like

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

```

It all that I needed

---

### Post by qsr.nrwn on 2008-05-24
That realy annoyed me, since I cannot read PHP so well, but a simple search with slocate prompted where do I have to search

And I believed in you...:lolflag:

---

