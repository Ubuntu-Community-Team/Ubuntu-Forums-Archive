---
title: "Mercury Messenger: Webcam and libjmutil.so"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Victormd on 2008-08-20
I've been trying to get web cam support under Mercury Messenger and Hardy, and after searching through the forum, I came across a few dead-end threads so let's try to start a new one.

I can receive webcam but can't send it. When trying to set it up under options, this is what I get:

> VidConf-libs.jar in classpath: Passed
JavaLibs-linux.jar in classpath.: Passed
Native library files for Linux found: Passed
Copy libjmutil.so: Failed

So I searched for libjmutil.so and found out that I needed to install JMF-2.1.1e, so from the Sun website, I found this package and installed it (after a few teaks to get it to install under Hardy). Everything seemed to have gone according to planned, but there's still no libjmutil.so and I get the exact same error as quoted above. Has anyone had to deal with this and got it to work under Hardy?

I really liked the way Mercury messenger looks (way better than aMSN) the functionality (i.e., video conference - if I can get it to work) and would really like to get it working. If anyone has an alternative msn messenger with looks and functionality, please let me know. I've tried emesene, amsn (so far the winner for me), pidgin, and now mercury.

---

### Post by panx00 on 2008-08-22
El archivo se encuentra en la ubicacion /usr/share/mercury/jni/jmf/libjmutil.so

Tienes que copiarlo a la carpeta /usr/lib/jvm/java-7-icedtea/jre/lib/i386/libjmutil.so

ai tu version java es otra remplaza java-7-icedtea por tu version java

---ejemplo---
sudo cp /usr/share/mercury/jni/jmf/libjmutil.so /usr/lib/jvm/java-7-icedtea/jre/lib/i386/libjmutil.so

despues de eso reiniciar mercury y todo funcionara correctamente.

---

### Post by Sef on 2008-09-04
> El archivo se encuentra en la ubicacion /usr/share/mercury/jni/jmf/libjmutil.so

Tienes que copiarlo a la carpeta /usr/lib/jvm/java-7-icedtea/jre/lib/i386/libjmutil.so

ai tu version java es otra remplaza java-7-icedtea por tu version java

---ejemplo---
sudo cp /usr/share/mercury/jni/jmf/libjmutil.so /usr/lib/jvm/java-7-icedtea/jre/lib/i386/libjmutil.so

despues de eso reiniciar mercury y todo funcionara correctamente. The file is located at /usr/lib/jvm/java-7-icedtea/jre/lib/i386/libjmutil.so

You must copy it to this folder /usr/lib/jvm/java-7-icedtea/jre/lib/i386/libjmutil.so

There your version java is another one replaces java-7-icedtea by your version java  

---example---

sudo cp /usr/share/mercury/jni/jmf/libjmutil.so /usr/lib/jvm/java-7-icedtea/jre/lib/i386/libjmutil.so

after that restart mercury and everything would work correctly.

---

### Post by Lucias_Wong on 2009-08-13
i have no file libjmulti.so  how i can do? i'm so wonder i has just already install java-6-sun jre but i can't found this files
best regard

---

### Post by cabruca on 2010-02-20
Hi All, this is my first post at Ubuntu!

I have tested several instant messengers on Karmic and now trying Mercury because all applications don't support webcam very well. Unfortunately, this is a problem with Mercury too.

I suppose that the command lines are wrong here. I copied the file

FROM 
/usr/share/mercury/jni/jmf/

TO
/usr/lib/jvm/java-7-icedtea/jre/lib/i386/

using nautilus in root mode. However I received the same message error that Victormd.

Could you please help? I suppose that the solution is here. I try Mercury homepage unsuccessfully. [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

Thank you!

PS: Now I will install jre6-18 from Sun's homepage.

---

### Post by semelle on 2010-06-18
sudo ln -s /usr/share/mercury/jni/jmf/libjmutil.so /usr/lib/jvm/default-java/jre/lib/i386

mercury &

---

