---
title: "How to automatically update?"
date: 2015-06-04
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-06-04
Hello guys 
Is there a way or some kind of cron job that makes the update manager starts downloading and after upgrading at a certain time?

---

### Post by tristan16 on 2015-06-04
In the Update Settings, you can set up Ubuntu to automatically download and install security updates, but you'll still have to manually click the "accept" button for all other updates.

---

### Post by tristan16 on 2015-06-04
More info from this discussion: [http://askubuntu.com/questions/9/how-do-i-enable-automatic-updates](http://askubuntu.com/questions/9/how-do-i-enable-automatic-updates)

You could script a cron job with this: ```
sudo apt-get upgrade -y
```

The -y assumes yes to all prompts. **However, this could cause some packages to be removed** as noted in the linked discussion.

---

### Post by ian-weisser on 2015-06-04
> **remmas-sido said:**
> Hello guys 
Is there a way or some kind of cron job that makes the update manager starts downloading and after upgrading at a certain time?

Yes, there is. It's /etc/cron.daily/apt

The types of updates you can do automatically are set by /etc/apt/apt.conf.d/50unattended-upgrades , which is provided by the 'unattended-upgrades' package. It's powerful - many of those options do not have a corresponding checkbox in the GUI.

The GUI applications (software-updater and/or software-center) are NOT required to run these updates automatically or change settings.

For example, I run all -security and -updates from the Ubuntu repositories completely in the background...including kernel updates... with a single change to the 50unattended-upgrades file. No nagging, no passwords. software-updater isn't even installed. Non-ubuntu software like Chrome is not included; I do that separately.

---

