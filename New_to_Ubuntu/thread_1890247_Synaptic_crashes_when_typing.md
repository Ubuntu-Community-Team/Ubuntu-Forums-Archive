---
title: "Synaptic crashes when typing"
date: 2011-12-03
forum: New to Ubuntu
---

### Post by meyou1 on 2011-12-03
Hey guys, another problem in my hands......
Still using Lucid here and having some problems with Synaptic manager;

every time I open it there's no problem but when I start typing in the search box it crashes; no idea why
if I copy-paste in the search box it works as it should but when I manually type from the keyboard it exits after a few seconds;
I tried running it from terminal with gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic but only after I type sudo in front of it does the problem sove;
weirdly, after it crashes when open with terminal no error is seen like there's nothing wrong.....
a bug?

---

### Post by sadaruwan12 on 2011-12-03
Well I'm using Lucid but never had a problem like this any way I don't use the search to do my software browsing I just click the software list area and type letters in and it shows what I'm looking for just like that.

---

### Post by meyou1 on 2011-12-05
maybe, but I want to solve my problem;
I reinstalled synaptic using Synaptic (ironically) by copy-pasting it's name in the searchbox;
even so, no help;
it still crashes even now.....no idea what I'm supposed to do :(

---

### Post by cortman on 2011-12-05
> **meyou1 said:**
> maybe, but I want to solve my problem;
I reinstalled synaptic using Synaptic (ironically) by copy-pasting it's name in the searchbox;
even so, no help;
it still crashes even now.....no idea what I'm supposed to do :(

Try uninstalling and reinstalling synaptic using the command line?

```

sudo apt-get remove synaptic

sudo apt-get install synaptic

```

---

### Post by meyou1 on 2011-12-13
nope, reinstalling it didn't help at all :(

---

### Post by meyou1 on 2011-12-25
hmm, this was unexpected
it seems synaptic is back to normal; I'm starting to think my system is just ******* with me
anyways, I didn't do anything to repair it, it just fixed itself it seems;
the only thing I ever changed was my system theme from atolm to orta and whenever I revert back to atolm it fu*ks synaptic back up; it seems the theme is the problem here so if you're having the same problem find a different theme bc that seems to be the cause of it! hope anyone who has the same problem will find this thread useful

---

### Post by meyou1 on 2011-12-25
-edited
it's not the atolm theme itself, it's a saved version of it;
I modified it and saved an instance of it along with the wallpaper;
the original unmodified theme doesn't seem to be the problem but my modified version seems to be it;
if it's bc of that you might want to del your custom saved theme and recreate it from the original theme again; I didn't do it myself but I've got a hunch it might solve the problem;
if not, then don't use any saved customized theme from atolm and it should be fine; suit yourselves!

---

