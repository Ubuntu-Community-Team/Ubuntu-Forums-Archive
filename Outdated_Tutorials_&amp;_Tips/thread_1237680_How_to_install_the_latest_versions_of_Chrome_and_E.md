---
title: "How to install the latest versions of Chrome and Epiphany (webkit) browsers on Jaunty"
date: 2009-08-11
forum: Outdated Tutorials &amp; Tips
---

### Post by linuxed on 2009-08-11
**Chrome:**
[list=1]
[*]Open the sources.list file in gedit:
```

sudo gedit /etc/apt/sources.list

```
[*]Copy the following and paste it at the very bottom of the sources.list file:
```

## Google Chrome
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main

```
[*]Click save and close gedit.
[*]Import the gpg key:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4E5E17B5

```
[*]Update your sources:
```

sudo apt-get update

```
[*]Install chrome:
```

sudo apt-get install chromium-browser

```
[/list]

**Epiphany (webkit)**
[list=1]
[*]Open the sources.list file in gedit:
```

sudo gedit /etc/apt/sources.list

```
[*]Copy the following and paste it at the very bottom of the sources.list file:
```

## Epiphany (webkit)
deb http://ppa.launchpad.net/webkit-team/epiphany/ubuntu jaunty main
deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main

```
[*]Click save and close gedit.
[*]Import the gpg key:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2D9A3C5B

```
[*]Update your sources:
```

sudo apt-get update

```
[*]Install epiphany:
```

sudo apt-get install epiphany-webkit

```
[/list]

**To enable java and flash for Chrome and Epiphany**
```

sudo apt-get install sun-java6-plugin flashplugin-installer

```

---

### Post by fishyf on 2009-09-26
I believe that with the newer developer's versions of chrome, this is largely outdated. I downloaded the deb from [http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb](http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb) and it said that it updated the sources.list and indeed, they were updated after it installed.

It works really well, providing Flash and Java applets. They only problem is the really annoying issue that it starts up with a tab which points out that it is a dev build. There is a workaround which is to start chrome with the  chrome://newtab option.

I did this in the menus by (system->preferences->mainmenu, then internet, chrome, properties and changed the command from /opt/google/chrome/google-chrome  %U to /opt/google/chrome/google-chrome  chrome://newtab %U

I found this from a link on a bug report which pointed to some guy's site. Sorry for lack of proper attribution.

---

### Post by falconindy on 2009-09-26
> **fishyf said:**
> I believe that with the newer developer's versions of chrome, this is largely outdated. I downloaded the deb from [http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb](http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb) and it said that it updated the sources.list and indeed, they were updated after it installed.

It works really well, providing Flash and Java applets. They only problem is the really annoying issue that it starts up with a tab which points out that it is a dev build. There is a workaround which is to start chrome with the  chrome://newtab option.

I did this in the menus by (system->preferences->mainmenu, then internet, chrome, properties and changed the command from /opt/google/chrome/google-chrome  %U to /opt/google/chrome/google-chrome  chrome://newtab %U

I found this from a link on a bug report which pointed to some guy's site. Sorry for lack of proper attribution.
I've been "subscribing" to the daily chromium build repository for several weeks now as described in the OP. The about:linux-splash developer warning disappeared for me about a week ago. Perhaps you have the outdated version?

I'm actually posting this from Chromium 4.0.219.3 (build 27181).

---

### Post by Vevmesteren on 2009-10-12
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4E5E17B5

times out...

any ideas?

---

### Post by troelsfrostholm on 2009-10-16
I had apt-key time out too. I just tried again a bunch of times, and finally it got through. 

When installing Chrome using this tutorial, to enable flash and java plugins, you must:
- make a symbolic link to your java runtime in chromiums plugin dir
```
cd /usr/lib/chromium-browser/plugins
ln -s /usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/i386/libnpjp2.so .
```
(if your java runtime is located somewhere else, try: locate libnpjp2.so)

- start chromium with the following options
```
chromium-browser --enable-user-scripts --enable-extensions chrome://newtab
```
The newtab part is optional. It just opens on chromiums start tab, as is default behaviour for the stable windows version. 
I should add that I did this on Ubuntu 8.04, but I suppose it would be the same on different distributions.

---

### Post by Rapture_Ready on 2009-10-16
Forgive me for my ignorance but are either of these browsers better than Firefox or are they just different? Is there any advantage to using either one over the default Firefox?

Thanks.

---

### Post by linuxed on 2009-10-16
@Rapture_Ready
Chrome and Epiphany both use webkit while Firefox uses Gecko.  If you're a developer or if you're just interested in having support for the latest css properties and web standards I'd recommend a webkit based browser.  Firefox still seems to lack support for a few css properties (e.g., text-overflow and background-size) and has also scored lower in the acid3 test.

[https://developer.mozilla.org/en/CSS/text-overflow](https://developer.mozilla.org/en/CSS/text-overflow)
[http://www.w3.org/TR/css3-background/#the-background-size](http://www.w3.org/TR/css3-background/#the-background-size)
[http://en.wikipedia.org/wiki/Acid3#Desktop_browsers](http://en.wikipedia.org/wiki/Acid3#Desktop_browsers)

@troelsfrostholm
You can also install the sun-java6-plugin package which will automatically create a link to the java plugin for most browsers including Firefox, Epiphany and Chrome.  After installing the package you can test the plugin using the link below.

[http://java.com/en/download/installed.jsp?detect=jre&try=1](http://java.com/en/download/installed.jsp?detect=jre&try=1)

You can also install the flashplugin-installer package to automatically install the flash plugin for Chrome and Firefox.  I haven't tested the plugin in Epiphany yet but I'm guessing that it probably works fine in Epiphany as well.  To test the flash plugin use the link below.

[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

---

### Post by ptcbus on 2009-12-06
If one does not want to go through the command line (example those who are very new to ubuntu/linux) can install it using synaptic package manager. See this [link]("http://ptcbus.blogspot.com/2009/11/installing-chromium-google-chrome-for.html").

---

### Post by deepclutch on 2010-01-15
Epiphany-Webkit is not detecting JRE manually installed. libnpjp2.so(amd64) is available;Is epiphany looking onto /usr/lib/mozilla/plugins directory for plugins?Still ,flash is working;but no JAVA!needs help urgently.

PS:I got java 7 latest snapshot installed,downloaded from java community.

---

### Post by linuxed on 2010-01-15
Try installing the java6 plugin.
```

sudo apt-get install sun-java6-plugin

```
If that doesn't work you may need to update your default java version or manually create a symlink to the java plugin.
```

update-alternatives --list java
update-alternatives --display java

```
If the java link is pointing to the wrong version then update it with the following.  Make sure to replace the paths below with one of the paths that were displayed from the commands above.
```

sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jre1.6.0_14/bin/java" 1
sudo update-alternatives --set java /usr/lib/jvm/jre1.6.0_14/bin/java
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/jre1.6.0_14/bin/javaws" 1
sudo update-alternatives --set javaws /usr/lib/jvm/jre1.6.0_14/bin/javaws

```
If the java path is correct then try creating a symlink to the java plugin.  I don't currently have Epiphany installed so I can't tell you the exact plugin path but it would look something like the following.
```

sudo ln -s /usr/lib/jvm/jre1.6.0_14/lib/amd64/libnpjp2.so /usr/lib/firefox-addons/plugins/libnpjp2.so

```
And finally, test your java versions.
```

java -version
javaws

```
Java.com also offers a simple java applet test. Just click the 'Do I have java?' link on the homepage.

---

