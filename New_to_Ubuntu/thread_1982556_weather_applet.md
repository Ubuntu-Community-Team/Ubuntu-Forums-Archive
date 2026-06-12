---
title: "weather applet"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-05-18
have the ubuntu, xbuntu, and xfce desktops installing on ubuntu 12.04. has anyone found a way of enabling the weather applet that was an option with xfce4.8. it is nowhere to be found in xfce4.10.
no big deal just curious. really like xfce4.10 though

---

### Post by Toz on 2012-05-18
How did you install 4.10? The xfce-weather applet needs to be recompiled for 4.10 so that it works.

---

### Post by rburkartjo on 2012-05-18
toz used a deb install(amd64)

[http://sourceforge.net/projects/babble777.u/files/xfce-4.10-daily/Ubuntu%2012.04/](http://sourceforge.net/projects/babble777.u/files/xfce-4.10-daily/Ubuntu%2012.04/)
also added this ppa to xubuntu
[http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html](http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html)
dont know how to  recompile.

---

### Post by Toz on 2012-05-18
It looks like its available in the ppa from your second link: [https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10?field.series_filter=precise]("https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10?field.series_filter=precise").

The following should get it for you:
```
sudo apt-get install xfce4-weather-plugin
```

---

### Post by rburkartjo on 2012-05-18
get this error message 


THIS IS A LINUX COMPUTER HAVE FUN
ray@ray-GC660AA-ABA-SR5123WM:~$ sudo apt-get install xfce4-weather-plugin
[sudo] password for ray: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xfce4-weather-plugin is already the newest version.


but it is not installed and dont see an option for it under add new items to the panel

---

### Post by rburkartjo on 2012-05-18
only could get the weather indicator that is standard with 12.04 to work

---

### Post by Toz on 2012-05-18
What does the following say?
```
apt-cache policy xfce4-weather-plugin
```

---

### Post by rburkartjo on 2012-05-18
here is the output

THIS IS A LINUX COMPUTER HAVE FUN
ray@ray-GC660AA-ABA-SR5123WM:~$ apt-cache policy xfce4-weather-plugin
xfce4-weather-plugin:
  Installed: 0.7.4-3+ppa1
  Candidate: 0.7.4-3+ppa1
  Version table:
 *** 0.7.4-3+ppa1 0
        500 [http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/](http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/) precise/main amd64 Packages
        100 /var/lib/dpkg/status
     0.7.4-3 0
        500 [http://mirrors.gigenet.com/ubuntuarchive/](http://mirrors.gigenet.com/ubuntuarchive/) precise/universe amd64 Packages

---

### Post by Toz on 2012-05-18
Hmmm - everything looks right. What if you tried reinstalling it?
```
sudo apt-get install --reinstall xfce4-weather-applet
```
...does it show up in the Items to add tab then?

---

### Post by rburkartjo on 2012-05-19
this is weird 

THIS IS A LINUX COMPUTER HAVE FUN
ray@ray-GC660AA-ABA-SR5123WM:~$ sudo apt-get install --reinstall xfce4-weather-applet
[sudo] password for ray: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xfce4-weather-applet
however spm shows i have xfce4-weather-plugin 0.7.4-3 installed

---

### Post by Toz on 2012-05-19
Sorry, my bad:
```
sudo apt-get install --reinstall xfce4-weather-plugin
```

---

### Post by rburkartjo on 2012-05-19
still no luck


THIS IS A LINUX COMPUTER HAVE FUN
ray@ray-GC660AA-ABA-SR5123WM:~$ sudo apt-get install --reinstall xfce4-weather-plugin
[sudo] password for ray: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  thunderbird-locale-zh-cn thunderbird-locale-en-gb thunderbird-locale-en-us gstreamer0.10-fluendo-mp3:i386
  liboil0.3:i386 thunderbird-locale-zh-hans thunderbird-locale-en
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 509 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/](http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/) precise/main xfce4-weather-plugin amd64 0.7.4-3+ppa1 [509 kB]
Fetched 509 kB in 1s (350 kB/s)                
(Reading database ... 265505 files and directories currently installed.)
Preparing to replace xfce4-weather-plugin 0.7.4-3+ppa1 (using .../xfce4-weather-plugin_0.7.4-3+ppa1_amd64.deb) ...
Unpacking replacement xfce4-weather-plugin ...
Processing triggers for hicolor-icon-theme ...
Setting up xfce4-weather-plugin (0.7.4-3+ppa1) ...

---

### Post by Toz on 2012-05-19
I think the babble777 and xubuntu-dev installs are conflicting. babble777 installs xfce into /usr/local while xubuntu-dev installs into /usr. 

Best bet to avoid future headaches would be to uninstall babble777 xfce and reinstall from xubuntu-dev. 

To try to fix this without uninstalling babble777, try this:
```
sudo ln -s /usr/lib/x86_64-linux-gnu/xfce4/panel-plugins/xfce4-weather-plugin /usr/local/lib/xfce4/panel-plugins/
sudo ln -s /usr/share/xfce4/panel-plugins/weather.desktop /usr/local/share/xfce4/panel-plugins/
```

---

### Post by rburkartjo on 2012-05-19
ln: failed to create symbolic link `/usr/local/lib/xfce4/panel-plugins/xfce4-weather-plugin': File exists

---

### Post by Toz on 2012-05-19
Then lets try:
```
sudo mv /usr/local/lib/xfce4/panel-plugins/xfce4-weather-plugin /usr/local/lib/xfce4/panel-plugins/xfce4-weather-plugin.BAK
sudo mv /usr/local/share/xfce4/panel-plugins/weather.desktop /usr/local/share/xfce4/panel-plugins/weather.desktop.BAK
```
...then
```
sudo ln -s /usr/lib/x86_64-linux-gnu/xfce4/panel-plugins/xfce4-weather-plugin /usr/local/lib/xfce4/panel-plugins/
sudo ln -s /usr/share/xfce4/panel-plugins/weather.desktop /usr/local/share/xfce4/panel-plugins/
```

If that doesn't work, it might be best to purge your system of the babble777 version and stick with just the xubuntu-dev PPA.

---

### Post by rburkartjo on 2012-05-19
toz didn't work okay how do i purge my system of  babble777


really appreciate the help

---

### Post by rburkartjo on 2012-05-19
toz got it figure out just ran

gksu nautilus /etc/apt/sources.list.d/

then removed both ppa and reinstalled the xubuntu one
works great tks again

---

### Post by Toz on 2012-05-19
Good to hear. Please mark this thread as solved. Thanks.

---

### Post by rosswmcgee on 2012-05-26
I found the two weather apps to be less than desired so... with opera I just put the weather channel on one tab and Intellicast radar on another. Better data, better picture. Sorry I wish they had just left the weather app that is in Classic, one stop
shop accurate data. Sometimes the improvements are not.

---

