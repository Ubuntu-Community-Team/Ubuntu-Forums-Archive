---
title: "How can i remove KDE?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by iwannalearn on 2008-05-10
Before i used KDE but now i am using gnome only, is there a way to remove all KDE?

When i boot up i get the kubuntu and not ubuntu (where the line shows before splash screen)

I am also having a problem when i select system > preferences > art manager it seems a window open for a fraction of a second then closes?

Thanks

---

### Post by N.N. on 2008-05-10
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)?

---

### Post by iwannalearn on 2008-05-10
Ok seems to have done the trick, only thing now when i go Applications > Add/Remove i get the following;

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

Is there something i must enable within Synaptic?

Thanks

---

### Post by N.N. on 2008-05-10
I've never encountered that problem before. [Supposedly]("http://ubuntuforums.org/showpost.php?p=3001962&postcount=10") you can fix it by reverting to a backup version of /var/lib/dpkg/status:
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-BROKEN
sudo cp -a /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by iwannalearn on 2008-05-10
Ok tried the above with no luck!

But i did go Synaptic Package Manager and reinstalled kio-unmountwrapper and all is back!

Many thanks

---

