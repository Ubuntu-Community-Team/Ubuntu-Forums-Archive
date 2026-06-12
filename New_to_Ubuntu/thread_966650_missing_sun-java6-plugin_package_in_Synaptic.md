---
title: "missing sun-java6-plugin package in Synaptic"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by nacholariguet on 2008-11-01
just installed Ibex desktop 64-bit on a notebook

need Java runtime in order to run Cisco ASDM and the like

researched a bit, installed sun-java6-jre & sun-java6-bin from Synaptic package manager but can't find the sun-java6-plugin package to enable Java on FireFox 3 -it is not listed at all and thus when I attempt to run Cisco ASDM I got an asdm-jnlp file which it can't be opened, just downloaded

byt the way I'm seasoned Windows developer that don't know a damn thing 'bout Linux distros

---

### Post by Axos on 2008-11-01
I wonder if the repository gave you the 64-bit version of Java since you are running the 64-bit version of Ubuntu. Because...

Sun's site says: "There are no 64-bit versions of the Java Plugin, Java Web Start or Java Control Panel; however the 32-bit versions of the JRE can be installed on 64-bit systems in order to obtain this functionality. Note that only 32-bit browsers are supported at this time."

I'm not sure how to tell if you've got the 64-bit version of Java. Try opening a terminal and running "java -version". Does it say anything about 64-bit? Oh, also try running "javaws" (which is the program which launches JNLP files). If it finds javaws, you have the 32-bit version installed and all you need to do is tell Firefox to run JNLP files with javaws (it doesn't know by default). Or you can manually run JNLP files from a terminal (or script) just by passing the URL to the JNLP file to javaws:

```
javaws http://blah/blah/blah/foo.jnlp
```

If you need to get the 32-bit version of Java, I can give you detailed instructions for downloading and installing it directly from Sun's site (which is how I always install Java).

---

### Post by nacholariguet on 2008-11-01
first and foremost thanks for the advice !

you indeed give me some clues

1) I installed Ibex 64 beacuse I thought 64 was the "normal/common" scenarios for Linux but for no particular reason, I don't need anything that requires a 64-bit OS to begin with

2) That sun-java6-plugin is 32-bit code explains many things to me: a few moments ago I realized this package was dropped from Ibex and read somewhere else that it is still in some repository named medibuntu which I added to my sources (with some cryptic commands from the time being) but afterwards it is still missing from Synaptic so this is a dead-end

3) from what I gatehered there are two alternatives for Java RE on Ibex:
a) openjdk-6-jre + icedtea6-plugin (a more license friendly)
b) sun-java6-jre|bin|plugin

I'm now uninstalling the sun ones ... will re-install the openjdk and attempt to associate them to the jnlp in firefox

keep you posted !

a BIG thanks !

---

### Post by BGFG on 2008-11-01
Hi,
I currently use 64 Intrepid and used 64 Hardy. In synaptic i see Sun-java6-bin which is what i think you need. 
I installed the same in Hardy and was able to use limewire and fristwire normally.
When i visited the sun java site they had a list of names that the runtime is called in different distros. I also downloaded the runtime directly from sun.

jre-6u10-linux-x64.bin

[http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80)
 
Hope this is in fact what you need.
On another note, stick with 64 :) faster!

---

### Post by Nepherte on 2008-11-01
He also wants the java web plugin, which is **not** available for 64bit.

I have openjdk and icedtea-gcjwebplugin and it works fine. You could also install a 32bit browser and the 32bit java + plugin.

---

### Post by Axos on 2008-11-01
If the OpenJDK works, great. But if it isn't compatible with Cisco's app, installing the Sun version really isn't hard and doesn't do anything invasive to your system. The **non-RPM** version on Sun's site just installs itself in a subdirectory in your current working directory. No sudo required. In my opinion it's much neater and cleaner than a repository install. I can provide the rest of the details if you want them.

---

### Post by nacholariguet on 2008-11-01
exactly, the bin's there but not the plugin

I dunno if will stick with Ubuntu since I cannot tell how many apps will work on it but one thing I can tell you 'em all: I know good support when I see it and this is exactly that, it rocks !

so thank all

now back to business: openjdk installed with icedtea along, associated jnlp with javaws in FireFox, it starts, I can see it is talking with the firewall a bit (some progress window) but one second after is dead ... no trace ... gone ... so openjdk seems incompatible with Cisco apps (which by the way is one of the common crap enterprise-grade apps still trying to figure out the basic GUI fundaments in 2008) (sorry, can't resist that)

I'll attempt to uninstall openjdk and the sun ones from repository and install them directly from sun as suggested

I'll be back

THANKS

---

### Post by nacholariguet on 2008-11-01
I got the jre-6u10-linux-x64-rpm.bin saved on my desktop as suggested by Axos. Synaptic does not allow me to select it from add download packages ... it sees it on my desktop but it is faded (?)

On the other hand: it is the fifth time in almost two days that I got a freezed screen except for the mouse pointer; the systems hangs for no apparent reason and the thing kept alive is the mouse pointer ... the computer is a Dell Inspiron 9400/E5701 with the WiFi/BlueTooth/modem cards physically removed and everything else that cannot be removed (non-essential) disabled from BIOS (ie: firewire/card-reader/acoustics-management etc) ... a minimal config

first time: while opening computer under system menu
second time: in synaptic manager after successfully removing some apps (open office)
third time: under synaptic also
fourth time: while attempting to modify sys time
last time: while opening computer under system menu

any clues ?

---

### Post by Axos on 2008-11-01
Horrors...not the RPM!!! :) I said the **non-RPM**.

Once you've got the non-RPM, open a command terminal and...

cd to the directory where you want to install Java. It can be any directory. The installer will create a subdirectory within it named after the version you are installing.

Assuming you downloaded the JDK installer to your Desktop (modify this if you downloaded the JRE and/or you downloaded it somewhere else besides your Desktop):

chmod +x ~/Desktop/jdk-6u10-linux-i586.bin
~/Desktop/jdk-6u10-linux-i586.bin

You'll have to mash the space bar several times while you "read" (yeah, right) the Sun user agreement. Finally, you'll type "yes" to say you agree. Then it'll extract all the files.

To find out right away if the app will work, just run this from the terminal (again, you'll have to modify this if you downloaded the JRE rather than the JDK):

```
jdk1.6.0_10/bin/javaws http://blah/blah/blah/foo.jnlp
```

If you want, you can add the Java bin directory to your PATH environment variable. To make it visible to everything you launch from GNOME, set the variable in your ~/.gnomerc file (which doesn't exist by default):

PATH=/*whatever*/jdk1.6.0_10/bin:$PATH

If you have a 32-bit browser installed and want to be able to use the plugin (not necessary for JNLP apps), create a symbolic link (change "whatever" to the full path to the directory you installed the JDK in):

```
ln -s /whatever/jdk1.6.0_10/jre/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins
```

I hope I haven't made any typos. Sanity-check every command before you run it. :)

---

### Post by Axos on 2008-11-01
In case the Cisco app isn't working for some other reason, here's a link to a sample JNLP app on Sun's site. It's just a temperature converter:

[http://java.sun.com/docs/books/tutorialJWS/uiswing/learn/ex6/CelsiusConverter.jnlp](http://java.sun.com/docs/books/tutorialJWS/uiswing/learn/ex6/CelsiusConverter.jnlp)

---

### Post by Axos on 2008-11-02
I need to apologize. I booted the 64-bit LiveCD and the 32-bit JRE won't even install. It bombs trying to extract the files. I **stupidly** assumed that I could believe Sun when they said the 32-bit version would work on a 64-bit OS:

"...however the 32-bit versions of the JRE can be installed on 64-bit systems in order to obtain this functionality."

Yeah, right.

---

### Post by Axos on 2008-11-02
Update: I got the 32-bit Sun JRE to install by first installing a package called "ia32-libs". But then javaws (Java Web Start) wouldn't work (not even from the command line, outside the browser).

---

### Post by nacholariguet on 2008-11-07
hi guys, thanks for the replies, I was out of town since yesterday, back to business ...

I'm having lots of hangs up by now with a clean installation thus I stopped attempting to install the JRE till I know what's going on here.

The problem I'm encountering more and more often is a freezed screen except for the cursor which I can move freely but besides this nothing more. I have to cold shutdown the machine to regain control. The cursor always remains the pointer/clock icon stating something's going on (wait).

The notebook is a Dell Inspiron 9400/E1705 dual-core 2 GB RAM.

- BlueTooth card physically removed and disabled from BIOS
- WiFi card physically removed and disabled from BIOS
- modem card physically removed and disabled from BIOS
- CD/DVD combo enabled but not used at all
- everything non-essential disabled from BIOS
- minimal config

- refused to install restriced drivers which were offered by the setup ... is this OK or should I install them ?

anyone guessing what could be the problem ?

From what I read I understand that a clean up Ubuntu setup WITHOUT any third-party driver is extremely rare to hang up ... am I right ?

---

### Post by Axos on 2008-11-07
You should start a new thread because the word "Java" in the subject may keep many people from reading it.

I'm afraid I have no clue why your system is hanging. I've always had very good luck. I'm running 8.10 on an old Toshiba notebook (1.5 GHz single-core) and a newer HP notebook (2.2 GHz dual-core). My wild, uneducated guess would be to try resetting the BIOS to its default settings to see if it makes any difference.

---

### Post by Axos on 2008-11-07
Oh, and I strongly recommend using the 32-bit version of Ubuntu if you want to use Sun's Java. I tried the OpenJDK and it made my apps look awful. Sun's Java is currently the only way to go.

---

### Post by nacholariguet on 2008-11-07
you're right axos; I'll try to get a stable system first whatever that means and when it's done I'll be back here to fix the Java thingy

thank you for your advice, very good indeed !

---

### Post by nacholariguet on 2008-11-15
back once again

it was the default video driver that was hanging my system; I replaced it with the restricted/proprietary one and voilà ! a stable system, so the default driver is a no go

now, from all the answers I got here it seems there's no way to install JRE+FireFox plugin on the 64-bit platform without replacing the default installed FireFox 64-bit with the 32-bit version ?

am I right ?

---

### Post by dafi on 2008-11-15
> **nacholariguet said:**
> 
now, from all the answers I got here it seems there's no way to install JRE+FireFox plugin on the 64-bit platform without replacing the default installed FireFox 64-bit with the 32-bit version ?

am I right ?

I've posted an alternative solution on my blog

[http://dafizilla.wordpress.com/2008/11/07/java-plugin-with-prism-under-ubuntu-64-bit/](http://dafizilla.wordpress.com/2008/11/07/java-plugin-with-prism-under-ubuntu-64-bit/)

---

### Post by nacholariguet on 2008-11-15
huh ...

* Install the 32bit version of java

- the Sun one ? ie: jre-6u10-linux-x64-rpm.bin ?

* Create a symlink to plugin
      ln -s /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so \
      /home/dave/.mozilla/plugins/

- this [/usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so] will be created by installing the mentioned JRE ?

* Create a prism webapp, for example using the Sun test page

---

### Post by nacholariguet on 2008-11-15
downloaded jre-6u10-linux-x64.bin from Sun to my desktop

cd desktop
sudo chmod +x jre-6u10-linux-x64.bin
./jre-6u10-linux-x64.bin

and I got a jre1.6.0_10 folder on my desktop with all the inflated files

now how I install them ?

---

### Post by dafi on 2008-11-16
> **nacholariguet said:**
> huh ...

* Install the 32bit version of java

- the Sun one ? ie: jre-6u10-linux-x64-rpm.bin ?

* Create a symlink to plugin
      ln -s /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so \
      /home/dave/.mozilla/plugins/

- this [/usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so] will be created by installing the mentioned JRE ?

* Create a prism webapp, for example using the Sun test page

I've modified my post because it was a bit incomplete

You need to install java 32 bit

sudo apt-get install ia32-sun-java6-bin

This install the 32bit plugin so you can create the symlink

PS
Consider I've both 32 and 64 bit Java installed

---

### Post by norreman on 2008-11-25
By default there is no plugins dir under ~/.mozilla so I created it, and created the symbolic link. Prism test app (sun test page) still doesn't work. A window pops up to download java...

---

