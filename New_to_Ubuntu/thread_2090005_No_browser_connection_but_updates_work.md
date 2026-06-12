---
title: "No browser connection but updates work?"
date: 2012-11-30
forum: New to Ubuntu
---

### Post by ACuriousGuy on 2012-11-30
OK. This is weird (for me, at least). I previously had 12.04 installed using WUBI on my Winblows notebook. It worked fine for months and months. I had downloaded the wireless drivers using a LAN and then went wireless no problem. Good signal strength. A couple of weeks ago I suddenly could get any websites to launch. Chromium and Firefox both came up dead. I also could not check for updates (kept failing). I don't remember what the error message was anymore. 

After much searching and lots of trial and error I found a page where the poster said that there was a problem with the most recent update for the network manager. I followed their post about downloading the last version from the Ubuntu website. There were four files to download and they were:

libnm-glib-vpn1_0.9.4.0-0ubuntu3_amd64.deb
libnm-glib4_0.9.4.0-0ubuntu3_amd64.deb
libnm-util2_0.9.4.0-0ubuntu3_amd64.deb
network-manager_0.9.4.0-0ubuntu3_amd64.deb

After following that I restarted and I still couldn't browse the internet (or ping) BUT updates worked. I updated everything (except for those network manager files). Still nothing. 

Then I saw that 12.10 was available. I thought "great, new start." I used the update manager to get 12.10. I'm still having the same problems. Network Manager updated itself and that's fine. Updates still work but no browser connections.

I'm lost. I have not installed any firewalls. The SO occasionally plays but she says she hasn't installed any firewalls that she is aware of. I read in one post here where someone installed Shorewall by accident (or as part of an upgrade). I checked and Shorewall is not installed on this machine. I'm at a total loss for how to proceed. I really don't want to uninstall ubuntu (using Windows) and then re-install using WUBI. 

Any idea's/suggestions? Please note I have used Ubuntu for awhile but am still, at the absolute best, a complete newbie. If there are any suggestions if you could phrase them/give examples of what to run/etc. that would be most appreciated.

Thank you in advance for any and all help that you can give.

---

### Post by gnusci on 2012-11-30
Install Wicd and then purge the network-manager, then try to reverse.

---

### Post by mansonfan78 on 2012-11-30
The config files in your browsers may have been corrupted by the problematic update.   You could try reinstalling Firefox and/or Chromium with Synaptic.  Or, if you don't have Synaptic you can try installing Opera (or any other browser that you don't already have) from the software center and see if it works.

---

### Post by ACuriousGuy on 2012-11-30
> **gnusci said:**
> Install Wicd and then purge the network-manager, then try to reverse.

I have no idea how to do the purge then reverse. 

> **mansonfan78 said:**
> The config files in your browsers may have been corrupted by the problematic update.   You could try reinstalling Firefox and/or Chromium with Synaptic.  Or, if you don't have Synaptic you can try installing Opera (or any other browser that you don't already have) from the software center and see if it works.

I uninstalled Opera, Firefox and Chromium. I then used the Software Center to re-install both. I still get nothing.

When trying to go to [www.google.com](www.google.com), I get this:

Chromium: This webpage is not available.
Firefox: Unable to connect. Firefox cannot establish a connection to the server at [www.google.com](www.google.com)

Weird that I was able to uninstall using these commands: 

sudo apt-get remove --purge opera*
sudo apt-get remove --purge chromium*
sudo apt-get remove --purge firefox*

And then easily able to reinstall using the Software Center. But still no connection with the browsers.

Again, thank you for the suggestions and any additional help/suggestions/etc is greatly appreciated.

---

### Post by mansonfan78 on 2012-11-30
Are web browsers the only thing affected?  What about email clients?  Could proxy settings be an issue?  And have you tried connecting directly to a lan again?  Does this happen at multiple locations or have you only used it at home (if only at home it could be a router issue)?  I'm just guessing here, I don't know why system updates would connect but not a browser (unless the update manager uses different connection settings than everything else).

---

### Post by ACuriousGuy on 2012-11-30
> **mansonfan78 said:**
> Are web browsers the only thing affected?  What about email clients?  Could proxy settings be an issue?  And have you tried connecting directly to a lan again?  Does this happen at multiple locations or have you only used it at home (if only at home it could be a router issue)?  I'm just guessing here, I don't know why system updates would connect but not a browser (unless the update manager uses different connection settings than everything else).

Well, I've only tried this at home. But I don't think it's a router issue as all my other computers (including the Winblows on the same laptop) can connect. If I log out of Ubuntu and log onto Windows Vista the connections are fine.

I don't know about email clients because all of my accounts are browser based.

I can not ping from Terminator. If I try [www.google.com](www.google.com) or an actual server IP address I get the same response ("Destination Port Unreachable").

---

### Post by ACuriousGuy on 2012-12-01
Well, just got done doing a download for a new linux distro. Once restarted I'm still having the same issue. Any other idea's anyone?

---

### Post by ACuriousGuy on 2012-12-05
Well, one more update. Updates work fine. Also my network is working fine. I was able to copy a torrent file from my windows machine to my ubuntu machine. Then I used Transmission BitTorrent Client to download that torrent. So that part is working.

Yet still I open my browsers and get the error messages (even after uninstalling/reinstalling). And also pings fail (as noted above).

Any idea's anyone? If nothing soon I'll have to just uninstall and reinstall Ubuntu. I'm really hoping I don't have to go that route. There has to be something simple I'm missing (as I never try anything really complicated). The SO is still confused as she doesn't remember installing anything that would have caused this.

Thanks again for any help/ideas/suggestions/etc. It is very much appreciated.

---

