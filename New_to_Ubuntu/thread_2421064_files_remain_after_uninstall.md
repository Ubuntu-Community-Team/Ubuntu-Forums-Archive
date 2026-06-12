---
title: "files remain after uninstall"
date: 2019-06-15
forum: New to Ubuntu
---

### Post by josephfg on 2019-06-15
Sure this is a newbie question.

I uninstalled Tor Browser and the associated updater from the Programs GUI.  Seemed to work ok, but I checked the directory where the program had been, and it was still present, along with files and directories it had installed.  Is this normal behavior for uninstalling a program?  I deleted the whole directory manually, but shouldn't that have been done by the uninstall?

---

### Post by Bashing-om on 2019-06-15
josephfg; Well -

Depends on what the directive was to UN-install.
apt remove removes the binary, but NOT the configs; in the premise that the binary might be re-installed
whereas - apt purge also removes the config files on the premise that you want it all gone,
Now there may be files in your /home - that is your domain and the system will not mess with your domain, It is on you as to what you want to do with these.

[INDENT]make sense, yes ?
[/INDENT]

---

### Post by josephfg on 2019-06-19
Yes, that makes sense. It would appear, then, that the behavior of uninstalling from the Programs GUI (I am using Ubuntu Studio) is, by default, apt remove rather than apt purge.  Am I correct?

---

### Post by Bashing-om on 2019-06-19
josephfg; Welp;

I do CLI interface - I do not have the experience in the GUI to know what to expect.
Others here can advise here the better.

-aknowitall I am not-

---

### Post by Impavidus on 2019-06-20
It appears so. If you use the synaptic package manager (probably the best GUI package management tool), you can choose between remove and purge.

---

### Post by ajgreeny on 2019-06-20
> **Impavidus said:**
> It appears so. If you use the synaptic package manager (probably the best GUI package management tool), you can choose between remove and purge.

In synaptic the terminology used when you click on the package icon is "Mark for removal" or "Mark for complete removal", the latter being equivalent to Purge.

---

### Post by jikaczmarski on 2019-06-21
joesphfg; hey,
What version of linux are you running and are you using the default package manager?

Nevermind I see you're using Ubuntu Studio, if you are just clicking remove I assume you're using the actual software center as opposed to Synaptic Package Manager. The remove button marks for a soft removal but using synaptic you can do a full removal via the instructions above.

---

### Post by wildmanne39 on 2019-06-21
Hello and welcome to the forum jikaczmarski, please note this thread is marked solved.

Thanks

---

