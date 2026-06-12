---
title: "Getting rid of Kubuntu desktop on Ubuntu"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Sailorcancer on 2008-10-31
While searching the forums I thought it would be interesting to try out Kubuntu.  I entered the following code in:

```
sudo aptitude install kubuntu-desktop
```

Well I would like to get rid of it now.  I have tried the following two codes:

```
sudo aptitude remove kubuntu-desktop
```
```
sudo aptitude install ubuntu-desktop
```

I've restarted after each, but Kubuntu still remains.  Am I doing something wrong?  How can I get rid of Kubuntu?

---

### Post by randy78 on 2008-10-31
Psychocats has the fix you need ;) : [http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by Sailorcancer on 2008-10-31
Should I be entering this in the Ubuntu desktop or the Kubuntu desktop?

---

### Post by fooman on 2008-10-31
do this while logged into ubuntu.

---

### Post by Sailorcancer on 2008-10-31
Ok so I entered all that code in and went to go restart.  Now I just have a screen of text.  The last thing it says is:

* Checking Battery state...               [OK]

I can press enter and it will go down.  Do I have to press the restart button?

---

### Post by Sailorcancer on 2008-10-31
THANK YOU!  Everything is back to the way it was

---

### Post by ezramorris on 2008-10-31
Just incase you were wondering, kubuntu-desktop is a meta package. This means that it doesn't actually contain anything, but will automatically install everything needed for Kubuntu to work.

However, when you uninstall it, all the packages that it automatically installed still exist, so have to be removed manually.

---

