---
title: "Howto: Google Gears on Firefox 3.5 on Jaunty x86_64"
date: 2009-07-02
forum: Outdated Tutorials &amp; Tips
---

### Post by tuxcantfly on 2009-07-02
This howto will install Gears on Firefox 3.5 for your Ubuntu 9.04 system. This will allow you to use Offline Gmail. I've tested it on x86_64 and i386.

**Installing Firefox 3.5 from ubuntu-mozilla-daily PPA**

(skip to next section if you've already done this)
Head to [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa) and follow the instructions to add the repo, then install the "firefox-3.5" package. Or if you just want to copy-past commands into a terminal:

```
sudo su
apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 247510BE
echo "deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main" >> /etc/apt/sources.list
aptitude update
aptitude install firefox-3.5
exit
```

**Installing Gears**

For the lazy, I've posted prebuilt xpis, to install these files just go to Tools->Addons, then either download the appropriate file and drag the xpi file onto the addons button, or click the one of the following links and authorize the sources when prompted:

**Linux x86_64:** [http://gkovacs.xvm.mit.edu/google-gears/gears-linux-x86_64-opt-0.5.29.0.xpi](http://gkovacs.xvm.mit.edu/google-gears/gears-linux-x86_64-opt-0.5.29.0.xpi)

**Linux i386:** [http://gkovacs.xvm.mit.edu/google-gears/gears-linux-opt-0.5.29.0.xpi](http://gkovacs.xvm.mit.edu/google-gears/gears-linux-opt-0.5.29.0.xpi)

**Windows:** [http://gkovacs.xvm.mit.edu/google-gears/gears-win32-opt-0.5.25.0.xpi](http://gkovacs.xvm.mit.edu/google-gears/gears-win32-opt-0.5.25.0.xpi)

It was built from [http://gears.googlecode.com/svn/trunk](http://gears.googlecode.com/svn/trunk) revision 3373

If you'd like to build it yourself, use the following commands:

svn co [http://gears.googlecode.com/svn/trunk](http://gears.googlecode.com/svn/trunk) -r3373
cd trunk
wget [http://gkovacs.xvm.mit.edu/google-gears-firefox-3.5-x86_64/gears-gcc433.diff](http://gkovacs.xvm.mit.edu/google-gears-firefox-3.5-x86_64/gears-gcc433.diff)
patch -p0 -i gears-gcc433.diff
chmod +x third_party/gecko_1.9/linux/gecko_sdk/bin/xpidl
sed -i "s/\-Werror//" gears/tools/config.mk
cd gears
make MODE=opt

Patch is attached (rename to gears-gcc433.diff after downloading), if you'd prefer to download see
[http://gkovacs.xvm.mit.edu/google-gears-firefox-3.5-x86_64/gears-gcc433.diff](http://gkovacs.xvm.mit.edu/google-gears-firefox-3.5-x86_64/gears-gcc433.diff)

**Uninstalling Google Gears and Firefox 3.5**

First go to Tools->Add-ons, select Google Gears, and press uninstall. Then remove firefox 3.5:

```
sudo aptitude remove firefox-3.5
```

---

### Post by jpeddicord on 2009-07-07
Approved, thank you for your T&T contribution. :)

---

### Post by DouglasCaixeta on 2009-07-14
Now, Google Gears officialy supports Firefox 3.5 but when I go to their webpage I still get the message: Your browser is not currently supported.

---

### Post by animaster on 2009-07-15
Thanks for the useful tips. I have been looking around for guide on installing Gears for Firefox 3.5 a.k.a Shiretoko. ^^

---

### Post by tuxcantfly on 2009-07-15
> **DouglasCaixeta said:**
> Now, Google Gears officialy supports Firefox 3.5 but when I go to their webpage I still get the message: Your browser is not currently supported.

If it's not letting you download the extension, use User Agent Switcher [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59) to spoof as some other version of Firefox

If you're using x86_64, you'll need to build it yourself or use my build above.

If you're using a version that's newer than 3.5 (the ppa has 3.5.1 and 3.6), you'll need to extract the extension .xpi, edit install.rdf, change <maxversion>3.5</maxversion> to <maxversion>3.6</maxversion>

---

### Post by DouglasCaixeta on 2009-07-15
> **tuxcantfly said:**
> If it's not letting you download the extension, use User Agent Switcher [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59) to spoof as some other version of Firefox


Thank you very much! The User Agent Switcher thing solved my problem!

---

### Post by binbash on 2009-07-24
Thanks for agent switcher trick

---

### Post by aliencam on 2009-07-26
Hey thank you for the compiling instructions, I have been looking for those forever! 

Should this .diff work for future releases of gears as well?  If it is based off of the original .diff I saw in the gears google group, I imagine that it would.  

The reason I ask is that I am looking for a steady source for updating google gears (and I certainly don't mind doing it myself, I could just never get it to compile right).  It seems every time a new version is released, the last person who compiled it and posted it does not update their post :P.

---

### Post by El Viejo Lobo on 2009-09-24
Just to send my thanks, it was swift and nice install and works right away.

---

### Post by hanzj on 2009-10-26
how can i get a revision later than your 3373? I'm using Shiretoko (version 3.5.5pre) on Karmic Koala (Ubuntu 9.10) and 3373 ([http://gkovacs.xvm.mit.edu/google-gears/gears-linux-opt-0.5.29.0.xpi](http://gkovacs.xvm.mit.edu/google-gears/gears-linux-opt-0.5.29.0.xpi)) doesn't work. Thanks.

---

### Post by John RG on 2009-11-07
Thanks, works nicely for me. Cheers, John

---

### Post by Fastjack77 on 2010-01-21
Working nicely with Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.7) Gecko/20100106 Ubuntu/9.10 (karmic) Firefox/3.5.7

Thank you! :KS

---

### Post by oliviagj on 2010-01-27
Thank you very much!

---

### Post by blogmaniak on 2010-04-03
I just tried to download the i386 xpi and the file would not download. I have installed v3.5.8 Shiretoko on my ubuntu 9.04. Any suggestions on how to install the latest, stable build for gears?

---

### Post by Pifilatakanemu on 2010-10-12
I'm trying to install Gears, too.

Any feasible way to install it under 10.10 ?

---

