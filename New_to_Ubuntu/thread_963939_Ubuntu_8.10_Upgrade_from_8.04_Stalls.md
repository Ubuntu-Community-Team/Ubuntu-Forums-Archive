---
title: "Ubuntu 8.10 Upgrade from 8.04 Stalls"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by fade79 on 2008-10-30
Hi I tried to upgrade my 8.04 to 8.10 and it stalled during the Cleanup phase with endless HD thrashing.  In the terminal it was stuck on something related to running delayed ldconfig processes. 

I did a restart and I was able to log back into my 8.04 system but now my "Software Sources" in the System Administration will not load at all.  I can run the Update Manager and now it lists 619 updates (while before the attempt to install 8.10 there were none) and it only gives me an option to do a partial update.  When I try the update it fails saying the the tool does not support an upgrade from 'intrepid' to 'hardy.'

Is there any way to complete the upgrade or revert back to a working 8.04?

---

### Post by kansasnoob on 2008-10-30
I don't believe there is any way to revert (I wish there was).

My thought (which could be wrong) is to go ahead with the updates.

Also read this:

[http://ubuntuforums.org/showthread.php?t=950851](http://ubuntuforums.org/showthread.php?t=950851)

Now, I've not done it, but bobnutfield has helped me several times so I consider him a trusted source.

Also, if the updates are successful the first command I'd run is:

```
sudo apt-get -f install
```

To hopefully resolve any unmet dependencies. It may result in an "auto-remove" prompt or something of that nature if so, certainly do as it says, just remember to "sudo".

---

### Post by nynoah on 2008-10-30
I really hate the upgrade option.  I have rarely heard it working for people.  Most people do not realize that if they have any other repositories enabled besides the standard Ubuntu ones that those do not upgrade and you are left with a partial upgrade that either locks your computer of within time will lock it.  I know I have like 5 different non standard repos in my library.  Any one of those could cause a problem for Ibex.

I always recommend a complete fresh install with a complete wipe of the hard drive prior to upgrade.

---

### Post by fade79 on 2008-10-30
Thanks!  I'll give it a try and if all else fails a clean install.


> **kansasnoob said:**
> I don't believe there is any way to revert (I wish there was).

My thought (which could be wrong) is to go ahead with the updates.

Also read this:

[http://ubuntuforums.org/showthread.php?t=950851](http://ubuntuforums.org/showthread.php?t=950851)

Now, I've not done it, but bobnutfield has helped me several times so I consider him a trusted source.

Also, if the updates are successful the first command I'd run is:

```
sudo apt-get -f install
```

To hopefully resolve any unmet dependencies. It may result in an "auto-remove" prompt or something of that nature if so, certainly do as it says, just remember to "sudo".

---

