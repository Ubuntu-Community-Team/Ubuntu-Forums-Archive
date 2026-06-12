---
title: "How to clean installed programs/start fresh without a full reinstall?"
date: 2013-05-19
forum: New to Ubuntu
---

### Post by abexman on 2013-05-19
So my installs of Ubuntu that I have been running for some months have a number of pieces of software I have installed via terminal that I don't need. A lot of things I installed in attempts to fix one issue or  another I was having, and I still haven't quite got how to "uninstall" a lot of this stuff. They don't show easily or intuitively in Synaptics Package Manager for example. I might have configured OS related settings in a sub-optimal way. I'm sure some of these things have dependencies too which I would imagine might make them difficult to remove for me.

Is there a way without having to reinstall the whole OS, to sort of wipe the programs installed and maybe set Ubuntu back to default state without losing all my directories/file structure?

Sorry if I am being sort of vague. I'll see if I can give some examples if it helps.

---

### Post by ajgreeny on 2013-05-19
Example of what and how you installed would certainly help as "installed via terminal" does not really tell us enough detail; did you compile and install from source or did you use a shell script from the application website, as you can do for hplip, for example.

---

### Post by oldos2er on 2013-05-19
> **abexman said:**
> So my installs of Ubuntu that I have been running for some months have a number of pieces of software I have installed via terminal that I don't need. A lot of things I installed in attempts to fix one issue or  another I was having, and I still haven't quite got how to "uninstall" a lot of this stuff. They don't show easily or intuitively in Synaptics Package Manager for example. 

In Synaptic, click the Status bar in the lower left corner, then in the upper left corner click Installed. All your installed packages are listed here, so to uninstall one, right-click on it, and check either Mark for Removal, or Mark for Complete Removal. Complete Removal uninstalls the package, its dependencies (same as Removal), and any system configuration files, not including any config files in your home folder; those will need to be manually removed.

---

