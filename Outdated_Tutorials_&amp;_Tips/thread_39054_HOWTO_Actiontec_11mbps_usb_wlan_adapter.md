---
title: "HOWTO: Actiontec 11mbps usb wlan adapter"
date: 2005-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by DarkT on 2005-06-03
After much searching and banging of head on wall I've managed to get my actiontec adapter working under ubuntu (and other 2.6.* kernel OS's) and hopefully the instructions will work for others aswell. 
 
[COLOR=Red]**Things to download before you start:**[/COLOR]
Vistit the [Berlios](http://at76c503a.berlios.de/cvs.html) cvs page and either grab their cvs snapshot or check it out, follow instructions on the page. It's worth mentioning that neither the ubuntu source package nor the atmel-firmware package work with this adaptor or possibly even a 2.6.* kernel so don't go down that route, it's a waste of time.

Next go to [http://thekelleys.org.uk/atmel/](http://thekelleys.org.uk/atmel/) (at the time of writing this site is down) and grab the latest firmware tarball (1.3 at the time of writing).
 
[COLOR=Red]**Making and Installing:**[/COLOR]
This bit should be simple, I'm making the assumption you have all the appropriate build packages installed (build-essentials etc.).

cd to a tmp dir and install the firmware like so:
```
tar -xzf path/to/firmware/atmel-firmware-version.tar.gz
cd atmel-firmware
sudo ./install.sh
```

Now to install the driver, first either cd to the directory you checked out of cvs or follow the instructions from the Berlios site for checking out the snapshot tarball and cd to the new directory. Now:
```
make
sudo make install
```
...should build and install the drivers. If not it probably means you haven't got all the requirements installed, check the errors and try to find the packages you need .

Now unplug(if it's already plugged in) and plug in the wireless adaptor, then run
```
tail -f /var/log/messages
ctrl+c to quit
```
...after a few secconds this *should* tell you that the device has been detected, the appropriate firmware sent and it's been registered (as wlan0 unless you've passed the module other perameters), if not you may need a restart although this is unlikely.

[COLOR=Red]**Configuring:**[/COLOR]
This is slightly more difficult to describe but hopefully I can generalize it enough for people to figure it out. I should first say that all the wireless apps that come with ubuntu/kubuntu such as gnome's network tools and kde's KWifiManager haven't worked at all for me and I've had to edit configs manually. That said it all works fine and shouldn't be too much of a problem.

You'll want to open up /etc/network/interfaces with your favorite text editor (with root privalages, so gksudo/kdesu if you are using a graphical editor) i.e. 
```
gksudo gedit
``` or ```
sudo nano /etc/network/interfaces
``` if you're a console whore like me ;)

Now you will want to add something resembling this to interfaces (ignoring the text in red):
```
auto wlan0 [COLOR=Red](starts the network automatically on startup, please note dhcp server must be running otherwise startup will take ages as your dhcp client searches for the network)[/COLOR]
iface wlan0 inet dhcp [COLOR=Red](this indicates that you connect to a dhcp server and I *think* inet means you connect to the internet via this adapter)[/COLOR]
wireless-essid YOUR-ESSID [COLOR=Red](the ID that identifies the network)[/COLOR]
wireless-key your-hex-key [COLOR=Red](or if it's a string precede it with s: e.g. s:mypassword )[/COLOR]
wireless-mode ad-hoc [COLOR=Red](a choice between: Ad-Hoc, Managed,  Master, Repeater, Secondary, Monitor or auto)[/COLOR]
wireless-channel 1 [COLOR=Red]The channel your network opporates on[/COLOR]
wireless-ap auto [COLOR=Red]Unsure, auto works for me[/COLOR]
wireless-rate 11M [COLOR=Red]The speed of your wireless network, if it varies depending on the slowest adaptor connected at the time then set to auto[/COLOR]
```

This should be enough setting up to get your network up and running, however if you have problems or don't understand the settings then try ```
man iwconfig
``` or looking up some more general wireless howtos for debian based distros.

[COLOR=Red]**Running:**[/COLOR]

So if all has gone well you should now be able to start your network with:
```
sudo ifdown -a
sudo ifup -a
```
This turns off all network interfaces and then starts all network interfaces, the -a tells it to do this to all interfaces marked auto as we did in /etc/network/interfaces. Try pinging another adapter on the network, or viewing a webpage if you connect to the net via the adapter. Hopefully you will goggle with joy that you've gotten your adapter working in linux like I did :) 

[COLOR=Red]**Final Note:**[/COLOR]

Because of the way it's been set up the network should set itself up every time you boot your computer but if you re-plug your adapter you will have to run ```
sudo ifdown -a
sudo ifup -a
```
or at the least just ```
sudo ifup -a
```

If you wish to change the way the network is registered, from wlan0 to something else, you do this by passing the appropriate module (check /var/log/messages) arguments. I have no idea how to go about this. Howver you must remember to update /etc/network/interfaces to reflect how you change it.

Hopefully people will find this useful, but if you have problems with this you can PM me or post here and I will append/fix anything I've gotten wrong. I will try to help with problems but I'm no expert. 
Not too bad for a first HOWTO :)

---

