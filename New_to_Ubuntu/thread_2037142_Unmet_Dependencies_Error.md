---
title: "Unmet Dependencies? Error?"
date: 2012-08-03
forum: New to Ubuntu
---

### Post by southerndave on 2012-08-03
Hi! New here and new user of Ubuntu. Installed after sick of Windows. All fine until recent udates when an error message appeared and a stop sign is on the upper right toolbar. The error reads:

E:Read error - read (5: Input/output error), E:The package lists or status file could not be parsed or opened.

I have no idea what these means. Occasionally the screen has started fading and everything locks for a few second before coming back to normal. I know the HDD is knackered on this machine but has been running okay for week with Linux/Ubuntu right up until the last update.

I am not overly clever with codes and scripts so any fix needs to be fairly user friendly!!

---

### Post by Linuxratty on 2012-08-03
I have never had a problem like this,so I'm afraid I can't help you with it.
I'd suggest you go to the help forum and post.

Kind regards

---

### Post by QIII on 2012-08-03
If your disk is belly up and going down by the bow, there is really no point in trying to salvage the OS.  Recover what data you can and get a new drive.

From the sound of it, what you are saying is "It ran fine until the drive failed completely."

---

### Post by southerndave on 2012-08-03
No, the other way round! When it had WIndows on it, it died. I took windows off and installed Ubunutu and all has been running fine. The disk check software still shows the dirve is poorly but it is limping along enough to work with the vastly reduces reources that Linux takes in comparison to Windows. As I said all running fine and dandy until the last auto update when this error appears. I therefore assumed it has something more to do with the update than the disk...?

---

### Post by QIII on 2012-08-03
Limping along probably means "about to fall down", which it may have done. The updates may have either been coincidental or depended on something in a physical spot on the disk that is no longer readable.
 
Assuming a temporal cause and effect relationship in this case may be succumbing to the fallacy of Post Hoc Ergo Propter Hoc (After this, therefore because of this). The relationship may be casual or causal. If causal, it may be the opposite of what it seems: The update may have failed because the disk is failing.
 
If your disk is reporting its health as poor, best not to push your luck.  If the disk is in poor condition, there is little use in trying to fix the issue by means of a fix to the OS.

---

### Post by southerndave on 2012-08-03
I suspect you are correct but thought I'd ask anyway. If other have had similar issues, it may well be software/OS rather than drive in which case, great  my failing disk can limp along some more. But if the general consensus is that the disk error is the more likely cause, then fair enough. I can put up with the nagging error messages for a while until the HD goes bye-bye.

---

### Post by QIII on 2012-08-03
Fat fingers!

---

### Post by QIII on 2012-08-03
You can try```
sudo apt-get clean
```

```
sudo dpkg --configure -a
``` 

if it asks you to.  Then 

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

---

### Post by NikTh on 2012-08-03
Hi , 
about hard disk you can check SMART and see what tells you. 
```
sudo apt-get install smartmontools --no-install-recommends
sudo smartctl -a /dev/sda
``` 

post the results back here ,by click on NewReply and click # , paste results between brackets. 

For updates problem you can try some cleaning commands as QIII suggests . 
* QIII Congratulations on new Ubuntu membership. * :)

---

