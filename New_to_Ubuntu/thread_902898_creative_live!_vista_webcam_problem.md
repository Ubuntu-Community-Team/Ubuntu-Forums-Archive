---
title: "creative live! vista webcam problem"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by armyben on 2008-08-27
Hi all, I'm a new user to ubuntu. I had it on my pc before, with ervything working fine, until in a mad fit of madness i decided to install vista over ubuntu :( However, since having switched back I am having problems getting my creative live! vista (0420) to work.  Can anybody help?

P.S I should also mention that I still have the disk that came with the camera. Would running it in WINE help?

---

### Post by mewithafez on 2008-08-27
Hi, this camera uses the "ov51x-jpeg" driver from rastageeks.org if you are sure it is the Creative Live! Vista (0420)

open up a terminal and enter:

sudo apt-get update

it will ask for your password because you are using sudo, so just provide it and it will update. then enter:

sudo apt-get install ov51x-jpeg-source module-assistant

this will get the source code and something to help you install the driver and use it. finally, enter:

module-assistant a-i ov51x-jpeg 


You can see if it worked using cheese, which you can install from "add/remove programs"

all the best!

---

### Post by armyben on 2008-08-27
you are fantastic! I've spent the better part of all day trying to follow the instructions on rastageeks.org trying to get this camera to work and here you are with 3 lines of code :) i now have a working webcam.  Thank you very much.

---

### Post by mewithafez on 2008-08-28
Haha thank you, great to hear it worked. The info is on the wiki if you run into trouble in the future at [http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall#Install_debian_module_package](http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall#Install_debian_module_package)

---

