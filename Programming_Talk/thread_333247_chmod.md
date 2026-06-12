---
title: "chmod ???"
date: 2007-01-07
forum: Programming Talk
---

### Post by ESPOiG on 2007-01-07
this is just an example but i was wonderin how i could do something

#!/bin/bash
echo "this requires root access"
sudo cp /usr/share/pixmaps/vlc.png /home/$USER/Desktop/vlc.png
sudo chmod a+rws /home/$USER/Desktop/vlc.png

ok now this does all i want it to do but 1 thing, which is allow the current user (me) to right click it in nautilus and change the permissions, because they are all set to root, how can i change the ownership of the file to me, i thought the 's' did that but i dunno im not really sure

thanks

---

### Post by Ramses de Norre on 2007-01-07
s is the set group id, and for safety you might better remove it again:
```
sudo chmod a-s /home/$USER/Desktop/vlc.png
sudo chown `whoami`:`whoami` /home/$USER/Desktop/vlc.png
```
The last line will make you owner of the file, ownership can be changed with chown and not with chmod.

---

### Post by ESPOiG on 2007-01-07
thanks i was a bit confused with all the chmod and chown commands but as long as it works ill remeber it :D... thx

---

