---
title: "Adeona - System for tracking lost or stolen laptops"
date: 2008-10-08
forum: Outdated Tutorials &amp; Tips
---

### Post by nhenry on 2008-10-08
[Adeona]("http://adeona.cs.washington.edu/index.html")

> Adeona is the first Open Source system for tracking the location of your lost or stolen laptop that does not rely on a proprietary, central service. This means that you can install Adeona on your laptop and go — there's no need to rely on a single third party. What's more, Adeona addresses a critical privacy goal different from existing commercial offerings. It is privacy-preserving. This means that no one besides the owner (or an agent of the owner's choosing) can use Adeona to track a laptop. Unlike other systems, users of Adeona can rest assured that no one can abuse the system in order to track where they use their laptop. 

Step 1: Install the packages that Adeona needs
```
sudo apt-get install build-essential libssl-dev openssl traceroute cron
```

Step 2: [Download]("http://adeona.cs.washington.edu/sourcedownload.html") the latest version of Adeona to your home folder

Step 3: Unzip/Untar the tar file
```
tar -xvf adeona-0.2.1.tar.gz
```

Step 4: Move to adeona directory
```
cd adeona/
```

Step 5: Run the configuration and compile
```
./configure
make
```

Step 6: Install Adeona
```
sudo make install
```

Step 7: During the install it asks you to add a line to your cron/crontab... Make sure you copy this line, then open cron/crontab
```
sudo crontab -e
```

and then paste this line as a new line at the end of your cron/crontab file and then save it.

---

