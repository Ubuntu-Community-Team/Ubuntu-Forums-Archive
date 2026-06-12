---
title: "distro upgrade tool lost"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by pierreyy on 2012-04-26
hey guys, 

so i open the update manager today and push the "upgrade" button to update from 11.10 to 12.04. the tool downloads okay but the internet connection goes down, anw i cant find the tool again and its not showin up in the update manger, any ideas to where i can find it again? 

thanks alot!

---

### Post by mikewhatever on 2012-04-26
Try launching the update manager with 'update-manager -d'. Alternatively, run 'do-release-upgrade' in a terminal.

---

### Post by pierreyy on 2012-04-26
thanks for the come back 
 i ran ```
 sudo apt-get update 
``` then ```
 do-release-upgrade 
```

i got >  Checking for a new ubuntu release
No new release found


---

### Post by NoNameWill on 2012-04-26
Upgrade has already started. My 32 bit laptop froze twice while upgrading through the GUI. The first time the repos had already been changed. When I rebooted from that I was given the option to do a partial upgrade from update manager. Froze again. Went to CLI to finish up. 

Have any packages came up?
```
sudo apt-get update && sudo apt-get upgrade
```

I tried ```
 sudo apt-get dist-upgrade
``` from a 64 bit and 32 bit 11.10 machine. I got the same reply no new upgrades.:confused:

---

### Post by pierreyy on 2012-04-27
> **NoNameWill said:**
> Upgrade has already started. My 32 bit laptop froze twice while upgrading through the GUI. The first time the repos had already been changed. When I rebooted from that I was given the option to do a partial upgrade from update manager. Froze again. Went to CLI to finish up. 

Have any packages came up?
```
sudo apt-get update && sudo apt-get upgrade
```

I tried ```
 sudo apt-get dist-upgrade
``` from a 64 bit and 32 bit 11.10 machine. I got the same reply no new upgrades.:confused:

sounds like the same thing thats goin on with me... i have a 32 bit 11.10... could that be the problem?

---

### Post by pierreyy on 2012-04-28
bump

---

### Post by pierreyy on 2012-04-28
i ran  ```
 sudo apt-get 
```
and i got >  Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG 588CD9FC28446D73 Launchpad PPA for Antono Vasiljev
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A80C8DFE23A187B2
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG 94E58C34A8670E8C Launchpad PPA for Screenlets
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG C2518248EEA14886 Launchpad VLC


any ideas guys?

---

### Post by pierreyy on 2012-05-07
bump

---

### Post by oldos2er on 2012-05-07
You should disable all PPAs before upgrading to a new version of Ubuntu.

---

### Post by pierreyy on 2012-05-09
i removed all the ppa but the official ubuntu one. then i ran ```
 sudo apt-get update
``` then ```
 do-release-upgrade
``` and that did the trick,


thanks!!

---

