---
title: "Does swappiness affect wifi?"
date: 2013-08-04
forum: New to Ubuntu
---

### Post by GirlFromMars on 2013-08-04
I just installed ubuntu and it was running pretty slowly.  I have 2gb of Ram and saw suggestions of changing swappiness from 60 to 10.  I made a temporary change and this appeared to speed it up so I changed it in /etc/sysctl.conf.  Then on reboot it wouldn't connect to the wifi.  Just got stuck in an endless loop of trying to connect.  So I removed the line vm.swappiness = 10 and on reboot it will connect to the internet??!! 

This is the method I used:

[COLOR=#333333][FONT=Verdana]To temporarily change the swappiness value to 10, use the following command:[/FONT][/COLOR]
[INDENT][COLOR=#333333][FONT=Verdana]sudo sysctl vm.swappiness=10[/FONT][/COLOR]
[/INDENT][COLOR=#333333][FONT=Verdana]This change will be lost when your system restarts. If you want to preserve the value between boots, edit the /etc/sysctl.conf file:[/FONT][/COLOR]
[INDENT][COLOR=#333333][FONT=Verdana]gksu gedit /etc/sysctl.conf[/FONT][/COLOR]
[/INDENT][COLOR=#333333][FONT=Verdana]Look for vm.swappiness in the file and change its value. If it doesn’t exist, add it to the end of the file on a new line, like so:[/FONT][/COLOR]
[INDENT][COLOR=#333333][FONT=Verdana][FONT=Calibri]vm.swappiness=10[/FONT][/FONT][/COLOR]
[/INDENT]

---

### Post by ibjsb4 on 2013-08-04
Nope, [COLOR=#333333][FONT=Verdana]swappiness has nothing to do with wifi.  You got something else going on.  As for swap, you could just turn it off with [URL="http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gparted&sa=Search&cof=FORID:9"]gparted[COLOR=#333333] or ..

[http://manpages.ubuntu.com/manpages/precise/man8/swapon.8.html](http://manpages.ubuntu.com/manpages/precise/man8/swapon.8.html)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=turn+off+swap&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=turn+off+swap&sa=Search&cof=FORID:9)
[/COLOR][/URL]
[/FONT][/COLOR]

---

### Post by wildmanne39 on 2013-08-04
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

