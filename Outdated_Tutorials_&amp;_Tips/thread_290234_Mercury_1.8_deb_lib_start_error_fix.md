---
title: "Mercury 1.8 deb lib start error fix"
date: 2006-10-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Omnios on 2006-10-31
Greetings. This fix is based on the Mercury WIki fix on the Mercury Wiki which will not work with the Mercury 1.8.deb. The fix for Ubuntu is similar to there fix but the deb installes in differnt folders so these have to be modified. The original fix is located here.
[http://mercury.to/index.php?page=Wiki&wikipage=Linux_Setup](http://mercury.to/index.php?page=Wiki&wikipage=Linux_Setup)

> 

 Original fix that is being moded for Ubuntu.

 extract the update zip file to the directory you wish Mercury to be installed in (in this example I used /usr/share/Mercury)
 (*you might need to use sudo if you wish to install it in a location you  don't have write access to*)
[LIST=1]
[*] make sure permissions are correct
 (*chgrp -R users /usr/share/Mercury* and *chmod -R 775 /usr/share/Mercury*)
[*] make the starup script executable
 (*chmod +x /usr/share/Mercury/startup/startup_linux.sh*)
[*] finally create the symlink to the startup script
 (*ln -s /usr/share/Mercury/startup/startup_linux.sh /usr/bin/Mercury*)[/LIST]  Start Mercury by typing Mercury   Note: the startup script in 1.8 doesn't work with symlinks, use [this script]("http://download.mercury.to/1.8/startup_linux.sh") (save as, overwrite the old one)   To get the tray working on Linux, I suggest you read [this]("http://mercury.to/index.php?page=Wiki&wikipage=Linux_Tray")   

 First download the startup_linux.sh= [this script]("http://download.mercury.to/1.8/startup_linux.sh") now there are a few differences here the wiki states the files as being [I]/usr//mercury/startup/startup_linux.sh

 The ubuntu.deb install is in /usr/lib/mercury/startup[/I][I]/startup_linux.sh

 Also notice that the mercury directory is a small m not a capital M. 

The changes are as follows.
[/I]```

 extract the update zip file to the directory you wish Mercury to be installed in (in this example I used /usr/lib/mercury)
 (*you might need to use sudo if you wish to install it in a location you  don't have write access to*)
[LIST=1]
[*] make sure permissions are correct
 (*chgrp -R users /usr/lib/mercury* and *chmod -R 775 /usr/lib/mercury*)
[*] make the starup script executable
 (*chmod +x /usr/lib/mercury/startup/startup_linux.sh*)
[*] finally create the symlink to the startup script
 (*ln -s /usr/lib/mercury/startup/startup_linux.sh /usr/bin/mercury*)[/LIST]   Start mercury by typing sudo mercury        Start mercury with sudo mercury just for the first run so it can make files etc in root directories.

```

 Emjoy.

---

### Post by Meersie on 2006-11-01
Works like a charm!

Thanks!

---

### Post by Omnios on 2006-11-01
Debug round two:

 K the above fixes the lib errors. However now after closing and restarting I am getting this error 
```

./resources/settings/Default_Global.xml is not a valid XML file

```

 This is easily fixed by downloading the linux zip file.
[http://mirror.tuxhosting.net/mercury/1.8.zip](http://mirror.tuxhosting.net/mercury/1.8.zip)

 You can either unzip the hole thing or the specific file by navigationg /resources/settings/Default_Global.xml also this is the dir address to find the file after unzipping the hole package.
What you want is this file   Default_Global.xml and you need

 Now Cd / to the directory where you untared  Default_Global.xml

Use:
```

sudo mv Default_Global.xml /usr/lib/mercury/resources/settings

```

 I have tested this and it works. 

 If you have any problems post one.

---

### Post by Omnios on 2006-11-01
Debug round three

 K last bug is the menu setting as it does not work. This is rather simple to fix. First go: Menu: /system / Preferences / Menu Layout. 

 In the menu editor look for Internet and the Mercury entry. RIght click it and edit the command from what it was to messenger.

---

### Post by krauli on 2007-01-04
I got a problem :confused: 

I cant initialize Mercury. 

> rui@rui-laptop:~$ sudo mercury
22:34:10:625 Mercury/1.8 [20060811] starting...
22:34:11:685 [5%] Welcome root...
22:34:11:685 [10%] Starting Mercury 1.8...
22:34:11:685 [12%]   Verifying classpath...
22:34:11:685 [14%]   Verifying library path...
22:34:11:686 [16%] 
22:34:11:686 [18%]   Checking for update file...
22:34:11:686 [20%]   Loading tray icon...
22:34:11:736 [22%] Starting initializations
22:34:11:736 [24%]   18 initializations remaining
22:34:11:751 [26%]   17 initializations remaining
22:34:11:813 [28%]   16 initializations remaining
22:34:11:864 [30%]   15 initializations remaining
22:34:11:935 [32%]   14 initializations remaining
22:34:11:983 [34%]   13 initializations remaining
22:34:11:984 [36%]   12 initializations remaining
22:34:11:987 [38%]   11 initializations remaining
22:34:11:989 [40%]   10 initializations remaining
22:34:12:047 [42%]   9 initializations remaining
22:34:12:048 [44%]   8 initializations remaining
22:34:12:049 [46%]   7 initializations remaining
22:34:12:050 [48%]   6 initializations remaining
22:34:12:096 [50%]   5 initializations remaining
22:34:12:161 [52%]   4 initializations remaining
22:34:12:198 [54%]   3 initializations remaining
22:34:12:244 [56%]   2 initializations remaining
22:34:12:252 [58%]   1 initializations remaining
22:34:13:162 [60%]   0 initializations remaining
22:34:13:172 [70%]   Initializations done
22:34:16:665 [74%] Starting plugins...
22:34:16:665 [78%] Loading Startup Tabs...
22:34:17:525 [100%] Done.
22:34:17:530 [100%] init completed in 6932 ms
rui@rui-laptop:~$ mercury
22:34:44:037 Mercury/1.8 [20060811] starting...
22:34:45:167 [5%] Welcome rui...
22:34:45:168 [10%] Starting Mercury 1.8...
22:34:45:168 [12%]   Verifying classpath...
22:34:45:168 [14%]   Verifying library path...
22:34:45:168 [16%] 
22:34:45:168 [18%]   Checking for update file...
22:34:45:168 [20%]   Loading tray icon...
22:34:45:261 [22%] Starting initializations
22:34:45:264 [24%]   18 initializations remaining
22:34:45:270 [26%]   17 initializations remaining
22:34:45:297 [28%]   16 initializations remaining
22:34:45:338 [30%]   15 initializations remaining
22:34:45:368 [32%]   14 initializations remaining
22:34:45:370 [34%]   13 initializations remaining
22:34:45:467 [36%]   12 initializations remaining
22:34:45:481 [38%]   11 initializations remaining
22:34:45:521 [40%]   10 initializations remaining
22:34:45:585 [42%]   9 initializations remaining
22:34:45:660 [44%]   8 initializations remaining
22:34:45:692 [46%]   7 initializations remaining
22:34:45:706 [48%]   6 initializations remaining
22:34:45:711 [50%]   5 initializations remaining
22:34:45:768 [52%]   4 initializations remaining
22:34:45:773 [54%]   3 initializations remaining
22:34:45:783 [56%]   2 initializations remaining
22:34:45:811 [58%]   1 initializations remaining
22:34:46:718 [60%]   0 initializations remaining
22:34:46:727 [70%]   Initializations done
22:34:46:869 [74%] Starting plugins...
22:34:46:873 [78%] Loading Startup Tabs...
22:34:47:757 [100%] Done.
22:34:47:758 [100%] init completed in 3737 ms


i got this but also a grey window of mercury :-#

---

### Post by tonyo46 on 2007-01-06
Hello !

I have exactly the same problem as krauli. Everything seams to work fine but I only see a grey window !!

---

### Post by Wacky WeLsH LaD on 2007-01-18
You refer to a zip file. Where is it?

---

