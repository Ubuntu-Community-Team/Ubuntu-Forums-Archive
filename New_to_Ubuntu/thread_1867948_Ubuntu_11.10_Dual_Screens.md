---
title: "Ubuntu 11.10: Dual Screens"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by Drowz0r on 2011-10-23
Hello everyone

Just installed Ubuntu 11.10 (64 bits) and doing the final touches, installing this and that.

It mentioned to me that my Nvidia driver needed activating, so I did it with the recommended driver. I followed the instructions and rebooted.

However, whereas before I had a dual screen display, I am now only able to have my desktop on this single display.

So, in a nut shell, using any of the four possible drivers that "additional drivers" points me to:

NVIDIA accelerated graphics driver (version 173)
NVIDIA accelerated graphics driver (post-release updates)(version 173-updates)
NVIDIA accelerated graphics driver (version current) [Recommended]
NVIDIA accelerated graphics driver (post-release updates)(version current-updates)

I can only get 1 display to show anything and my desktop doesn't extend anywhere. However, on the initial driver I had on the ubuntu install, I had dual displays just fine.

Any ideas guys? Can't see an option to roll back drivers like in Windows.

Thanks

---

### Post by celticbhoy on 2011-10-23
TBH the Nvidia drivers in the repo's are really quite old. The latest versions can be downloaded from here 

[http://www.nvidia.co.uk/Download/index.aspx?lang=en-uk]("http://www.nvidia.co.uk/Download/index.aspx?lang=en-uk")

---

### Post by beew on 2011-10-23
instead of downloading and installing the driver manually from Nvidia you should either use the xorg-edgers or xswat ppa for updated drivers.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

ATM xorg-edgers breaks Unity in 11.10 so I would suggest x-swat as a small stable option.

---

### Post by Drowz0r on 2011-10-23
Hello both

Thanks for the info. I found the driver on the Nvidia website ([http://www.nvidia.co.uk/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/285.05.09/NVIDIA-Linux-x86_64-285.05.09.run&lang=uk&type=GeForce](http://www.nvidia.co.uk/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/285.05.09/NVIDIA-Linux-x86_64-285.05.09.run&lang=uk&type=GeForce)) but after clicking "agree and download" the page just shows a bunch of text and no file :(. Either the link is broken or it doesn't like firefox.

I'm checking [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates") but is there something specific I am looking for? The site seems to contain an awful lot of files and I can't actually see any way of downloading anything. Do I add it as a source? I've only been running ubuntu for a few days :)

---

### Post by celticbhoy on 2011-10-23
> **Drowz0r said:**
> Hello both

Thanks for the info. I found the driver on the Nvidia website ([http://www.nvidia.co.uk/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/285.05.09/NVIDIA-Linux-x86_64-285.05.09.run&lang=uk&type=GeForce](http://www.nvidia.co.uk/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/285.05.09/NVIDIA-Linux-x86_64-285.05.09.run&lang=uk&type=GeForce)) but after clicking "agree and download" the page just shows a bunch of text and no file :(. Either the link is broken or it doesn't like firefox.

I'm checking [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates") but is there something specific I am looking for? The site seems to contain an awful lot of files and I can't actually see any way of downloading anything. Do I add it as a source? I've only been running ubuntu for a few days :)

Yeah, your adding an additional software source, or repository (Repo for short). Open a terminal, then type this

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Drowz0r on 2011-10-23
Ah-ha. Alrighty, I'll let this baby update and let you know how it goes...

---

### Post by Drowz0r on 2011-10-23
Well a lot of updating and such happened in the terminal but nothing seems to have changed. I rebooted as well and checked additional drivers in ubuntu out again. Still don't have the option to extend or mirror to my other monitor. Weird how it was working on the initial install of ubuntu.

---

### Post by celticbhoy on 2011-10-23
Look in your app list for an app called nvidia-settings, if its not there type this onto a terminal 

sudo apt-get install nvidia-settings

once installed, run it, and see if you can enable the second monitor from there.

---

### Post by mbelos on 2011-10-23
I have an NVidia card, and I can confirm that the in-built "Displays" application does not do anything when the NVidia drivers are installed. There used to be an error message that popped up when you accessed the "Displays" program that said something like "Use nvidia-settings to change your display preferences" but that doesn't happen in 11.10 any more...

---

### Post by beew on 2011-10-24
To actually use the Nvidia driver after you install it you have to run in the terminal

> sudo nvidia-xconfigand then reboot.

---

### Post by Drowz0r on 2011-10-24
> **celticbhoy said:**
> Look in your app list for an app called nvidia-settings, if its not there type this onto a terminal 

sudo apt-get install nvidia-settings

once installed, run it, and see if you can enable the second monitor from there.

I ran it and it worked but said I needed a reboot. On rebooting it found my 2nd display but there are no menus. I get a cursor and an extended desktop accross two monitors and that's it. No keyboard hotkeys trigger anything and I'm unable to access anything at all :/

Reformat it seems. I'll just reformat it and not touch the default drivers because those seemed to work.

Thanks for the help anyway guys.

---

### Post by Drowz0r on 2011-10-24
Well I reformatted and I'm back to my single display and ubuntu is working again but no dual screen. Went through the steps before but not rebooted just yet. I'll try it in a minute.

Strangely when I run ubuntu from disk the "displays" menu thing in the top right works perfectly and I can see through both monitors. Once ubunutu is installed it stops working.

> **beew said:**
> To actually use the Nvidia driver after you install it you have to run in the terminal

and then reboot.

Tried that and got the error:

[FONT=Courier New]Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
[/FONT]

---

### Post by b2zeldafreak on 2011-10-24
I had the same problem as you; with the Unity desktop. I prefer the KDE desktop most of the time anyway, so I installed that. KDE handles both monitors perfectly, and even has built in support for a different wallpaper on each monitor.

---

### Post by Drowz0r on 2011-10-24
> **b2zeldafreak said:**
> I had the same problem as you; with the Unity desktop. I prefer the KDE desktop most of the time anyway, so I installed that. KDE handles both monitors perfectly, and even has built in support for a different wallpaper on each monitor.

Ah jeez. The thing is I have another two machines (so 3 in total) that use Nvidia cards so I'd really like to get this working rather than converting both to a KDE desktop. Trying to get all machines in the house on the same ubuntu so people here can get used to it - not everyone here knows exactly how to use a computer heh and I don't want to add varying desktops to their confusion. I'd rather not change the desktop on a load of other perfectly fine machines to conform with the KDE ones too.

Tried running the commands after some reboots again, I get:

[FONT=Courier New]drowz0r@Prime:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'.[/FONT]

This is cray-zay

---

### Post by Drowz0r on 2011-10-24
> **celticbhoy said:**
> Look in your app list for an app called nvidia-settings, if its not there type this onto a terminal 

sudo apt-get install nvidia-settings

once installed, run it, and see if you can enable the second monitor from there.

On reflection, after following these steps, it just seemed to activate the original:

NVIDIA accelerated graphics driver (version 173)

---

### Post by Drowz0r on 2011-10-24
> **Drowz0r said:**
> On reflection, after following these steps, it just seemed to activate the original:

NVIDIA accelerated graphics driver (version 173)

After noticing this, I attempted to re-install the [recommended] driver mentioned earlier and it worked. Configuration TwinView and save to X configuration File (but not merge with) seems to work... now to hope it retains it after a reboot...

---

### Post by Drowz0r on 2011-10-25
Worked on my other machines too.

---

### Post by mgolden on 2011-11-02
b2zeldafreak, you are seeing the multihead work out of the box for KDE?  I have a system76 laptop machine with a Nvidia GeForce GTX 560M graphics card.  The machine works fine with the LCD display, but (a) it doesn't find the external monitor when it's plugged in, and (b) if I set up the external monitor with the nvidia configuration utility, it works, but the system settings for KDE doesn't claims that multi monitor isn't set up.

Also, very oddly, it only works with the analog output, not digital.

Did you have to do anything to get it to work?

---

### Post by themissinglinka on 2011-11-08
> **Drowz0r said:**
> After noticing this, I attempted to re-install the [recommended] driver mentioned earlier and it worked. Configuration TwinView and save to X configuration File (but not merge with) seems to work... now to hope it retains it after a reboot...
sweet as fullas, i seemed to get more options by going to the nvida app, rather than the system settings. its all there, cheers again now i can relax and watch stuff on my 920x1280 bad boy! woo hoo!:guitar:

---

