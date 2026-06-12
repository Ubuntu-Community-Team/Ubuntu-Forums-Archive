---
title: "Building FrostWire Source?"
date: 2009-07-08
forum: Programming Talk
---

### Post by justin10ec on 2009-07-08
Does anyone know how to build the FrostWire source (preferably using Eclipse)? I've asked on Gnutella forums and the official FrostWire forums but both communities are very slow and unresponsive.


Thanks in advanced. :)

---

### Post by .Maleficus. on 2009-07-08
I've already responded to your first thread [here]("http://ubuntuforums.org/showthread.php?t=1206255"), but I'll respond again.

Do you really need to build the source?  It is a much worse way of managing packages, especially if there is a .deb available (which there is).  If you really want to build the source though, the standard way is to do this:

```
./configure
make
sudo make install
```

---

### Post by justin10ec on 2009-07-08
I completely forgot about that thread! I would like to play around with the source code. I can't even figure out how they have their SVN set up.

---

### Post by .Maleficus. on 2009-07-08
To checkout from SVN:
```
svn co https://frostwire.svn.sourceforge.net/svnroot/frostwire/trunk frostwire
```
And then to build, the standard "./configure, make, sudo make install".

---

### Post by gubatron on 2011-02-24
**Building from the command line**

Build-Depends: ant, libgnome2-dev, libxt-dev, maven2,
 default-jdk, python, zlib1g, libc6, libgcc1, libacl1-dev, javahelper

```
#clone repo
hg clone https://bitbucket.org/frostwire/frostwire frostwire.desktop
cd frostwire.desktop
ant
./run

#update the latest changes
hg pull -u
ant clean
ant
./run

```

**Building from eclipse**

After you have cloned the project, you'll want to copy the classpath.linux to .classpath and refresh your eclipse project (F5)

You can do so on your command line

```

cp classpath.linux .classpath

```

After you refresh, you'll probably have a Build Path issue in eclipse, it'll be complaining about themes.jar missing (if you're building prior to March 2011, this issue will go away soon since we will be using substance.jar for our themes)

To build themes.jar go to lib/themes and execute the makeThemesJar.sh script

```

cd lib/themes
sh makeThemesJar.sh

```

Now go back to eclipse and refresh (F5), the build issues should be gone.

To execute, create a Run Configuration where the main class will be **com.limegroup.gnutella.gui.Main**, as VM Arguments pass -Ddebug=1 optionally.

**Building from Debian Source Package **
If you want to build a .deb from the Debian Source Package (available at [http://sourceforge.net/projects/frostwire/](http://sourceforge.net/projects/frostwire/))

```

$ #extract the sources
$ dpkg-source -x frostwire_x.y.z.dsc
$ cd frostwire-x.y.z
#build the package
$ dpkg-buildpackage -us -uc -rsudo

```

Enjoy
FrostWire Development Team

---

