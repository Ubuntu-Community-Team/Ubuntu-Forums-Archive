---
title: "HP Jaserjet P1505 - jobs don't leave queue"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Blipo on 2008-09-06
I have a new HP Jaserjet P1505. I hooked it up and printed the test page with no problems, however after that I couldn't get anything to print. Google turned up someone with the same problem - it appears that jobs aren't being removed from the print queue, and so are preventing further jobs from going through. I can only get another job to go by manually removing the job from the queue, through the command line. I'm using Ubuntu 8.04. Anyone have any way to solve this?

Thanks.

---

### Post by bmac on 2008-09-07
Have you installed the HP print driver?

[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

It solved numerous problems with my all-in-one printer and this driver does support your printer.

Hope this helps....

---

### Post by Blipo on 2008-09-07
Yes, that was the first thing I tried when I installed.

---

### Post by fballem on 2008-09-07
> **Blipo said:**
> Yes, that was the first thing I tried when I installed.

Forgive the question, but did you install it from the repository or did you install it from Source Forge? And if you installed from Source Forge, did you completely remove the one from the Repository first?

The reason that I ask is that the one from the Repository is usually installed at the same time as you're installing ubuntu - and it is out of date. For example, in order to even use my printer, which is also new, I have to use the one from Source Forge.

---

### Post by Blipo on 2008-09-07
I'm not sure, so I think I should just uninstall everything, and then start again with SF. How do I go about doing that? ._.

---

### Post by bmac on 2008-09-07
I did not remove the old HPLIP when I installed the new driver from Source Forge. I simply used the HP installer listed on that site. It must have installed the new driver and after installation was complete, the new driver version was automatically selected.
An HP icon was installed in my panel immediately after installation and everything just worked. Including Xsane image scanner....

---

### Post by fballem on 2008-09-07
> **Blipo said:**
> I'm not sure, so I think I should just uninstall everything, and then start again with SF. How do I go about doing that? ._.

The following link describes the uninstall process for the HPLIP from Source Forge: [http://hplip.sourceforge.net/howtos/uninstall.html](http://hplip.sourceforge.net/howtos/uninstall.html)

As for uninstalling the hplip from the repository, I would use Synaptic (System > Administration > Synaptic Package Manager). Once it's open, do a search for hplip. If hplip is installed, it will likely be marked as installed. Right click and select the Mark for Complete Removal option. Don't worry about what else will get removed.

Once you have done that, go to the [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html) page and follow the instructions for the automatic installer.

Hope that this helps,

---

### Post by tahina on 2008-09-07
Hi.

I don't know if this applies, but I have an HP printer aswell (LaserJet 1020) and I need to run ```
sudo hp-setup
``` (which is installed by default) to get it working. It will download something proprietary from the internet and setup the printer (after I answer a few questions or press enter for the default answers a few times).

---

### Post by fballem on 2008-09-07
> **tahina said:**
> Hi.

I don't know if this applies, but I have an HP printer aswell (LaserJet 1020) and I need to run ```
sudo hp-setup
``` (which is installed by default) to get it working. It will download something proprietary from the internet and setup the printer (after I answer a few questions or press enter for the default answers a few times).

When I open hp-setup, I get the attached information in the terminal. The current version number (from Source Forge) is 2.8.7. The version that is in the repository is 2.8.2.

This will let you know which version is installed. Bottom line - if you have installed from the Repository _and_ your printer is working correctly, then there is no need to install from Source Forge. If your printer is not working from the version on the Repository, then you should uninstall the Repository version, then install the version from Source Forge and see if that corrects your problem.

If the Source Forge version does not solve your problem, then register a bug on Launchpad. I had a problem with an HP cp1581ni, and the developer was really responsive!

---

### Post by Blipo on 2008-09-07
So that didn't work. It's still not clearing the queue.

---

### Post by Sef on 2008-09-08
> So that didn't work. It's still not clearing the queue.

It's a [bug]("https://bugs.launchpad.net/ubuntu/+bug/260665").  I would download [Intrepid Ibex]("http://cdimage.ubuntu.com/daily/current/") Live CD and see if it works with that.  Note:  Ibex is still not for stable computers, so I wouldn't recommend installing it, unless you like living at the bleeding edge.

---

### Post by Sef on 2008-09-09
There was an update today for Intrepid Ibex, so the P1505 should run on that out of the box. If it was applied to Hardy Heron, that should also resolve the problem.

---

### Post by tech@aie.com.au on 2008-11-01
I have succcessfully installed the HP P1505 on Intrepid Ibex server. I'm running the 8.10 server (latest version after running do-release-upgrade) and installed the P1505 today (1 Nov 2008 ).

The trick is NOT to rely on the initial 8.10 server recognition of the P1505 out of the box (using the HPLIP GUI).

It is necessary to delete the auto-recognised device (use the HPLIP GUI - start it from the from the command prompt by running hp-toolbox ) and do a fresh install of the device. This will download some firmware from the internet, and should install the device properly. 

The FIRST time I reinstalled the device it didn't work, but after restarting 8.10 server (a nasty little MS windows touch!) it worked.

To be honest, trying to get printers working on Ubuntu server has been a real headache!!

Some proper, comprehensive documentation is desperately needed from Ubuntu!

---

