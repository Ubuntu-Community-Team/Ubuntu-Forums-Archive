---
title: "Installing and running Anaconda"
date: 2018-08-28
forum: New to Ubuntu
---

### Post by romntkac2 on 2018-08-28
Hello everyone,
I'm having trouble to install and run Ananconda in Xubuntu.

I installed Anaconda using this guide: [https://tutorialforlinux.com/2018/01/21/anaconda-python-xubuntu-18-04-bionic-install/](https://tutorialforlinux.com/2018/01/21/anaconda-python-xubuntu-18-04-bionic-install/)

However I cannot lunch it by typing anaconda-navigator in the terminal.

Any ideas?

Thanks,
RB.

---

### Post by monkeybrain20122 on 2018-08-28
In terminal type 

```

source activate 
anaconda-navigator

```

(or source activate whatever virtual environment you want to load, by default it loads the "base" environment or "root")


You need "source activate" to invoke the conda environment before you can run anything installed in it.

---

