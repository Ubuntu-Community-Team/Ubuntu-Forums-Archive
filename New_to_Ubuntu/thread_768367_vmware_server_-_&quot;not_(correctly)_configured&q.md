---
title: "vmware server - &quot;not (correctly) configured&quot;"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by alzwded on 2008-04-26
Okay, so i read a few threads about this, but i couldn't manage to get a permanent fix for it. Evry time i (re)boot the /etc/not_configured file gets recreated and i have to delete it each and every time to get vmware running. Could anybody point me to a permanent solution for the prolem?

VMware runs fine after i delete the file but it's annoying to do so. Note, i did not have VMware player or previous version of server installed.

---

### Post by RealPSL on 2008-04-28
Based on the /etc/init.d/vmware script line 646 the /etc/not_configured file gets created if the VMware network configuration fails or if the virtual machine monitor fails. This obviously does not solve your problem but hopefully narrows your search area. Have you tried rerunning vmware-config.pl to ensure that is completes successfully?

---

### Post by alzwded on 2008-06-02
Well, finally got it working - running vmware-config.pl (or whatever its name was) makes vmware run into the same error. However, i remevoed the check for the not_configured file in the init script and it runs without any problems whatsoever (runs well, might i add :P) so basicly if you're 100% sure you configured it right and it says it's not configured, and you're looking for a temporary hack, sudo open the vmware init script, search for "not_configured" (without quotes) and delete the whole code block. It works fine for me now, it might be useful in the future.

And thanks for the tip RealPSL, but i couldn't find anything conclusive as to why it keeps creating the file each time. As far as i remember i think it got created when running at boot time. Despite the error, like i said, it runs fine without the check.

Another alternative would be creating a script:
```

sudo rm -f /etc/vmware/not_configured && vmware

```

P.S. (sorry for such vague info, i'm on another computer at the moment and cannot remember the file names/paths)

---

### Post by MartinG on 2008-11-15
The only trouble with this is that you lose the "safety check".  

This whole issue does all come down to start and stop scripts, it appears.  Building on the post by scananza in the following

[http://ubuntuforums.org/showthread.php?t=313362&page=2](http://ubuntuforums.org/showthread.php?t=313362&page=2)

I realized that the VMware install/configure process places K08vmware as well as S90vmware in /etc/rc2.d and for me at least this appears to be the problem.  I have now run the following two commands and that seems to sort it:

```
sudo update-rc.d -f vmware remove
sudo update-rc.d vmware defaults 90 08
```

The key difference from scananza's solution is that when/if you upgrade/reconfigure, you won't be left with K99vmware or S99vmware scripts lying around!

---

