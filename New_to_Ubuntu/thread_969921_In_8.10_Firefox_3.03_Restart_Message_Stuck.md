---
title: "In 8.10 Firefox 3.03 Restart Message Stuck"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by R_U_Q_R_U on 2008-11-03
Hi,

I just did an upgrade to 8.10 and everything seems fine. The only visible problem I see is in Firefox 3.03. There is a yellow message bar at the top that says "Your browser has been updated and needs to be restarted."

Problem: no matter how many times I restart Firefox the error never goes away. Any clue how to fix this?

THANKS>

UPDATE: The error console says:

Failed to load XPCOM component: /usr/lib/xulrunner-1.9.0.3/components/pyabout.py
Failed to load XPCOM component: /usr/lib/xulrunner-1.9.0.3/components/libpyloader.so

---

### Post by R_U_Q_R_U on 2008-11-04
This has been reported in Launchpad as bug #270303

[https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/270303](https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/270303)

                 A workaround:
 Firefox menu > File > Quit
Then execute in terminal:
sudo killall -9 -r firefox
sudo apt-get purge firefox firefox-3.0 ubufox
sudo apt-get install --reinstall firefox firefox-3.0 firefox-3.0-gnome-support
 When it's done, try run firefox

---

### Post by guerby on 2008-11-18
Removing the following file cured the issue for me:

$HOME/.mozilla/firefox/default.XXX/localstore.rdf

Thanks to #firefox people.

---

### Post by jnylen on 2008-11-27
> **guerby said:**
> Removing the following file cured the issue for me:

$HOME/.mozilla/firefox/default.XXX/localstore.rdf

Thanks to #firefox people.

This did not work for me, and I was not willing to purge/reinstall to fix the problem.  Disabling the ubufox extension, however, did make the incredibly annoying problem go away.

---

### Post by ayeomans on 2008-12-18
Rather than remove all customisation by uninstalling firefox or deleting localstore.rfd, my workround was 

close firefox
edit ~/.mozilla/firefox/<profile>/localstore.rdf to remove the 6 lines referring to "sanitize.xul" 

```
<RDF:Description RDF:about="chrome://browser/content/sanitize.xul#SanitizeDialog"
                       screenX="439"
                       screenY="345" />
<RDF:Description RDF:about="chrome://browser/content/sanitize.xul">
  <NC:persist RDF:resource="chrome://browser/content/sanitize.xul#SanitizeDialog"
</RDF:Description>
```
then restart.
The repeated dialogue goes away.

---

### Post by thirdspace on 2009-04-27
A less drastic fix that worked for me was to open a terminal,
cd to the applicable subdirectory of .mozilla/firefox, and "touch localstore.rdf". This just updates the last modified date on that file without actually changing its contents. It seems that whoever implemented the restart message thought that restarting firefox always updates that file, but they were wrong. Anyway "programming as if every phenomenon is an interface" is dumb because it makes software fragile.

---

### Post by slickvguy on 2009-04-29
> **thirdspace said:**
> A less drastic fix that worked for me was to open a terminal,
cd to the applicable subdirectory of .mozilla/firefox, and "touch localstore.rdf". This just updates the last modified date on that file without actually changing its contents. It seems that whoever implemented the restart message thought that restarting firefox always updates that file, but they were wrong. 

Had an update today (Intrepid) and unfortunately saw that this bug has still not been fixed. I've successfully used the "sanitize" method previously, but this "touch" method worked and is a better approach. 

Thank you, thirdspace.

---

### Post by xouns on 2009-05-08
In Jaunty, this didn't work for me, though I like the "touch" command...

---

### Post by slickvguy on 2009-06-13
FF3 3.0.11, Ubuntu 8.10
FF updated today, and this problem still exists. 
The touch method worked again. Be sure to cd into the user subdirectory under ~/.mozilla/firefox/ because there's also a localstore.rdf in the firefox directory.

Hard to believe this annoying bug hasn't been fixed yet. Annoying.

---

### Post by ubunoobie on 2009-06-16
I was also having this problem. It just started today. I took care of it following the workaround in this thread, but then I started to have the problem where apparently all of the security certificates are gone from firefox, and each time I go to a secure site, I have to manually add the exception, as described in the following thread ( [http://ubuntuforums.org/showthread.php?t=1141476](http://ubuntuforums.org/showthread.php?t=1141476) ).

Has anyone encountered this? (and what to do about it)

---

### Post by ubunoobie on 2009-06-17
> **ubunoobie said:**
> I was also having this problem. It just started today. I took care of it following the workaround in this thread, but then I started to have the problem where apparently all of the security certificates are gone from firefox, and each time I go to a secure site, I have to manually add the exception, as described in the following thread ( [http://ubuntuforums.org/showthread.php?t=1141476](http://ubuntuforums.org/showthread.php?t=1141476) ).

Has anyone encountered this? (and what to do about it)

Update:

A couple of firefox updates came down through the update manager this morning (actually was an upgrade to 3.0.11) and seem to have fixed this issue.

---

### Post by slickvguy on 2009-07-22
FF3 updated today. Running Intrepid 8.10 w/ FF3 3.0.12. 
Bug still exists. Touch method did not work.

---

