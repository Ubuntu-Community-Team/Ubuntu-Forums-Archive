---
title: "How do I uninstall a program?"
date: 2019-02-03
forum: New to Ubuntu
---

### Post by redus on 2019-02-03
Hi all I'm just trying to figure out how to uninstall a couple of programs like vim and visual studio. I'd like to learn how to do this through the terminal, but any other ways are also appreciated. Thanks!!

---

### Post by yetimon_64 on 2019-02-03
For vim ...
```
sudo apt remove vim
```
or
```
sudo apt purge vim
```
The first code will remove the vim installation but may leave configuration files behind IF they exist on the system.
The second code will remove the vim installation AND any configuration files IF they exist.
Neither of the above codes will remove any config files in your home directory IF any such files exist; any home folder config files will need to be manually cleaned out of the home directory if they exist there.

Regarding visual studio, how have you installed it being a Microsoft package?
Are you running it in wine or have you added a microsoft repo and installed a debian package for it, for direct code usage in Linux ?
It will depend on how it was originally installed.

---

### Post by redus on 2019-02-04
yetimon, thank you. I think I tried "sudo apt uninstall vim", which didn't work, but I was able to just do it outside of the terminal. I opened "Show Applications" >> right click any app/program >> "Show Details" >> "Installed" >> find it and click "Remove"

---

### Post by yetimon_64 on 2019-02-05
Sounds like you discovered the software center program (I think the name is changed in newer releases, though not sure about that), there are other package manager GUI apps including my personal favorite "Synaptic package manager"; though Synaptic is not installed by default but is available in the repositories.

Have you managed to remove visual studio program with the GUI app you found as well?

---

### Post by SeijiSensei on 2019-02-05
> **redus said:**
> yetimon, thank you. I think I tried "sudo apt uninstall vim", which didn't work, but I was able to just do it outside of the terminal. I opened "Show Applications" >> right click any app/program >> "Show Details" >> "Installed" >> find it and click "Remove"

That's because the command is
```
sudo apt remove vim
```
not "uninstall."

---

