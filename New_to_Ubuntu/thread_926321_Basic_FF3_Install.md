---
title: "Basic FF3 Install"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by AutumnPhoenix on 2008-09-21
I'm trying to remember what to do.  I keep messing up

 I'm triying to install Fire Fox 3.  Its sitting on my desktop.  I know next I can open up terminal.

And I've tried various commands I know but they don't do anything for firefox.

Help please!

---

### Post by shafi on 2008-09-21
> **AutumnPhoenix said:**
> I'm trying to remember what to do.  I keep messing up

 I'm triying to install Fire Fox 3.  Its sitting on my desktop.  I know next I can open up terminal.

And I've tried various commands I know but they don't do anything for firefox.

Help please!

```

sudo apt-get install firefox

```
if it doesn't worked check the System ==> administration ==> Software sources, then click the Ubuntu Software Tab, all the check boxes except the source code [ optional ] in that tab should be active if not, made them active.

---

### Post by AutumnPhoenix on 2008-09-21
I did both but I still open up to my old version of firefox.:confused:

---

### Post by Dr Small on 2008-09-21
Untar the file in /opt:
```
sudo tar xvf nameoftarball.tar.bz2 /opt
```

Then attempt to execute it, to see if it works:
```
/opt/firefox/firefox
```

---

### Post by MegaJim on 2008-09-21
Are you trying to install firefox 3 from a downloaded file?

If you are trying to install the latest firefox 3 from the repositories (which it seems you have tried) can you post the output of

```
sudo aptitude show firefox
```

---

### Post by aysiu on 2008-09-21
Try this:
[http://www.psychocats.net/ubuntu/firefox#terminal](http://www.psychocats.net/ubuntu/firefox#terminal)

---

### Post by shafi on 2008-09-21
> **AutumnPhoenix said:**
> I did both but I still open up to my old version of firefox.:confused:

```

sudo synaptic

```
then search for firefox after that right click on the firefox package and select the "Mark for Complet Removal".
after that search again for firefox and there you will see a package name firfox if you read the description of the package then you can find out which version is that, then install it.

---

### Post by aysiu on 2008-09-21
That should be ```
**gk**sudo synaptic
```

---

