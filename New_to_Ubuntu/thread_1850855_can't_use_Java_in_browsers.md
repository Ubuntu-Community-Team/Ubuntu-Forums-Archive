---
title: "can't use Java in browsers"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by thailande on 2011-09-27
I opened the page [http://www.chessgames.com/perl/chessgame?gid=1306138]("http://www.chessgames.com/perl/chessgame?gid=1306138") in Firefox and Chrome, and it couldn't display normally. Chrome gave the Warning:
```
Fatal: Initialization error: Could not initialize applet

```
Details:
```
net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: Could not initialize applet.
	at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:728)
	at net.sourceforge.jnlp.Launcher.getApplet(Launcher.java:672)
	at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:884)
Caused by: net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: A fatal error occurred while trying to verify jars.
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:441)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:169)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:288)
	at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:697)
	... 2 more
Caused by: 
net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: A fatal error occurred while trying to verify jars.
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:441)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:169)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:288)
	at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:697)
	at net.sourceforge.jnlp.Launcher.getApplet(Launcher.java:672)
	at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:884)

```

I think this is something wrong about Java, my Ubuntu version is Ubuntu 11.04, Java version is ```
java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.2) (6b22-1.10.2-0ubuntu1~11.04.1)
OpenJDK Client VM (build 20.0-b11, mixed mode, sharing)
```

Could you help me? Thanks in advance

---

### Post by thailande on 2011-09-27
I tried to install Sun Java, but failed when I entered the command
[COLOR="Red"]rpm -ivh jre-7-linux-i586.rpm[/COLOR]
```
/usr/bin/python: can't find '__main__' module in '/usr/share/command-not-found'
```

---

### Post by Miljet on 2011-09-27
rpm files are NOT for Ubuntu, the are for Red Hat (and deritives).

The easiest way to install Sun java is to either use Synaptic or the terminal.

Open Synaptic (System -> Administration -> Synaptic Package Manager). Click on Settings -> Repositories to open the Software Sources window. Then select the Other Software tab and place a check beside the "partner" repository. Close the Software Sources window. Next click the "Reload" button at the top left. 

After it finishes reloading, you are ready to install Sun java. Type "sun-java" (without the quotes) in the Quick Search box. You want to mark the following files for installation: sun-java6-jre, sun-java6-fonts, and sun-java6-plugin. You will get a message that other files are going to be installed. Just say yes to all. Now click on "Apply" at the top of the screen and sit back and wait while the files are installed. At some point during the installation, you will have to accept the EULA. You may have to use the "tab" key on your keyboard to enable the accept button.

After I install Sun java, I usually remove the Icedtea plugin because it somtimes conflicts with the Sun plugin. While you are still in Synaptic Package Manager, just type icedtea in the Quick Search box, locate the icedtea6-plugin and mark it for removal. Click the Apply button again.

Then close Synaptic and you should be all set.

---

### Post by aura7 on 2011-09-27
Install the browser plugin... 

sun-java6-plugin

from Synaptic Package Manager and try running the game again.

---

### Post by thailande on 2011-09-27
I installed Sun Java by using Miljet's method, then I chose the default Java by the command
[COLOR="Red"]sudo update-alternatives --config java[/COLOR]
And it works.
Thank you all very much!

---

