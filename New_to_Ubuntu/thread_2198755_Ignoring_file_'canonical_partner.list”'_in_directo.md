---
title: "Ignoring file 'canonical_partner.list”' in directory '/etc/apt/sources.list.d/'"
date: 2014-01-10
forum: New to Ubuntu
---

### Post by singhal425 on 2014-01-10
Please find out the solution for this!

---

### Post by oldos2er on 2014-01-10
Moved to Absolute Beginners.

It helps to give as many details about your problem as possible, including Ubuntu version, copy/paste or screenshot of any errors, etc.

Open Software Center, Edit, Software Sources, Other Software tab, configure the partner repository how you prefer it.

To remove the problem file run ```
sudo rm /etc/apt/sources.list.d/canonical_partner*
```

---

### Post by deadflowr on 2014-01-10
How did you get a "canonical_partners.list in the sources/list.d folder?
canonical partners is part of the main sources.list file.
simply, as stated remove the file from the /etc/apt/sources.list.d folder and if your goal is to enable the canonical partners repos then
```
gksu gedit /etc/apt/sources.list
```
find the line[s](it is normally near the bottom) for the canonical partners, and remove the # symbol at the beginning.
Save the file and close it.
the run an update
```
sudo apt-get update
```

Added, you can also add a check to the entry in the program "software sources".
Depending on which version of Ubuntu you are using, you open that either through the settings in update-manager(12.04), or in later versions the program "software and updates".
Once open, in the software sources go to other software, canonical partners is part of this section, click the check box and close.

---

