---
title: "Sorry, you need a Java-enabled browser to see the simulation."
date: 2018-07-03
forum: New to Ubuntu
---

### Post by sed_faster on 2018-07-03
Hello,

I can't resolve this problem it Java on firefox "Sorry, you need a Java-enabled browser to see the simulation." on this website: [http://ecee.colorado.edu/~mcleod/teaching/Circuits2250/Extras/circuit/e-pnp.html](http://ecee.colorado.edu/~mcleod/teaching/Circuits2250/Extras/circuit/e-pnp.html)

I was try install java on firefox but I can't find the software or plugin through add-on options on browser. Have any idea how can I solve this issue? Also I tried google chrome, but hte result it is the same!

Thanks

---

### Post by QIII on 2018-07-03
Hello!

Neither Firefox nor Chrome support NPAPI plugins such as the old Java plugin.  Mozilla dropped that in all versions after 52.

Mozilla offered Firefox 52 ESR, a 32 bit version of FF, which still supported Java.  I'm not sure that it is still available.

The page you are trying to access is 10 years old.  If it uses a Java applet, you are out of luck unless you find and install FF 52 ESR.

Just to avoid confusion, the Java plugin and JavaScript are two entirely different things.

---

### Post by Holger_Gehrke on 2018-07-03
You are (somewhat) in luck. This applet actually seems to work with the appletviewer, a tool that's part of the jdk and is actually meant to debug applets without a browser. Open a terminal and enter
```

appletviewer http://ecee.colorado.edu/~mcleod/teaching/Circuits2250/Extras/circuit/e-pnp.html

```
On my system (XUbuntu 17.10 with OpenJDK 8 installed) this shows me a simulation of a simple transistor circuit with two sliders to change voltages. Whether or not that's all that applet was supposed to do I can't tell you. Applets that have any interaction with the browser usually either don't work at all or misbehave when run in appletviewer.

Holger

---

### Post by sed_faster on 2018-07-03
This is awesome! Thanks folk! :)
I did this "sudo apt-get install openjdk-11-jdk" and simply run command appletviewer and works.

Since this website it is hold maybe is better download all this apps! I tried do wget on website and I obtain all pages html but  when I run this command:
```

$ appletviewer file:///home/user/Desktop/simulation/ecee.colorado.edu/~mcleod/teaching/Circuits2250/Extras/circuit/e-555saw.html

```

This the result on this page, please: [https://snag.gy/1G6leJ.jpg](https://snag.gy/1G6leJ.jpg)

Thanks

**[UPDATE1]**
Also I installed "xxx" but the behavior it is the same! I search to relative software through terminal but I can relate none of them!
```

$ sudo apt-cache search openjdk
default-jdk - Standard Java or Java compatible Development Kit
default-jdk-doc - Standard Java or Java compatible Development Kit (documentation)
default-jdk-headless - Standard Java or Java compatible Development Kit (headless)
default-jre - Standard Java or Java compatible Runtime
default-jre-headless - Standard Java or Java compatible Runtime (headless)
openjdk-11-dbg - Java runtime based on OpenJDK (debugging symbols)
openjdk-11-doc - OpenJDK Development Kit (JDK) documentation
openjdk-11-jdk - OpenJDK Development Kit (JDK)
openjdk-11-jdk-headless - OpenJDK Development Kit (JDK) (headless)
openjdk-11-jre - OpenJDK Java runtime, using Hotspot JIT
openjdk-11-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
openjdk-11-source - OpenJDK Development Kit (JDK) source files
icedtea-8-plugin - web browser plugin based on OpenJDK and IcedTea to execute Java applets
jtreg - Regression Test Harness for the OpenJDK platform
libhsdis0-fcml - HotSpot disassembler plugin using FCML
libreoffice - office productivity suite (metapackage)
openjdk-11-demo - Java runtime based on OpenJDK (demos and examples)
openjdk-11-jre-zero - Alternative JVM for OpenJDK, using Zero
openjdk-8-dbg - Java runtime based on OpenJDK (debugging symbols)
openjdk-8-demo - Java runtime based on OpenJDK (demos and examples)
openjdk-8-doc - OpenJDK Development Kit (JDK) documentation
openjdk-8-jdk - OpenJDK Development Kit (JDK)
openjdk-8-jdk-headless - OpenJDK Development Kit (JDK) (headless)
openjdk-8-jre - OpenJDK Java runtime, using Hotspot JIT
openjdk-8-jre-dcevm - Alternative VM for OpenJDK 8 with enhanced class redefinition
openjdk-8-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
openjdk-8-jre-zero - Alternative JVM for OpenJDK, using Zero/Shark
openjdk-8-source - OpenJDK Development Kit (JDK) source files
uwsgi-app-integration-plugins - plugins for integration of uWSGI and application
uwsgi-plugin-jvm-openjdk-8 - Java plugin for uWSGI (OpenJDK 8)
uwsgi-plugin-jwsgi-openjdk-8 - JWSGI plugin for uWSGI (OpenJDK 8)
uwsgi-plugin-ring-openjdk-8 - Closure/Ring plugin for uWSGI (OpenJDK 8)
uwsgi-plugin-servlet-openjdk-8 - JWSGI plugin for uWSGI (OpenJDK 8)
java-package - Utility for creating Java Debian packages

```

**[UPDATE2]**
Also I tried this but the result it is the same "appletviewer -encoding utf-8 Desktop/pge.html"

---

### Post by Holger_Gehrke on 2018-07-03
AFAIK wget does not understand the applet-Tag, so it does not download applets or files they use. Also, while the author has published the java-source (the file 'Circuit.java'), he doesn't mention a license, open source or otherwise, so downloading the program might be problematic from a legal perspective ...

Holger

---

