---
title: "Upgrade or Install : EEE PC netbook user planning the move to 10.04 Lucid"
date: 2010-05-13
forum: Programming Talk
---

### Post by pete_m on 2010-05-13
i'm planning an imminent move to Ubuntu Lucid  ( & Debian Sid ? ) . . 

i've put some work into my existing Ubuntu install based on 9.10 karmic nbr2 and am very happy with the results - full credit and thanks to all

i've uploaded some screenshots. . .[http://www.youtube.com/watch?v=YoI4wRVVjBs](http://www.youtube.com/watch?v=YoI4wRVVjBs)

i'm therefore hoping to be able to upgrade my machine rather than do a fresh install, tho i have by now got .iso's of my present install and backups( dumps ) of gconf.

i found this thread . .

>Old  2 Weeks Ago          #1           >rossholley         >Ubuntu 9.10 Karmic Koala asked . .
    
>Anybody manage to get this working on an eee pc? 

seemed a promising topic so thought i'd subscribe but . .

>Sorry! This forum is not accepting new posts.

not sure why this is the case . ... th'o i guess it's because Lucid Testing is now closed . .
maybe such ( recently live ) threads could be shunted to appropriate forum locations when sub-forums close

that thread suggested that there may be WIFI problems with Lucid  for  some users. i don't know if these had been fixed before the release . . 
from launchpad .  .[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093)
check out post 53 . .

in any event i suspect i may find some wrinkles on the way

so i'm posting a fresh thread here about this process  in case fellow programmers may be interested & to see if others have experience to share or guidance to offer . .


P..S. writing this in EB4 booted from a  USB stck made in 9.10 - all good tho' couldn't get the stick to function with persistent storage. .


P.P.S. 
for those like me who like to tinker.. i've made a handful of custom launchers  - here are the command lines. .

NAUTILUS  - home 
gksu nautilus --no-desktop --browser %U


AYOR - use these with caution as you may do serious damage from here - not for total newbies.

NAUTILUS  - home  as ROOT
gksu nautilus --no-desktop --browser %U

NAUTILUS  - filesystem as ROOT
gksu  nautilus --no-desktop --browser /

ROOT terminal :
gksu /usr/bin/x-terminal-emulator

ROOT GNOME CONFIGURATION  :
gksu gconf-editor

---

