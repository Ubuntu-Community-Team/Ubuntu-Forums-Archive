---
title: "Mozilla 1.7.13 error libgtk-1.2.so.0"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by jwferk on 2008-07-21
I've downloaded and tried to install Mozilla 1.7.13 using both the prepackaged Mozilla installer or the tar file. Followed the README directions in both cases.  When I try to run Mozilla after either installation approach I get the following error:


./mozilla-bin: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

Synaptic shows I have both libgtk1.2 and libgtk2.0.0 installed properly (libgtk2.0.0 was the default installation when I installed Ubuntu; Mozilla gave the same message when that was the only version of libgtk on my machine).

Any suggestions?

Firefox 3.0 works just fine.

---

### Post by Dark_Stang on 2008-07-22
Why not just install seamonkey (the new mozilla browser) from the repositories?

---

### Post by ET! on 2008-07-22
try re installing both the packages

---

### Post by jwferk on 2008-07-22
Thanks for the suggestions.  Unfortunately it appears neither worked.

I did a complete removal of all Firefox related items using Synaptic and then manually deleted the Mozilla folder I had put in /usr/local.

I installed Seamonkey via Synaptic.  It works very nicely.  Mozilla would still not install.

I reinstalled Firefox 3.0 with Synatptic.  It works very nicely.  Mozilla still does not install.

As for why I am trying to do this I use Sancho as a p2p GUI.  Sancho works fine with the exception of the web browser function.  The Sancho help page says:

*The integrated SWT browser requires a certain version of Mozilla with XFT support. It works with the gtk/motif/photon/carbon widget sets. More information on getting it to work is here.*

If you follow the next link you get this message:
[[I]I]
A: You need one of the following: 
Mozilla 1.4 GTK2 - 1.6 GTK2 can be used with Eclipse 3.0 and newer.
Mozilla 1.4 GTK2 - 1.7.8 GTK2 can be used with Eclipse 3.1 and newer.
Mozilla 1.4 GTK2 - 1.7.12 GTK2 can be used with Eclipse 3.2 and newer.
Firefox can be used with Eclipse 3.1 and newer (Linux only), provided that it has been compiled with linkable Gecko libraries. It is important to note that Firefox downloads from mozilla.org currently do not satisfy this criteria, but Firefox installations that are included in major Linux distributions often do in the absence of a XULRunner installation. Attempting to use a statically-linked Firefox install will display the error message "No more handles [NS_InitEmbedding...error -2147221164]".
XULRunner 1.8.x can be used with Eclipse 3.3 and newer
XULRunner 1.9.x can be used with Eclipse 3.4 and newer

The version of Mozilla or Firefox installed on your system varies with your Linux distribution. 
The following Linux distributions meet the Mozilla requirements for using the Browser widget. 
RedHat Enterprise Linux 3
Suse 9

The following Linux distributions meet the Firefox requirements for using the Browser widget. 
RedHat Enterprise Linux 4 
Note that you may need to set the environment variable MOZILLA_FIVE_HOME to the folder containing your Firefox install. e.g. setenv MOZILLA_FIVE_HOME /usr/lib/firefox-1.0.4[/I]

This specifies a requirement for MOzilla 1.4 -1.7.12[/I]

I already have Eclipse 3.2.2 running as well as XULrunner.

---

### Post by Bob Stine on 2010-11-01
I ran into this error today (1 Nov 2010) trying to install the chrome SDK on CentOS.  The solution for me was to install packages gtk+.i386 and gtk+-devel.i386.  

YMMV.

---

