---
title: "apt-key deprecated, upgrade abored, can't renew/migrate keys, pls help"
date: 2024-09-24
forum: New to Ubuntu
---

### Post by dfrusone on 2024-09-24
Dear communiy,

It all began when I tried to upgrade the OS, but it failed with an error. Then, I tried to update the packages using `apt update`, and the following errors appeared. I attempted to migrate the expired keys, but after migrating and deleting them, the issue reappears. Can someone help me fix this? Did I do something wrong? Why is this happening?


W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_22.04](https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_22.04) ./ InRelease: The following signatures were invalid: EXPKEYSIG B8AC39B0876D807E home:npreining OBS Project <home:npreining@build.opensuse.org>
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu](https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu) groovy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 179999B1339E73B7 NO_PUBKEY D45DF2E8FC91AE7E
W: Failed to fetch [https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu/dists/groovy/InRelease](https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu/dists/groovy/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 179999B1339E73B7 NO_PUBKEY D45DF2E8FC91AE7E
W: Failed to fetch [https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_22.04/./InRelease](https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_22.04/./InRelease)  The following signatures were invalid: EXPKEYSIG B8AC39B0876D807E home:npreining OBS Project <home:npreining@build.opensuse.org>
W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by wildmanne39 on 2024-09-24
Moved to New to Ubuntu sub-forum.

---

### Post by grahammechanical on 2024-09-24
It would help if you told us what version of Ubuntu you were using and what version of Ubuntu you were upgrading to.

The errors refer to a PPA = Personal Package Archive. It is most likely that the maintainer of the PPA has not transitioned the software over to the newer version of Ubuntu.

You also have a non-Ubuntu repository (opensuse) as a software source (repository). The same reason could apply here. That opensuse repository is not valid for that newer release of Ubuntu. It may not even exist for that version of Ubuntu.

When doing an online upgrade to newer versions of Ubuntu we are supposed to disable all PPA's and reactivate them as new after the upgrade. If they exist in the newer version. The error messages will go away if you remove those two repositories from your sources list text file.

Or, you could edit the internet address of both repositories by changing the reference to the new Ubuntu version and replace it with the old Ubuntu version.

For example., I purchased a laptop with Ubuntu 20.04 pre-installed. Drivers provided by the supplier gave additional functions to the keyboard. These additional functions were lost when I installed Ubuntu 22.04. The suppliers repository for those drivers was not available in 22.04. So, I copied the internet address from the 20.04 sources.list file into the sources.list file of 22.04. I ran update/upgrade and I used Synaptic Package Manager to access and search the supplier repository for keyboard drivers and install the driver. 

I mention that to illustrate why you are getting those two errors.

Regards

---

### Post by dfrusone on 2024-09-25
[FONT=&amp]Thank you very much for your response. The current version is still the same, 22.04.5 LTS Jammy. The problem arose because the operating system attempted to upgrade, but due to the issues described above, the process always ended in error. What can I do? I have also tried to remove these external resources, but unfortunately, I cannot find these resources listed in the settings. They only appear during the update process. Thanks a lot![/FONT]

---

### Post by dfrusone on 2024-09-27
i already tried to remove the npreining.list.save in /etc/apt/sources.list.d but helped nothing :(

---

