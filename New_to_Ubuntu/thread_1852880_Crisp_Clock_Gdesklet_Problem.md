---
title: "Crisp Clock Gdesklet Problem"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by technosysind on 2011-10-01
I was trying to change some colors in Crisp Clock(gdesklet) by editing the source code.
I think I made a mistake and now I cannot even access the source code.
I want to now uninstall the Crisp Clock gdesklet and reinstall so that it atleast works as I'm really fond of it.

Please tell me how can I do that?
I'm attaching the screenshot of the error also

---

### Post by technosysind on 2011-10-02
bump

---

### Post by fantab on 2011-10-03
**Remove** gDesklets using Synaptic or Software Center. **Reinstall it**. 

gDesklets is very old... it has display issues with gtk3... it works well in gtk2 Distros, like Debian and LinuxMint, etc.

I really love CrispClock but as things are... I gave up.

---

### Post by technosysind on 2011-10-04
Hi, Thanks for the advice. I just uninstalled from synaptic and then reinstalled it. Guess what? Crisp clock appears itself with it and it is giving the same error. I think gdesklet was not fully uninstalled.

Is there a way to uninstall gdesklet fully? and when i reinstall gdesklet,  crisp clock is not there so that i can install a fresh copy of crisp clock manually?

---

### Post by fantab on 2011-10-04
> **technosysind said:**
> Hi, Thanks for the advice. I just uninstalled from synaptic and then reinstalled it. Guess what? Crisp clock appears itself with it and it is giving the same error. I think gdesklet was not fully uninstalled.

Is there a way to uninstall gdesklet fully? and when i reinstall gdesklet,  crisp clock is not there so that i can install a fresh copy of crisp clock manually?

After uninstalling gDesklets from Synaptic go to /Home and hit Ctrl+h your hidden files will be displayed... manually delete .gdesklets. Thats it.

Reinstall gdesklets and the crispclock.

---

### Post by wildmanne39 on 2011-10-04
Hi, you can also use this command to get rid of the it and the configuration files.
```
sudo apt-get --purge remove packagename
```
Thank you

---

### Post by technosysind on 2011-10-04
i did try purge remove but it did not work

---

### Post by technosysind on 2011-10-04
> **fantab said:**
> After uninstalling gDesklets from Synaptic go to /Home and hit Ctrl+h your hidden files will be displayed... manually delete .gdesklets. Thats it.

Reinstall gdesklets and the crispclock.


Its working now. I did what [fantab]("http://ubuntuforums.org/member.php?u=1275004") told me and it is working fine now.
Thank you so much [fantab]("http://ubuntuforums.org/member.php?u=1275004")

---

