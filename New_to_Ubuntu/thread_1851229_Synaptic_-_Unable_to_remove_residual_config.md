---
title: "Synaptic - Unable to remove residual config"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by mdavis1231 on 2011-09-27
Ubuntu 11.04 Natty isn't letting me remove any residual configuration packages through Synaptic Package Manager.  I check all of them, mark them for complete removal, but the "Apply" button remains unactivated.  I'm seeing posts all over the Internet regarding this, but have yet to find a solution.  Has  anyone been able to resolve this issue?

[B]Mark in Cincinnati
*"It's great to be free from Windoze...YIPPEE!!!"* ):P
[/B]

---

### Post by dwasifar on 2011-09-27
Remove the packages from the terminal instead.  

sudo apt-get remove [packagename1] [packagename2] etc.

---

### Post by mdavis1231 on 2011-09-27
I did figure out that you can "fool" Synaptic Package Manager.  You simply have to mark a package for installation which will activate the "Apply" button, then mark all of the residual configurations for complete removal, then _**unmark**_ your installation, and the "Apply" button will remain activated, and you can remove the residual configuration packages.

Not really sure why this hasn't been fixed by now...isn't 11.10 due out next month????? :confused:  Hmmmmm.....

[B]Mark in Cincinnati
*"It's great to be free from Windoze...YIPPEE!!!" ):P*
[/B]

---

