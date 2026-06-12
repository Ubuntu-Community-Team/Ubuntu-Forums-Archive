---
title: "[SOLVED] Hide upgrade notice in Gutsy Update manager?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by bornagainpenguin on 2008-05-29
Can this be done?  How can I do it?  I still want to get updates, I just don't want anyone to be seeing the notice about upgrading the distro from Gutsy to Hardy.

Anyone know this one?  Thanks in advance!

--bornagainpenguin

---

### Post by starcannon on 2008-05-29
I'd also like to know this one, I need to remove upgrade notices from some clients machines.

---

### Post by kansasnoob on 2008-05-29
Go to Synaptic. Click on Settings > Repositories. This will open the Software Sources window. Click on the Updates tab. At the very bottom where it says, "Release Upgrade" just select never.

Close that window and then close synaptic.

---

### Post by kansasnoob on 2008-05-29
I just happened to think, Software Sources shows up in the default Administration menu without having to open synaptic.

I just have a lot of menu options hidden on my machine :)

---

### Post by bornagainpenguin on 2008-05-29
> **kansasnoob said:**
> Go to Synaptic. Click on Settings > Repositories. This will open the Software Sources window. Click on the Updates tab. At the very bottom where it says, "Release Upgrade" just select never.

Close that window and then close synaptic.

Ummm....where?

**Update:** I just checked with my laptop; that option only seems to exist in Hardy, and not in Gutsy.  Maybe its also possible this is a LTS release only feature?  Is it recommended to try installing the Hardy deb on Gutsy for the update-manager?

--bornagainpenguin

---

### Post by kansasnoob on 2008-05-29
My bad. I'd only used Gutsy for a couple of months and I was looking at Hardy's Software Source menu. I see after booting the Gutsy Live CD that option didn't exist then. Sorry!

I've also searched and searched for an answer with no luck. There simply must be a way to edit the update manager in Gutsy. But I've not found it.

Sorry again for the noob error.

Consider this a free bump :confused:

---

### Post by bornagainpenguin on 2008-05-29
> **kansasnoob said:**
> Consider this a free bump :confused:

Thanks for the free bump!  What do you (or anyone who knows more about this type of thing) think about trying to install one of these in Gutsy?

[http://packages.ubuntu.com/hardy/i386/update-manager-core/download](http://packages.ubuntu.com/hardy/i386/update-manager-core/download)

Would installing the updated version add that option or am I barking up the wrong tree?

--bornagainpenguin

---

### Post by kansasnoob on 2008-05-29
I'm thinking repost this question in Main Support Categories > Installation & Upgrades. I think they get more Forum Staff attention.

This really should be something that can be fixed. While I'm happy with Hardy I can absolutely guarantee you that I want to be able to edit everything in my Ubuntu.

There has to be a way to disable dist-upgrades in the Update Manager without disabling the whole thing. I wonder if it's possible to update the update-manager to the Hardy version without breaking everything?

---

### Post by bornagainpenguin on 2008-05-29
> **kansasnoob said:**
> I'm thinking repost this question in Main Support Categories > Installation & Upgrades. I think they get more Forum Staff attention.

This really should be something that can be fixed. While I'm happy with Hardy I can absolutely guarantee you that I want to be able to edit everything in my Ubuntu.

There has to be a way to disable dist-upgrades in the Update Manager without disabling the whole thing. I wonder if it's possible to update the update-manager to the Hardy version without breaking everything?

I made a new post where you indicated, [here]("http://ubuntuforums.org/showthread.php?p=5072609").  Hopefully someone who knows will see and tell me how to do this without borking the system...

--bornagainpenguin

---

### Post by mc4man on 2008-05-29
In applications -> system tools -> configuration editor -> apps -> update manager you can turn off check dist. upgrade
If conf. editor isn't there enable thru edit menus

---

### Post by bornagainpenguin on 2008-05-29
> **mc4man said:**
> In applications -> system tools -> configuration editor -> apps -> update manager you can turn off check dist. upgrade
If conf. editor isn't there enable thru edit menus

Thank you!  That worked!!  I knew there had to be *something* like this somewhere...

--bornagainpenguin

---

### Post by starcannon on 2008-05-29
aye aye, thanks man, conf editor was the ticket.

---

