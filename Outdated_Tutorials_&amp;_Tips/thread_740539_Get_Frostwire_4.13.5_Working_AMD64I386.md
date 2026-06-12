---
title: "Get Frostwire 4.13.5 Working AMD64/I386"
date: 2008-03-30
forum: Outdated Tutorials &amp; Tips
---

### Post by thatguy2223 on 2008-03-30
I wrote a crude shell script made from many threads to fix Frostwire, 
This will also fix Java web browser issues.

For best results, please remove "java-common package" before running this script.

Here is the code.
If you don't want the Firefox fix just delete icedtea-gcjwebplugin.
Otherwise you can download JavaFrost.sh and run it as root.

#!/bin/sh

#Frostwire 4.13.5 Install Script

#AMD64 and I386

#This will install Sun Java 1.6 I386/Firefox Java Fix

apt-get install ia32-sun-java6-bin icedtea-gcjwebplugin

#Please make /ia32-java-6-sun your default Java handler

update-alternatives --config java

#Frostwire 4.13.5 Install

wget -c -P /home  [http://superb-west.dl.sourceforge.net/sourceforge/frostwire/frostwire-4.13.5.i586.deb](http://superb-west.dl.sourceforge.net/sourceforge/frostwire/frostwire-4.13.5.i586.deb)
dpkg -i /home/frostwire-4.13.5.i586.deb

#Sun Java 1.6 Patch

LIB_TO_PATCH=libmawt.so
for f in `find /usr/lib/jvm -name "$LIB_TO_PATCH"`
do
echo "Patching library $f"
sed -i 's/XINERAMA/FAKEEXTN/g' "$f"
done

I hope this helps someone out there.

---

### Post by SilvaRizla on 2008-04-05
Legend, utter legend.  Thanks a lot

---

### Post by ravenon on 2008-04-05
Hey, thats a nice solution to Frostwire on 64 bit and the patch does a nice job for the java plugin.

An alternative to running Frostwire is to stay with the sun java 6 (64 bit) and start Frostwire with a script

#!/bin/sh
cd /usr/lib/frostwire &&
java -ea -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar

I found this solution somewhere else in the forums. Don't know why it works, but it does.

---

