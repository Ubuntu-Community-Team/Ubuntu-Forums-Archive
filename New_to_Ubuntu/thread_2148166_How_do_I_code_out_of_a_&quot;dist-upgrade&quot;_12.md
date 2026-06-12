---
title: "How do I code out of a &quot;dist-upgrade&quot;? 12.04 is trying to upgrade to 12.10, disaster!"
date: 2013-05-24
forum: New to Ubuntu
---

### Post by megenk11 on 2013-05-24
I brainlessly trusted another total newbie (on Ultimate Edition) and used "dist-upgrade" after a promise that nothing but a list of possible upgrades would appear. Now my update notification is always lit. How do I code back out of that "dist-upgrade"? Ubuntu is trying to upgrade my beloved 12.04 to 12.10 and I was told never to kill my update manager.megenk

Thanks to Lisati for teaching me how to mark my threads solved!

Thank you SlugSlug, I had to use 
       sudo leafpad /etc/update-manager/release-upgrades,      instead of
       gksudo leaf /etc/update-manager/release-upgrades,
And I got very big smiles when it actually let me edit and save a page! I  usually feel like some miniture beings really control this box, not I!
Happy First Solo Terminal Editing Day to me........

---

### Post by SlugSlug on 2013-05-24
you can edit the file 

/etc/update-manager/release-upgrades

change it to
Prompt=lts

think xubuntu is using leaf?

gksudo leaf /etc/update-manager/release-upgrades

---

### Post by Dennis N on 2013-05-24
Xubuntu 13.04 - exact path and titles may be different in your version (eg: "software and updates" could be "update manager"):

[B]Settings > System > Software and Updates > Updates Tab
[/B]
Change the settings in "notify me of a new Ubuntu version".

**Checked an Xubuntu 12.04:**

**System > Update Manager > Settings > Updates Tab**

Change the settings in "notify me of a new Ubuntu version".

---

### Post by ibjsb4 on 2013-05-24
Just for your info, an dist-upgrade is the same thing you do when you use the Update Manager.  Just no GUI :)

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by megenk11 on 2013-06-01
[Solved]
Thanks SlugSlug, Dennis N, and ibjsb4. With putting all of your incoming data together, I turned off my update manager for a few days and Voila, problem gone. Thanks again! Megenk.
P.S. How do I mark a thread "solved" without starting a new thread with it's drop down menu?

---

### Post by lisati on 2013-06-01
> **megenk11 said:**
> P.S. How do I mark a thread "solved" without starting a new thread with it's drop down menu?
Se here: [http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

### Post by megenk11 on 2013-06-02
Thank you SlugSlug
I had to use 
       sudo leafpad /etc/update-manager/release-upgrades      instead of
       gksudo leaf /etc/update-manager/release-upgrades
And I got very big smiles when it actually let me edit and save a page! I usually feel like some miniture beings really control this box, not I!
Happy First Editing Day to me........

---

