---
title: "Font in IntelliJ IDEA"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by silvestr1994 on 2014-04-23
I installed idea 13.1 and Oracle JDK 1.8. When I launch idea I see very bad font it is ugly. How I can fix this. Ubuntu 14.04 x64
And I don`t want to uninstall Oracle JDK 1.8.

---

### Post by mgt2000 on 2014-10-24
first off all &#8211; need to install OpenJDK with Fonts Patch.
 
wget [http://urshulyak.com/jdk-8u5-tuxjdk-b08.tar.gz](http://urshulyak.com/jdk-8u5-tuxjdk-b08.tar.gz)
tar -zxvf jdk-8u5-tuxjdk-b08.tar.gz
sudo mv jdk-8u5-tuxjdk-b08 /usr/lib/jvm
rm jdk-8u5-tuxjdk-b08.tar.gz




And after need to start idea with this JDK using the following script:






#!/bin/sh
# change to your location
IDEA_HOME=/opt/idea


export JAVA_HOME=/usr/lib/jvm/jdk-8u5-tuxjdk-b08/


# Note: Can modify $IDEA_HOME/bin/idea{,64}.vmoptions
# instead of setting here.
# "-Dawt.useSystemAAFontSettings=on" seems worse to me
# "-Dsun.java2d.xrender=true" makes fonts darker
export _JAVA_OPTIONS="-Dawt.useSystemAAFontSettings=lcd \
                      -Dsun.java2d.xrender=true"


# Having this set makes menu font size smaller (wtf?)
export GNOME_DESKTOP_SESSION_ID=this-is-deprecated
# unset GNOME_DESKTOP_SESSION_ID


exec $IDEA_HOME/bin/idea.sh "$@" 








Only note that need to change IDEA_HOME location for your path of idea

---

### Post by pissedoffdude on 2014-10-24
Hi,

What do you mean by ugly? When it comes to font rendering, opinion is incredibly crucial, so maybe post a screenshot so we can take a look. That said, type this into a terminal ```
export _JAVA_OPTIONS='-Dawt.useSystemAAFontSettings=on -Dswing.aatext=true -Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel'
idea.sh

```

Or replace idea.sh with whatever the IntelliJ command is  (you can find out by launching it and checking the system monitor)

If that improves it, make the change persistent by appending the first command to /etc/profile.d/jre.sh.

If that's not its location, do a ```
find /etc/ -name jre.sh
```

And edit the correct file.

---

