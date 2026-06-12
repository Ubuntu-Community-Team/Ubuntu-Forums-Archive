---
title: "Finding source codes."
date: 2007-08-02
forum: Programming Talk
---

### Post by gamingx2005 on 2007-08-02
I wanted some source codes so I tried to get them by typing

sudo apt-get source <package name>

but I get an error, 
E: You must put some 'source' URIs in your sources.list
What is the problem. Am I missing something?

---

### Post by PaulFr on 2007-08-02
You should have some deb-src lines in your /etc/apt/sources.list file. Start Synaptic Package Manager and in Settings -> Repositories dialog, ensure that the Source checkbox is selected and then click Reload. Now exit Synaptic and run your sudo apt-get source <package_name>. If you add any repositories manually, please also add the relevant deb-src line.

---

