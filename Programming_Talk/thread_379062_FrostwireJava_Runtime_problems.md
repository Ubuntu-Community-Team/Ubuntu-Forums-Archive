---
title: "Frostwire/Java Runtime problems"
date: 2007-03-08
forum: Programming Talk
---

### Post by Jsgrabo on 2007-03-08
Hopefully i'm posting this in the right section but I apologize if i am not. Ok, im trying to get Frostwire to run. I installed the latest JRE using the guide on [http://www.java.com/en/download/help/5000010500.xml#selfextracting]("http://www.java.com/en/download/help/5000010500.xml#selfextracting").
When i attept to run Frostwire, i get this:

```

# frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
Java exec found in  /usr/java/jre1.5.0_11/bin/
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com  [/usr/java/jre1.5.0_11/bin/java = Error]
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com

```

I really just do not know what to do to make it go. Any help/advice is greatly appreciated. 

Thanks

---

### Post by lnostdal on 2007-03-08
why are you installing java using the generic instructions on suns site?

suns version of java is included in the ubuntu repositories now; always use the ubuntu repositories

[https://help.ubuntu.com/community/Java#head-21b44ff330436e9f387606a337f458a3c2113a3e](https://help.ubuntu.com/community/Java#head-21b44ff330436e9f387606a337f458a3c2113a3e)

---

### Post by Jsgrabo on 2007-03-08
I didnt know what else to do.

I'm at school right now but i'll give it a try when I get home later.

---

### Post by Ramses de Norre on 2007-03-08
The old versions of frostwire don't work with java6, download the newer version from the frostwire site and install it.

Or download a java5 jre and change the runFrost.sh script to something like ```
/path/to/java -jar /path/to/frostwire.jar
``` where the java is java5 of course.

---

### Post by phossal on 2007-03-08
> **lnostdal said:**
> why are you installing java using the generic instructions on suns site?

suns version of java is included in the ubuntu repositories now; always use the ubuntu repositories

[https://help.ubuntu.com/community/Java#head-21b44ff330436e9f387606a337f458a3c2113a3e](https://help.ubuntu.com/community/Java#head-21b44ff330436e9f387606a337f458a3c2113a3e)

lol Always use the repositories? That's ridiculous. The repositories *suck*. The backports version of Java, sun-java6-jdk, is just a packaged version of Sun's .bin file anyway. Why use that when it's virtually as easy, definitely as secure if not more so, and so much faster and easier to update by using the .bin file?

I recommend *avoiding* the package manager unless you *dig* out-of-date, poorly packaged versions of software.

---

### Post by Jsgrabo on 2007-03-08
Ok well I ran the installer (Sun Java 5.0 Runtime) from the ubuntu repositories and i'm still getting this:

```

# frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
Java exec found in  /usr/java/jre1.5.0_11/bin/
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com  [/usr/java/jre1.5.0_11/bin/java = Error]
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com

```

---

### Post by Smerity on 2007-04-09
I have a similar issue with Limewire-Free and no real solution as of yet. Uninstalled and installed this various times but to no avail.

Strange thing is that Azureus, another Java based application, had issues around the same time as this.

Will tell you if I find anything.

---

### Post by ithuwakaga on 2007-04-29
Type in 

```
sudo update-alternatives --config java
```

Pick the one that says "Sun" in the name.

Hope that helps, did for me.

---

### Post by vikasvishnu on 2007-04-30
It definitely does work.. thanks a million...


> **ithuwakaga said:**
> Type in 

```
sudo update-alternatives --config java
```

Pick the one that says "Sun" in the name.

Hope that helps, did for me.

---

### Post by trishacupra on 2007-04-30
I just had the same issue and searched for the solution. This worked for me, too! I chose option 5...

```
trisha@trisha-laptop:~$ sudo update-alternatives --config java
Password:

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
          2    /usr/lib/jvm/java-gcj/jre/bin/java
          3    /usr/lib/jvm/java-6-sun/jre/bin/java
          4    /usr/lib/j2se/1.4/bin/java
          5    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 5
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.
trisha@trisha-laptop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading FrostWire:
```

---

### Post by trishacupra on 2007-04-30
Hmmm. Actually, it didn't really work. Now Frostwire loads up, but just gives me a blank window. Back to Google...

Edit: If anyone else reading this gets a white/gray window, here's why:

> Special Problems and Known Bugs

Q: When I open FrostWire, the window is completely white or gray. How do I fix this?

A: If the contents of the FrostWire window are completely white or gray, then there is an incompatibility with your graphics settings and Java's ability to render the FrostWire window. Try setting your graphics settings to factory default and/or reduce your refresh rate. If this does not work, others have had success by either upgrading their graphics drivers, rolling them back to a previous version, or disabling any hardware-driven graphics functions such as anti-aliasing.

[http://www.frostwire.com/index.php?id=faq#sta2](http://www.frostwire.com/index.php?id=faq#sta2)

---

### Post by phossal on 2007-04-30
Lots of misinformation in this thread. Lots of half-baked attempts to fix problems that shouldn't be problems at all.

---

