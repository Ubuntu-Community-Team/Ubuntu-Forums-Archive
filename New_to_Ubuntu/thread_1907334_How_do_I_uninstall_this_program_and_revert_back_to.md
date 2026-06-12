---
title: "How do I uninstall this program and revert back to Ubuntu's one?"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by hopelessone on 2012-01-11
Hi,

> git clone git://linuxtv.org/media_build.git
cd media_build 
./build
sudo make install

From:
[http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

I can't uninstall it...

> blade@oneiric:~/Software/media_build$ sudo make uninstall
make -C /home/blade/Software/media_build/v4l uninstall
make[1]: Entering directory `/home/blade/Software/media_build/v4l'
make[1]: *** No rule to make target `uninstall'.  Stop.
make[1]: Leaving directory `/home/blade/Software/media_build/v4l'
make: *** [uninstall] Error 2
blade@oneiric:~/Software/media_build$ 

What do I do?

---

### Post by Krytarik on 2012-01-11
Try instead:
```
sudo make rminstall
```> **make rminstall** ... you would use this to remove the currently installed driver set (located within the relevant /lib/modules/["kernel version"]/kernel/drivers/media directory to which they were installed)[http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers#Retrieving_and_Building.2FCompiling_the_Latest_V4L-DVB_Source_Code](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers#Retrieving_and_Building.2FCompiling_the_Latest_V4L-DVB_Source_Code)

Then, to make sure the default drivers are installed, run:
```
sudo apt-get install --reinstall linux-image-`uname -r`
```Note: In case the first command fails, this would possibly simply replace all the installed drivers with default ones.

Regards.

---

### Post by Buntumatic on 2012-01-11
If everything else fails you can repeat install and pay attention which files are copied in the install phase. Those are the files you need to remove by hand.
Since in this case these are kernel modules they won't be used when you upgrade the kernel.

---

### Post by hopelessone on 2012-01-11
Thanks everyone!

The solution from Krytarik worked.

Was worried I'd have to do a reinstall

---

