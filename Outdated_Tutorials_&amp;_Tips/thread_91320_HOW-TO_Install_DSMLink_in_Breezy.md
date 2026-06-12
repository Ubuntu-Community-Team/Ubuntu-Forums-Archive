---
title: "HOW-TO: Install DSMLink in Breezy"
date: 2005-11-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Ride Jib on 2005-11-16
**HOWTO: Install DSMLink in Breezy**

**Intro:** DSMLink is a piece of software in combination with a modified ecu for a 'DSM' vehicle. DSM vehicles include, but are not limited to, Mitsubishi Eclipses and  Eaglon Talons. The DSMLink company modifies your ecu with their custom chip so it can work with this software. The software lets you modify numerous settings as well as monitor everything that your car's ecu sees. I will guide you through setting this up to work on your Breezy laptop (because I'm sure nobody brings a desktop into their car to tune it). I doubt anyone will find this useful, but I figured I'd put it up here anyway.

**Version:** 2.5.2.16 (most recent version of DSMLink as of this HOW-TO)

Step 1: Install Blackdown's JDK libraries.
```
sudo apt-get install j2sdk1.4
```
Step 2: Download JavaComm API (this allows java to communicate with your serial ports)
*Note: This is a tarball I created of the necessary files. If you want to register at Sun.com and download the whole thing, go ahead.
```
wget http://ubuntuforums.org/attachment.php?attachmentid=3643&stc=1&d=1132202105
tar -xvf javacomm.tar.gz
```
Step 3: Place comm files in appropriate directories
```
sudo mv javax.comm.properties /usr/lib/j2se/1.4/jre/lib
sudo mv comm.jar /usr/lib/j2se/1.4/jre/lib/ext
sudo mv libLinuxSerialParallel_g.so libLinuxSerialParallel.so /usr/lib/j2se/1.4/jre/lib/i386

```
Step 4: Download DSMLink application file
```
wget http://www.dsmlink.com/dsmlink.jar
```
Step 5: Create space for DSMLink
```
mv dsmlink.jar /opt/
```

Step 6: Create code for launcher
```
sudo gedit /usr/bin/dsmlink.sh
```
Add the following to it:
```
cd /opt
java -jar dsmlink.jar

```

Step 7: Create a launcher.
```
sudo gedit /usr/share/applications/DSMLink.desktop
```

Then add this to the file:
```
[Desktop Entry]
Name=DSMLink
Comment=DSMLink Engine Management
Exec=dsmlink.sh
Icon=
Terminal=false
Type=Application
Categories=Application;Other;

```
Step 8: Refresh your panel:
```
sudo killall gnome-panel
```

Step 9: There is no Step 9

Happy tuning!

---

### Post by angrylittleman on 2005-11-17
Amazing.....I love the fact that true geeks drive DSMs....

Just as an aside, is there any other ECU mod software for linux?  For other makes?

---

### Post by Ride Jib on 2005-11-17
[QUOTE=angrylittleman]Amazing.....I love the fact that true geeks drive DSMs....

Just as an aside, is there any other ECU mod software for linux?  For other makes?[/QUOTE]

I'm sorry to disappoint you, but I actually don't drive a DSM. I drive a turbocharged 5.0 Mustang. I did this task for my roommate as his laptop had died and he is looking to make it to the track tomorrow night.

As for other makes, none that I know of. However, from what I have gathered, MegaSquirt is an OSS standalone engine management. A few of my friends have it, and everyone raves about how great it is, plus how cheap it is to comparable commercial products.

---

### Post by angrylittleman on 2005-11-17
Darn, if I could use OSS to run my supra, I would be in heaven.....

/BeginOT
Megasquirt looks pretty cool, but it is hard to be AEM for stand alone on the factory interface.  Sorry to hijack the tread
/EndOT

Thanks!

---

### Post by twdorris on 2005-11-17
[QUOTE=Ride Jib]I'm sorry to disappoint you, but I actually don't drive a DSM.[/QUOTE]
Don't be too disappointed.  I wrote the DSMLink application and it was actually developed originally under Linux for a couple years.  Then, reality smacks you in the face and you have to accept that 98% of your user base runs Windows, so what can you do?

Anyway, nice write up.  Thanks.  We will also be releasing a native Linux installer package at some point too (hopefully within a month or so), but because we really haven't had any requests for it, the project hasn't been on my high priority list.

Also note that this will probably work fine for second generation (1995-1999) DSMs because they use a "standard" 9600 baud interface to the ECU.  But first generation ECUs are limited to 1952 (that's not a typo) and the "normal" comm.jar from Sun does not allow this.  Additionally, the normal Sun dll for windows did not allow this either.  At least not without some touchup...  Not sure on the library you're using here.  But if the comm.jar is the one Sun provides by default, it won't allow the goofy baud rate selection.

Thomas Dorris
ECMTuning, Inc.

---

### Post by Ride Jib on 2005-11-18
[QUOTE=twdorris]Anyway, nice write up.  Thanks.  We will also be releasing a native Linux installer package at some point too (hopefully within a month or so), but because we really haven't had any requests for it, the project hasn't been on my high priority list.

Also note that this will probably work fine for second generation (1995-1999) DSMs because they use a "standard" 9600 baud interface to the ECU.  But first generation ECUs are limited to 1952 (that's not a typo) and the "normal" comm.jar from Sun does not allow this.  Additionally, the normal Sun dll for windows did not allow this either.  At least not without some touchup...  Not sure on the library you're using here.  But if the comm.jar is the one Sun provides by default, it won't allow the goofy baud rate selection.

Thomas Dorris
ECMTuning, Inc.[/QUOTE]

Thanks for the comments Thomas. I am using Sun's comm API, version 3.0.1, so you're right, it probably will not work on the 1G's. Perhaps over Thanksgiving holiday I will be able to search around more. I will let you know if I find anything interesting.

-Brad

---

### Post by Tsurara on 2005-11-20
Thank you SO much for this !

Now I don't have to buy a Windows laptop :)

---

### Post by 1fastgst on 2005-12-19
I have the dsmlink api running successfully, but when I try to connect to the ecu, I get a message that says "not all parameters suppported by kernel".  Then, there is a delay, and I get a command timeout.  I am using the same serial dongle that I use in windows.  I try the generic serialusb module, and I try the one that is written for my harware: belkin_sa.

My configuration is as follows:

2g dsmlink v 2.0
Belkin usb -> serial adapter (forget model, I left it in the car)
Slackware 10.1
Kernel 2.6.14.2  Custom

Do I have to 'setserial' the port to set the baudrate, or will it autodetect.  

I appreciate any replies that I recieve.

---

### Post by Ride Jib on 2005-12-20
The above HOWTO only includes the Java API files for the serial port communication. If you can find the files on Sun's website for USB communication, just download them and place them in the directory they specify (probably your lib directory). That should do it.

---

### Post by 1fastgst on 2005-12-21
[QUOTE=Ride Jib]The above HOWTO only includes the Java API files for the serial port communication. If you can find the files on Sun's website for USB communication, just download them and place them in the directory they specify (probably your lib directory). That should do it.[/QUOTE]

I am pretty sure that the usb -> serial is transparent.  I can be wrong though.  The kernel should handle all of the usb -> serial translations and the software should just connect to the device node without knowing what is going on.  This is not the problem.

I have the serial adapter in the house here.  I am going to mess with it today

Model is: f5U109

it uses the mct_u232 driver

From what I have been reading it is unable to generate breaks.  However in its native enviroment (windows)  it is also unable.  Since dsmlink works in windows, this must not be the problem.

This is the last thing I need to get working before I delete my windows partition. hehe

---

