---
title: "HOWTO: Compile and setup of Maxemum TV-Guide"
date: 2006-01-25
forum: Outdated Tutorials &amp; Tips
---

### Post by GoldBuggie on 2006-01-25
A great TV-Guide application for your favourite channels that I just needed to share. Works for ***Canada**,* the ***USA**,* the ***UK**,* ***Germany**,* ***Austria**,* ***Finland**,* ***Spain**,* the ***Netherlands**,**Hungary**,*  ***Denmark**,* ***Japan**, **Sweden**, **France**, **Norway***, *Belgium* and [I]**Romania**.



[/I]**[SIZE=3][COLOR=SeaGreen]Needed packages:[/COLOR][/SIZE]**
```
sudo apt-get install xmltv xmltv-gui xmltv-util build-essential checkinstall
``` [B][SIZE=3][COLOR=SeaGreen]
Download the latest source[/COLOR][/SIZE][/B]
[http://sourceforge.net/project/showfiles.php?group_id=137586]("http://sourceforge.net/project/showfiles.php?group_id=137586")

**[SIZE=3][COLOR=SeaGreen]Untar[/COLOR][/SIZE]**
```
tar xvzf [COLOR=Black][maxemumtvguide-5.10.26.tar.gz]("http://prdownloads.sourceforge.net/mtvg/maxemumtvguide-5.10.26.tar.gz?download")[/COLOR]
cd <NAME OF DIRECTORY>
``` 
[B][SIZE=3][COLOR=SeaGreen]Compile, build and install
[/COLOR][/SIZE][/B][COLOR=SeaGreen](uses checkinstall for .deb creation so that you can uninstall using regular apt/synaptic/adept)[/COLOR]
```
./configure --prefix=/usr
make
sudo checkinstall -D make install
``` 
**[SIZE=3][COLOR=SeaGreen]Configure which channels to fetch[/COLOR][/SIZE]**
To see which command to use for your country do a ```
ls /usr/bin/tv_grab_*
```. For me it is Sweden so I will use that as an example below. Just substitute the command for your country.
```
tv_grab_se --configure
``` [B]
[SIZE=3][COLOR=SeaGreen]Fetch the channels info[/COLOR][/SIZE][/B]
tv_grab_se --output ~/.xmltv/tvguide.xml
[B][COLOR=SeaGreen]
[/COLOR][SIZE=3][COLOR=SeaGreen]Start Maxemum TV-Guide and configure the update button[/COLOR][/SIZE][/B]
```
maxemumtvguide
``` goto **preferences->updates** and enter your *XML TV-File* ```
/home/<USERNAME>/.xmltv/tvguide.xml
``` and your *update command* ```
tv_grab_se --output /home/<USERNAME>/.xmltv/tvguide.xml
``` (make sure to use the full path to your xml-file since the application doesn't handle ~)

---

### Post by htonl on 2007-05-06
You can also download the prebuilt .deb package from [http://downloads.sourceforge.net/mtvg/maxemumtvguide_7.3.2-1_i386.deb]("http://downloads.sourceforge.net/mtvg/maxemumtvguide_7.3.2-1_i386.deb").

---

### Post by Buzzdee on 2008-08-11
For the other Germans among us: :)
Please use the grabber *_ch_search, this provides Swiss data, which is more or less the same as the German ones, some local programmes might be missing.

---

