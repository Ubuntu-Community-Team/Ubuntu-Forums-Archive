---
title: "firefox and flash issues"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by trynet on 2008-04-29
when I go and click on the big play icon that comes up in place of the flash object. for youtube, it has no sound. but for everything else, nothing happens.
any help?

---

### Post by aheckler on 2008-04-29
Are you running 64-bit by chance?

---

### Post by whitefort on 2008-04-29
I've no solution, but I thought I'd leave a note to let you know you're not alone.  I have the exact same problem since switching to Hardy and Firefox 3.

I really wish Hardy hadn't shipped with such a buggy beta Firefox, though I'm sure (or I hope!!!) that there'll be an update one of these days to fix it.

---

### Post by trynet on 2008-04-29
not sure...I don't know how to check...
before the update it all worked fine though. then suddenly when I updated ubuntu, and got the updated firefox that came with it (that I can't say I'm very fond of as it is) I've been having problems with everything.

---

### Post by aheckler on 2008-04-29
The first time you tried to watch a Flash video, did you install the plugin? Which one: Gnash, Swfdec, or the regular Adobe one?


(PS- If you you want to go back to Firefox 2, the link in my sig will show you how.)

---

### Post by trynet on 2008-04-29
I think the adobe one didn't work so I installed the gnash.
I think I'll just downgrade >.> glitchy glitchs are glitchy.
thanks.

---

### Post by aheckler on 2008-04-29
> **trynet said:**
> I think the adobe one didn't work so I installed the gnash.
I think I'll just downgrade >.> glitchy glitchs are glitchy.
thanks.

Adobe's didn't work? Hmm, that's the first time I've seen that happen. Did you restart Firefox after it installed?

---

### Post by trynet on 2008-04-29
heres what came out when I tried down-grading for the 2nd time since the first time nothing happened.
> tyler@tyler-desktop:~$ sudo apt-get purge firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firefox is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tyler@tyler-desktop:~$ rm -r ~/.mozilla/firefox
tyler@tyler-desktop:~$ sudo apt-get install firefox-2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tyler@tyler-desktop:~$ 
tyler@tyler-desktop:~$ 

and I'm really not sure what I did, I was just in a rush to get things working, and they did work...for around 10 minutes.

---

### Post by aheckler on 2008-04-29
Try:

```
sudo apt-get purge firefox-3.0
rm -r ~/.mozilla/firefox
sudo apt-get install firefox-2
```

---

### Post by trynet on 2008-04-29
that worked, but I'm back to the flash issues still...

---

### Post by aheckler on 2008-04-29
Hmm, well you might need to install the Flash plugin again. I'm not really sure where to go from here, I just installed Adobe's Flash thing and it worked.

Maybe try "sudo apt-get install flashplugin-nonfree" and see what that does.

---

### Post by trynet on 2008-04-29
I just installed it, now I can't change the default...
I don't know which one I'm using...

---

### Post by aheckler on 2008-04-29
Alright, let's try this.

[LIST=1]
[*]Close Firefox.
[*]Go into Synaptic Package Manager.
[*]Search for "gnash".
[*]If anything in the results is installed, remove it.
[*]Search for "swfdec".
[*]If anything in the results is installed, remove it.
[*]Restart Firefox and see if Adobe's Flash plugin works now.
[/LIST]
See if that allows Adobe's version to run uninhibited.

---

### Post by trynet on 2008-04-29
yep, thanks!

---

### Post by movrshakr on 2008-04-29
Here is another thread about Firefox flash issues.


[http://ubuntuforums.org/showthread.php?p=3945403#post3945403](http://ubuntuforums.org/showthread.php?p=3945403#post3945403)

At least a couple of people got flash to work by getting the .so (dot ess oh) file out of the flash pkg and putting it into the plugins folder.

---

