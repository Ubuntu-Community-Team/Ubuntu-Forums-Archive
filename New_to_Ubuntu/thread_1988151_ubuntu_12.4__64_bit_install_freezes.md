---
title: "ubuntu 12.4  64 bit install freezes"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by interceptorV8 on 2012-05-27
repost: 

since the last version of ubuntu with the annoying side panel, i decided to devote the next 6 months to linux mint. well i was going to give ubuntu another try.

i downloaded the torrent of the .iso, made a disc, rebooted, tried to install and when the ubuntu screen opens, the flashing balls underneath the ubuntu logo alternate and go through the motions for a few minutes before it just freezes. balls stop blinking... it just hangs there; frozen.

so i make another disc thinking perhaps the first was a bad disc. again, the same problem.

i downloaded the .iso directly from the site this time rather than the torrent. again - same problem

i then downloaded the full DVD version from the site and made a live usb drive with UNetbootin... surprise surprise... same problem.

so right now, ubuntu 12.4 isn't looking very promising if the damn thing won't even get past the welcome screen. i've been a loyal follower of ubuntu since gutsy... i'm starting to lose faith in ubuntu and shuttleworth.

---

### Post by wildmanne39 on 2012-05-27
Hi, try nomodeset option here is a link.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by westcoast01 on 2012-05-27
> **wildmanne39 said:**
> Hi, try nomodeset option here is a link.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

Sure sounds like you need to check the nomodeset option. Let us know the results.:KS

---

### Post by interceptorV8 on 2012-05-27
tried the nomodeset option.  it appears as if the ubuntu logo and the "orbs" are loading but in a lower resolution.  

it still freezes though this time it gives me the message about not having the correct drivers for the b43 cutter firmware device and offers a web address to go to.  i go to the site and see nothing of any help.

as a test, i uninstall the b43 driver and b43 installer and try installing ubuntu again...   still freezes and still gives the b43 error message.

---

### Post by anewguy on 2012-05-27
There are other threads in the forum regarding the b43 problems like you are having.  OOPPSS - I removed my previous text here as I see wildmanne39 is already helping you.  They are a guru on the wireless issues.

As far as the ubuntu desktop with the menu on the side - that's the unity desktop and has been there for a couple of releases.  However, you don't HAVE to use it - there are other desktop managers you can install after you install ubuntu - I use gnome-shell, others use lxde or kde.  All of these are available in the package manager.

You should probably also check this thread:  [http://ubuntuforums.org/showthread.php?t=1966631&highlight=install+error+b43]("http://ubuntuforums.org/showthread.php?t=1966631&highlight=install+error+b43")

Dave ;)

---

### Post by westie457 on 2012-05-27
Hi , there is a work around for this.

Boot the CD/USB into 'Try' mode - the Live Desktop - and connect an ethernet cable.

Go to this link [http://ubuntuforums.org/showpost.php?p=11860231&postcount=8](http://ubuntuforums.org/showpost.php?p=11860231&postcount=8) to download and install the b43 driver. Run all of the commands ignoring any messages of failure. Create your wireless connection - unplug the cable - check that it is working. Do not attempt a restart as you lose the wireless because it is installed to the Live Desktop in RAM.

Click on the 'Install' icon on the Desktop. The install should now go through without ant hang-ups. Use the nomodeset option if you like.

Hope this helps.

---

### Post by interceptorV8 on 2012-05-27
okay, i found the main culprit.  i had to phyiscally remove my wireless card just in order for the live cd to boot in order to install ubuntu.  this is a first...  

i thought if i used my usb wireless adapter, i could install the b43 drivers and then reconnect the card, but no...  as soon as i put the card back into the pci slot, ubuntu freezes on startup.

---

### Post by wildmanne39 on 2012-05-27
Hi, please tell us the specs of the computer and did you try all the options in the link I gave you for nomodeset there are several there.
Thanks

---

### Post by interceptorV8 on 2012-05-27
okay... from the software center, i installed the b4 installer, which i THOUGHT i already had installed... i selected the plugin for it at well and the shut down, put the card back in, turned on...  and so now it seems to be working.  ugh...  irritating.   

anyhow... i may not be out of the woods yet, however, in the meantime, thank you eveyone.  the people in this forum are always very helpful :)

---

### Post by wildmanne39 on 2012-05-27
Hi, good luck! and if the issue is resolved please use thread tools at the top of the page to mark the thread solved.
Thanks

---

