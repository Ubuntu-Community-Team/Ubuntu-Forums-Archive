---
title: "Scratch 32 bit on x64 help"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by rjsanch on 2012-01-25
Hey, I am taking the CS 50 class online via Harvard's site. Brand new to ubuntu with 1 year or so of tech support as my only computer science experience.
So Scratch from MIT is the first program the class works with. Unfortunately Scratch only offers a 32 bit version.
A fix is offered:

sudo dpkg --force-architecture -i ./scratch_1.4.0.1-0ubuntu5_i386.deb

which I have finally got running to no avail due to some error. Any help would be great.

hesupprt@Test:~/Desktop$ sudo dpkg --force-architecture -i ./scratch_1.4.0.1-0ubuntu5_i386.deb
(Reading database ... 143908 files and directories currently installed.)
Preparing to replace scratch:i386 1:1.4.0.1-0ubuntu5 (using .../scratch_1.4.0.1-0ubuntu5_i386.deb) ...
Unpacking replacement scratch:i386 ...
dpkg: dependency problems prevent configuration of scratch:i386:
 scratch:i386 depends on libv4l-0 (>= 0.5.0).
dpkg: error processing scratch:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for hicolor-icon-theme ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Errors were encountered while processing:
 scratch:i386

---

### Post by oldos2er on 2012-01-25
Which version of Ubuntu are you using? This > dpkg: dependency problems prevent configuration of scratch:i386:
scratch:i386 depends on libv4l-0 (>= 0.5.0). is telling you scratch needs a newer version of libv4l than the one you currently have.

---

### Post by rjsanch on 2012-01-25
Thanks! there were like 288 updates pending, letting those go before I try it again I am assuming that libv4l is somewhere in there.

---

