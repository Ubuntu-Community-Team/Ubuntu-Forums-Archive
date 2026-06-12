---
title: "Upgrading to Ubuntu 12.04.1"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by nickelbox on 2012-08-25
How do I upgrade to 12.04.1 without downloading the entire file again? I checked for the update in the update manager and it wasn't available...

Thanks

---

### Post by Wirephire on 2012-08-25
Its just a regular upgrade, nothing special. If you applied all offered updates then you're already on 12.04.1. Check your version with ***lsb_release -a***


*~wph*

---

### Post by PaulW2U on 2012-08-26
> **nickelbox said:**
> How do I upgrade to 12.04.1 without downloading the entire file again?

As Wirephire has already said you are probably already running 12.04.1 if you have applied all the updates offered to you.

These minor releases are just snapshots of the release version so far. As 12.04 is an LTS with five years of support it provides a means to drastically reduce the amount of updates downloaded immediately after installation.

Further minor updates, 12.04.2, 12.04.3 and 12.04.4 will be released in due course. There'll be no need to specifically upgrade to those either.

---

### Post by nickelbox on 2012-08-26
I see now that I am on 12.04.1. What confused me was when I looked in system settings, it showed I was on 12.04. 

Thanks

---

### Post by Dalek Draco ON LINUX on 2012-08-26
When you go to update manager, check your settings to ensure that you are receiving upgrades (settings - updates - check for new distribution releases). 

If you have that set, then you should be automatically receiving the latest upgrades and updates, and as has been said above, you'll be on 12.04.1

---

### Post by MoebusNet on 2012-08-26
On a bit of a tangent, I like to keep a CD with the version of Ubuntu that is installed on my machine. If worst comes to worst, I can boot from the Live-CD and use GParted to check the files on my hard drive and hopefully recover. I can also use it to reinstall If everything is completely borked.

As to your question about not downloading the entire iso image, a tool to update your current Ubuntu iso to the latest Ubuntu iso image (e.g. 12.04 to 12.04.1) is jigdo:

[http://ubuntu.paslah.com/jigdo-jigsaw-download/](http://ubuntu.paslah.com/jigdo-jigsaw-download/)

Using jigdo, you can download only the parts of the file that have changed to build the new iso image.

Note: I did not find jigdo available when I searched Dash Home. Using this may take a bit of research, but Debian has been using jigdo for quite a while now.

---

### Post by vexorian on 2012-08-26
Some redundant bits: Point releases like 12.04.1 exist to save uptime for people installing 12.04 after months from first release. Each of these releases is exactly 12.04 but with all the packages updated to 12.04 repos.

If you are currently running 12.04, you really should not do a 12.04.1 install, because simply updating all your packages will do it. But you might like to download the 12.04.1 live CD, because if something bad happens, when you have to reinstall it will save you time not to download a lot of updates again. So here is where MobiousNet post can be useful, as it can help you "upgrade" your .iso file.

---

### Post by MoebusNet on 2012-08-26
Upon doing just a bit more reading, zsync also is used to update Ubuntu iso images:

[http://ubuntu-tutorials.com/2009/10/29/use-zsync-to-update-existing-iso-images/](http://ubuntu-tutorials.com/2009/10/29/use-zsync-to-update-existing-iso-images/)

Note: While Dash Home did not show jigdo or zsync as available for download, Synaptic Package Manager does.

---

