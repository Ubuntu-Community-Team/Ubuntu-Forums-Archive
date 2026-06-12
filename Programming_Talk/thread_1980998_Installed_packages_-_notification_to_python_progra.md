---
title: "Installed packages - notification to python programme"
date: 2012-05-16
forum: Programming Talk
---

### Post by Tony Flury on 2012-05-16
I have a python programme which is being notified of file changes - using iNotify library - that works well.

I would like my programme to also capture changes to installed packages - i.e. someone executing "sudo apt-get install", or "sudo apt-get remove" or similar from the synaptic GUI.

is there a way to trap this simply - without the user having to go through extra steps.

Is there a master list of installed packages that gets updated that my programme could monitor using iNotify - or is there another method that can alert my application to changes in packages.

---

### Post by diesch on 2012-05-16
You can monitor /var/lib/dpkg/status

---

