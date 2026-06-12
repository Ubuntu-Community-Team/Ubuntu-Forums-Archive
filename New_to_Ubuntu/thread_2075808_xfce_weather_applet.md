---
title: "xfce weather applet"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-10-24
since i have upgraded to 12.10 cant get the weather applet to work. usually can fix most things but have been trying to get to work for over 2 weeks i had updated to 12.10 rc first. any help would be appreciated. tks

---

### Post by Cheesehead on 2012-10-24
Wel, according to [this previous thread]("http://ubuntuforums.org/showthread.php?t=2070807"), you did some investigating and tried a few solutions. What worked then?

---

### Post by Toz on 2012-10-24
What do you mean by "cant get the weather applet to work"? Does it start up? Does it display? 

Since you upgraded, what version of the weather applet is installed?
```
apt-cache policy xfce4-weather-applet
```

And, is there anything related and of interest in ~/.xsession-errors?

---

### Post by rburkartjo on 2012-10-25
weird spm show i have xfce-weather-plugin version 0.8.1-0ubuntu1

when i run the command you gave me i get

THIS IS A LINUX COMPUTER HAVE FUN
ray@ray-GC660AA-ABA-SR5123WM:~$ apt-cache policy xfce4-weather-applet
N: Unable to locate package xfce4-weather-applet
ray@ray-GC660AA-ABA-SR5123WM:~$

---

### Post by rburkartjo on 2012-10-25
from errors

(xfce4-panel:5414): xfce4-panel-CRITICAL **: Plugin weather: Unable to read from desktop file "/usr/local/share/xfce4/panel-plugins/weather.desktop"

---

### Post by Toz on 2012-10-25
> **rburkartjo said:**
> weird spm show i have xfce-weather-plugin version 0.8.1-0ubuntu1

when i run the command you gave me i get

THIS IS A LINUX COMPUTER HAVE FUN
ray@ray-GC660AA-ABA-SR5123WM:~$ apt-cache policy xfce4-weather-applet
N: Unable to locate package xfce4-weather-applet
ray@ray-GC660AA-ABA-SR5123WM:~$

oops. that should have been:
```
apt-cache policy xfce4-weather-plugin
```

> (xfce4-panel:5414): xfce4-panel-CRITICAL **: Plugin weather: Unable to read from desktop file "/usr/local/share/xfce4/panel-plugins/weather.desktop"
Interesting location for the desktop file - not the default location. Have you built the plugin manually at any point in time? 

You could try:
```
sudo ln -s /usr/share/xfce4/panel-plugins/weather.desktop /usr/local/share/xfce4/panel-plugins/weather.desktop
```

---

### Post by rburkartjo on 2012-10-27
toz here is output

THIS IS A LINUX COMPUTER HAVE FUN
ray@ray-GC660AA-ABA-SR5123WM:~$ apt-cache policy xfce4-weather-plugin
xfce4-weather-plugin:
  Installed: 0.8.1-0ubuntu1
  Candidate: 0.8.1-0ubuntu1
  Version table:
 *** 0.8.1-0ubuntu1 0
        500 [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal/universe amd64 Packages
        100 /var/lib/dpkg/status
     0.7.4-3+ppa1 0
        500 [http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/](http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/) precise/main amd64 Packages
     0.7.4-3 0
        500 [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) precise/universe amd64 Packages

THIS IS A LINUX COMPUTER HAVE FUN
ray@ray-GC660AA-ABA-SR5123WM:~$ sudo ln -s /usr/share/xfce4/panel-plugins/weather.desktop /usr/local/share/xfce4/panel-plugins/weather.desktop
[sudo] password for ray: 
ln: failed to create symbolic link `/usr/local/share/xfce4/panel-plugins/weather.desktop': File exists
ray@ray-GC660AA-ABA-SR5123WM:~$

---

### Post by pqwoerituytrueiwoq on 2012-10-27
were you using xfce 4.10 on 12.04?
if so i would use ppa purge on that ppa it might fix it 

my applet works great
```
~$ apt-cache policy xfce4-weather-plugin
xfce4-weather-plugin:
  Installed: 0.8.1-0ubuntu1
  Candidate: 0.8.1-0ubuntu1
  Version table:
 *** 0.8.1-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
        100 /var/lib/dpkg/status
~$ apt-cache policy xfce4-panel
xfce4-panel:
  Installed: 4.10.0-1ubuntu2
  Candidate: 4.10.0-1ubuntu2
  Version table:
 *** 4.10.0-1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by Toz on 2012-10-27
Looks like you installed the xubuntu-dev 4.10 packages in 12.04 then upgraded. Whats interesting is that the correct new version of the weather applet is installed, but it is referencing the location from the previous version. A few suggestions:

1. Remove the weather plugin from the panel, delete the ~/.config/xfce4/panel/weather*.rc file and the ~/.cache/xfce4/weather-plugin directory, and re-add the plugin (you will need to reconfigure it). Perhaps it is still somehow running the previous version.

2. What happens if you move the file that currently exists in /usr/local/share?
```
sudo mv /usr/local/share/xfce4/panel-plugins/weather.desktop /usr/local/share/xfce4/panel-plugins/weather.desktop.BAK
```
...does it work? Do you get the same error message?

3. If its still not working, then try to create the link:
```
sudo ln -s /usr/share/xfce4/panel-plugins/weather.desktop /usr/local/share/xfce4/panel-plugins/weather.desktop
```

4. Run ppa-purge against the xubuntu-dev version.

Hopefully #1 will fix it for you.

---

### Post by rburkartjo on 2012-10-27
toz still no go however compare my output to pk's whos applet is working and mine that isnt look at difference

THIS IS A LINUX COMPUTER HAVE FUN
ray@ray-GC660AA-ABA-SR5123WM:~$ apt-cache policy xfce4-weather-plugin
xfce4-weather-plugin:
  Installed: 0.8.1-0ubuntu1
  Candidate: 0.8.1-0ubuntu1
  Version table:
 *** 0.8.1-0ubuntu1 0
        500 [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal/universe amd64 Packages
        100 /var/lib/dpkg/status
     0.7.4-3 0
        500 [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) precise/universe amd64 Packages

---

### Post by rburkartjo on 2012-10-27
note the difference in the version table

---

### Post by pqwoerituytrueiwoq on 2012-10-27
have you tried purging it and reinstalling it?```
sudo apt-get purge xfce4-weather-plugin; sudo apt-get install xfce4-weather-plugin
```if that does not work use synaptic to force a version

---

### Post by rburkartjo on 2012-10-28
yes pq and still get the same results.

---

### Post by mr_pouit on 2012-10-28
Files in /usr/local do not come from official packages (same for the xubuntu-dev ppas), so either you have installed a buggy third-party package, or you compiled the plugin by yourself.

Also, files in /usr/local will override files in /usr, so you'll have to manually clean spurious files in /usr/local/lib/xfce4/panel/plugins, /usr/local/lib/xfce4/panel-plugins, /usr/local/share/xfce4/panel/plugins and /usr/local/share/xfce4/panel-plugins.

---

### Post by rburkartjo on 2012-10-29
mr did it still same problem

---

### Post by rburkartjo on 2012-10-29
any more ideas or should i just wait until xfce 4.12 or xubuntu 13.04 come out?

---

### Post by rburkartjo on 2012-10-30
i tried to reinstall the xubuntu desktop but that didnt help.

---

### Post by Frogs Hair on 2012-10-30
I responded to your other thread and the weather applet in the XFCE Goodies is working fine on 12.10. I had _My Weather Indicator_ working in the XFCE Session also but removed it because I had two weather indicators. In your last thread you indicated you found a solution.

---

### Post by rburkartjo on 2012-10-31
frog yes but still not working after update to 12.10.(i removed a ppa ) oh well will leave this thread open for a while. aggravating when i cant figure out how to fix

---

### Post by Frogs Hair on 2012-10-31
Is weather update showing up in the add to panel items ? Once added to the panel location settings can be made in properties found by right clicking the indicator.

---

### Post by rburkartjo on 2012-10-31
no it isnt frog but spm shows it is installed

---

### Post by Frogs Hair on 2012-10-31
Is the applet listed in the settings editor under panel? Keep in mind I am using the XFCE 4.10 session an not the Xubuntu desktop so there may be differences.

---

### Post by rburkartjo on 2012-10-31
my bad will switch to a xfce session and see if i have that option

---

### Post by rburkartjo on 2012-10-31
not in the xfce session either.

---

### Post by Frogs Hair on 2012-10-31
I have no suggestions other than resetting the panel.
 [http://bevanscanterburylife.blogspot.com/2011/02/reset-xfce-panel.html](http://bevanscanterburylife.blogspot.com/2011/02/reset-xfce-panel.html)

---

### Post by rburkartjo on 2012-10-31
frog will give that a try tks

---

### Post by rburkartjo on 2012-10-31
frog note the error message i get if i try the first line on the link you gave me.

THIS IS A LINUX COMPUTER HAVE FUN
ray@ray-GC660AA-ABA-SR5123WM:~$ xfce4-panel --exit
xfce4-panel: Unknown option --exit.

---

### Post by rburkartjo on 2012-10-31
frog really appreciate all your suggestions tks again

---

### Post by pqwoerituytrueiwoq on 2012-10-31
try ```
xfce4-panel --quit
``` instead
if the applet does not work on your guest account that will not help, if it does 
run this in place of that other rm command, that way it will not reset the entire panel to default
```
rm ~/.config/xfce4/panel/weather-*.rc
```

---

### Post by rburkartjo on 2012-10-31
tks pq first command worked but link by frog did help followed it to the tee! oh well

---

