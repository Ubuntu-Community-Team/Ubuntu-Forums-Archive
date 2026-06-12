---
title: "How to upgrade Sun  JDK 6 to 6 update 1."
date: 2007-06-03
forum: Programming Talk
---

### Post by hantsy on 2007-06-03
I try to use the make-jpkg tool to build deb package from sun binary package  for myself . But it prompt the message:
------------------------------------------------------------------------------------------------------------------
Creating temporary directory: /tmp/make-jpkg.oSMEl13663
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

Detected Debian build architecture: i386
Detected Debian GNU type: i486-linux-gnu

No matching plugin was found.
Removing temporary directory: done

--------------------------------------------------------------------------------------------------------------------
How can I do this?
Why the offical Sun JDK 6 not upgrade to 6 update1?

---

### Post by steve.horsley on 2007-06-04
I haven't a clue what you're talking about there. But I sould suggest downloading the self-extracting binary from Sun, and running that. It installs into /opt - you will need to re-point /usr/bin/java, which is a link to the existing java install.

---

### Post by hantsy on 2007-06-07
I see the method you provided.
I do not understand the ubuntu why not upgrade jdk 6 to 6 update1.
The new version has some feature good  for Gnome user.
For example ,
1.Desktop 3D effect bug fix for Beryl decoration
2.More friendly GTK look and feel  support to make java GUI application has no difference from other GTK native application.

---

### Post by steve.horsley on 2007-06-07
For stability reasons, Ubuntu is not updated after release - only security updates are released. This is true of most Linux distros, I believe. So if you want updates to a released version, you will have to make your own arrangements.

I have discovered recently that instead of overwriting the symlinks in /usr/bin, you can ut a link in /usr/local/bin and this is earlier than /usr/bin in the path, so you don't need to trash the original link.

---

### Post by JustAnotherVagueAnon on 2008-05-20
.

---

