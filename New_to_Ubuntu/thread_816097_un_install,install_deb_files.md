---
title: "un install,install deb files"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by phanipalagummi on 2008-06-02
i have 2 doubts

1.how to un install the installed programs(did not installed from synaptic or add or rem.) using CLI

2.how to install .deb files using cli

and please give some material for installing and un installing softwares

---

### Post by Seisen on 2008-06-02
To uninstall packages from CLI:
```
sudo dpkg -r packagename
```

To install packages from CLI:
```
sudo dpkg -i packagename
```

---

### Post by phanipalagummi on 2008-06-02
i dont know the package name
because i downloaded .tar.gz file and installed using running in terminal
and i later renamed the .tar.gz file

---

### Post by ajgreeny on 2008-06-02
So what is the program used for and how do you start it?  Does it appear in the menus or do you use Alt+F2 for the run dialog box?  You must surely have a clue as to what you renamed the program's tar.gz file.  If so open it up with the archive manager by double clicking it and have a look for clues to its name.  Then you can try to remove it.

Without a few more clues and information it will be impossible to tell you what to do.

---

### Post by phanipalagummi on 2008-06-02
the program is flash player,i downloaded from site(link given in youtube)
running in terminal means i right clicked the extracted file(.tar.gz)and clicked the option run in terminal

---

### Post by durand on 2008-06-02
You should always check in synaptic to see if the package is there because it will be much easier to install and update. For Flash, install flashplugin-nonfree:

```
sudo aptitude install flashplugin-nonfree
```

You **do not** need to use the tar.gz file.

---

### Post by ajgreeny on 2008-06-02
You may even be able to remove it that way (synaptic), whether or not that is the way you installed it.

---

### Post by durand on 2008-06-02
No, not if it is a tar.gz file, ie, custom installer.

---

