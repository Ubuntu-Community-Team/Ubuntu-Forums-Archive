---
title: "Howto: getting Speedtouch USB ADSL in Ubuntu Hoary"
date: 2005-04-11
forum: Outdated Tutorials &amp; Tips
---

### Post by cpinto on 2005-04-11
Hi all,
I noticed there are a few users asking how to get the Speedtouch USB ADSL modem working with Ubuntu and I just made a quick guide about making it work. 

Hope this is helpful to anyone:

------
Let's get started by downloading the speedtouch-suite from [http://s1x.homelinux.net/projects/speedtouch_suite](http://s1x.homelinux.net/projects/speedtouch_suite).
Follow the instructions in that website, namely the ones about downloading the firmware.
Once you've installed that one, you'll have to edit the file /etc/hotplug/usb/speedtouch by executing the command:
> 
    % sudo gedit /etc/hotplug/usb/speedtouch 


Now locate the following text lines, which will be at the top of the file:
> 
    ####
    # Load correct modules.conf
    MODULES_CONF=""
    [ -f /etc/modules.conf ] && MODULES_CONF=/etc/modules.conf
    [ -f /etc/modprobe.conf ] && MODULES_CONF=/etc/modprobe.conf
    [ -z $MODULES_CONF ] && exit 1 

Replace those lines with:
> 
    ####
    # Load correct modules.conf
    MODULES_CONF=""
    [ -f /etc/modules.conf ] && MODULES_CONF=/etc/modules.conf
    [ -f /etc/modprobe.conf ] && MODULES_CONF=/etc/modprobe.conf
    [ -f /etc/modprobe.d/aliases ] && MODULES_CONF=/etc/modprobe.d/aliases
    [ -z $MODULES_CONF ] && exit 1 

This is why speedtouch-suite and GNOME PPX do not work out-of-the-box.
Next thing to do is to install GNOME PPX. Get the installer file from [http://gnome-ppx.berlios.de/download/](http://gnome-ppx.berlios.de/download/) and run it by executing the command:
> 
    % sh gnome-ppx-0.6.1.package 

When this finishes, try connecting your Speedtouch USB ADSL modem. When the green lights stop blinking you have an ADSL link ready to go.

On the Applications/System menu there are the PPPOE and PPPOA Dialer items. Execute the one you see fit to get connected. BTW, you'll probably run into an issue and get a popup stating that pppoe doesn't have the suid bit on. Right click on the menu item and choose "Add this launcher to panel". Then right-click on the new panel icon and in the command insert gksudo before whatever is there. For example, to use the pppoe_dialer the command must be: gksudo pppoe_dialer.

Click on it, choose "nas0" as network interface (I think pppoa users must choose tap0 instead), type in your username and password and click connect.

This should get you up and running. Bear in mind that you should install a firewall, in which case the firestarter package is a really nice choice.

---

### Post by rdfi on 2005-04-20
I couldn't get it to work...
First the script speedtouch_suit tries to install gnome-ppx from the internet, which I obviouly don't have access to.
Anyway I  installed gnome-ppx by downloading the installer file from [http://gnome-ppx.berlios.de/download/](http://gnome-ppx.berlios.de/download/) but nothing new appears on the applications/System menu.
I tried to use the command pppe_dialer but this crashes.
What am I doing wrong?

---

### Post by saul on 2005-04-22
Hi, you could try this [http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html](http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html), it works. I apologize for my english.

---

### Post by poofyhairguy on 2005-05-13
bump

---

### Post by brookiemonsta on 2005-06-16
Hi,

 I tried following the instructions above, and got absolutely nowhere. The "autopackage" installer that is used in the method described does not support Ubuntu. Also, the installation script requires you to be online when you run it -  a bit of a problem if you are relying on your SpeedTouch USB modem for your internet connection!   ](*,) 

 However, I have found an installation method that works perfectly on Ubuntu Hoary with my SpeedTouch 330 - apparently it works with other SpeedTouch modems too. There are instructions at [http://speedtouchconf.sourceforge.net/](http://speedtouchconf.sourceforge.net/)  :grin: 

 You will need to make sure that you have the *gcc* and *make* packages installed because the install script has to compile some of the code automatically. Other than that the only information you need is your ISP username and password, and your VCI and VPI settings.

 Happy installing!

---

### Post by Karlos on 2005-06-17
i agree .. the speedtouchconf script works fine for me.
it even configures the modem to fire up on boot
but you do have to add pppoatm to your /etc/modules
and to make it connect on boot you have to adjust your /etc/speedtouch.conf
you change LOAD_USBCORE and LOAD_USBINTERFACE from =1 to =0
also I personally have found that the script from NOV 2004 works best

---

### Post by mhearn on 2005-06-22
[QUOTE=brookiemonsta]Hi,

 I tried following the instructions above, and got absolutely nowhere. The "autopackage" installer that is used in the method described does not support Ubuntu. Also, the installation script requires you to be online when you run it -  a bit of a problem if you are relying on your SpeedTouch USB modem for your internet connection!   ](*,) 

 However, I have found an installation method that works perfectly on Ubuntu Hoary with my SpeedTouch 330 - apparently it works with other SpeedTouch modems too. There are instructions at [http://speedtouchconf.sourceforge.net/](http://speedtouchconf.sourceforge.net/)  :grin: 

 You will need to make sure that you have the *gcc* and *make* packages installed because the install script has to compile some of the code automatically. Other than that the only information you need is your ISP username and password, and your VCI and VPI settings.

 Happy installing![/QUOTE]
 Hi, that isn't quite correct, autopackage works just fine on Ubuntu. If the gnome-ppx package didn't install for you, we need to investigate and find out why, then fix it.

Incidentally you can download a couple of files and put them in the same directory as the .package file to make it work offline. We need to document this better.

---

### Post by frank_b on 2005-08-05
Hi all.


I tried to follow the procedure described here in the first post and it didn't work. (I couldn't even see the error messages since the windows just suddently closed...)

I then tried the first alternative instructions that "saul" suggested here - [http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html](http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html) - and it worked just fine...  ;-)  (thank you "saul"!)  :) 

Therefore, I suggest to everyone confused by the previous contradictry posts to just ignore the original one and try the first alternative.


Also, about the procedures listed in the "speedtouch suite", for the record, I also (even) live in Portugal...  ;-)

---

