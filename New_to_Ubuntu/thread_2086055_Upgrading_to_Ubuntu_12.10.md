---
title: "Upgrading to Ubuntu 12.10?"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by JSF16 on 2012-11-19
Trying to upgrade to 12.10, however the Update Manager does not offer me a chance to upgrade, and I'd rather not have to install the whole thing from scratch.

---

### Post by wojox on 2012-11-19
Press Alt+F2 and type in ```
update-manager -d
``` What happens?

---

### Post by Bucky Ball on 2012-11-19
Do you have your Update Manager set to notify of new releases? There is a drop down list and you may have it set to LTS releases only or something.

Be aware that the upgrade process can be lengthy and sometimes problematic. You generally get a cleaner result with a clean install and it would be quicker than an upgrade through software centre. 

Is there a particular reason you are upgrading? 12.04 LTS not working for you?

---

### Post by deadflowr on 2012-11-19
+1 to what Bucky Ball said.

The upgrade defaults to LTS releases.
To change go to the settings in the update manager and go to updates and change the settings for notify me of new versions to anything but lts-releases only.(It'll give you several choices.
Then close it(don't revert) and click the check button into the update manager(this will reload the repos and the upgrade option should show at the top when all is said and done).

---

### Post by sandyd on 2012-11-19
First, open the software center, and go to edit -> software sources

[IMG]http://oc.sandyd.me/public.php?service=files&token=84ef995c120d9dc145e5ca0e41110bc8c740fa93&file=/images/screenshots/uf/softwaresources_open%20(2).jpg[/IMG]

Then, go to the 'Updates' tab, and select "Notify me of a New Ubuntu Version". It should be at "For any new version"

[IMG]http://oc.sandyd.me/public.php?service=files&token=1fbe93bfbf3b0f5ec7fe522b0a559e70f7368531&file=/images/screenshots/uf/softwaresources_lts%20(2).jpg[/IMG]

Afterwards, go back to the update manager, and click the "Check" button

---

### Post by newb85 on 2012-11-19
I'm not speaking from experience, but from what I've read, you're best off installing all available updates before running the upgrade, if indeed you're going to run the upgrade.

And make sure you've backed up any valuable files.

---

### Post by deadflowr on 2012-11-20
> **newb85 said:**
> I'm not speaking from experience, but from what I've read, you're best off installing all available updates before running the upgrade, if indeed you're going to run the upgrade.

And make sure you've backed up any valuable files.

I've never understood this.
Updating your packages, only to have your system upgrade all versions of packages installed seems redundant. I know if you upgrade from a clean fresh install without updating the system, nothing bad happens.

And yes, do backup what's precious to you.

---

### Post by alphacrucis2 on 2012-11-20
> **deadflowr said:**
> I've never understood this.
Updating your packages, only to have your system upgrade all versions of packages installed seems redundant. I know if you upgrade from a clean fresh install without updating the system, nothing bad happens.

And yes, do backup what's precious to you.

One possibilty is getting updates that fix bugs in apt or dpkg that would otherwise cause the release upgrade to fail.

---

