---
title: "Deja Dup backups everything?"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by XenonX on 2012-01-19
Hi..
I've done many things to my ubuntu 11.10.

installed restricted extras, VLC ... etc

installing these are done using SUDO

My question: if I back my system up by Deja Dup, will all software installed by SUDO be there in my restored ubuntu? 

is backing up ( /home ) is enough to restore the progs I mentioned above?



another question though: I changed the default OS to be XP .. will the deja dup save this configuration as well? 


Regards

---

### Post by mastablasta on 2012-01-19
sudo is just premission from the owner to install things. 
 
yes it would back them up.
 
no, /home is like My Documents and stores only settings and your personal files.
 
that configuration is done in Grub. If you make an image of the whole install it iwll save it otherwise not. What are you trying to do actually?
 
An easy to use backup tool for backing up only programmes/settings and data in home is Mintbackuptool.
 
however, if you plan to install newer version of linux it will have new version of those programmes you installed anyway. so you will have to download the new verison again. unless you know how to use the old version with new or old libraries.

---

### Post by XenonX on 2012-01-19
All I want is to make a backup for later use, just in case something happened to my PC so I won't have to look for the programs and terminal codes again. 
is deja dup useful for me? if there's another tool which can do it better of course I'd like to know it. 

Thanks

---

