---
title: "Howto:Upgrade Boinc Manager 5.4.11"
date: 2007-06-11
forum: Outdated Tutorials &amp; Tips
---

### Post by lonoy on 2007-06-11
Howto: Upgrade Boinc Manager 5.4.11 (Feisty 32 Bit)

Ubuntu 7.02 repositories offers the Boinc Manager 5.4.11. Unfortunately this version does not seem to  pay heed to your preferences and will keep your CPU running at 100%. If you don't wish this to occur then the following how to offers an alternative by upgrading the Boinc client to a later version. 

I am a Ubuntu novice, please use the following at your own risk.

Download  the latest Boinc version 5.8.16:

Go to : [http://boinc.berkeley.edu/](http://boinc.berkeley.edu/)

and click on the "Download and run BOINC software" link.

Download version 5.8.16 for Linux/x86 (4.25 MB). Save it to your home folder.

Login in as root.

Run the downloaded file in your Home directory. 

Open the folder it creates called Boinc.

Rename the bin file named boinc to boinc_client

Shut down Boinc. 

Copy the following files from your newly created bin folder :
boinc_client, boincmgr and boinc_cmd to your  /usr/bin/

Restart Boinc.

Edit the following file:

/etc/init.d/boinc-client

Add "ulimit -s unlimited" to a new line AFTER the lines that start with # then save. 

Open Boinc via Applications: Accessories. 

A different looking interface will appear known as the Simple View. Click on preferences and adjust your settings as applicable. Save.

Give the Boinc Manager a minute to adjust to the new settings then check your system monitor to see if your new CPU settings have taken effect. 

Clicking on Advanced on the Boinc Manager will take you to the familiar Boinc interface. To return to the Simple Interface select View: Simple Interface.

If you not a Boinc user and wish to learn more then please go to the following page which will give you further details on who you can put your computers down time to good use:

[http://boinc.berkeley.edu/projects.php](http://boinc.berkeley.edu/projects.php)


Cheers
Lonoy

Since posting the above I have located a Deb package for Boinc Manager 5.8.17. There is a package for Feisty 32 & 64 bit systems

[http://www.getdeb.net/app.php?name=Boinc](http://www.getdeb.net/app.php?name=Boinc)

Download it, right click to install and not only do you avoid the above work but also get the latest version;)

---

