---
title: "broken packages"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by djhbrown on 2013-05-04
ubuntu 12.10 amd 64
trying to find a way to select text in a linearised pdf file
pdf edit doesnt work, xjournal doesnt work
so tried to install acrobat reader
followed instructions on
[http://www.liberiangeek.net/2012/10/install-adobe-reader-in-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/10/install-adobe-reader-in-ubuntu-12-10-quantal-quetzal/)
but this is what happens:

david@david-HP-Pavilion-dv6700-Notebook-PC:~$ sudo apt-get install ia32-libs
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
E: Unable to correct problems, you have held broken packages.
david@david-HP-Pavilion-dv6700-Notebook-PC:~$ sudo apt-get install ia32-libs-multiarch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: gstreamer0.10-plugins-base:i386 but it is not going to be installed
                            Depends: gstreamer0.10-plugins-good:i386 but it is not going to be installed
                            Depends: gtk2-engines:i386 but it is not going to be installed
                            Depends: gtk2-engines-murrine:i386 but it is not going to be installed
                            Depends: gtk2-engines-pixbuf:i386 but it is not going to be installed
                            Depends: gtk2-engines-oxygen:i386 but it is not going to be installed
                            Depends: gvfs:i386 but it is not going to be installed
                            Depends: ibus-gtk:i386 but it is not going to be installed
                            Depends: libasound2-plugins:i386 but it is not going to be installed
                            Depends: libcanberra-gtk-module:i386 but it is not going to be installed
                            Depends: libdbus-glib-1-2:i386 but it is not going to be installed
                            Depends: libgail-common:i386 but it is not going to be installed
                            Depends: libgconf-2-4:i386 but it is not going to be installed
                            Depends: libglapi-mesa:i386 but it is not going to be installed
                            Depends: libglu1-mesa:i386 but it is not going to be installed
                            Depends: libgtk2.0-0:i386 but it is not going to be installed
                            Depends: libpulse-mainloop-glib0:i386 but it is not going to be installed
                            Depends: libqt4-dbus:i386 but it is not going to be installed
                            Depends: libqt4-network:i386 but it is not going to be installed
                            Depends: libqt4-opengl:i386 but it is not going to be installed
                            Depends: libqt4-qt3support:i386 but it is not going to be installed
                            Depends: libqt4-script:i386 but it is not going to be installed
                            Depends: libqt4-scripttools:i386 but it is not going to be installed
                            Depends: libqt4-sql:i386 but it is not going to be installed
                            Depends: libqt4-svg:i386 but it is not going to be installed
                            Depends: libqt4-test:i386 but it is not going to be installed
                            Depends: libqt4-xml:i386 but it is not going to be installed
                            Depends: libqt4-xmlpatterns:i386 but it is not going to be installed
                            Depends: libqtcore4:i386 but it is not going to be installed
                            Depends: libqtgui4:i386 but it is not going to be installed
                            Depends: libqtwebkit4:i386 but it is not going to be installed
                            Depends: librsvg2-common:i386 but it is not going to be installed
                            Recommends: libgl1-mesa-glx:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

great... now what?

---

### Post by fantab on 2013-05-05
This is the one of the reasons why you are NOT recommended to use software from WWW. You always, as far as possible, install packages from [Ubuntu Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu"). Adobe Reader is available from Ubuntu Partner Repositories, I think. To be able to install it from "Software Center" you have to ENABLE "PARTNER" repository. You can do this with "Software Center".

Also, you are encourage to install "Synaptic Package Manager"... such issues can be handled and corrected with it with relative ease.

To solve your issue, try from Terminal:
sudo dpkg remove --purge AdbeRdr9 ia32-libs
sudo apt-get autoremove
sudo apt-get -f install
sudo apt-get clean

Now open 'Software Sources' and enable "Partner" repositories under "Other software". then:

sudo apt-get update

Open software center and look for either "acroread" or "adobe-reader", I don't exactly remember what that package is called.

---

