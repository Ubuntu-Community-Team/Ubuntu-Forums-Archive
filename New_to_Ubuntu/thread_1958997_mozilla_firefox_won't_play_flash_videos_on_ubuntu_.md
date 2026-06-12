---
title: "mozilla firefox won't play flash videos on ubuntu 11.10?"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by linuxlooser on 2012-04-15
whenever i try and play a video, i comes up with:

"you need the latest version of adobe flash player _get it here_"
so i download it, restart mozilla and it still doesn't play any video's
i've tried lots of sudo stuff and it always comes up with something along the lines of "E: *whatever was typed in* couldn't be found"
 
i remember seeing something about removing ubuntus gnash player or something but not sure :S
thanks in advance!

---

### Post by bobman321123 on 2012-04-15
I'm not sure about this... but I heard something about Adobe deciding to *only* support Chrome for flash in the future... 

I could be wrong though.

---

### Post by NikTh on 2012-04-15
Hi linuxlooser (what with the username? haha)

Try to install flash player from terminal
Open terminal(ctrl+alt+t) and type ```
sudo apt-get install adobe-flashplugin 
``` When installation finish open Firefox and check if works.

If something goes wrong with installation process , copy-paste the output of terminal here.

---

### Post by Curtis6767 on 2012-04-15
There is also Flash-Aid on the Firefox web site.

BTW, I have Shockwave Flash 11.2 r202 installed on my 12.04 LTS Beta system and so far I am not having these issues.

---

### Post by lovinglinux on 2012-04-15
Please attach the firefox-report.txt file generated in your desktop after running the commands below:

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'pluginreg.dat' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat ~/.mozilla/firefox/**/pluginreg.dat >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

