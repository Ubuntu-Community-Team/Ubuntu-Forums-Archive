---
title: "HOWTO: Install ibus-sunpinyin on Ubuntu (Ubuntu ibus"
date: 2010-03-26
forum: Outdated Tutorials &amp; Tips
---

### Post by chenxiaolong on 2010-03-26
In Ubuntu 10.10 and up, it's really easy to install sunpinyin. Just run,

```
sudo apt-get install ibus-sunpinyin sunpinyin-data
```

**[COLOR="Red"]The information below is not required anymore![/COLOR]**

SunPinyin is an excellent &#25340;&#38899; project by the SunPinyin group. In my experience, it has the best dictionary I've ever used (on Linux) and I'm going to show you how to install it the proper way by creating deb packages.

1. First, you need to install the packages: [COLOR="Blue"]libtool libibus-dev sqlite3 libsqlite3-dev libgtk2.0-dev build-essential debhelper autotools-dev git-core scons[/COLOR]:

```
sudo apt-get install libtool libibus-dev sqlite3 libgtk2.0-dev build-essential debhelper autotools-dev git-core scons
```

2. Then, you need to install the "cdbs" package from the Debian Sid repository as the Ubuntu version is too old and doesn't include the file: "/usr/share/cdbs/1/class/scons.mk"

```
wget http://ftp.us.debian.org/debian/pool/main/c/cdbs/cdbs_0.4.89_all.deb
sudo dpkg -i cdbs_0.4.89_all.deb
```

3. Create a directory and change to it in a terminal:

```
mkdir ~/build_sunpinyin
cd ~/build_sunpinyin
```

4. Download the latest source from the git repository:

```
git clone git://github.com/sunpinyin/sunpinyin.git
```

5. Change to the "sunpinyin" directory within the "~/build_sunpinyin" directory:

```
cd sunpinyin
```

6. Generate the "debian/control" file for building a deb package.

```
DEB_AUTO_UPDATE_DEBIAN_CONTROL=yes fakeroot debian/rules clean
```

7. Build the deb package:

```
dpkg-buildpackage -us -uc
```

8. Step 7 creates 4 deb packages in ~/build_sunpinyin:

> ibus-sunpinyin*.deb
sunpinyin-data-be*.deb
sunpinyin-data-le*.deb
xsunpinyin*.deb

DO NOT INSTALL ALL OF THEM!

Only install (3 packages: libsunpinyin, libsunpinyin-dev, sunpinyin-data-le): [COLOR="Blue"]libsunpinyin3*.deb sunpinyin-data-le*.deb[/COLOR]:

```
sudo dpkg -i libsunpinyin3*.deb sunpinyin-data-le*.deb
```

9. Change into the "~/build_sunpinyin/sunpinyin/wrapper/ibus" directory.

```
cd ~/build_sunpinyin/sunpinyin/wrapper/ibus
```

10. Once again, generate the "debian/control" file.

```
DEB_AUTO_UPDATE_DEBIAN_CONTROL=yes fakeroot debian/rules clean
```

11. Then, generate the [COLOR="Blue"]ibus-sunpinyin[/CODE] deb package.

```
dpkg-buildpackage -us -uc
```

12. Change to the parent directory: "~/build_sunpinyin/sunpinyin/wrapper"

```
cd ~/build_sunpinyin/sunpinyin/wrapper
```

13. Install the [COLOR="Blue"]ibus-sunpinyin[/COLOR] package.

```
sudo dpkg -i ibus-sunpinyin*.deb
```

14. Right or left click the iBus icon in the system tray and click Restart.

15. Goto System > Preferences > iBus Preferences.

16. Goto the Input Method tab.

17. Under "Select an input method," choose Chinese > SunPinyin and click Add. 

18. Close the preferences, right click the iBus icon in the system tray, and click Restart.

19. Enjoy typing in Chinese!

---

### Post by wt8008 on 2010-06-04
Step 1, package libsqlite3-dev needed, I couldn't complete step 5
Step 5, typo for prefix?

Also, use the restart feature in the tray for the iBus icon before adding in Sunpinyin

Thanks for the guide in English, it made installing go faster.

---

### Post by chenxiaolong on 2010-06-04
Sorry about those mistakes. I tried to think of the dependencies off the top of my head because I already had everything installed.

About step 5....yeah....my touchpad tends to be a little (VERY) jumpy.

I'll correct the mistakes in the first post.

---

### Post by wt8008 on 2010-06-04
You should left click on the ibus icon to bring the menu up, if you right click you bring up the regular Gnome Applet menu. :P

---

### Post by chenxiaolong on 2010-06-04
Shoot, I forgot about the indicator applet thingy :(. I was using a different theme.

---

### Post by NelsonYao on 2010-07-23
Where is "autogen.sh"? There is no such file in the directory.

---

### Post by chenxiaolong on 2010-07-23
The ibus-sunpinyin developers recently updated their method of compilation. I'll modify my first post sometime tomorrow :D.

---

### Post by chenxiaolong on 2010-08-03
Sorry for the the late reply. One of my hard drives in my RAID0 configuration died :(.

Anyway, I've updated the first post of this thread to include the new instructions :D.

---

### Post by adellalin on 2010-09-09
when needs lib dependency like the following 
dpkg-checkbuilddeps: Unmet build dependencies: libsqlite3-dev (>= 3.6)
dpkg-buildpackage: warning: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: warning: (Use -d flag to override.)

Install lib here-
sudo apt-get install libsqlite3-dev

---

### Post by opodaniel on 2010-11-30
New version out so 
> wget [http://ftp.us.debian.org/debian/pool/main/c/cdbs/cdbs_0.4.88_all.deb](http://ftp.us.debian.org/debian/pool/main/c/cdbs/cdbs_0.4.88_all.deb)
sudo dpkg -i cdbs_0.4.88_all.deb
should be change to 
wget [http://ftp.us.debian.org/debian/pool/main/c/cdbs/cdbs_0.4.89_all.deb](http://ftp.us.debian.org/debian/pool/main/c/cdbs/cdbs_0.4.89_all.deb)
sudo dpkg -i cdbs_0.4.89_all.deb

---

### Post by chenxiaolong on 2010-11-30
Thank you for the update. I'll change the first post.

As a side note, Ubuntu 10.10 has ibus-sunpinyin in its repos. It can be installed with "sudo apt-get install ibus-sunpinyin".

---

### Post by opodaniel on 2010-11-30
>  It can be installed with "sudo apt-get install ibus-sunpinyin".
Just discover that, and wanted to post :d

To be able to write chinese using pinyin is greate when your Chinese skils are good but for the people who are in the process of learning Chinese, hand write imput is important for learning the meaning of new characters ( beside learning wubi of course). 

I know it is not on topic but could you recommend some Ubuntu software that can:
- recognize the hand writing using the mouse more or less like [&#25163;&#20889;&#36755;&#20837;&#27861;1.1.0.30]("http://pinyin.sogou.com/?p=40031101&kw=") made for Windows by Sogou team?
- Show the stroke order of Chinese caracters like : [eStroke]("http://www.eon.com.hk/estroke/") also made for Windows.

Thanks 
ps. Since it is off-topic if you see fit we can continue the discution on PM.

---

