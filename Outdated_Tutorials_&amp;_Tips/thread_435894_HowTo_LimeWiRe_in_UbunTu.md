---
title: "HowTo LimeWiRe in UbunTu"
date: 2007-05-07
forum: Outdated Tutorials &amp; Tips
---

### Post by AlexenderReez on 2007-05-07
as i was windows user ( long time ago...)suddenly i wonder  is there any way to use Limewire in ubuntu...so i decided to check it in official website.....but there is only contains Limewire in RPM package.....so this is howto basically howto convert limewire  RPM package to deb package..this works with gutsy (development ) and previous versions ...


firstly download Limewire from official website or any wbsite.....like

> [http://www10.limewire.com/download/LimeWireLinux.rpm](http://www10.limewire.com/download/LimeWireLinux.rpm)   

                                  stable version

 
                                        or

> [http://www9.limewire.com/beta/LimeWireLinux.rpm](http://www9.limewire.com/beta/LimeWireLinux.rpm)

                        development version


then just install alien

> sudo apt-get install alien

save limewire in one folder...let say it is ' limewire ' folder (name )...in home

then just

> sudo alien 

copy than rpm package paste it to terminal....

> cd 
copy that folder then paste it after that...(actually this is just change directory . . .easier than if you try to type the folder name,and save time with just copy that folder and paste it...

> sudo dpkg -i *.deb


then
> sudo gedit /usr/bin/limewire

you may see like

> #!/bin/bash
cd /usr/lib/LimeWire
sh ./runLime.sh

change it to become

> #!/bin/bash
cd /usr/lib/LimeWire
bash ./runLime.sh

ok then save...exit....you should can use your limewire right now....:)

EDIT:actually i just realized that you can even download limewirein deb package  at its official website......

---

### Post by oGGe on 2007-06-03
> **reez0105 said:**
> as i was windows user ( long time ago...)suddenly i wonder  is there any way to use Limewire in ubuntu...so i decided to check it in official website.....but there is only contains Limewire in RPM package.....so this is howto basically howto convert limewire  RPM package to deb package..this works with gutsy (development ) and previous versions ...


firstly download Limewire from official website or any wbsite.....like

   

                                  stable version

 
                                        or



                        development version


then just install alien



save limewire in one folder...let say it is ' limewire ' folder (name )...in home

then just



copy than rpm package paste it to terminal....


copy that folder then paste it after that...(actually this is just change directory . . .easier than if you try to type the folder name,and save time with just copy that folder and paste it...




then


you may see like



change it to become



ok then save...exit....you should can use your limewire right now....:)

EDIT:actually i just realized that you can even download limewirein deb package  at its official website......

Why use LimeWire when you can get more speed by using the clone FrostWire with Ubuntu package on their website? Duh ;D

---

### Post by greeni08 on 2008-12-09
Limewire was originally made for linux...it's been around for years so I don't know how you needed to do all that conversion but I agree that you should use FrostWire...it's much better

---

