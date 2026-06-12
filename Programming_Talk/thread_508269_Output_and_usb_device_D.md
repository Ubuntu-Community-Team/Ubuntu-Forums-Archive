---
title: "Output and usb device :D"
date: 2007-07-24
forum: Programming Talk
---

### Post by shadow_of__soul on 2007-07-24
Hi,

i have some question if any can help me :D

i need to do a program what detect when a usb drive is conected, mount (if this is not mounted yet) and check if have a file, and if have it execute a program.

i think do this with a bash script running background. now the mount,read and execution function i have it but i dont now how detect if have a usb connected.

i thinking run a sg_scan -i command to now the devices, but i need to run every minute and this is not the best choice :( (if i dont have other option i do this xD)

for this i question:

any know if the OS do some signal when a usb drive is connected? something what i can catch to know if the usb is connected?

if i need to use the command, how i can save the output of the command to a variable to analyze that and know if a usb is connected?

remember, maybe the os where it running, dont have "plug and play" like ubuntu :D

i apreciate any help you can hive me :D

By Shadow

---

### Post by Carlos Santiago on 2007-07-24
Check this:
[http://ubuntuforums.org/showthread.php?t=502864](http://ubuntuforums.org/showthread.php?t=502864)

---

