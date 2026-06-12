---
title: "Sophos Antivirus installation"
date: 2017-05-04
forum: New to Ubuntu
---

### Post by johnny7oak on 2017-05-04
Hi, 
I downloaded Sophos Antiviral utility
It was a > ".tar"  
I extracted all the files into the folder,
extracted all that I could into sub-folders,
 now what do I do?

---

### Post by howefield on 2017-05-04
Run the following command (from the folder containing the extracted folder or use the path to it)

```
sudo sh install.sh
```

It will launch the install wizard and ask you several questions, once complete it will auto start.

```
sudo sh install.sh
[sudo] password for hugh: 



Sophos Anti-Virus
=================
Copyright (c) 1989-2016 Sophos Limited. All rights reserved.

Welcome to the Sophos Anti-Virus installer. Sophos Anti-Virus contains an on-access scanner, an on-demand command-line scanner, the Sophos
Anti-Virus daemon, and the Sophos Anti-Virus GUI.

On-access scanner         Scans files as they are accessed, and grants access
                          to only those that are threat-free.
On-demand scanner         Scans the computer, or parts of the computer,
                          immediately.
Sophos Anti-Virus daemon  Background process that provides control, logging,
                          and email alerting for Sophos Anti-Virus.
Sophos Anti-Virus GUI     User interface accessed through a web browser.


Press <return> to display Licence. Then press <spc> to scroll forward.
```

---

