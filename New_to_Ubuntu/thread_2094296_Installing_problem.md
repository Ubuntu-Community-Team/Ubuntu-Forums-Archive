---
title: "Installing problem"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by pensioner77 on 2012-12-13
I have 12.04 on my computer with win 7 as a partion. I was looking at an item on BBC page which stated that I needed to upgrade the installed "Flash" player I followed the download and the file 'install-flash-player-11 linux.i386.tar.gz' is now in the Archive Manager. I also tried to install a dedicated driver for my Canon printer and this file 'ip4500-debian.tar' is also in the Archive Manager. I am at a loss as to how to now get them installed?? I have tried to open them but receive a message about "Broken Dependences' and the suggestion to fix this by running either 'gksudo synaptic' or sudo apt-get install-f' in terminal. I tried both with no result. Can anyone explain how to proceed,I would add that I am an 81 year old novice at this IT stuff.

---

### Post by Mark Phelps on 2012-12-13
Sorry, but that's quite possibly the "hardest" way to install anything as it involved compiling executables from source, which requires the installation of packages and libraries to make that happen.

I read about something called FlashAid (or something like that) which you should be able to get from the Software Center -- and it will install Flash for you.

As to the drivers, I would first install Synaptic from the Software Center, as it does a much better job of detailing and reporting on installations and their progress, than does Software Center.

Once you do that, you should then go into Synaptic and install build-essential.  That will be needed to compile just about anything.

---

### Post by ibjsb4 on 2012-12-13
Do you have restricted formats installed, flash is part of that package.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by GordThompson on 2012-12-13
re: Flash

According to a previous thread here:

[http://ubuntuforums.org/showthread.php?t=1847124](http://ubuntuforums.org/showthread.php?t=1847124)

installing the Flash-Aid plugin would seem to be the easiest solution if you are using Firefox as your web browser.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)


re: printer driver

That .tar file looks like it contains a couple of Debian packages (.deb) files. To install them I *believe* that all you need to do is use Archive Manager to extract them to a convenient location, then double-click...

cnijfilter-common_2.80-1_i386.deb

...first, followed by...

cnijfilter-ip4500series_2.80-1_i386.deb

---

### Post by pensioner77 on 2012-12-14
Thanks all, I did it seems that there is no easy way such as just a double click in Windows, so I will have to continue to use the Win7 partition for any colour printing.

---

