---
title: "PyDev, JEE and CDT missing in Eclipse after Upgrade to Maverick"
date: 2010-11-11
forum: Programming Talk
---

### Post by navneeth on 2010-11-11
I had installed PyDev, the JEE package and CDT after installing Eclipse from the Lucid repo. Now that I take a look at Eclipse after upgrading to Maverick I don't find any of those perspectives available for use. I tried installing them again (*Help->Install New Software...*), but I get error messages saying that those things are already installed!

Current Eclipse SDK version: 3.5.2 Build id: M20100211-1343

---

### Post by pauljwells on 2010-11-25
Eclipse doesn't upgrade nicely. What you need to do is this:
Uninstall Eclipse (from synaptic or software center)
Then you need to sudo delete the folder /usr/lib/eclipse and all its contents. Then reinstall Eclipse. You can then reinstall all your plug-ins.

I think the new version of Eclipse doesn't seem to need to be started as sudo in order to install plug-ins. Try it as an ordinary user first. YMMV

---

### Post by navneeth on 2010-11-25
> **pauljwells said:**
> Eclipse doesn't upgrade nicely. What you need to do is this:
Uninstall Eclipse (from synaptic or software center)
Then you need to sudo delete the folder /usr/lib/eclipse and all its contents. Then reinstall Eclipse. You can then reinstall all your plug-ins.

I think the new version of Eclipse doesn't seem to need to be started as sudo in order to install plug-ins. Try it as an ordinary user first. YMMV

Thanks for your reply, Paul. Figuring that I didn't do Java all that much, I removed Eclipse and have begun finding my way around Geany and Code Blocks. However, I'll keep your tip in mind if I run into the same situation again. :)

---

### Post by chipr on 2010-12-22
It appears this bug is documented here:
[https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/633198](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/633198)

Unfortunately, I already de-installed Eclipse so I can't test out the proposed bundles.info change. I think I'm just going to download Eclipse and run it out of /opt.

---

