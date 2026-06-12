---
title: "Can Install AVIN2 for Kinect Ubuntu 13.10 64 bit"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by john_smith2 on 2014-02-26
Using Ubuntu 13.10 64 bit used this tutorial [http://igorbarbosa.com/articles/how-to-install-kin-in-linux-mint-12-ubuntu/](http://igorbarbosa.com/articles/how-to-install-kin-in-linux-mint-12-ubuntu/)

```
john@john-Aspire-5742:~/Kinect/sensorkin/Platform/Linux/CreateRedist$ sudo ./RedistMaker
Creating redist for Sensor v5.1.2.1
Cleaning previous outputs...
Building...
make: Entering directory `/home/john/Kinect/sensorkin/Platform/Linux/Build'
make -C XnCore CFG=Release
make -C XnDeviceSensorV2 CFG=Release
make[1]: Entering directory `/home/john/Kinect/sensorkin/Platform/Linux/Build/XnCore'
make[1]: warning: jobserver unavailable: using -j1.  Add `+' to parent make rule.
g++ -MD -MP -MT "./x64-Release/XnBuffer.d x64-Release/XnBuffer.o" -c -msse3 -O2 -DNDEBUG -I/usr/include/ni -I../../../../Include -I../../../../Source -I../../../../Source/XnCommon -DXN_CORE_EXPORTS -fPIC -fvisibility=hidden -o x64-Release/XnBuffer.o ../../../../Source/XnCore/XnBuffer.cpp
make[1]: Entering directory `/home/john/Kinect/sensorkin/Platform/Linux/Build/XnDeviceSensorV2'
make[1]: warning: jobserver unavailable: using -j1.  Add `+' to parent make rule.
In file included from ../../../../Source/XnCore/XnBuffer.cpp:25:0:
../../../../Source/XnCore/XnBuffer.h:28:18: fatal error: XnOS.h: No such file or directory
 #include <XnOS.h>
                  ^
compilation terminated.
g++ -MD -MP -MT "./x64-Release/Bayer.d x64-Release/Bayer.o" -c -msse3 -O2 -DNDEBUG -I/usr/include/ni -I../../../../Include -I../../../../Source -I../../../../Source/XnCommon -DXN_DEVICE_EXPORTS -fPIC -fvisibility=hidden -o x64-Release/Bayer.o ../../../../Source/XnDeviceSensorV2/Bayer.cpp
In file included from ../../../../Source/XnDeviceSensorV2/Bayer.h:28:0,
                 from ../../../../Source/XnDeviceSensorV2/Bayer.cpp:72:
../../../../Source/XnDeviceSensorV2/XnDeviceSensor.h:28:24: fatal error: XnPlatform.h: No such file or directory
 #include <XnPlatform.h>
                        ^
compilation terminated.
make[1]: *** [x64-Release/XnBuffer.o] Error 1
make[1]: Leaving directory `/home/john/Kinect/sensorkin/Platform/Linux/Build/XnCore'
make: *** [XnCore] Error 2
make: *** Waiting for unfinished jobs....
make[1]: *** [x64-Release/Bayer.o] Error 1
make[1]: Leaving directory `/home/john/Kinect/sensorkin/Platform/Linux/Build/XnDeviceSensorV2'
make: *** [XnDeviceSensorV2] Error 2
make: Leaving directory `/home/john/Kinect/sensorkin/Platform/Linux/Build'
john@john-Aspire-5742:~/Kinect/sensorkin/Platform/Linux/CreateRedist$ 

```

```
john@john-Aspire-5742:~/Kinect/sensorkin/Platform/Linux/CreateRedist$ sudo ./install.sh
ls: cannot access /home/john/Kinect/sensorkin/Platform/Linux/CreateRedist/./Lib/*: No such file or directory
john@john-Aspire-5742:~/Kinect/sensorkin/Platform/Linux/CreateRedist$ sudo sh install.sh
ls: cannot access /home/john/Kinect/sensorkin/Platform/Linux/CreateRedist/./Lib/*: No such file or directory
ls: cannot access /home/john/Kinect/sensorkin/Platform/Linux/CreateRedist/./Bin/*: No such file or directory
Installing PrimeSense Sensor
****************************

creating config dir /usr/etc/primesense...OK
copying shared libraries...cp: missing destination file operand after &#8216;/usr/lib&#8217;
Try 'cp --help' for more information.
OK
copying executables...cp: missing destination file operand after &#8216;/usr/bin&#8217;
Try 'cp --help' for more information.
OK
registering module 'libXnDeviceSensorV2KM.so' with OpenNI...install.sh: 111: install.sh: /usr/bin/niReg: not found
OK
registering module 'libXnDeviceFile.so' with OpenNI...install.sh: 111: install.sh: /usr/bin/niReg: not found
OK
copying server config file...cp: cannot stat &#8216;Config/GlobalDefaultsKinect.ini&#8217;: No such file or directory
OK
setting uid of server...chown: cannot access &#8216;/usr/bin/XnSensorServer&#8217;: No such file or directory
chmod: cannot access &#8216;/usr/bin/XnSensorServer&#8217;: No such file or directory
OK
creating server logs dir...OK
installing usb rules...cp: cannot stat &#8216;Install/55-primesense-usb.rules&#8217;: No such file or directory
OK
installing modprobe blacklist...cp: cannot stat &#8216;Install/blacklist-gspca-kinect.conf&#8217;: No such file or directory
OK
```

---

### Post by mörgæs on 2014-03-08
Now your original post has been decorated with five bumps. 

While it's technically OK to bump after more than 24 hours I doubt it will bring you answers. Might be better to read this:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by hellocatfood on 2014-04-19
This thread helped me. You need to check out the right version of OpenNi [http://stevenc1981.blogspot.co.uk/2013/10/to-run-nite-sample-in-ubuntu-1310-nite.html](http://stevenc1981.blogspot.co.uk/2013/10/to-run-nite-sample-in-ubuntu-1310-nite.html)

git clone git://github.com/OpenNI/OpenNI 

cd OpenNi

git checkout -b 1.5.4.0 Unstable-1.5.4.0

cd Platform/Linux/CreateRedist

./RedistMaker

cd ../Redist/$(Openni Version)/

sudo install.sh

---

### Post by david259 on 2014-07-28
you have to install freecnet driver, OpenNI and nite for Ubuntus 14.4? the app several OpenNI driver and nite which I setup to run well? I have installed the following from the app store> NiViewer libopenni-dev,-NiAudioSample Sample, Sample-NiBackRecorder, Sample-NiCRead, Sample-NiConvertXToONI, Sample-NiHandTracker, Sample-NiRecordSynthetic, Sample-NiSimpleCreate, Sample-NiSimpleRead, Sample-NiSimpleSkeleton , Sample-NiSimpleViewer, Sample-NiUserSelection, Sample-NiUserTracker, niLicense, niReg, libopenni-sensor-pointclouds0 and libopenni0 but then other programs do not work well. RGBD-slam've tried, and it works without ROS RTABmap works but only the interface, then when you Connect with kinect is blocked and now I've tried this but it gives me error compiling the library [http://pointclouds.org/documentation/tutorials](http://pointclouds.org/documentation/tutorials) / using_kinfu_large_scale.php # using-Kinfu-large-scale 
  the truth that makes me really need to scan 3D'm maker, and now I open a word lab near my town with some friends, we have a scanner and 2 senser 3D printers, and am looking for a way to have more than one scanner, without paying such high license, I have seen many things but none an worked for me to scan, the point is that people can go to scan what you want, I imprimirselo 3D but if we set 8 computers is 8 license thing no no we allow the help they give us for nogocio, we have we have purchased us! leaving us our savings, Ubuntus use since version 9 and fantastic I love and always will continue with it, I tell you this so you can see it is not a matter of me scanning the ass to grace and ready, if there is a program that works well 8 computers iran with Ubuntus, and I have to congratulate the new version 14.4 and the program 3D printers repsnapper buenisimo, I hope podais me hechar mates one hand, I do not want a business with windows: (

[http://robotica.unileon.es/mediawiki/index.php/PCL/OpenNI_tutorial_1:_Installing_and_testing#Installing](http://robotica.unileon.es/mediawiki/index.php/PCL/OpenNI_tutorial_1:_Installing_and_testing#Installing) ;)

---

