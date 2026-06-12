---
title: "System Rollback"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by philpense on 2012-12-04
Roll Back

Have Lubuntu 12.10 operating from a USB drive.  Had worked well until updates were attempted.  Synaptics packages, Chromium updates, etc. have all failed and now I find system issues.  The chromium browser is now either generating the error message "aw snap" or is simply closing without warning.  Is there some rollback feature that would bring the system to a prior time?  Guidance sought.

---

### Post by Rex Bouwense on 2012-12-04
Can you simply un-install the browser and then re-instal?

---

### Post by monkeybrain2012 on 2012-12-04
Are you using a live usb with persistence as oppose to a full install in the usb drive? Live usb doesn't support a lot of system level upgrades (e.g synaptic, kernels and apt etc) I don't know about chromium though. You may also have run out of space (live usb uses FAT, so it can only have 4G of capacity no matter how big your usb drive is)

---

### Post by philpense on 2012-12-04
Thought that update was a better choice than uninstall... that would leave me temporarily without a browser.  Additionally, I have not seen specific guidance on how to uninstall.

---

### Post by arpanaut on 2012-12-04
No roll-back system in Ubuntu unless you have manually created a backup image of the drive yourself.

A little information?
Is this a USB flashdrive or a hard drive in an USB enclosure?
What method did you use for the initial install?

If you have synaptic you can search there and remove and then reinstall from there also. No need to be without a browser, or install firefox temporarily until you get chromium working again.

---

### Post by COMECON on 2012-12-04
Try re-installing Chromium. Follow this steps (on a Terminal):
** $ sudo apt-get purge chromium-browser **
This will remove your Chromium browser and your configurations, so if you don't want to remove them change **purge** with **remove**. Then:
** $ sudo apt-get install chromium-browser**
Hope it works!

---

### Post by philpense on 2012-12-04
Much thanks for the support.  The USB install was done through the Lubuntu 12.10 version.  The "YUMI" or universal multi installer ported the Lubuntu ISO files to the USB drive.  General operations including internet navigation through the wireless adapter was flawless for several days.  This was an indication that the install was stable.  Updates were then attempted.  If this 'persistent' USB install is what would allow updates and customization I would want this.  Allow the USB drives used for Lubuntu have been formatted 4GB sticks.  Continued support appreciated.

---

### Post by arpanaut on 2012-12-04
You would have had to specifically created a persistence file for you to be able to save settings, do upgrades and updates, as all changes would be lost between boots. Plus I wonder if there would be enough space on 4Gig. flash drives.
Take a look at this page, go down to Known Issues etc. then scroll down to additional notes then [COLOR=#339966][B]Persistently Saving Changes.
[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

[COLOR=Black]Hope this Helps.

[/COLOR][/B][/COLOR]Edit: I Think that tool is for creating multi-boot flash drives, that use the iso's "as is" I'm not sure that iso's can be updated in a "live state" as it is not truly a full installation.  I am not positive as to this point, someone please correct me if I am wrong.

---

### Post by monkeybrain2012 on 2012-12-04
A live usb with persistence is not the same as installing Ubuntu in a usb. It doesn't support system level upgrades so for example, attempt to upgrade the kernel will break the system.  Therefore one should be careful of what is being upgraded and I would definitely **NOT **do

```
sudo apt-get update

sudo apt-get upgrade 
```

as this would install all upgrades available and will likely include some system level upgrade and mess up your system as a result.

Also because a live usb uses FAT which has a 4 G limit (regardless how big your flash drive is) so if you may run out of space if you install too many things or upgrade too many things.

---

### Post by philpense on 2012-12-04
Followed your learned guidance back to the pendrivelinux site from a university computer. Regrettably, reputational servers have major alerts for this URL.  I've emailed pendrive Linux about it but in the interim I would ask if a known 'safe' site could be recommended.  Better yet... could a safe version be hosted by ubuntu?   Just cleaned up a very nasty trojan and do not want another such experience.

---

### Post by arpanaut on 2012-12-04
That's very strange, those folks have been around for 6 years and given the nature of the Linux community, if they have been doing nefarious things they would have been exposed,
Sounds like some overzealous MS reputation program blacklisting Linux related software sites.
But that's probably just my own paranoia... LOL  I would expect it to be some kind of false positive from the rep prog. 

It would seem that to fix your issue you would need to remove the iso on the flash drive and then restore the original and refrain from doing updates and upgrades. then create the persistence file as stated on that site, after that you will be able to save data and keep your settings, bookmarks, etc. between reboots.

---

