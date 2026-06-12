---
title: "No-effort XGL/Compiz package (with AfterBirth)"
date: 2006-09-19
forum: Outdated Tutorials &amp; Tips
---

### Post by dyssident on 2006-09-19
Ive created a package to install and configure XGL/Compiz with Gnome as part of a larger project called [AfterBirth]("http://www.ubuntuforums.org/showthread.php?t=257116").

There are two ways to install: method 1 uses the full AfterBirth app, method 2 just installs the afterbirth-xgl-gnome package.

Method 1

```

sudo apt-get update && sudo apt-get upgrade
sudo cp /etc/apt/sources.list /etc/apt/sources.list.afterbirth-`date +%Y%m%d%H%M%S`
# Make sure universe is enabled
echo 'deb http://archive.ubuntu.com/ubuntu/ dapper universe' | sudo tee -a /etc/apt/sources.list
echo 'deb http://www.voxpopulimedia.com/debian dapper main' | sudo tee -a /etc/apt/sources.list
sudo apt-get update && sudo apt-get install afterbirth

```

After installation, run `afterbirth` from the command line or Applications > System Tools > AfterBirth. Select 'Gnome Eyecandy' to install XGL/Compiz.

Log out. Select Xgl from Sessions menu and log back in.

Please report your AfterBirth experience [to this thread]("http://www.ubuntuforums.org/showthread.php?t=257116").

Method 2

```

sudo apt-get update && sudo apt-get upgrade
echo 'deb http://www.voxpopulimedia.com/debian dapper main' | sudo tee -a /etc/apt/sources.list
echo 'deb http://www.beerorkid.com/compiz/ dapper main ' | sudo tee -a /etc/apt/sources.list
sudo apt-get update && sudo apt-get install afterbirth-xgl-gnome

```

Log out. Select Xgl from Sessions menu and log back in. Your fancy new eyecandy should start up immediately.

---

