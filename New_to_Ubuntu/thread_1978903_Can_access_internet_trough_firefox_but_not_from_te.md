---
title: "Can access internet trough firefox but not from terminal"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by gip_mad on 2012-05-12
Hello, I'm on vacation in France and I'm using public hotspots to get internet, the ones where you must input your user name and password on a web page to get access. I can navigate around on firefox, but the terminal can't get to the internet, apt-get fails and so do pings. I started downloading packages manually and compile them, but solving all cross references is killing me, it's taking the whole day.
I also tried this solution with no luck: [http://ubuntuforums.org/showthread.php?t=1677623](http://ubuntuforums.org/showthread.php?t=1677623)

Can anyone please suggest some workaround?
Thank you!
Regards

---

### Post by gip_mad on 2012-05-12
Hello, I'm on vacation in France and I'm using public hotspots to get internet, the ones where you must input your user name and password on a web page to get access. I can navigate around on firefox, but the terminal can't get to the internet, apt-get fails and so do pings. I started downloading packages manually and compile them, but solving all cross references is killing me, it's taking the whole day.
I also tried this solution with no luck: [http://ubuntuforums.org/showthread.php?t=1677623](http://ubuntuforums.org/showthread.php?t=1677623)

Can anyone please suggest some workaround?
Thank you!
Regards

---

### Post by CharlesA on 2012-05-12
They are using a captive portal. Login via firefox and then try running from the terminal.

---

### Post by gip_mad on 2012-05-12
I tried this, but the problem persists... I'm writing this post but can't use apt-get! :(

---

### Post by Utkarsh Ray on 2012-05-12
I think there is something there in the connection configuration. Click on network applet and make a new internet connection configuration, looking at the FireFox's connection setup may help.

If the only trouble is to be forced to download, compile, check dependencies etc.
1. visit packages.ubuntu.com
2. get list of everything needed for synaptic package manager
3. go to archive.ubuntu.com/ubuntu/pool
4. find synaptic here
5. Download the .deb's
6. install them using software center

Now to install programs
1. Open synaptic
2. Select the programs
3. File > Generate package download script
4. Extract URLs
5. download and save them and install

You can cd to the directory where .debs are saved and use dpkg -iR for install recursively.

---

### Post by overdrank on 2012-05-12
Threads merged.

---

### Post by gip_mad on 2012-05-12
Thank you! Synaptic works and can connect, but curiously "ubuntu software center" can't connect to the internet. This hopefully solves my software problem, but still doesn't explain why I can't use internet with my terminal... Oh well! Thanks! :)

---

