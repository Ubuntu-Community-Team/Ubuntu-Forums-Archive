---
title: "JMF don't detect WebCam on Ubuntu"
date: 2009-07-05
forum: Programming Talk
---

### Post by manoelcampos on 2009-07-05
Folks, I googled and searched in the forum, but I din't find any solution.
I have java 6 jdk and I installed JMF. I configured environment variables in my ~/.bashrc file with the lines below:

export JAVA_HOME=/usr/lib/jvm/java-6-openjdk
export JMFHOME=/usr/lib/jvm/java-6-openjdk/jre/lib
export CLASSPATH=$JMFHOME/ext/jmf.jar:.:$CLASSPATH
#export LD_LIBRARY_PATH=$JMFHOME/ext:$LD_LIBRARY_PATH

LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$JMFHOME/lib:$JAVA_HOME/jre/lib/i386:$JAVA_HOME/jre/lib/i386/client
export LD_LIBRARY_PATH

I tried the jmfinit and jmfregistry application, included in the jmf distribution, but jmfregistry doesn't detect my webcam in my notebook.

I putted the .so files into /usr/lib/jvm/java-6-openjdk/jre/lib/i386/ and
the jmf .jar files into /usr/lib/jvm/java-6-openjdk/jre/lib/

My system pass by the test of the page [http://java.sun.com/javase/technologies/desktop/media/jmf/2.1.1/jmfdiagnostics.html](http://java.sun.com/javase/technologies/desktop/media/jmf/2.1.1/jmfdiagnostics.html), showing: 

JMF Version... 2.1.1e
All Java Build
Native Libraries Found

But the webcam isn't detected.

Can someone help me?

---

### Post by Karthick.Mohanraj on 2009-08-08
I also got similar problem.
But the difference is The jmfregistry and jmfinit detected my wecam but the jmfstudio displays a scrambled output with grids and lines when I try to capture video.
(Webcam works fine with other applications egcheese)

Somebody help!!!

I your case, Is ur webcam works fine with other applications???

---

