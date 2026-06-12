---
title: "Efficient screen recorder (with GUI)"
date: 2014-12-18
forum: New to Ubuntu
---

### Post by mkoniecz on 2014-12-18
With gtk-recrormydesktop and Kazam encoding phase is extremely slow (recrormydesktop is at least showing progress bar). Is there something more efficient?

---

### Post by CantankRus on 2014-12-18
Try [**_[COLOR="#B22222"]SimpleScreenRecorder[/COLOR]_**]("http://www.maartenbaert.be/simplescreenrecorder/")
Gives you more options to play around with in the GUI.

---

### Post by MartyBuntu on 2014-12-18
> **mkoniecz said:**
> ...encoding phase is extremely slow...


This is largely dependent on your computer's processor speed...

---

### Post by pqwoerituytrueiwoq on 2014-12-19
kazam, it encodes during the record process, though i have not used it on extremely old hardware
[https://launchpad.net/~kazam-team/+archive/ubuntu/stable-series](https://launchpad.net/~kazam-team/+archive/ubuntu/stable-series)
edit overlooked you have tried it, i should go back to sleep now

---

### Post by Bucky Ball on 2014-12-19
> **pqwoerituytrueiwoq said:**
> kazam, it encodes during the record process, though i have not used it on extremely old hardware
[https://launchpad.net/~kazam-team/+archive/ubuntu/stable-series](https://launchpad.net/~kazam-team/+archive/ubuntu/stable-series)
edit overlooked you have tried it, i should go back to sleep now

Kazam is in the repos. You don't need to manually add a PPA. ;)

@mkoniecz: Welcome. What are your computer specs? If they are low, then might be difficult to find something more efficient for this purpose. If you have a recent CPU and plenty of RAM, then perhaps you could try tweaking the settings on the screen recorder (fps?) and see if that makes any difference. If you are going for super-high quality recordings, that could be the issue. Can be a combination of things.

---

### Post by pqwoerituytrueiwoq on 2014-12-19
> **Bucky Ball said:**
> Kazam is in the repos. You don't need to manually add a PPA. ;)
i used it to get a critial bug fix that made had rendered it useless, maybe the patch is in the repos now

---

### Post by Bucky Ball on 2014-12-19
got ya. ;)

---

### Post by mkoniecz on 2014-12-24
> **Bucky Ball said:**
> @mkoniecz: Welcome. 

Thanks!

> What are your computer specs? If they are low, then might be difficult to find something more efficient for this purpose.

Processor: Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz        : 1200,00MHz
4GB of RAM.

It may be not really new, but I was not expecting encoding lasting longer than recording.


>  If you have a recent CPU and plenty of RAM, then perhaps you could try tweaking the settings on the screen recorder (fps?) and see if that makes any difference. If you are going for super-high quality recordings, that could be the issue. Can be a combination of things.


According to [http://recordmydesktop.sourceforge.net/rug/p1_2d.php](http://recordmydesktop.sourceforge.net/rug/p1_2d.php) "Setting the compression higher(lowering the quality), will make encoding last longer, up to several times." - so I kept default (no compression).

---

### Post by mc4man on 2014-12-24
Your hardware is what it is but did you try the app suggested in post 2? It's superior in all ways to the 2 you've mentioned

---

### Post by mkoniecz on 2015-01-04
> **CantankRus said:**
> Try [**_[COLOR=#B22222]SimpleScreenRecorder[/COLOR]_**]("http://www.maartenbaert.be/simplescreenrecorder/")
Gives you more options to play around with in the GUI.

Thanks, it works really well. Has sane defaults so it is not necessary to wait for a conversion.

mc4man - thanks, I somehow missed this post.

---

