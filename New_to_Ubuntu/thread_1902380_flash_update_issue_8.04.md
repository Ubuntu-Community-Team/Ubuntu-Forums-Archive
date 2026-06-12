---
title: "flash update issue 8.04"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by jhonijim on 2011-12-30
Im running 8.04 I could not get my old firefox 3.6.17 to update flash said I have flash7 would not take the 10 update... installed firefox 9 if I load from root terminal it works and I have flash 10 but if I load it by clicking on thhe icon or through the terminal(not root) it  only has flash7.... any ideas don't really want root terminal open all the time.

---

### Post by lovinglinux on 2011-12-31
How did you install Firefox 9? You shouldn't use a root terminal to run Firefox, otherwise it will cause issues with the profile folder ownership.

All you need is to download Firefox from Mozilla and extract it to your home folder, then launch it from there.

---

### Post by jhonijim on 2011-12-31
I did extract it to my home folder but if I load it any way other than root it doesn't recognize the latest flash.... says shockwave flash 7.0 r68 and everywhere I go it says flash plugin has crashed.. if I load with root it shows flash 10 and everything works?????

---

### Post by crazy bird on 2011-12-31
First of all, Ubuntu 804 is out-of-date, it's no longer supported by Canonical. I advise you to upgrade to Ubuntu 11.10 (if your system can handle this version) or if you want stability use Ubuntu 10.04 LTS.
 
Secondly, to install the correct flash for your system, please read this: [https://sites.google.com/site/tipsandtricksforubuntu/multimedia/installing-flash](https://sites.google.com/site/tipsandtricksforubuntu/multimedia/installing-flash)

---

### Post by LowSky on 2011-12-31
flash is up to version 11 now. Just grab it from their website if you can. To run the newest firfox there is a few options, I think adding the ppa repo as best.

---

### Post by sammiev on 2011-12-31
> **jhonijim said:**
> I did extract it to my home folder but if I load it any way other than root it doesn't recognize the latest flash.... says shockwave flash 7.0 r68 and everywhere I go it says flash plugin has crashed.. if I load with root it shows flash 10 and everything works?????

Your not up to date! :( You really need to update by a few years.

---

### Post by lovinglinux on 2011-12-31
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

BTW, why are you still using 8.04?

---

### Post by LinuxFan999 on 2011-12-31
Ubuntu 8.04 is now End-Of-Life. I strongly recommend that you upgrade to Ubuntu 10.04 or 11.10.
After upgrading Ubuntu, you can get a newer version of Adobe Flash Player.

---

### Post by jhonijim on 2012-01-01
Here's the report.... as far as 8.04.... the system its running on could handle an update it's just some older parts thrown together to watch videos on and for my fiancee to play evony on.... has no cdrom and is using the same SCSI and install I've had in three machines now and i don't want to download all the stuff I've got installed would take forever i already hit my download allowance everyday(hughesnet)

---

### Post by lovinglinux on 2012-01-01
Run these commands on a terminal to remove conflicting plugins and put the flash 10 plugin in the proper place. Since I don't know exactly which software you have, there might be some applications that depend on these packages. If you see a message that other application not related to flash will be removed, let me know before proceeding:

```
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get remove libflash-mozplugin
sudo apt-get remove libflash0c2
rm /home/josh/.mozilla/plugins/libflashplayer.so
mv /home/josh/Desktop/install_flash_player_10_linux/libflashplayer.so /home/josh/.mozilla/plugins/libflashplayer.so
rm -fr /home/josh/Desktop/install_flash_player_10_linux
sudo rm -f /usr/lib/adobe-flashplugin/libflashplayer.so
sudo rm -f /usr/lib/flashplugin-nonfree/libflashplayer.so
```

Restart Firefox.

---

