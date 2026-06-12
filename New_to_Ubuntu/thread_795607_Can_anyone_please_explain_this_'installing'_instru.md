---
title: "Can anyone please explain this 'installing' instructions for me please?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by bilbo.san on 2008-05-15
Hi,
I want to install my Canon printer IP4200 on Ubuntu 8. Found this instructions, but as I do not understand much about this things... I found my self lost on the step # 7.
It tells about linking files one to the other, and I do not know if that is risky for the system or if it could spoil something else up.

Thanks
b.

---

### Post by celticbhoy on 2008-05-15
You will need to post a link to your instructions

---

### Post by bilbo.san on 2008-05-15
Oh... yes.. sorry, the instructions found are here [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

thanks again.

---

### Post by celticbhoy on 2008-05-15
I think I would just type each command into a terminal just in case - wont do any harm.

 sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3 

 sudo ln -s /usr/lib/libpng.so /usr/lib/libpng.so.3 

 sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1 

 sudo ldconfig 

Then move on to step eight.

---

### Post by stchman on 2008-05-15
> **bilbo.san said:**
> Oh... yes.. sorry, the instructions found are here [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

thanks again.

Those instructions are pretty straightforward.  You might want to automate them in a script.

```

#!/bin/sh


sudo apt-get update 
sudo apt-get install alien libxml1 libpng12-0 libpng12-dev libgtk1.2 libgtk1.2-common

cd ~

mkdir canon 
cd canon
wget http://software.canon-europe.com/files/soft24302/software/iP4200_Linux_260.tar.gz

tar -xvzf iP4200_Linux_260.tar.gz

sudo alien cnijfilter-common-2.60-1.i386.rpm cnijfilter-ip4200-2.60-1.i386.rpm 

sudo dpkg -i *.deb

sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

sudo ln -s /usr/lib/libpng.so /usr/lib/libpng.so.3

sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1

sudo ldconfig

sudo /etc/init.d/cupsys restart 


```

Save the code and call it canon_ip4200.sh in your home folder.

After that make the script executable by doing:

```
chmod 755 ~/canon_ip4200.sh

```
Then run it as root by doing:
```

sudo ~/canon_ip4200.sh
```

Then add the printer using instruction 9.

9. Add a new printer. Under GNOME, this is accessed in System|Preferences|Printing. Select Canon as the manufacturer, click on "Install Driver..." and select /usr/share/cups/model/canonip4200.ppd. Now select "iP4200 Ver.2.60" under "Model". Select "Standard" for the driver (this should be the only option). Make sure the connection is correct. Hopefully, printing a test page will work!

---

