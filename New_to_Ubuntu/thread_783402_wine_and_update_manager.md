---
title: "wine and update manager"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by kattou22 on 2008-05-05
Hi,  
Thanks god i am a newbiw so i dont feel that silly!!!..
I wanted to uninstall wine as it was not letting me play a certain game. I thought maybe it was not properly installed as the site says to uninstall all previous wine.  I did a search and found a whole bunch of files with wine in it and removed it. 

I have no clue if this is related to the problem i am having now, but my update manager does not really work anymore. 
When i try to check for new updates it freezes on 21 out of 31. Anything that has to do with these file FAILS
Translation_En_Ca
Realease.gpg

I tried also upgrading to hardy and its the same problem. :( 
Can anyone help me. Thanks  I am using Gutsy

---

### Post by Oldsoldier2003 on 2008-05-05
> **kattou22 said:**
> Hi,  
Thanks god i am a newbiw so i dont feel that silly!!!..
I wanted to uninstall wine as it was not letting me play a certain game. I thought maybe it was not properly installed as the site says to uninstall all previous wine.  I did a search and found a whole bunch of files with wine in it and removed it. 

I have no clue if this is related to the problem i am having now, but my update manager does not really work anymore. 
When i try to check for new updates it freezes on 21 out of 31. Anything that has to do with these file FAILS
Translation_En_Ca
Realease.gpg

I tried also upgrading to hardy and its the same problem. :( 
Can anyone help me. Thanks  I am using Gutsy
try this :
```
sudo apt-get purge wine
```
then if you aren't afraid of losing anything you've done with wine so far:
```
rm -rf ~/.wine
```

next(regardless if you did step 2)
```
sudo apt-get install wine
winecfg
```

---

### Post by macaholic on 2008-05-05
I highly doubt that either of those issues has anything to do with another, but for whatever reason, your update manager isn't able to download all the files it needs, I would try switching servers. Go to synaptic, then to settings > repositories > under "download from" choose other, then select best server. Try updating again.

---

### Post by kattou22 on 2008-05-05
[COLOR="Red"]```
rm -rf ~/.wine
```[/COLOR]

 but does this last command delete wine from all directories or just my home directory as ~ stands for home???

---

### Post by Oldsoldier2003 on 2008-05-05
> **kattou22 said:**
> [COLOR="Red"]```
rm -rf ~/.wine
```[/COLOR]

 but does this last command delete wine from all directories or just my home directory as ~ stands for home???

thats will completely clean out your "personal" wine install. the apt-get purge will remove wine from the system.

when you set up wine it makes a "fake c drive" in your home directory. if you wipe this out too you'll have a clean start

---

### Post by kattou22 on 2008-05-05
> **macaholic said:**
>  I would try switching servers. Go to synaptic, then to settings > repositories > under "download from" choose other, then select best server. Try updating again.

Should i do this even if i am using update manager, not synaptic package manager?

---

### Post by macaholic on 2008-05-05
> **kattou22 said:**
> Should i do this even if i am using update manager, not synaptic package manager?
It's the same backend, update manager is essentially just synaptic without listing all the packages and just checking and autoselecting updates, so yes you should.

---

