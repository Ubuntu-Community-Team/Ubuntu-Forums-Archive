---
title: "Where are Nvidia drivers stored and how to update them?"
date: 2015-01-26
forum: New to Ubuntu
---

### Post by garycheng12 on 2015-01-26
I have a pretty old laptop and after trying Kubuntu (Linux in general), I wanted to start from a clean state because I most likely tinkered with the system too much. I reformatted Kubuntu on the root drive but kept the Home drive and this time, I wasn't ask to choose whether I want Nvidia drivers or Nouveau drivers. I'm guessing the drivers are installed in the Home drive then?

 Also, I've been recommended to choose Nvidia over Nouveau drivers because it is more stable. Suspend to RAM doesn't work when I tried Nouveau but works when I used Nvidia. However, I remember one time there was a system update and when I rebooted the computer, it gave me a black screen with some text and something with tty1--I could never get to the GUI login screen. I googled and while there were many different methods that failed, I came across one where I essentially removed Nvidia driver completely and then switched to Nouveau. What exactly is happening and how to prevent it from happening again (or how to deal with it)?

Lastly, how to properly update Nvidia drivers? When I reformatted the laptop completely, it gave me a list of drivers to choose from. The Nvidia recommended driver was not the latest for the laptop (I checked the website for the laptop's drivers). How do I install the latest one?

Thanks.

---

### Post by Jonor on 2015-01-26
Have a look at [this list]("http://ubuntuforums.org/search.php?searchid=6875120") which is an advanced search of the tutorial section for threads with nvidia in the title.
Worth reading a few of them, there is mention of the DKMS module used to ensure kernel updates don't bork your driver.
I hesitate to say much more than that as my graphics hardware is different to yours but for reference one of those threads got me these notes which work very well :

Nvidia drivers --- (may need to add a nomodeset option for GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" of etc/default/grub and then do sudo update-grub).

```
sudo add-apt-repository ppa:xorg-edgers/ppa
``` 

n.b. this is where there are some nvidia drivers 


```
sudo apt-get update && sudo apt-get upgrade
```

Now search for nvidia driver within synaptic application (around 343-ish) and install them and reboot.

Also :
 lspci | grep VGA --- shows what graphics hardware is installed (onboard wont show if disabled in BIOS)
 sudo glxinfo | grep OpenGL --- shows what graphics driver is installed (will need sudo apt-get install mesa-utils beforehand)
 If the renderer string is Mesa then it is not a proprietary driver.

---

### Post by efflandt on 2015-01-27
Assuming you have Nvidia graphics, how old is old. If it is too old you might actually need an older driver instead of one of the current or ppa drivers. If it is not that old and has hybrid graphics, "lspci | grep VGA" might show Intel graphics and "lspci | grep 3D" (without quotes) might show Nvidia graphics.

---

### Post by buzzingrobot on 2015-01-27
Drivers are not "stored" in a user's home directory.

If an Nvidia card is active, the open source Nouveau driver is used by default. The installer does not ask you to choose between Nouveau and the closed-source proprietary driver from Nvidia.

The safest way to install/update/remove the Nvidia proprietary Nvidia driver in Ubuntu is to use the "Additional Drivers" function, often also called "Driver Manager" in KDE.  It will display drivers in the Ubuntu repos that are appropriate for the Nvidia card in your system. That may often not be the very latest driver. Nvidia provides legacy support for older cards.

Visit nvidia.com to determine which driver they say is currently available for your card. 

PPA's providing drivers for Nvidia typically publish cautions about when and if their drivers should be used.  Read those before deciding to use a PPA driver. Replacing core Ubuntu packages, like a driver,  with unofficial and unsupported-by-Canonical packages -- e.g., from a PPA -- can, for instance, create updating problems in the future, espcially if using a PPA means a number of dependencies are installed to support the package you're after.

---

### Post by monkeybrain20122 on 2015-01-27
> **buzzingrobot said:**
> Drivers are not "stored" in a user's home directory.

If an Nvidia card is active, the open source Nouveau driver is used by default. The installer does not ask you to choose between Nouveau and the closed-source proprietary driver from Nvidia.


I think it does. If you check the box "install third party/proprietary .." during installation then it will get installed. At least that was the case up to 13.10 when I had a Nvidia laptop, I don't have ant Nvidia machine anymore.

> 
The safest way to install/update/remove the Nvidia proprietary Nvidia driver in Ubuntu is to use the "Additional Drivers" function, often also called "Driver Manager" in KDE.  It will display drivers in the Ubuntu repos that are appropriate for the Nvidia card in your system. That may often not be the very latest driver. Nvidia provides legacy support for older cards.

Unless the card is really old I think Nvidia-current should be the one. 


> PPA's providing drivers for Nvidia typically publish cautions about when and if their drivers should be used.  Read those before deciding to use a PPA driver. Replacing core Ubuntu packages, like a driver,  with unofficial and unsupported-by-Canonical packages -- e.g., from a PPA -- can, for instance, create updating problems in the future, espcially if using a PPA means a number of dependencies are installed to support the package you're after.

 There was a bug in xorg-edger that installing the Nvidia driver would automatically install bumble-bee which would disable the Nvidia driver on reboot (as it assumes dual graphic card), so if you don't have an Intel graphic card you will boot into a blackscreen. The workaround was to remove all bumble bee packages before rebooting. Don't know whether they have fixed that or not. Other than that I have not had any problem, I had used xorg-edgers on my Nvidia machines for a few years. The stock driver is only as good as Nvidia makes it, --Canonical has nothing to do with the quality of the driver,--you get bug fixes and improvements only from ppa updates. 

If it is a relatively new Nvidia card I would definitely recommend xorg-edgers, but have ppa-purge ready just in case (on the other hand I would be more cautious if it is an AMD card, the fglrx often doesn't survive updates very well in my experience, now I only use open source drivers for AMD)

---

### Post by buzzingrobot on 2015-01-27
When I've installed here with Nvidia active and take the "Install third party..." option, I'm on Nouveau after the reboot. To get the proprietary driver, I install from Additional Drivers and reboot.  I've always assumed the driver is actually downloaded via Additional Drivers, given the time that lapses. But, maybe it is downloaded during the actaul install; I've never checked.

The advice about PPA's was trying to be rather broad.  PPA use can install any number of dependent packages that can impact upgrade success down the road. Hence, the suggestion to see what the actual PPA page has to say.  Many users simply copy and paste blindly from some random website hyping the arrival of the newest drivers. They won't notice if/when a dozen other packages come along with it.

ppa-purge is certainly vital for recovering from bad driver installs, but it is likely to frighten the terminal-averse new user. Plus, they need to remember the correct name of the PPA they installed from.  If they just copied and pasted from a site in the past and the problem didn't surface until later, I think there's a good chance they won't know it, assuming they recognize that the PPA is the source of the problem.

---

### Post by monkeybrain20122 on 2015-01-27
> **buzzingrobot said:**
> When I've installed here with Nvidia active and take the "Install third party..." option, I'm on Nouveau after the reboot. 
.

As I remember you have to run sudo nvidia-xconfig and reboot for it to work (In Ubuntu 10.XX jargon, 'driver installed but not activated' at first boot)

---

### Post by buzzingrobot on 2015-01-27
> **monkeybrain20122 said:**
> As I remember you have to run sudo nvidia-xconfig and reboot for it to work.

Thanks.  I'll remember that for next time.

I installed Deepin Linux the other day just for a look.  When I ran their Nvidia installer, the screen went black. I assumed the worst and was opening up a console to reboot when the screen re-displayed, without a reboot, with the Nvidia driver active. A nice touch.

---

### Post by Jonor on 2015-02-11
> **buzzingrobot said:**
> 
PPA's providing drivers for Nvidia typically publish cautions about when and if their drivers should be used.  Read those before deciding to use a PPA driver. Replacing core Ubuntu packages, like a driver,  with unofficial and unsupported-by-Canonical packages -- e.g., from a PPA -- can, for instance, create updating problems in the future, espcially if using a PPA means a number of dependencies are installed to support the package you're after.

Seems like my  PPA suggestion has just crashed my graphics so i'll heed the above, belatedly !

---

