---
title: "How do I remove a program with the Terminal?"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by cliveT on 2012-01-31
Hi Guys
 
I recently installed QCAD rc3 - with this forums help, thankyou for that.
 
I now need to remove the program in order to update to the latest release (they recommend uninstalling the last release first! -how do I do this please with the terminal?
 
I ran this to install it and it worked fine -
 
 
Desktop/qcad-3.0.0-rc2-prof-linux.bin
 
 If I do try to just update without uninstalling the last release -how would I do this please?
 
Regards
 
Clive :)

---

### Post by Bodsda on 2012-01-31
> **cliveT said:**
> Hi Guys
 
I recently installed QCAD rc3 - with this forums help, thankyou for that.
 
I now need to remove the program in order to update to the latest release (they recommend uninstalling the last release first! -how do I do this please with the terminal?
 
I ran this to install it and it worked fine -
 
 
Desktop/qcad-3.0.0-rc2-prof-linux.bin
 
 If I do try to just update without uninstalling the last release -how would I do this please?
 
Regards
 
Clive :)

Assuming that the original install was compiled from source, or installed without the use of dpkg/apt/aptitude/etc. then you should just be able to delete the files from the build directory.

If you didn't have to build from source, then they may have provided an uninstallation script. 

Hope this helps,
Bodsda

---

### Post by cliveT on 2012-01-31
> **Bodsda said:**
> Assuming that the original install was compiled from source, or installed without the use of dpkg/apt/aptitude/etc. then you should just be able to delete the files from the build directory.
 
If you didn't have to build from source, then they may have provided an uninstallation script. 
 
Hope this helps,
Bodsda
 
The original install is just from the QCAD download site there is no un-installation script -so how do I delete the files from the build directory as stated?

---

### Post by corncob on 2012-01-31
Back around Ubuntu 10.04 there was an app called 'Computer Janitor' that appeared to want to remove programs that weren't installed through Synaptic or the Software Center.  I considered this to be a bug but it might be a useful one for your purpose.  It no longer comes with Ubuntu but I see it in the software center.

---

### Post by cliveT on 2012-01-31
looking at the reviews for the "clean up Janitor" -it looks a bit dodgy!

---

### Post by Lars Noodén on 2012-01-31
Looking at the trial version, it seems it is installed in /opt.  Find the qcad directory in /opt and move or delete it. 

It would be much better if they would make a version that the package manager could use.

---

### Post by cliveT on 2012-02-01
Yes it would be much better -agreed.

---

### Post by corncob on 2012-02-04
> **cliveT said:**
> looking at the reviews for the "clean up Janitor" -it looks a bit dodgy!

You probably read my review on it lol:
> It will clean up many useful softwares as long as they are not installed from official source.
 Back in 10.04 it wanted to remove 'Caffeine' from my system even while it was running, apparently just because I had not installed it through the package manager.  I just thought you could use this quirk to your advantage as it did allow you to uncheck things you wanted to keep.  Currently it finds nothing to remove but everything has been installed from official sources on this installation.

---

