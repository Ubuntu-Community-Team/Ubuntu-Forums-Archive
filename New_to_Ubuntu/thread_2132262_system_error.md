---
title: "system error"
date: 2013-04-04
forum: New to Ubuntu
---

### Post by plejac on 2013-04-04
i am currently using ubuntu 12.04.i have been getting 'system error' .i had tried to install 12.10 and it was not successful.

So the error message is as follows[COLOR=#ff0000]:
'Error:opening the cache(E:Encountered a asection with no package:header,
E:problem with mergelist/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_packages,
E:THe package lists or total security file could not be opened.[/COLOR]'

i want only the ubuntu 12.04 ,so how  will i get the files that has been installed for 12.10 removed as i am not interested in updating.

kindly advise .

Thanks

---

### Post by ibjsb4 on 2013-04-04
Thats a version upgrade.  If you have already done this, there is no going back short of a reinstall :(

For your problem at hand, [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter these commands one at a time:

```
sudo rm -r /var/lib/apt/lists/*
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get update
```

And welcome to the forums :)

---

### Post by DuckHook on 2013-04-04
lbjsb4 is correct.

Based on your description, that 12.10 failed to complete its installation, it is probably partially installed, so it is impossible at this point to back out the changes made to your system when you tried to version-upgrade. You likely have a hodge-podge of 12.04 system files and 12.10 system files confusing your operating system right now.

1. If you have important data on your box, back it up.
2. Test the back up to make sure it is readable.
3. Use a LiveCD/USB to get into a LiveCD session.
4. Use gparted to either repartition or reformat your HDD so that you have no legacy files residing on disk.
5. Install 12.04.2 cleanly to your blank HDD.

If 12.10 did not proceed to the actual installation phase, then you may still be able to just use 12.04, but it is impossible to tell where the upgrade process left off and you will spend more time trying to chase down errors and incompatibilities than you would just reinstalling. Also, you will never be confident that some issue you encounter in the future wasn't due to the failed upgrade.

---

