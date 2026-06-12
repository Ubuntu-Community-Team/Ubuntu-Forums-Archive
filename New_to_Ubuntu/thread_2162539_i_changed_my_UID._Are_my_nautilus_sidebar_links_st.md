---
title: "i changed my UID. Are my nautilus sidebar links still using the old uid?"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by mathew.davis on 2013-07-15
I changed my UID, to make my dual boot play nice.

Are my nautilus sidebar links to other devices still using the old uid to mount/unmount?


Hello,

I have set up my macbook pro 8,1 with dual boot ubuntu 13.04 / oxs mountain lion.

after everything was installed i changed my linux uid to 501 so that it matches the uid on the osx install
i updated all file permissions
linux seems happy with what i have done. 

I can mount the osx partions in terminal, and I don't need sudo with:

/usr/bin/udisks --mount /dev/sda3

and they mount to 

/media/<user>/<device name>


then I can read the osx partitions and write to the unjournaled partition.

here's just one problem:

in nautilus (files) there are links to the partitions under 'devices' in the sidebar, but these links won't mount the partitions they link to.

I get a message that the location cannot be displayed i don't have the necessary permissions.

if I mount the partitions in terminal first, then the sidebar links do work.

but the links won't work to unmount without authenticating, it pops up a message saying they were mounted by another user.

all this makes me suspect that the sidebar links are using my old uid : 1000 to mount and unmount.


any advice about how i can dig a bit further into understanding and fixing this?

cheers and thanks for help,

mat



and extra details about gid:

i added my linux user to the group with gid 20, to be compatible with the gid of my osx user. 
maybe i'll have to switch the gui of my linux user to 20,
but  as 20 already exists i'm trying to keep my changes minimal for now  while I understand the consequences of fiddling with the gids in the two  operating systems.
maybe i can just add my osx user to group 1000, the default group for my linux user?

UPDATE: according to the syslog, clicking the link does use the correct UID, but it doesn't work even though mounting via terminal with the same user does.

Jul 15 17:42:34 silverfox dbus[930]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Jul 15 17:42:34 silverfox dbus[930]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jul 15 17:42:41 silverfox udisksd[1920]: Mounted /dev/sda3 at /media/mathew/book on behalf of uid 501
Jul 15 17:50:24 silverfox dbus[930]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Jul 15 17:50:24 silverfox dbus[930]: [system] Successfully activated service 'org.freedesktop.hostname1'

Jul 15 17:50:26 silverfox udisksd[1920]: Cleaning up mount point /media/mathew/book (device 8:3 is not mounted)
Jul 15 17:50:26 silverfox udisksd[1920]: Unmounted /dev/sda3 on behalf of uid 501

---

