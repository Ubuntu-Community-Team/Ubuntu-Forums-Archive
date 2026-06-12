---
title: "update"
date: 2012-12-03
forum: New to Ubuntu
---

### Post by jlshankar on 2012-12-03
hai,

i am getting the following error while updating my os.

help me to solve.

"accountsservice adobe-flash-properties-gtk adobe-flashplugin apport apport-gtk apt apt-transport-https apt-utils bind9-host dbus dbus-x11 dhcp3-client dhcp3-common dnsutils eog evince evince-common firefox firefox-branding firefox-globalmenu firefox-gnome-support firefox-locale-en ghostscript ghostscript-cups ghostscript-x ginn gir1.2-rb-3.0 gir1.2-totem-1.0 glib-networking glib-networking-common glib-networking-services gnome-control-center gnome-control-center-data gnome-dictionary gnome-media gnupg gnupg-curl google-chrome-stable gpgv grub-common grub-pc grub-pc-bin grub2-common gstreamer0.10-plugins-bad gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs isc-dhcp-client isc-dhcp-common jockey-common jockey-gtk libaccountsservice0 libapt-inst1.4 libapt-pkg4.12 libart-2.0-2 libbind9-80 libc-bin libc-dev-bin libc6 libc6-dev libdbus-1-3 libdns81 libevince3-3 libframe6 libgc1c2 libgdict-1.0-6 libgdict-common libgeis1 libgnome-control-center1 libgnome2-0 libgnome2-bin libgnome2-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgrail5 libgrip0 libgs9 libgs9-common libgstreamer-plugins-bad0.10-0 libisc83 libisccc80 libisccfg82 liblwres80 libnux-2.0-0 libnux-2.0-common librhythmbox-core5 libssl1.0.0 libtotem0 libunity-2d-private0 libunity-core-5.0-5 libxml2 libxml2-utils libxslt1.1 linux-firmware linux-generic linux-headers-3.2.0-32 linux-headers-3.2.0-32-generic linux-headers-3.2.0-32-generic-pae linux-headers-generic linux-headers-generic-pae linux-image-3.2.0-32-generic linux-image-generic linux-libc-dev login multiarch-support ntfs-3g ntfsprogs nux-tools nvidia-common onboard openssl passwd policykit-1-gnome python-apport python-gst0.10 python-libxml2 python-problem-report python-software-properties resolvconf rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins sessioninstaller software-center software-properties-common software-properties-gtk thunderbird thunderbird-globalmenu thunderbird-gnome-support totem totem-common totem-mozilla totem-plugins transmission-common transmission-gtk tzdata ubuntu-keyring unity unity-2d unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread unity-common unity-services update-manager"


shankar

---

### Post by Isamu715 on 2012-12-03
Please provide more information(maybe the full error message at least), all I can see here is a huge list of packages. Make sure you're connected to the Internet and try running:
```
sudo apt-get update
sudo apt-get upgrade
```You can also try to change your download mirror in "Software sources".

---

### Post by audiomick on 2012-12-03
There is no error message to be seen in there, or at least I can't see one. That is just a list of packages, presumably those that were to be updated.

A tip, though: when you post output like that, use the button marked with # at the top of the posting window, and put the output between the code tags that it makes [noparse] ```
 here 
``` [/noparse]

---

