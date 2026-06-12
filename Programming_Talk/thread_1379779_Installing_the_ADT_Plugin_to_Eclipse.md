---
title: "Installing the ADT Plugin to Eclipse"
date: 2010-01-12
forum: Programming Talk
---

### Post by topviet on 2010-01-12
I got this error message when install the ADT plugin to Eclipse 3.5.1 (Galileo) on my Ubuntu 9.10.

> Missing requirement: Android Development Tools 0.9.5.v200911191123-20404 (com.android.ide.eclipse.adt.feature.group 0.9.5.v200911191123-20404) requires 'org.eclipse.wst.xml.ui 0.0.0' but it could not be found


Any suggestion to overcome this error. Thanks.

---

### Post by steve. on 2010-01-13
> **topviet said:**
> I got this error message when install the ADT plugin to Eclipse 3.5.1 (Galileo) on my Ubuntu 9.10.

Missing requirement: Android Development Tools 0.9.5.v200911191123-20404 (com.android.ide.eclipse.adt.feature.group 0.9.5.v200911191123-20404) requires 'org.eclipse.wst.xml.ui 0.0.0' but it could not be found

Any suggestion to overcome this error. Thanks.

I had the same problem and the first post in this thread helped me sort it out.
[http://ubuntuforums.org/showthread.php?t=1305691](http://ubuntuforums.org/showthread.php?t=1305691)

I just added all of these and it found the missing requirement.
> Help Menu -> Install New Software

* Add:
[https://dl-ssl.google.com/android/eclipse/](https://dl-ssl.google.com/android/eclipse/)
[http://download.eclipse.org/datatools/updates](http://download.eclipse.org/datatools/updates)
[http://download.eclipse.org/webtools/updates/](http://download.eclipse.org/webtools/updates/)
[http://download.eclipse.org/modeling/emf/updates/releases/](http://download.eclipse.org/modeling/emf/updates/releases/)
[http://download.eclipse.org/tools/gef/updates/releases/](http://download.eclipse.org/tools/gef/updates/releases/)
[http://dl.google.com/eclipse/plugin/3.5](http://dl.google.com/eclipse/plugin/3.5) (think this one's optional)

---

### Post by topviet on 2010-01-16
Thank Steve. It works. 

Since I moved to Ubuntu from Windows, I thought Eclipse for Linux already included packages for Java EE such as datatools, webtools,... as Windows version. For Eclipse running on Ubuntu, we need install additional packages as you suggested.

---

### Post by santhoshpulliman on 2010-10-11
i have some prob in installing android sdk in eclipse 3.5.1 in ubuntu9.10.........
error comes is shown below

[Cannot complete the install because one or more required items could not be found.
  Software being installed: Android Development Tools 0.9.9.v201009221407-60953 (com.android.ide.eclipse.adt.feature.group 0.9.9.v201009221407-60953)
  Missing requirement: Android Development Tools 0.9.9.v201009221407-60953 (com.android.ide.eclipse.adt.feature.group 0.9.9.v201009221407-60953) requires 'org.eclipse.wst.xml.ui 0.0.0' but it could not be found]

please give me some solution......:confused:

---

### Post by Nikolai5 on 2010-10-19
Try running Eclipse with root permissions. sudo command:
sudo ./eclipse

---

### Post by Vexiphne on 2011-01-01
I've had similar problems, but solved it and wrote a tutorial on it. Hope it can help you, even if it's just a little bit :)

[[COLOR="Blue"]_How to install Eclipse and the Android SDK on Ubuntu 10.10_[/COLOR]]("http://www.hannacam.net/tutorials/android-tutorials/how-to-install-eclipse-and-the-android-sdk-on-ubuntu-10-10/")

---

