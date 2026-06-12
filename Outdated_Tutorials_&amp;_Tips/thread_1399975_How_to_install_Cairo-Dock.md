---
title: "How to install Cairo-Dock"
date: 2010-02-06
forum: Outdated Tutorials &amp; Tips
---

### Post by fabounet on 2010-02-06
**Current Stable Release**

1) Enable the PPA in your list of repositories.

    ```
sudo -v
    echo "deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu $(lsb_release -sc) main ## Cairo-Dock-PPA" | sudo tee -a /etc/apt/sources.list
    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
    sudo apt-get update
```

2) Install the dock

```
    sudo apt-get install cairo-dock
```

**Weekly Build**
Contains the latest features and bug-fixes, but may also contain some bugs.
1) Enable the PPA in your list of repositories.
```
    sudo -v
    echo "deb http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu $(lsb_release -sc) main ## Cairo-Dock-PPA" | sudo tee -a /etc/apt/sources.list
    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
    sudo apt-get update
```

2) Install the dock

    ```
 sudo apt-get install cairo-dock
```

---

