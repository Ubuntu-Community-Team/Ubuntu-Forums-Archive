---
title: "JRE errors in Open Office"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by freesitebuilder on 2008-04-28
Updated to Hardy today. I'm getting JRE errors in Open Office, as described here - [http://ubuntuforums.org/showthread.php?p=4669016](http://ubuntuforums.org/showthread.php?p=4669016) but I already have openoffice.org-java-common installed, version 1:2.4 in usr/lib/openoffice

OO options shows Sun Java 1.6.0_06 , in usr/lib/jvm

So which should I be using? I remember when I first switched to Ubuntu, I was using Dapper, and had to uninstall the Ubuntu JRE and install the Sun JRE.

TIA

---

### Post by freesitebuilder on 2008-04-30
A friend on the Ubuntu-UK mailing list solved this for me.

> I have had this exact issue and I managed to solve it by deleting the
> actual config file from the OpenOffice application directory in
> $HOME/.openoffice.org2/user/config/javasettings_Linux_x86.xml 
> 
> The file is recreated on OpenOffice restart and contains the correct
> path based on your next choice, it also remembers it in the OpenOffice
> dialogue. I'm guessing (for whatever reason) the file is locked and it
> refuses to change it.
> 
> 
> Just in case I'm wrong, please create a back up of that config file
> (or rename it) before attempting this. Ensure you shut down all
> running instances of OpenOffice before you delete it as well.

---

