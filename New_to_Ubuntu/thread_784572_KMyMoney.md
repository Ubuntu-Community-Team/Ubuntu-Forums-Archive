---
title: "KMyMoney"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by prc320 on 2008-05-06
I have updated to 8.04, Good. I went to synaptic package manager to update KMymoney, to the latest version 0.8.9 but that in 0.8.2.

If I download the latest version what do I need to do?

Robert

---

### Post by toddward on 2008-05-07
If you've already downloaded the latest version (I'm assuming a tar.gz file?) then you may need to manually compile and install the application.  I'm curious, though...are you running KDE or Gnome?  If you're running Gnome, then you may not be able to compile the package manually as you'll probably be missing some dependencies.

If 0.8.2 is provided by Synaptic (and you don't know how to compile), then I would just stay with it for the time being.

---

### Post by prc320 on 2008-05-08
> **toddward said:**
> If you've already downloaded the latest version (I'm assuming a tar.gz file?) then you may need to manually compile and install the application.  I'm curious, though...are you running KDE or Gnome?  If you're running Gnome, then you may not be able to compile the package manually as you'll probably be missing some dependencies.

If 0.8.2 is provided by Synaptic (and you don't know how to compile), then I would just stay with it for the time being.
OK I understand! By the way I used Gnome and have no problems with 0.8.2

---

### Post by oygle on 2008-06-03
From the KMyMoney mail listing in Feb ..

> 
USING THE NEWER VERSION OF KMM IN GUTSY SEPARATELY, and because only KMM Version 8.7.2 is available at the 'Ubuntu Repository,' you may wish to jump right to the "draft" version of KMM I call 9.0 (the leaders of the effort call CVS HEAD, I think.)   Mr. Clay Weber has posted it  HERE, packaged for GUTSY and ready to roll:  [https://edge.launchpad.net/~claydoh/+archive]("https://edge.launchpad.net/~claydoh/+archive")      

I have found it stable in GUTSY 7.10 (for past 7 days and counting) - and slick.   [I had been unable to get 8.8.1, like you.]

Here is how I installed 9.0, step by step, if interested:

   1. I uninstalled KMM Version 8.7.2 using the 'System, Synaptic Package Manager' in GUTSY.  Easy, as you know.
   2. I went to the site above, and selected the version for i386 called [kmymoney2_020102008cvs-0ubuntu1~gutsy1_i386.deb]("http://launchpadlibrarian.net/11860228/kmymoney2_020102008cvs-0ubuntu1%7Egutsy1_i386.deb")   [It is a good package, EFFORTLESS and LOADS AUTOMATICALLY using 'GDEBI Package Installer' in Ubuntu.  Version I installed was dated 2/11/08 to be precise.]
   3. I then simply opened the program (embeds in Office Apps) and told it to load the last .KMY file I used. 
   4. I then IMMEDIATELY SAVED IT with another name (this is a backup precaution if for some weird reason the "CVS" version is unstable on your machine - even though rock solid on mine).  And that's it....


(If you encounter difficulties, I have found it very easy to return to Version 8.7.2 by simply using Synaptic Package Manager again to remove the KMM CVS version and return to 8.7.2.  I did this to assure myself I could get back if need be.  Works great... thanks to Ubuntu.)


The same installation method would be applicable for HARDY. Just use the latest file, at present it appears to be [http://launchpadlibrarian.net/14739247/kmymoney2_05272008cvs-0ubuntu1%7Eppa1_i386.deb]("http://launchpadlibrarian.net/14739247/kmymoney2_05272008cvs-0ubuntu1%7Eppa1_i386.deb")

Just remember to backup prior to any changes though.

---

