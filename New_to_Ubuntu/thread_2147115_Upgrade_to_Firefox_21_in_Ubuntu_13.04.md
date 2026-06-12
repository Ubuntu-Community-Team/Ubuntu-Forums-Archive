---
title: "Upgrade to Firefox 21 in Ubuntu 13.04"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by 3mutts on 2013-05-20
I know this might be a stupid question, but I was wondering how to update Firefox 20 to 21 (I don't see the update thing when I go to help/about) because I don't like running out of date web browsers and I don't want to wait forever for Canonical to update the respiratory.

---

### Post by monkeybrain2012 on 2013-05-20
It has been updated a few days ago.

Easy way, go to terminal
```
sudo apt-get update
sudo apt-get upgrade
```

If you have synaptic installed you can open it, reload and check for upgrades.

Don't know about the update manager, I have disabled it. Prefer to check updates myself.

---

### Post by QIII on 2013-05-20
Hello and welcome to the forums!

When was the last time you did an update and upgrade/dist-upgrade?

Thanks.

---

### Post by 3mutts on 2013-05-20
^ & ^^ Thanks, I just did it but I still have Firefox 20, do I need to restart?

edit: restarted and its still Firefox 20 also tried the GUI way and it said all my software was up to date.

---

### Post by sammiev on 2013-05-20
I was at FF21 a few days a go and did a fresh install then for testing. Now I also show FF20 since. I'm testing 13.10

---

### Post by 3mutts on 2013-05-20
^ Maybe Canonical took it down because something was wrong with it? That's the only thing I can think of if you got reverted back to 20 from 21

---

### Post by monkeybrain2012 on 2013-05-20
Maybe you need to change your download server.

---

### Post by monkeybrain2012 on 2013-05-20
> **3mutts said:**
> ^ Maybe Canonical took it down because something was wrong with it? That's the only thing I can think of if you got reverted back to 20 from 21

Nope. I just uninstalled Firefox, cleaned the cache, and then reinstalled it, It is still FF21. :)

Edited: to change the download server, open Ubuntu Software Centre, go to Edit > Software Sources and then change the "down load from" entry  in the box like in the screenshot.

---

### Post by 3mutts on 2013-05-20
^ Ill try that next. ( if this doesn't work then Ill download firefox from the website).

---

### Post by vasa1 on 2013-05-20
> **3mutts said:**
> I know this might be a stupid question, but I was wondering how to update Firefox 20 to 21 (I don't see the update thing when I go to help/about) because I don't like running out of date web browsers and **I don't want to wait forever for Canonical to update the respiratory**.
1. Canonical does not take anywhere near forever to update the "respiratory" at least as far as Firefox is concerned. The Mozilla team is pretty efficient.
2. The version of Firefox that is available from the USC does **not** have the option to update under **Help, About**. If you want that option, you'll have to get Firefox direct from [http://www.mozilla.org/](http://www.mozilla.org/) :)
3. As others have implied, it's an issue at your end that needs to be fixed, by changing your download server or something else.
4. I'd hesitate to be negative about something when it's likely not to blame :)

---

### Post by sammiev on 2013-05-20
> **vasa1 said:**
> 1. Canonical does not take anywhere near forever to update the "respiratory" at least as far as Firefox is concerned. The Mozilla team is pretty efficient.
2. The version of Firefox that is available from the USC does **not** have the option to update under **Help, About**. If you want that option, you'll have to get Firefox direct from [http://www.mozilla.org/](http://www.mozilla.org/) :)
3. As others have implied, it's an issue at your end that needs to be fixed, by changing your download server or something else.
4. I'd hesitate to be negative about something when it's likely not to blame :)

It surely has not a thing to do with changing your download server as I had FF21 a few days back. A fresh install a few days later doesn't include FF21 on any update or server as I tried most. I do fresh installs almost daily as I usually test the next release. Try a fresh install and report back! Using 13.10 here.

---

### Post by 3mutts on 2013-05-20
^^ I'm sorry if I offended Canonical because I really do like 13.04. However some things in respiratory are really dated (Chromium is still at version 25)

---

### Post by QIII on 2013-05-20
I think the word you are looking for is "repository", not "respiratory".

Did you check your download source as suggested?  Are you using a mirror?

I see FF21 in the US repo.

---

### Post by 3mutts on 2013-05-20
> **QIII said:**
> I think the word you are looking for is "repository", not "respiratory".

Did you check your download source as suggested?  Are you using a mirror?

I see FF21 in the US repo.

I am using a mirror so that is probably it, I'll switch it back to the main server tomorrow.

---

### Post by 3mutts on 2013-05-21
Changing the download server fixed it, I'm never using another mirror again no matter how much faster it may be.

---

### Post by mastercode on 2013-06-13
wow! its work thanks man :)

just [COLOR=#ff0000]re[/COLOR] install fire fox from upuntu software center

---

