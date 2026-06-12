---
title: "Block unauthorized usb device . Disable automount."
date: 2013-02-09
forum: New to Ubuntu
---

### Post by hermydana on 2013-02-09
Hello. I wrote a bash script that checks every second for new mounted usb devices. When a new device is mounted, my script gets its serial number and compares it with the serials i wrote in a text file, which represents my database of valid usb-devices. If the new mounted serial matches with one of the serials in my db, it's okay, but if it doesn't, i get the message"invalid device detected", and in the next second i unmount it with the command umount. The script runs every second, so even if the invalid device is mounted, in the next second is unmounted, you don't get to perform any action on it. My question is how can i do the following: When an invalid device is detected, a new bash window should appear, asking for my root password. If i type the correct password and i login as root, i am being asked if i want to mount the invalid device detected or not. If i do, i mount it, and if i don't, ...So, for the new window, i tried the xterm -e command, but i don't really know what to do next. If you are interested in helping me, i can post my script, to show you what i've done this far. I work in ubuntu. Thanx a lot!

---

