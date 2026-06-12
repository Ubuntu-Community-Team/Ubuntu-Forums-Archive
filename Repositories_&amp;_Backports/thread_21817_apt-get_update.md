---
title: "apt-get update"
date: 2005-03-24
forum: Repositories &amp; Backports
---

### Post by ron126 on 2005-03-24
When i type "apt-get update" or "apt-get upgrade", will only my ubuntu linux be updated or are all the programs in ubuntu will be updated?

Furthermore, what is the difference between these 2 commands

---

### Post by mtron on 2005-03-24
"apt-get update" reads the total package list from the remote servers you have in your  sources list 
"apt-get upgrade" does the updating
"apt-get dist-upgrade" does the upgrading to newer versions - if available

all this can also be done via a GUI program called synaptic package manager. Locate it in System - Administration (hoary)

---

