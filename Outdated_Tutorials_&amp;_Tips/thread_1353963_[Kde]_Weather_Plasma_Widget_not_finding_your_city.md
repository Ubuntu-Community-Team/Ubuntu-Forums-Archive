---
title: "[Kde] Weather Plasma Widget not finding your city?"
date: 2009-12-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Islington on 2009-12-13
So there were some changes on recently to the way BBC delivers their weather info in their rss feeds. This has caused a breakage in the "search" of the plasma-widget. This will probably be fixed in lucid, but right now  if you lose your plasma configuration or accidentally delete the weather widget, there is no way to get it to find your city.

There is a workaround. It involves finding the new rss feed and giving it directly to your plasma-appletsrc file. Here is what you do. 

Part 1 getting the rss link:
0. Set your weather plasmoid using NOAA.
1. Navigate using your preferred webbrowser to the BBC weather website: [http://news.bbc.co.uk/weather/](http://news.bbc.co.uk/weather/)
2. Search for your city.
3. On the left hand side there is an Observations Box, it looks like this : 
[IMG]http://i.imgur.com/cVniP.png[/IMG]
4. click on the rss link, copy the rss link

Part 2 (editing your plasma-appletsrc).

1. Open Kate (or do this from vim or nano or ed)
2. Open /home/user/.kde/share/config/plasma-desktop-appletsrc
3. Scroll down until you see 
```
pressureUnit=
source=noaa|weather|[YOUR CITY]
speedUnit=mph
temperatureUnit=F
updateInterval=30
visibilityUnit=ml
```
4. Change this to:
```
pressureUnit=
source=bbcukmet|weather|[YOUR CITY]|[PASTE YOUR RSS LINK HERE]
speedUnit=mph
temperatureUnit=F
updateInterval=30
visibilityUnit=ml
```
5. Restart your plasma.

---

### Post by Islington on 2009-12-23
A heads up on this, but this seems to be fixed in kde 4.4 beta 2.

---

### Post by Jonathons on 2010-01-06
Thanks for this. 

Is the solution the same for multiple weather widgets (for more than one location)?

---

### Post by Islington on 2010-01-06
> **Jonathons said:**
> Thanks for this. 

Is the solution the same for multiple weather widgets (for more than one location)?

yes, the applets should appear separately in the appletsrc file.

---

### Post by nortexoid on 2010-01-09
Thanks!

(Beware: at first I forgot to put the rss link after the city name and it caused plasma-desktop to crash at login!)

---

### Post by Zeemvel on 2010-02-22
Hi,

I tried the above for "Brussels", and restarting the plasmoid does nothing. It still just keeps showing the stupid question mark and no city in its settings.

How can I get the weather of Brussels in a KDE widget in the taskbar?

In Gnome this was so easy... Namely just enter "Brussels" in it.

---

### Post by Shadyabhi on 2010-04-27
I have added the widget, but I am unable to find any relevant settings in the **plasma-desktop-appletsrc** file..

What can be the issue?? I am using kubuntu 9.10

---

### Post by Mark76 on 2010-05-15
I'm having the same problem. The lines mentioned appear nowhere in my plasma-desktop-appletsrc file despite the fact that I have weather-forecast installed.

Are you sure they exist?

---

### Post by Mark76 on 2010-05-15
Here's the file with the aforementioned lines busy not existing in it

> [$Version]
update_info=plasma_popupapplet_fix_groups.upd:PlasmaPopupAppletFixGroups1

[AppletGlobals][plasma_applet_pager]
rows=1

[AppletGlobals][plasma_applet_systemtray]
AyatanaNotifications=true
AyatanaNotificationsAlignment=66
ShowApplicationStatus=true
ShowCommunications=true
ShowHardware=true
ShowJobs=true
ShowNotifications=true
ShowSystemServices=true

[Containments]
JauntyUpgradeScriptRun=true

[Containments][1]
activity=
desktop=0
formfactor=0
geometry=0,0,1280,1024
immutability=1
location=0
plugin=desktop
screen=0
wallpaperplugin=image
wallpaperpluginmode=SingleImage
zvalue=0

[Containments][1][Applets][71]
geometry=20,45,22,19
immutability=1
plugin=ihatethecashew
zvalue=0

[Containments][1][Wallpaper][image]
slideTimer=600
slidepaths=/usr/share/wallpapers/
userswallpapers=
wallpaper=/usr/share/wallpapers/Winter_Track/
wallpapercolor=56,112,150
wallpaperposition=0

[Containments][14]
activity=
desktop=-1
formfactor=2
geometry=0,-215,1280,25
immutability=1
location=3
plugin=panel
screen=0
zvalue=150

[Containments][14][Applets][15]
geometry=817,0,142,24
immutability=1
plugin=systemtray
zvalue=0

[Containments][14][Applets][15][Configuration]
AutoHidePopup=true
hidden=KOrganizer Reminder Dæmon,hp-systray,update-notifier-kde

[Containments][14][Applets][15][Configuration][ExtenderItems][8]
extenderIconName=
extenderItemName=jobGroup
isCollapsed=false
isGroup=true
sourceAppletId=15
sourceAppletPluginName=systemtray

[Containments][14][Applets][15][Configuration][ExtenderItems][9]
extenderIconName=
extenderItemName=completedJobsGroup
extenderTitle=0 Recently Completed Jobs:
groupCollapsed=false
isCollapsed=false
isGroup=true
sourceAppletId=15
sourceAppletPluginName=systemtray

[Containments][14][Applets][15][PopupApplet]
DialogHeight=8
DialogWidth=0

[Containments][14][Applets][17]
geometry=991,0,211,24
immutability=1
plugin=digital-clock
zvalue=29

[Containments][14][Applets][17][Configuration]
announceInterval=0
defaultTimezone=Local
displayHolidays=false
holidaysRegion=gb
plainClockColor=20,19,18
plainClockFont=DejaVu Sans,23,-1,0,75,0,0,0,0,0
showDate=true
showDay=true
showSeconds=true
showTimezone=true
showYear=true
timeZones=
useCustomColor=false

[Containments][14][Applets][17][Configuration][ExtenderItems][10]
extenderIconName=view-pim-calendar
extenderItemName=calendar
extenderTitle=Calendar
isCollapsed=false
sourceAppletId=17
sourceAppletPluginName=digital-clock

[Containments][14][Applets][17][PopupApplet]
DialogHeight=248
DialogWidth=248

[Containments][14][Applets][18]
geometry=963,0,24,24
immutability=1
plugin=notifier
zvalue=2

[Containments][14][Applets][22]
geometry=1206,0,24,24
immutability=1
plugin=lockout
zvalue=0

[Containments][14][Applets][22][Configuration]
showLockButton=false

[Containments][14][Applets][28]
geometry=0,0,24,24
immutability=1
plugin=launcher
zvalue=1

[Containments][14][Applets][28][Shortcuts]
global=

[Containments][14][Applets][30]
geometry=196,0,617,24
immutability=1
plugin=panelspacer_internal
zvalue=3

[Containments][14][Applets][30][Configuration]
FixedSize=false

[Containments][14][Applets][33]
geometry=56,0,24,24
immutability=1
plugin=icon
zvalue=3

[Containments][14][Applets][33][Configuration]
Url=file:///usr/share/applications/kde4/rekonq.desktop

[Containments][14][Applets][35]
geometry=28,0,24,24
immutability=1
plugin=icon
zvalue=7

[Containments][14][Applets][35][Configuration]
Url=file:///usr/share/applications/kde4/dolphin.desktop

[Containments][14][Applets][36]
geometry=84,0,24,24
immutability=1
plugin=icon
zvalue=8

[Containments][14][Applets][36][Configuration]
Url=file:///usr/share/applications/kde4/ksysguard.desktop

[Containments][14][Applets][37]
geometry=112,0,24,24
immutability=1
plugin=icon
zvalue=8

[Containments][14][Applets][37][Configuration]
Url=file:///usr/share/applications/kde4/konsole.desktop

[Containments][14][Applets][38]
geometry=140,0,24,24
immutability=1
plugin=icon
zvalue=9

[Containments][14][Applets][38][Configuration]
Url=file:///usr/share/applications/kde4/kwrite.desktop

[Containments][14][Applets][41]
geometry=168,0,24,24
immutability=1
plugin=icon
zvalue=10

[Containments][14][Applets][41][Configuration]
Url=file:///usr/share/applications/kde4/ksnapshot.desktop

[Containments][14][Applets][75]
geometry=1234,0,24,24
immutability=1
plugin=weather
zvalue=0

[Containments][14][Applets][75][PopupApplet]
DialogHeight=308
DialogWidth=408

[Containments][14][Configuration]
maximumSize=1280,25
minimumSize=1280,25

[Containments][53]
activity=
desktop=-1
formfactor=2
geometry=0,-90,1280,28
immutability=1
location=4
plugin=panel
screen=0
zvalue=150

[Containments][53][Applets][55]
geometry=0,1,27,27
immutability=1
plugin=showdesktop
zvalue=10

[Containments][53][Applets][58]
geometry=31,1,1051,27
immutability=1
plugin=tasks
zvalue=22

[Containments][53][Applets][61]
geometry=1086,1,141,27
immutability=1
plugin=pager
zvalue=0

[Containments][53][Applets][63]
geometry=1231,1,27,27
immutability=1
plugin=trash
zvalue=0

[Containments][53][Configuration]
maximumSize=1280,28
minimumSize=1280,28

[General]
immutability=1


---

### Post by DJ_Peng on 2010-07-16
It didn't work for me. Neither the plasmoid nor the Beeb has any idea of where Malden, MA USA 02148 is, regardless of what permutation of the data I try.

---

### Post by nlaw on 2010-10-20
Some people have mentioned there is no weather entry in their plasma-desktop-appletsrc file.

The weather entry is only created first time the applet is succesfully configured, for me i just typed reading and reading Pennsylvania comes up, ok on it and let it configure.

Now look in the plasma-desktop-appletsrc file and the following entry should exist.

> [Containments][1][Applets][58][Configuration]
Share=false
pressureUnit=5008
source=bbcukmet|weather|[B]Reading Regional, Pennsylvania|[http://newsrss.bbc.co.uk/weather/forecast/3634/ObservationsRSS.xml](http://newsrss.bbc.co.uk/weather/forecast/3634/ObservationsRSS.xml)
speedUnit=9000
temperatureUnit=6001
updateInterval=30
visibilityUnit=2007

Or just copy and paste the avove entries into the file.

Now do as instructed in the first post as regards obtain the RSS feed from the BBC met website and paste it into the entry above replacing the text
> **Reading Regional, Pennsylvania|[http://newsrss.bbc.co.uk/weather/forecast/3634/ObservationsRSS.xml](http://newsrss.bbc.co.uk/weather/forecast/3634/ObservationsRSS.xml)**

Alternatively, download the full list of [BBC location codes]("http://www.clive-publishing.com/wp-content/uploads/2009/07/BBC_Weather_Observations_Codes_2009_07_08.pdf") open the 80 page document up and find your town, note it's code (right hand column) and replace the code for Basingstoke (4267) with the code for your town.


Here is an example for Basingstoke in the UK

> [Containments][1][Applets][60][Configuration]
Share=false
pressureUnit=5008
source=bbcukmet|weather|Basingstoke|[http://newsrss.bbc.co.uk/weather/forecast/4267/ObservationsRSS.xml](http://newsrss.bbc.co.uk/weather/forecast/4267/ObservationsRSS.xml)
speedUnit=9000
temperatureUnit=6001
updateInterval=30
visibilityUnit=2007

Removing the widget and adding it back to the desktop is not enough to get the widget using the new configuration. You will need to log out of KDE or reboot.

[IMG]http://www.mic-nucmed.co.uk/kde4.4.5.weather%20widget%20Basingstoke.jpeg[/IMG]

---

### Post by DJ_Peng on 2010-10-21
I've managed to get my city (Malden, MA 02148) added with an update to the plasmoid that also uses Google data to find the info. I also got an option to get info from AccuWeather but I stuck with Google since I'm not an AW user.

I'm not sure which version I'm running that brought the updated ability but I think it may have come after either installing Mint 9 KDE or the latest KDE updates.

I am having an issue with the text info not showing up on the tray icon but that may be more of a theme issue and I want to try to chase that down.

---

