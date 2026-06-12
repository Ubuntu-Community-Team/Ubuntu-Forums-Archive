---
title: "i can't start mercury"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by esva on 2008-04-22
each time I try to start mercury, it doesn't pass from the splash window. i re-installed it, and it's the same
it says:
An unexpected problem was detected at 22.04.2008 09:47:56. This could mean mercury will stop running correctly.
Unique ID:82A42EAA
Description:Init failed.

And a part where it said I should ask for help etc
what's going on! help please

---

### Post by Ub1476 on 2008-04-22
Delete the configuration folder/files in ~/.mercury (this will reset all settings). If it doesn't help, launch mercury from the terminal:

```
mercury
```

---

### Post by esva on 2008-04-22
oh it didn't work still. thanks for the sugestion there

---

### Post by Ub1476 on 2008-04-22
Can also try this:

```
sudo apt-get remove --purge mercury
sudo apt-get install mercury

```

And, by launching it from the terminal, I mean you shall post the output from terminal, example:

```
kasper@kasper-desktop:~$ emesene
If you are reading this, you may want to enable debug
It's the first option in the connection tab in preferences
File /home/kasper/.config/emesene1.0/mail_here_hotmail_com/custom_emoticons/map does not exist, skipping
```

---

### Post by esva on 2008-04-22
I don't really get this, it means I should put a better java? or that i should put it in that resources folder? I did have mercury running before this disaster happened.


@unknown-desktop:~$ mercury
22.04.2008 10:56:31 Mercury/1.9 [20071020]
22.04.2008 10:56:31 Resource Type > General
22.04.2008 10:56:31 Locations > Loading...
22.04.2008 10:56:32 Locations > Loaded OK.
22.04.2008 10:56:33 Main > Loading Global Settings...
22.04.2008 10:56:34 Main > Loading Splash Screen...
22.04.2008 10:57:07 J1.5+ : false&&false -> 1.7.0
22.04.2008 10:57:07 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Self, Changeable color
22.04.2008 10:57:07 J1.5+ : false&&false -> 1.7.0
22.04.2008 10:57:07 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Self, Status color
22.04.2008 10:57:07 J1.5+ : false&&false -> 1.7.0
22.04.2008 10:57:07 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Self, Glass
22.04.2008 10:57:07 J1.5+ : false&&false -> 1.7.0
22.04.2008 10:57:07 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Self, Blue Purple
22.04.2008 10:57:07 J1.5+ : false&&false -> 1.7.0
22.04.2008 10:57:07 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Self, Blue Green
22.04.2008 10:57:07 J1.5+ : false&&false -> 1.7.0
22.04.2008 10:57:07 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Self, Teal Purple
22.04.2008 10:57:07 J1.5+ : false&&false -> 1.7.0
22.04.2008 10:57:07 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Self, Yellow Red
22.04.2008 10:57:07 J1.5+ : false&&false -> 1.7.0
22.04.2008 10:57:07 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Changeable color
22.04.2008 10:57:07 J1.5+ : false&&false -> 1.7.0
22.04.2008 10:57:07 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Status color
22.04.2008 10:57:07 J1.5+ : false&&false -> 1.7.0
22.04.2008 10:57:07 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Glass
22.04.2008 10:57:07 J1.5+ : false&&false -> 1.7.0
22.04.2008 10:57:07 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob
22.04.2008 10:57:08 J1.5+ : false&&false -> 1.7.0
22.04.2008 10:57:08 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsSteam.zip Steam Self Contact
22.04.2008 10:57:08 J1.5+ : false&&false -> 1.7.0
22.04.2008 10:57:08 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsSteam.zip Steam Default Contact
22.04.2008 10:57:08 J1.5+ : false&&false -> 1.7.0
22.04.2008 10:57:08 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsSteam.zip Steam Default Contact With Bullet
22.04.2008 10:57:08 J1.5+ : false&&false -> 1.7.0
22.04.2008 10:57:08 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsSteam.zip Steam Default Contact With Star
22.04.2008 10:57:08 J1.5+ : false&&false -> 1.7.0
22.04.2008 10:57:08 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsSteam.zip Steam Group

---

### Post by esva on 2008-04-22
this is the info log in mercury:

22.04.2008 13:08:56 Starting Mercury 1.9 (Build: 20071020)
22.04.2008 13:08:56 	Java Version:       1.7.0
22.04.2008 13:08:56 	Java Vendor:        Sun Microsystems Inc.
22.04.2008 13:08:56 	Java Home:          /usr/lib/jvm/java-7-icedtea/jre
22.04.2008 13:08:56 	Starting Path:      /usr/share/mercury
22.04.2008 13:08:56 	Encoding:           UTF-8
22.04.2008 13:08:56 	Classpath:          lib/JavaLibs-linux.jar (JMF for Linux)
22.04.2008 13:08:56 	                    lib/Skins.jar
22.04.2008 13:08:56 	                    lib/SpellCheck.jar (Spellcheck Support)
22.04.2008 13:08:56 	                    lib/VidConf-libs.jar (AV Conference Libraries)
22.04.2008 13:08:56 	                    lib/commons-jxpath-1.1.jar
22.04.2008 13:08:56 	                    lib/dMSN.jar (Mercury Core Lib)
22.04.2008 13:08:56 	                    lib/idle.jar (Idle Support for Linux & Windows)
22.04.2008 13:08:56 	                    lib/linuxtray.jar (Tray Support for Linux)
22.04.2008 13:08:56 	                    lib/sbbi-upnplib-1.0.2.jar
22.04.2008 13:08:56 	                    lib/skinlf.jar (Skins LF)
22.04.2008 13:08:56 	                    lib/substance-lite.jar
22.04.2008 13:08:56 	                    lib/upnp.jar (UPNP Support)
22.04.2008 13:08:56 	Library Path:       jni
22.04.2008 13:08:56 	                    jni/jmf
22.04.2008 13:08:56 	Operating System:   Linux 2.6.22-14-generic (unknown)
22.04.2008 13:08:57 	  Distro (Beta):    Ubuntu
22.04.2008 13:08:57 	System Info:        32bit on i386
22.04.2008 13:08:57 	Memory & CPU:       508 MiB, 1 Processor(s)
22.04.2008 13:08:57 	Timezone:           Venezuela Time
22.04.2008 13:08:57 	  Daylight time:    false
22.04.2008 13:08:57 	  Offset:           - 4h
22.04.2008 13:08:57 	Resources:          General
22.04.2008 13:08:57 
22.04.2008 13:08:59 
22.04.2008 13:09:01 IP > Name : unknown-desktop
22.04.2008 13:09:01 IP > Addr : 127.0.1.1
22.04.2008 13:09:01 IP > IP 1 : 127.0.1.1
22.04.2008 13:09:01 IP > LocalIP = 127.0.1.1
22.04.2008 13:09:19 Splash visible in 24s 793ms
22.04.2008 13:09:26 Sounds > 11 total.
22.04.2008 13:09:27 Emoticon > Packages: 2
22.04.2008 13:09:27 Emoticon > Enabled:  128
22.04.2008 13:09:27 Emoticon > Unique:   0
22.04.2008 13:09:34 Views > 38 default views loaded
22.04.2008 13:09:35 Views > 0 installed views loaded
22.04.2008 13:09:39 Status Icons > 12 packages
22.04.2008 13:09:44 Setting look and feel failed
22.04.2008 13:09:46 LFUtil > Java Metal LF set
22.04.2008 13:09:46 JMF > VidConf-libs.jar in classpath : Passed
22.04.2008 13:09:47 JMF > JavaLibs-linux.jar in classpath. : Passed
22.04.2008 13:09:47 JMF > Native library files for Linux found : Passed
22.04.2008 13:09:48 JMF > UnsatisfiedLinkError for jmv4l; /usr/lib/jvm/java-7-icedtea/jre/lib/i386/libjmutil.so, exists:false, length: 0
22.04.2008 13:09:48 JMF > Copy libjmutil.so : Failed
22.04.2008 13:09:48 
22.04.2008 13:09:48 JMF > WARNING !!!!!!!!!
22.04.2008 13:09:48 JMF > Mercury was unable to copy /usr/share/mercury/jni/jmf/libjmutil.so to /usr/lib/jvm/java-7-icedtea/jre/lib/i386/libjmutil.so.
22.04.2008 13:09:48 JMF > You probably need to do this manually for the JMF (including your webcam) to function properly in Mercury...
22.04.2008 13:09:48 JMF > WARNING !!!!!!!!!
22.04.2008 13:09:48 
22.04.2008 13:10:58 A problem has been detected:
22.04.2008 13:10:58 	Description: readImage failed for ./resources/AppData/Images/Default.zip!/icons/rename.png
22.04.2008 13:10:58 	StackTrace:
22.04.2008 13:10:58 		java.awt.image.RasterFormatException: IntegerComponentRasters must have ComponentSampleModel or SinglePixelPackedSampleModel
22.04.2008 13:10:58			at sun.awt.image.ByteComponentRaster.<init>(ByteComponentRaster.java:197)
22.04.2008 13:10:58			at sun.awt.image.ByteInterleavedRaster.<init>(ByteInterleavedRaster.java:192)
22.04.2008 13:10:58			at sun.awt.image.ByteInterleavedRaster.<init>(ByteInterleavedRaster.java:114)
22.04.2008 13:10:58			at java.awt.image.Raster.createPackedRaster(Raster.java:484)
22.04.2008 13:10:58			at com.sun.imageio.plugins.png.PNGImageReader.createRaster(PNGImageReader.java:870)
22.04.2008 13:10:58			at com.sun.imageio.plugins.png.PNGImageReader.decodePass(PNGImageReader.java:991)
22.04.2008 13:10:58			at com.sun.imageio.plugins.png.PNGImageReader.decodeImage(PNGImageReader.java:1189)
22.04.2008 13:10:58			at com.sun.imageio.plugins.png.PNGImageReader.readImage(PNGImageReader.java:1281)
22.04.2008 13:10:58			at com.sun.imageio.plugins.png.PNGImageReader.read(PNGImageReader.java:1553)
22.04.2008 13:10:58			at javax.imageio.ImageIO.read(ImageIO.java:1439)
22.04.2008 13:10:58			at javax.imageio.ImageIO.read(ImageIO.java:1343)
22.04.2008 13:10:58			at org.0.5.4.3.5(Unknown Source)
22.04.2008 13:10:58			at org.0.5.4.3.1(Unknown Source)
22.04.2008 13:10:58			at org.0.5.4.3.0(Unknown Source)
22.04.2008 13:10:58			at org.0.5.4.3.2(Unknown Source)
22.04.2008 13:10:58			at org.0.4.0.0.2(Unknown Source)
22.04.2008 13:10:58			at org.0.4.0.2.4(Unknown Source)
22.04.2008 13:10:58			at org.0.4.0.2.3(Unknown Source)
22.04.2008 13:10:58			at org.1.4.4.0.0(Unknown Source)
22.04.2008 13:10:58			at org.0.6.2.0.11.12(Unknown Source)
22.04.2008 13:10:58			at org.0.6.2.0.11.11(Unknown Source)
22.04.2008 13:10:58			at org.0.6.2.0.11.<init>(Unknown Source)
22.04.2008 13:10:58			at org.0.6.2.0.2.5.<init>(Unknown Source)
22.04.2008 13:10:58			at org.0.6.2.7.1(Unknown Source)
22.04.2008 13:10:58			at org.0.6.2.7.<init>(Unknown Source)
22.04.2008 13:10:58			at org.0.7.0.4(Unknown Source)
22.04.2008 13:10:58			at org.0.7.0.2(Unknown Source)
22.04.2008 13:10:58			at org.0.7.0.main(Unknown Source)
22.04.2008 13:10:58			at com.dMSN.Main.main(Unknown Source)
22.04.2008 13:10:58
22.04.2008 13:10:58 
22.04.2008 13:10:58 A fatal problem has been detected:
22.04.2008 13:10:58 	Description: init failed
22.04.2008 13:10:58 	StackTrace:
22.04.2008 13:10:58 		java.lang.RuntimeException: Error getting ./resources/AppData/Images/Default.zip!/icons/rename.png
22.04.2008 13:10:58			at org.0.5.4.3.5(Unknown Source)
22.04.2008 13:10:58			at org.0.5.4.3.1(Unknown Source)
22.04.2008 13:10:58			at org.0.5.4.3.0(Unknown Source)
22.04.2008 13:10:58			at org.0.5.4.3.2(Unknown Source)
22.04.2008 13:10:58			at org.0.4.0.0.2(Unknown Source)
22.04.2008 13:10:58			at org.0.4.0.2.4(Unknown Source)
22.04.2008 13:10:58			at org.0.4.0.2.3(Unknown Source)
22.04.2008 13:10:58			at org.1.4.4.0.0(Unknown Source)
22.04.2008 13:10:58			at org.0.6.2.0.11.12(Unknown Source)
22.04.2008 13:10:58			at org.0.6.2.0.11.11(Unknown Source)
22.04.2008 13:10:58			at org.0.6.2.0.11.<init>(Unknown Source)
22.04.2008 13:10:58			at org.0.6.2.0.2.5.<init>(Unknown Source)
22.04.2008 13:10:58			at org.0.6.2.7.1(Unknown Source)
22.04.2008 13:10:58			at org.0.6.2.7.<init>(Unknown Source)
22.04.2008 13:10:58			at org.0.7.0.4(Unknown Source)
22.04.2008 13:10:58			at org.0.7.0.2(Unknown Source)
22.04.2008 13:10:58			at org.0.7.0.main(Unknown Source)
22.04.2008 13:10:58			at com.dMSN.Main.main(Unknown Source)
22.04.2008 13:10:58
22.04.2008 13:10:58 
 I don't get this, but what should i do according to it?

---

### Post by Ub1476 on 2008-04-22
Post the output of those commands:

```
cd /usr/lib/jvm/java-7-icedtea/jre/lib/i386/

dir

sudo cp /usr/share/mercury/jni/jmf/libjmutil.so /usr/lib/jvm/java-7-icedtea/jre/lib/i386/libjmutil.so

mercury

#Quit the program if it still do not work and see if root mode works:

sudo mercury

```


Just in case you want a temporarily feature rich IM program, I suggest Emesene:)

---

