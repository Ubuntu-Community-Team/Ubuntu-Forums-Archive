---
title: "SLi and USB belkin wireless"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by endrswrd on 2008-10-25
I actually have two questions. First how do I setup and enable SLi and two, I need some help getting my belkin usb wireless card to work.

**edit I have the drivers succesfully installed and the nvidia x server config installed also.

---

### Post by SteveLefty on 2008-10-29
I'm not sure about the wireless USB, but I have a solution for your SLI issue:

Before starting this, backup your xorg.conf file...just in case.  Open a terminal window and type the following:
"sudo cp /etc/x11/xorg.conf ~/xorg.conf.backup"

This will create a backup of your xorg.conf file and place it in your home directory (renamed "xorg.conf.backup").  This command will ask for your password.  That is because you typed "sudo", which gives you root privileges temporarily.  If you find that you need to revert to this xorg file, then open a command line and type:
"sudo ~/xorg.conf.backup /etc/x11/xorg.conf" --You shouldn't have to do this, hopefully

Now we'll use the Nvidia config to turn SLI on.  In the same terminal, type:
"sudo nvidia-xconfig --sli=on"

Now reboot your machine.  If it seems to fail, you'll need to revert that xorg file you backed up.  If not, SLI should be up and running!

---

### Post by MattBD on 2008-10-29
About the USB wireless card: What version of Kubuntu are you using?

If you're using Hardy, then it might be worth your while installing Intrepid when that's released tomorrow, because you generally find each new version is likely to include newer drivers, and each new version does seem to offer better support for a lot of devices.

Assuming that doesn't do the trick, you might want to run this command:
```
lspci
```
This will give details of the devices on your computer, including the wireless device if it's detected (which it probably will be, even if it doesn't work. It should be listed as something like Network Controller. That will give details of the chipset it uses, which you will need to know.

I'd check out [this link]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo?highlight=(\bCategoryWireless\b)"), it gives a lot of good information on getting wireless cards working. However, it does look quite old

---

