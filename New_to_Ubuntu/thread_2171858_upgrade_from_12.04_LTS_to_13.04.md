---
title: "upgrade from 12.04 LTS to 13.04"
date: 2013-09-02
forum: New to Ubuntu
---

### Post by Marchello_Lippi on 2013-09-02
Hi all, 

what is easy way to upgrade from 12.04 LTS to 13.04 (without reinstalling whole operating system if possible) ?

---

### Post by khat33b on 2013-09-02
Open a terminal using Ctrl+Alt+T and type the command ```
update-manager -d
```. If you can upgrade Ubuntu to a newer release, it will  give you an option to begin the upgrade.

---

### Post by deadflowr on 2013-09-02
I don't remember, but I think the liveCD install has an option to "upgrade from" selection.
Never used it myself, so not sure if it even exists. Or if it does, if it even works.

Running an upgrade through update manager, you would need to run it twice to get from 12.04 to 13.04.
No need to run update manager -d, just open up the update manager and go to the settings button.
When the settings(software sources) opens, go to updates, then go to Notify new versions, and select any new version.
Then close the software sources and then run 'check', which will reload the package list and when it finishes an upgrade will be available.

This of course will only upgrade you to 12.10, so if you choose this method, you'll need to run it again to get to 13.04.

You can only upgrade from LTS to LTS, or one distro to the next distro.
So if on 12.10 and you wanted to upgrade to 13.10(beta right now) you would need to upgrade to 13.04.

This might change, as the Ubuntu technical board was looking into changing it a while ago to make upgrading from any release to any release possible.
The jury is still out on that though.

The safest way, though, is to backup your files and reinstall fresh and clean.

---

### Post by vance_2 on 2013-10-02
Sorry for the dig but I did not see a good answer posted to this and it is a question I am seeing quite a bit. As posted yes you need to upgrade 12.04 > 12.10 > 13.04 and it is actually quite easy. There is a detailed and recent guide posted in ioflares KB >> [http://www.ioflare.com/portal/knowledgebase/2/Upgrade-Your-Ubuntu-1204-Cloud-Server-To-1304-With-SSH.html](http://www.ioflare.com/portal/knowledgebase/2/Upgrade-Your-Ubuntu-1204-Cloud-Server-To-1304-With-SSH.html)[h=2][/h][h=2][/h][h=2][/h]

---

