---
title: "Ant using wrong Java"
date: 2005-12-25
forum: Programming Talk
---

### Post by viscount on 2005-12-25
When running Ant from the command line
$ ant
Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/lib/tools.jar


However I do have sun-jdk1.5 installed and selected to be my default
$ sudo update-alternatives --config java
There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
      2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/lib/j2sdk1.5-sun/bin/java
 +    4        /usr/lib/j2se/1.4/bin/java


..so what gives? It seems that Ant can not find the 1.5 version and  falls back to the 1.4 version which is missing the .jar stuff.. 

Raises two questsions, why cant it find 1.5, and why doesnt 1.4 have jar stuff?

Thanks.

Also, I should have posted [this]("http://www.ubuntuforums.org/showthread.php?p=602826#post602826") in the development forum, perhaps a mod can change that for me.

---

### Post by viscount on 2005-12-25
Ahh.. blasted well fixed it!

$sudo apt-get remove --purge j2re-1.4
$sudo apt-get remove --purge java-gcj-compat
$sudo update-alternatives --config java
$sudo update-alternatives --config javac
$sudo update-alternatives --config jar

Now ant works as expected, hope this helps.

---

### Post by curtistee on 2005-12-25
[QUOTE=viscount]Ahh.. blasted well fixed it!

$sudo apt-get remove --purge j2re-1.4
$sudo apt-get remove --purge java-gcj-compat
$sudo update-alternatives --config java
$sudo update-alternatives --config javac
$sudo update-alternatives --config jar

Now ant works as expected, hope this helps.[/QUOTE]

Err... Not quite: Some of us use Open Office and ubuntu-desktop. 

Any other ideas? Meantime I'll just add the jar files to my classpath, like in the old days ;-)

---

### Post by viscount on 2005-12-25
[QUOTE=curtistee]Err... Not quite: Some of us use Open Office and ubuntu-desktop. 

Any other ideas? Meantime I'll just add the jar files to my classpath, like in the old days ;-)[/QUOTE]

sun-j2sdk1.5 wont work with Openoffice? I find that pretty hard to believe.

Enless of course you're just not using the sun jdk because its not
open sourse, in which case I see your point.

As far as I know ubuntu-desktop is just a meta package and not actually needed for anything after its been installed once.

I uninstalled it long ago.

---

