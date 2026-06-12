---
title: "HowTo restore original konqueror profiles/menu"
date: 2005-10-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Jens7677 on 2005-10-21
I spend some time to find out how to restore the original konqueror menu/profiles since I really don't like the kubuntu konqueror light version (without breaking something).

This is what I did (as user, not as root):
```
cp /usr/share/apps/konqueror/konqueror-orig.rc ~/.kde/share/apps/konqueror/konqueror.rc

cp /usr/share/apps/konqueror/profiles/* ~/.kde/share/apps/konqueror/profiles/
```

I hope this will help someone who missed "Open Terminal" like me .

---

### Post by oliwally on 2005-10-23
> I spend some time to find out how to restore the original konqueror menu/profiles since I really don't like the kubuntu konqueror light version (without breaking something).

Magic stuff! Thank you so much. The new version of Konqueror is indeed missing the goodies that we're used to. Why did they leave those features out? Are there other versions of Konqueror (non-light ones) that are fully featured?

---

### Post by berserker on 2005-10-23
I lost some Konqueror functionality (e.g., "Copy to..." and "Move to...") when I upgraded to Breezy but was able to restore it by installing the konq-plugins package.

---

### Post by oliwally on 2005-10-24
> I lost some Konqueror functionality (e.g., "Copy to..." and "Move to...") when I upgraded to Breezy but was able to restore it by installing the konq-plugins package.

I did have that one installed before making the changes mentioned by Jens7677, but it still didn't give me the beaut features we had before. Strange that - why would they make a newer version less good?

---

### Post by jeep05 on 2005-10-30
thanks for this tip ! very useful...
I prefer the original profiles of konqueror :)

---

### Post by tabinin on 2005-12-05
Beautiful!  Thank you.  This restores my "copy to..." and "move to..." menus that magically disapeared after I tried some new themes and icons.

---

