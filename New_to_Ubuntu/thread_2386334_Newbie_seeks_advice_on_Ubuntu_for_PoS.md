---
title: "Newbie seeks advice on Ubuntu for PoS"
date: 2018-03-04
forum: New to Ubuntu
---

### Post by desertsweeper on 2018-03-04
Hi folks, I am done with using Windows for my clients PoS requirements. People scrape off the oem stickers and staff cut the power at night causing the machines to corrupt with regular monotony. I figured, why not try Linux... so I checked the vendor's website for the Point of Sale computers we use and of course it has "Ubuntu Drivers". It is really just a Core i3 in a Touch-Screen shell. My due-diligence was to determine that the hardware would work - which it seems it does (Main-unit and Printer both have Ubuntu Drivers listed on the manufacturer website; the application is purely web-based so that should not be a problem (surely..); we use 4G Dongles (SIM Card USB Sticks) for internet connectivity for the food-kiosks...that may be a problem but willing to roll-up my sleeves and try. I have 30+ years experience as an IT Consultant in a strictly Microsoft world and I want to move this client to Ubuntu. I want to install the absolute slimmest version of Ubuntu with ONLY a browser that can ONLY open two sites that I would define.
So my questions to the community is: Can I wipe Windows and install a slim+slick version of Ubuntu that will provide users with a touch-screen interface to the PoS web-app and if so - can someone point me in the right direction where I start the journey. Are there stripped-out lean versions I can use or do I need to download the standard distro and strip that out? I see mention of "Ubuntu Flavours" ([https://www.ubuntu.com/download/flavours](https://www.ubuntu.com/download/flavours)) - anything there I can start with?
Any advice would be most welcome. Thank you in advance

---

### Post by mikewhatever on 2018-03-04
I don't think any of that is a good idea. Ubuntu is not a drop in replcement for Windows, and your 30+ years of experience with Windows is an impediment rather then advantage. 
I'd recommend to start testing the water slowly with the default Ubuntu. You'll likely find it very different to what you are used to. 
Make sure things you use actually work, do not just wipe and install.

---

### Post by SeijiSensei on 2018-03-04
I say go for it.  Take a look at the discussions about building kiosks with Ubuntu.  That's basically your application, a networked device with a fixed web interface.

[https://www.google.com/search?q=ubuntu+kiosks](https://www.google.com/search?q=ubuntu+kiosks)

Here's an example that includes the terminal commands needed to create one using the "--kiosk" command-line switch in Chrome:  [https://thepcspy.com/read/converting-ubuntu-desktop-to-kiosk/](https://thepcspy.com/read/converting-ubuntu-desktop-to-kiosk/)

In a nutshell, that set of commands first installs two packages, openbox and pulseaudio (probably have that already).  Then he creates two files from the command prompt with the lines having "EOF" in them.  Everything from the first EOF to the next is written to a file like "/opt/kiosk.sh."  (This method avoids opening an editor to create the files.) The first file is a "bash script," a series of commands written for the standard "bash" shell (similar to Windows batch files).  The second is an arbitrary configuration file.  He sets things up so that when the machine reboots it goes directly to Chrome and loads his home page by running the command 
```
google-chrome --kiosk --no-first-run  'http://thepcspy.com'
```

I haven't tested that myself, but it might be worth a try.

I don't know if there are kiosk packages with a GUI installer.  Most of the advice you're likely to get will rely on the command prompt.

I'd make life easy at first and start with a complete Ubuntu distribution rather than building up from something stripped down.  Here are the ISO images for the [current stable version]("http://cdimage.ubuntu.com/xenial/daily-live/20180304/"), 16.04.  The next stable version will be out in April ("18.04").  If you want to get going tomorrow, use 16.04.  If you don't mind a few bumps along the way, you can try the [development version for 18.04]("http://cdimage.ubuntu.com/daily-live/20180304/").  To keep current, run the software updater every so often.

You can create a simple web page as the default site with links to the two locations you want to allow.  Store it somewhere like /opt/mysites.html and replace the command above with

```
google-chrome --kiosk --no-first-run  'file:///opt/mysites.html'
```

(Note the three slashes in the URL.) I believe you can also use the open-source Chromium, Chrome with all the proprietary bits removed.  If you install the chromium-browser package, you can [replace]("https://askubuntu.com/questions/358898/how-to-launch-google-chrome-chromium-application-shortcut-in-fullscreen-kiosk-mo") "google-chrome" with "chromium-browser" in the command above.

I'd guess the most likely issue would be the touch-screen interface, but I'm almost certain there are drivers and code for that, too.

If you can't get the 4G dongles to work, you could try using a portable hotspot and USB wifi adapters instead. Those little [Edimax adapters]("https://www.newegg.com/Product/Product.aspx?Item=N82E16833315091") work great with Linux.

---

### Post by desertsweeper on 2018-03-05
Thank you for the advice [**[COLOR=#000000]SeijiSensei[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195") and I get your point mikewhatever - but if we abandoned things to common sense we would still be in the ice-ages...so I will still have a play with this and see what happens.

I downloaded 16.04 and have spent the day getting to grips with it - just learning the system and underlying concepts. The touch-screen interface works out-of-the-box, amazingly. The 3G Dongle on the other hand is a no go (It is a D-Link device that natively appears as removable-storage) - despite several hours of tinkering. This is not a train-smash as I can just buy a cheap compliant replacement or use the hotspot concept [**[COLOR=#000000]SeijiSensei[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195") mentions above. What I have been struggling with this afternoon (in my time zone) is getting the Slip-Printer to work. It has a Java Installer and references Ubuntu v12 - But I am getting there slowly... What absolutely blows me away is how fast it loads. It is just a Core-i3 (with an Intel SSD) but when you hit the power button it is seconds to the login screen...amazing

I will have a play with the kiosk setup described above - that is pretty much exactly what I need...
Thanks again folks!

---

### Post by oldfred on 2018-03-05
I have not used kiosk, but saved some links now all are older, but do not think there are major changes.

 Kiosk discussions:
[http://ubuntuforums.org/showthread.php?t=2113023](http://ubuntuforums.org/showthread.php?t=2113023)
[http://ubuntuforums.org/showthread.php?t=1872560](http://ubuntuforums.org/showthread.php?t=1872560)
[http://ubuntuforums.org/showthread.php?t=1881141](http://ubuntuforums.org/showthread.php?t=1881141)
[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)
[http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/](http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/)
chromium kiosk using Tiny Core Linux. Talk about small and light!
[http://ubuntuforums.org/showthread.php?t=1891594](http://ubuntuforums.org/showthread.php?t=1891594)
[http://spins.fedoraproject.org/kiosk/#home](http://spins.fedoraproject.org/kiosk/#home)
Older
[http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm)
[http://jacob.steelsmith.org/category/section/ubuntu-kiosk-edition](http://jacob.steelsmith.org/category/section/ubuntu-kiosk-edition) 

Ubuntu has multiple flavors which are different desktops. Where desktop is gui & default applications.

These do not have gui, so you have to use command line to add most apps.
Ubuntu also has the minimal install which is just the kernel and enough drivers to use Ethernet to get on-line to download whatever added apps you want.
 [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
HowTo Achieve "Ubuntu-Desktop-Minimal" 
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961) 

It also has server version which is a little more than minimal and runs tasksel app which asks which type of server and then a set of default apps or even add a desktop with all its apps. You can skip adding apps for an install so that server is a little more than the minimal.
With my desktop installs, I converted from using gui to add additional apps and learned to use command line. Then copied command lines from history command into a bash (like a Windows .bat) file to install specific apps that I want.

 [https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

### Post by desertsweeper on 2018-03-05
oldfred, fantastic links, thank you. I am now playing with MinimalCD - just for the hell of it...but I can see that is going to require a whole new level of knowledge, although that really is the ultimate solution for my needs. Of big interest is the far easier-looking chromium kiosk build you reference...a busy week ahead....

---

