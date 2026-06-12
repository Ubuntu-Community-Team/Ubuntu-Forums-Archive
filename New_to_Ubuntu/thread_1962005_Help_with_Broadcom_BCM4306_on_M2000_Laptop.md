---
title: "Help with Broadcom BCM4306 on M2000 Laptop"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by Ascarletrequiem on 2012-04-20
Hello guys,

I am a Linux noobie so please forgive my ignorance. I have been trying for several days to get my wireless card to function under Ubuntu (latest beta version). I have searched both the forums and google. I have tried Ndiswrapper installed from source and the official ubuntu install guide for b43-fwcutter.

I performed a clean install last night and so far i have tried this:

~$Sudo apt-get install b43-fwcutter
~$Sudo Apt-get install firmware-b43legacy-installer

After a restart the B43 drivers are not showing up in additional hardware and my wireless card is still reporting no firmware.

On a side note, being a noob to linux, i am having trouble finding the Applications menu. The walk through i have mentions a desktop menu with options applications>accessories>terminal; however, i am unable to find terminal without searching for it. I know this is probably a stupid question, but can someone point me in the right direction for finding this particular menu? 

Thank you for your patience and considerations.

---

### Post by lkraemer on 2012-04-20
You can just copy the Firmware to the proper folders.

Download the Firmware files located at:
[http://www.omattos.com/node/6](http://www.omattos.com/node/6)
to a USB Flash Drive and copy them to your Desktop, and Extract.
You should have two folders b43 & b43legacy. You will be copying
these folders to /lib/firmware/b43 and /lib/firmware/b43legacy

Here are the commands I used on my old Compaq V5201US, running the
10.04 LiveCD to get it working: (Open a Terminal Window)
```

cd /
cd /lib
cd firmware
pwd
ls
sudo cp -r /home/loginname/Desktop/b43* .
cd b43
ls
cd ..
cd b43legacy
ls
exit

```
Now you just have to Enable the Driver:
SYSTEM -> ADMINISTRATION ->HARDWARE DRIVERS
should have a Driver listed a driver listed for your wireless,
if so enable it. (If by chance you have already ENABLED it, go ahead
and let it try to uninstall, then install it again by clicking again.
It should find the drivers and load them, because the Firmware is where
it needs to be.

Check Network Manager (right click on the icon) to be sure the "Enable Wireless" box is checked (It should be ENABLED already by default.)

Check to see if you have wireless now. If not, you might need to
check the Loaded Modules, making sure there are no conflicts with other
Wifi drivers that might have been loaded, or others that cause conflicts.
```

lsmod

```

Post the output of lsmod.

lk

---

### Post by Ascarletrequiem on 2012-04-20
Update:

Possible fix located here: [http://ubuntuforums.org/showthread.php?t=1932141](http://ubuntuforums.org/showthread.php?t=1932141)

Will try this tonight and update.

---

### Post by Ascarletrequiem on 2012-04-20
@[lkraemer]("http://ubuntuforums.org/member.php?u=365139") Thanks! I will try this as well. Your reply is very much appreciated. Will update on status.

---

### Post by wildmanne39 on 2012-04-20
Hi, here is a link, in post 8 is everything you need including the firmware to make this a lot easier.
[http://ubuntuforums.org/showthread.php?p=11860231#post11860231](http://ubuntuforums.org/showthread.php?p=11860231#post11860231)
Thanks

---

### Post by Ascarletrequiem on 2012-04-20
> **wildmanne39 said:**
> Hi, since you have no internet connection  this should get you going but we may have to blacklist another driver.

Download the b43 zip file from a computer that has internet to a usb  flash drive then drag and drop the file to your ubuntu desktop.  Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```Thanks

Thanks so much to you all. The above worked flawlessly!

---

### Post by wildmanne39 on 2012-04-20
Hi, your welcome!
Enjoy

---

