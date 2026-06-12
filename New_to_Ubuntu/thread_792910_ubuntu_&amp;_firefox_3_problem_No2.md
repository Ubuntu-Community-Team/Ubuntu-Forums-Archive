---
title: "ubuntu &amp; firefox 3 problem No2"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by lunaluna on 2008-05-13
while i was browsing around(fullscreen) suddenly i saw a black screen 
i thought the pc logged out but then i heard a sound from the "workaholic"  timer program so i wasn't...

then i saw these messages:
```

*Starting anc(h)ronistic cron anacron
*Differed execution scheduler c...(don't remember exactly)
*Starting periodic command scheduler cron
*Checking battery state...
*Running local boot scripts (/etc/rc.local)

```

i pressed ctrl+alt+backspace nothing happened,then restart with ctrl+alt+delete...

what exactly happened? any ideas?
i must be the 5th time that this is happening...

---

### Post by hermes0710 on 2008-05-13
Any case you press the combination ctrl+alt+F?

---

### Post by lunaluna on 2008-05-13
> **hermes0710 said:**
> Any case you press the combination ctrl+alt+F?

i'm not sure...
what this stands for?

---

### Post by lunaluna on 2008-05-13
well its not from the combination..after all 
it just happened again...

---

### Post by OldTimeTech on 2008-05-13
Are you on a laptop?  Sounds to me like your battery just dropped to low and you need to plug in.

---

### Post by lunaluna on 2008-05-13
> **OldTimeTech said:**
> Are you on a laptop?  Sounds to me like your battery just dropped to low and you need to plug in.

im on laptop but i use it plugged on steady power
no battery installed on it

---

### Post by MarkX on 2008-05-13
Had PC shut down or lock numerous times for no reason after watching a site with flash in it. Installing firefox2 and dumping firefox3BETA cured the problem. 
Damn silly of them to "upgrade" people to a BETA, what on earth possessed them?

---

### Post by sunstriker on 2008-05-13
Indeed, kinda stupid. I had a problem (it's already fixed now) with ff3 beta when I wanted to add a security exception for the wifi network at school. when I clicked 'Allow' nothing happened. So without connection I couldn't download ff2 either. Lukely I was on Mac so I had Safari :p

---

### Post by lunaluna on 2008-05-13
is there an easy way to transfer my settings from 3 to 2 without to "type" everything

---

### Post by JoshuaRL on 2008-05-13
> **MarkX said:**
> Had PC shut down or lock numerous times for no reason after watching a site with flash in it. Installing firefox2 and dumping firefox3BETA cured the problem. 
Damn silly of them to "upgrade" people to a BETA, what on earth possessed them?

From what I hear it has to do with the upcoming FF3 final release.  That way when it hits, Hardy won't be stuck a full release behind.  Apparently that happened with FF2 also.  But the whole release has bugs here and there, that's what happens on a new release.  They'll get taken care of soon and you'll have a nice stable Hardy LTS.

---

### Post by drubin on 2008-05-13
> **MarkX said:**
> Had PC shut down or lock numerous times for no reason after watching a site with flash in it. Installing firefox2 and dumping firefox3BETA cured the problem. 
Damn silly of them to "upgrade" people to a BETA, what on earth possessed them?

Their reasoning was that Firefox2 would not have long enough support to be part of the 8.04 LTS version. The same reason that i think Kubuntu 8.04 is not marked as long term support the KDE version beta version is not stable enough, and the stable version is not going to be supported long enough.


But you could just upgrade to firefox3 when it came out of beta!!!!

---

### Post by elamericano on 2008-05-13
Fedora 9, which was just released, also includes FF3-Beta5. So, it couldn't have been that stupid if another major distribution is doing the same thing - and they don't even have the LTS situation to think about.

---

### Post by lunaluna on 2008-05-13
they could just put fire...v3 in order to give it an acceleration for the new realese to come sooner

---

### Post by Victormd on 2008-05-13
> **lunaluna said:**
> is there an easy way to transfer my settings from 3 to 2 without to "type" everything

Open a terminal and type:
```
firefox -profilemanager
```

This will open, well, the profilemanager. You will see the folder where all your firefox information is stored (bookmarks/addins/etc).
Now you can do 2 things (not necessarily in this order):
1. uninstall ff3:
  a. backup the folder shown in the profilemanager
  b. uninstall ff3
2. install ff2
  a. install ff2
  b. run the command and when creating your profile, point the folder to your backed up folder and this should do the trick.

---

### Post by lunaluna on 2008-05-14
> **Victormd said:**
> Open a terminal and type:
```
firefox -profilemanager
```

This will open, well, the profilemanager. You will see the folder where all your firefox information is stored (bookmarks/addins/etc).
Now you can do 2 things (not necessarily in this order):
1. uninstall ff3:
  a. backup the folder shown in the profilemanager
  b. uninstall ff3
2. install ff2
  a. install ff2
  b. run the command and when creating your profile, point the folder to your backed up folder and this should do the trick.

typed the command but it just opened another window...no profile-data-whatever appeared...

---

