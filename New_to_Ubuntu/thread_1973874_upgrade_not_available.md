---
title: "upgrade not available"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by peterson43 on 2012-05-05
I am currently running ubuntu 11.10 on my laptop. I want to upgrade to 12.04, but when I run update-manager it doesn't have the upgrade button available at the top telling me there is a new release available. How do I fix this?

---

### Post by cryptotheslow on 2012-05-05
Have a look in the Settings for Update Manager - on the Update tab there is a drop down to select what new releases should be offered: None / LTS only / All

Make sure that is on LTS or All and check for available updates again.

---

### Post by Cavsfan on 2012-05-05
While I recommend a clean install after backing up everything, the command, you can upgrade to 12.04 by opening a terminal and typing  **update-manager -d**

---

### Post by peterson43 on 2012-05-05
I should have mentioned that I checked the settings already. I have the new releases offered option set to "all" already so the upgrade should be showing up. 

Also, I have another computer running Ubuntu that is offering me the option to upgrade, so I tried checking the other options in the settings of update-manager with that computer and everything appears to be normal to me.

---

### Post by Cavsfan on 2012-05-05
[[COLOR=blue]_http://www.unixmen.com/how-to-upgrade-from-ubuntu-1004-1010-1104-to-ubuntu-1110-oneiric-ocelot-desktop-a-server/_[/COLOR]]("http://www.unixmen.com/how-to-upgrade-from-ubuntu-1004-1010-1104-to-ubuntu-1110-oneiric-ocelot-desktop-a-server/")

---

### Post by grahammechanical on 2012-05-05
You should check this link

[https://launchpad.net/ubuntu/+archivemirrors]("https://launchpad.net/ubuntu/+archivemirrors")

What mirror are you using to get your updates?

I see that you are in Indiana. And the Indiana University mirror is one week behind. Could that be the reason? Are the two machines set to different mirrors?

Regards.

---

### Post by peterson43 on 2012-05-05
The mirror suggestion is a good idea, but how do I check which mirror I'm using?

---

### Post by philinux on 2012-05-05
> **peterson43 said:**
> The mirror suggestion is a good idea, but how do I check which mirror I'm using?

Update manager settings see screenshot. Change to Main Server.

---

### Post by peterson43 on 2012-05-07
For whatever reason, changing the mirror didn't work (I tried several different mirrors). However, running the command **update-manager -d** from a terminal did work. Thanks for the suggestions.

---

