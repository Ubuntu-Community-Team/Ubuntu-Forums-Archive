---
title: "Play Mac Ads in Konqueror"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by patrickaupperle on 2008-06-13
I have become pretty familiar with Ubuntu, but am now using the KDE version Kubuntu. I want to play the mac ads from apples website, and can not seem to figure it out. Can anyone help?

---

### Post by gr4nf on 2008-06-13
```

sudo apt-get install sun-java6-plugin

```
maybe? That may work.

---

### Post by madjr on 2008-06-13
> **patrickaupperle said:**
> I have become pretty familiar with Ubuntu, but am now using the KDE version Kubuntu. I want to play the mac ads from apples website, and can not seem to figure it out. Can anyone help?

you can watch them at youtube

or other sites

else,

install **firefox 3** and **mplayer-mozilla** plugin

---

### Post by patrickaupperle on 2008-06-13
Thank you both for the answers. Although I already knew they were on youtube, I much prefer to watch them off the apple site. Is there a way to do that?

---

### Post by patrickaupperle on 2008-06-13
Whoa, I completely forgot to mention I am using 8.04 kde4

---

### Post by canthus13 on 2008-06-13
install the restricted extras, if you haven't already.  Apple is most likely using Quicktime,and I think the restricted extras include something to support QT.

```
sudo aptitude install kubutu-restricted-extras
```

--Me

---

### Post by patrickaupperle on 2008-06-14
> **canthus13 said:**
> install the restricted extras, if you haven't already.  Apple is most likely using Quicktime,and I think the restricted extras include something to support QT.

```
sudo aptitude install kubutu-restricted-extras
```

--Me
I thought it would work, until I remembered I already installed that. Thank you for trying to help, but the problem persists.

---

### Post by patrickaupperle on 2008-06-20
> **madjr said:**
> you can watch them at youtube

or other sites

else,

install **firefox 3** and **mplayer-mozilla** plugin

Ok, I installed firefox. Now how do I install mplayer-mozilla?

edit: Nevermind I found it. ```
sudo apt-get install mozilla-mplayer
```

---

