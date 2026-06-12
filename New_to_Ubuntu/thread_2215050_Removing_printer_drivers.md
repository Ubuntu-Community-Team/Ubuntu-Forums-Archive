---
title: "Removing printer drivers"
date: 2014-04-04
forum: New to Ubuntu
---

### Post by Ramon_Tristani on 2014-04-04
The newest driver for my Canon MF4800 does not run in my Ubuntu 12.04 installation. I would like to remove the driver and re-install the old driver but the system would not allow this because "a newer driver is installed". How do I remove one and install the one I want? 

thanks,
Ramon

---

### Post by bapoumba on 2014-04-04
How did you install the drivers you want to remove ?

---

### Post by Ramon_Tristani on 2014-04-04
With the Ubuntu Software Center.

---

### Post by bapoumba on 2014-04-04
Does you previous driver work with your release ? If so :
```
sudo apt-get update
sudo apt-get purge <your_new_driver>
sudo apt-get install <your_old_driver>
```

Does the software center have an option to remove the package ?

---

### Post by pdc on 2014-04-05
You will be using the Canon UFR driver? The latest version is it the 2.8 version, issued 26th February 2014; ..........so pretty recent update ........

one could obtain it from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html) ........if one wished to download it .............. it comes down as [COLOR="#008000"]Linux_UFRII_PrinterDriver_V280_uk_EN.tar.gz[/COLOR]

Inside it are various instructions: taken from the above: 

to delete the printer driver Canon suggest:

1) **_[COLOR="#008000"]Delete the printer's spooler registration:[/COLOR]_** > [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -x MF4800[/COLOR]

2) **_[COLOR="#008000"]Uninstall the UFR II printer driver module[/COLOR]_**. > [COLOR="#FF0000"]dpkg -P cndrvcups-ufr2[/COLOR]

3) [COLOR="#008000"]**_Uninstall the common module for CUPS drivers_**[/COLOR] > [COLOR="#FF0000"]dpkg -P cndrvcups-common[/COLOR]

_______________________-

you should then be "all clean" and you can re-install other versions as you wish

---

