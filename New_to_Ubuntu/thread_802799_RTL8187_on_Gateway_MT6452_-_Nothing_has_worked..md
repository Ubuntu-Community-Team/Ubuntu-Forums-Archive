---
title: "RTL8187 on Gateway MT6452 - Nothing has worked."
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Twilight in Zero on 2008-05-21
I hate to open on a bad note, but having received no help on my thread in General Help, I was forced to reinstall Ubuntu for my third time. But then again, I probably shouldn't have started out in General Help. My mistake. I'm using the 32-bit version instead of the 64-bit version this time. I'm using Wubi, by the way, but it shouldn't matter here. And my Ubuntu is version 8.04, Hardy Heron.

Now that Ubuntu actually starts up, I'd like to get to the issue at hand. I want to get my wireless card working. It's an onboard card, the infamous Realtek rtl8187. I don't know if mine is 8187 or 8187b. It's infamous for its native driver dropping connections often (or not even connecting at all).

I've done forum and internet searches galore, but I haven't gotten anything to work. Being a Linux newbie (I'm good with Windows, mind you), I don't really know how to uninstall drivers and replace them with new ones. I've seen many recommendations toward Win98's driver with ndiswrapper, but using ndisgtk to install it only kills off whatever connection I already had.

I followed some directions [_here_]("http://ubuntuforums.org/showthread.php?t=529090") to install the Win98 drivers, but they did nothing. I couldn't connect to my router. I don't like that method anyways; I want to be able to pick my network via the wireless icon, especially once I start back up at school in August. I don't want to do everything via shell scripts and terminals. I've left it in the state it was in after trying those instructions. I don't really know how to revert the changes except for bringing back the Network Manager. I haven't done so yet.

I'm in Windows right now, at a loss for what to do. I'd really like to use Ubuntu more regularly, but it's impossible unless I have an internet connection.

I'll take any step you tell me to, regardless of whether or not I've already done it (Except install 64-bit Windows drivers; that's what killed Ubuntu the last two times). Any and all help will be appreciated. Thank you! :)

---

### Post by spiderbatdad on 2008-05-21
This card is supposedly supported since Edgy. You may need to install headers. First try installing network manager, if you have removed it:
```
sudo apt-get install network-manager-gnome
```

Then add headers:```
sudo apt-get install linux-headers-`uname -r` 
```
create a link to the build modules:
```
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

```

Reboot. Select your network from the network monitor applet...if you dont see the applet, try adding the 'notification area' to your panel...if you still don't see it. Alt+F2 run: nm-applet

Good luck.

---

### Post by Twilight in Zero on 2008-05-21
Thank you, spider. But I already had the linux headers.

But I figured that the best thing to do first was to get the native drivers back. I've been having the best luck with them, even though that luck is bad luck. I've got the native drivers back up, and NetworkManager back too.

But the speed varies **wildly** and they still drop connection after a little bit. I have to restart it with this little bit I found somewhere:```
rmmod rtl8187
modprobe rtl8187
/etc/init.d/networking restart
```
It's unfortunate to say that I'm becoming more familiar with the terminal this way. :(

I've seen other drivers (not ndiswrapper; actual Linux drivers) across the web, though. How would I go about replacing the native drivers with those? That's probably the next step I should take... unless someone has a better idea?

---

### Post by Twilight in Zero on 2008-05-22
I've installed aircrack-ng drivers. They seem to work (emphasis on seem; I don't want to jinx myself), but they don't start when I start the computer, and I can't execute the wlan0up script. I have to execute all the commands in the terminal myself, but it does connect to my router and give me internets, and they seem to work. At least the connectsion hasn't dropped yet.

At any rate, how do I get the script to run every time my computer starts? I've inserted pre-up and post-down thingies into my /etc/network/interfaces, but that doesn't seem to do anything.

---

### Post by spiderbatdad on 2008-05-22
I believe the place for the script would be /etc/init.d
Great work compiling the driver.

---

### Post by Twilight in Zero on 2008-05-22
Thank you! Anyways, init.d wasn't the place for it. I just ended up chmodding wlan0up and wlan0down to 777 (so they'd be executable; I don't care to figure out what the securest setting would be), and just putting```
pre-up     /blah/blah/blah/rtl8187_linux_26.1010.0622.2006/wlan0up
post-down  /blah/blah/blah/rtl8187_linux_26.1010.0622.2006/wlan0down
```
into /etc/network/interfaces.

It starts up automatically now, and it works well! :D Thanks for the help, spider!

---

