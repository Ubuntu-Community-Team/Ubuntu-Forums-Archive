---
title: "ePSXe Guide for 64bit Users &amp; Proper ATI Graphic Card Driver Tutorial... TESTED! :D"
date: 2006-12-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Coldbird on 2006-12-04
First... due to me having enough trouble to setup the ATI fglrx Drivers (I HIGHLY SUGGEST TO INSTALL THEM IF YOU GOT A ATI CARD!) I also will explain how to install them...

--- ATI Driver Installation Guide ---
[SIZE="1"]Optional and only for ATI Users who want to use Hardware Acceleration with the PSX Emu... But trust me... you WANT HW-Acceleration in ePSXe... so you can enjoy the nice nice nice XGL2 Plugin from Pete... and therefore GOOD Graphix![/SIZE]
1. Uninstall xorg-driver-fglrx and fglrx-control Packages if you got them installed in your Ubuntu... This is important...

2. Start the Software-Source Manager and activate to also scan Universe and Multiverse Repositories... :-)

3. Install the following Packages using the Synaptic Package Manager :
linux-headers-generic
build-essential
debconf
dh-make
fakeroot
gcc-3.4
libstdc++5
module-assistant

4. Download a fglrx Driver that fits your Cards... Newer Cards will want to use something like 0.30.X and above... I use 0.30.3 - just if you wanna know... Or 0.28.X if you got some of the older Cards that aren't supported anymore in the newer Driver... ;-)

Btw... here's the Direct Link to the ATI fglrx Driver Download Page...
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=356](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=356)

5. Open a Terminal of your Choice and execute the following Command...
```
sudo ln -sf /bin/bash /bin/sh
```
This Code switches to Bash... you will need it to install create the needed Deb-Packages.

6. Navigate to where you downloaded the ATI fglrx Driver .run File and edit and execute this Command to fit your ATI fglrx Driver Filename:
```
./ati-driver-installer-X.XX.X.run --buildpkg Ubuntu/edgy
```

7. You should now have some Packages named like this... Some Version Numbers might be attached to the Filenames... but Im sure you Guys are clever enough to know what is what...
xorg-driver-fglrx - Graphic Card Driver (NEEDED)
fglrx-kernel-source - Kernel Driver Source (NEEDED)
fglrx-control - ATI-Configuration Device (optional)
fglrx-sources - Source for the Configuration Device (USELESS)
xorg-driver-fglrx-dev - Source for the Graphic Card Driver (USELESS)

8. chmod the Files xorg-driver-fglrx and fglrx-kernel-source to make them executeable and install them in the GUI... Dont worry... it MIGHT say it failed to install... it doesnt matter... For some Reason I couldnt get it running if I didnt take this Step... ;-)

9. Now in the Terminal execute the Bash Link Code again to revert to old Dash Settings...
```
sudo ln -sf /bin/dash /bin/sh
```

10. In the Terminal execute the following Lines of Code now...
```
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant a-i fglrx
sudo depmod -a
```

11. Open the Xorg-Config File - We need to do some Alterations... A good way to do so with Root-Access would be executing the following line of code in the Terminal...
```
sudo gedit /etc/X11/xorg.conf
```

In the **Section "Device"** Subarea switch the Tag Value of Driver from "vesa" to "fglrx".

At the End of the File add the following Code... And make sure you format it right...
```
Section "Extensions"
        Option "Composite" "Disable"
EndSection
```

Now save and close the File...

12. Reboot your System... You should now be able to choose higher Resolutions than 1024x768 and have proper OpenGL Hardware Acceleration...
You can check if everything went fine by opening a Terminal and executing the following Code...
```
fglrxinfo
```
If everything worked out... and you indeed now got Hardware Acceleration...
It should display something like this...
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300 Generic
OpenGL version string: 2.0.6119 (8.30.3)
```

Congratulations... you now got Hardware Acceleration...
If it didnt work out for you... its probably because of busted Installs... or other sort of damage you did to your System... :P

--- FAQ - Why does ePSXe not run on its own?! ---
ePSXe is a somewhat discontinued Project... its sad - but hell - its true... and there never was a 64bit Version of it out... :-(
Also once you installed 32bit Support the Thing fails to work... Afterall its a complicated Applications... Haha... :-)

What makes it work out of the Sudden?
A nice Module named lib32ncurses5 and some Tweaks of mine... :-)

Tweaks?
Actually its more of a 32 bit Module Collection I puzzled together from i386 RPM and DEB Files that are needed for ePSXe to work properly!...

--- Lets get us going... Cheerio! ---
Download that... Read Readme... and be happy...

WHAT? No big Tutorial? ---!!!
Yes... no Big Tutorial... I kept it simple and backed my Setup up for you Guys... just download it... follow the 6 or 7 Orders... and ur set... :-)
Also the Download contains about every useful Plugin you might need for Linux PSX Gaming... :P
[http://coldbird.free.fr/ubuntu/epsxe64bitubuntu.tar.gz](http://coldbird.free.fr/ubuntu/epsxe64bitubuntu.tar.gz)

---

