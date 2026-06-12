---
title: "Question about upgrades for stuff I don't use."
date: 2008-05-29
forum: New to Ubuntu
---

### Post by RedMartin on 2008-05-29
In todays updates there was a load of stuff for Evolution.

I use Thunderbird in preference to Evo and this leaves me with two questions.

1. Can I leave these updates or should they be installed for 'security reasons'?

2. If I choose to leave them will Update Manager keep telling me they are available every day until I cave in?

Thanks.

---

### Post by kwacka on 2008-05-29
If you remove evolution you won't get the reminders.

Use synaptic; there are a couple of libraries that it seems gnome depends on so keep those. 

Removing ubuntu-desktop isn't a problem - its a a meta package that tells synaptic to install everything.

A further alternative is to open synaptic, search for evolution, highlight the packages and then click on 'package --> lock package.  This stops it being upgraded.

---

### Post by RedMartin on 2008-05-30
> **kwacka said:**
> If you remove evolution you won't get the reminders.

Use synaptic; there are a couple of libraries that it seems gnome depends on so keep those. 

Removing ubuntu-desktop isn't a problem - its a a meta package that tells synaptic to install everything.

A further alternative is to open synaptic, search for evolution, highlight the packages and then click on 'package --> lock package.  This stops it being upgraded.

Thanks for the answer. I'll give it a go.

---

### Post by Inxsible on 2008-05-30
Keep in mind though, that if you remove ubuntu-desktop, you will not be able to upgrade to a newer version of the OS. for eg when Intrepid releases. 

You can however, install ubuntu-desktop again, go thru the upgrade and then remove it one more time.

---

