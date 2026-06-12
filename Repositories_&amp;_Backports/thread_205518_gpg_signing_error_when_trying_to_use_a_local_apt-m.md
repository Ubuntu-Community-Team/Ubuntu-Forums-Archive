---
title: "gpg signing error when trying to use a local apt-mirror repository"
date: 2006-06-28
forum: Repositories &amp; Backports
---

### Post by iwagner on 2006-06-28
I've got a bunch of computers to install and configure at work, so I want to create a local mirror of the packages.  I installed apt-mirror and it downloads everything just fine.  I changed my sources.list to point to the new local repository and did an apt-get update.  I get the following error after trying the update:

W: GPG error: file: dapper-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

There is obviously something with the Release.gpg file in the dapper-updates directory that it doesn't like.  Does anyone know why, and is there anything that can be done about it?

Thanks

---

### Post by pogson on 2006-07-04
I was using debmirror for the same purpose today, and had that error. I had downloaded the [email]ftpmaster@ubuntu.com[/email] public key as my normal user, but was downloading as root. Of course root and I have different keyrings...:o  so debmirror could not verify the signature. Running debmirror as myself made the error go away because the key was in my keyring. I hope this helps some newbie. I am not a newbie. I should have known better, but I forget a lot. I should not have been downloading as root, but I had to be root to mount the filesystem and I just kept going that way without thinking. Haste make waste.

---

