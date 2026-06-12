---
title: "JNLP Files Not Opening with Iced Tea"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by Ebonhawke on 2013-05-04
Having a problem

Appears to be a similar issue to that reported in the thread below.  Any time I try to open a jnlp file with IcedTea, I get the following error message "abcdefg.jnlp could not be opened, because an unknown error occurred".  Have tried it with multiple jnlp files.  I believe the problem stems from my computer crashing while an update was occurring.  Have tried reinstalling openjdk6 etc, without luck.

[http://ubuntuforums.org/showthread.php?t=1432953](http://ubuntuforums.org/showthread.php?t=1432953)

However, this is with Iced Tea, rather than sun, and I've checked the solution that they identified (changing the exec to usr/bin from usr/lib)

This is my icedtea.netx.javaws.desktop

[Desktop Entry]
Name=IcedTea Java Web Start
Name[fi]=IcedTea Java - Web Start
Comment=IcedTea Java Web Start
Comment[fi]=IcedTea Java - Web Start
Exec=/usr/bin/javaws %u
Terminal=false
Type=Application
Icon=javaws
Categories=Application;Network;
MimeType=application/x-java-jnlp-file;
NoDisplay=true

---

### Post by Ebonhawke on 2013-05-08
Been a few days without a response - apologies for the bump

---

