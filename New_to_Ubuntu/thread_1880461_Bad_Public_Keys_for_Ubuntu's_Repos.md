---
title: "Bad Public Keys for Ubuntu's Repos"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by Promaster91 on 2011-11-13
I keep getting this error everytime I try to update. I don't know what happened to the public keys. I have tried to reset them to the default keys by going to Synaptic->Settings->Repos->Auth->Restore Defaults however it seems that does not work. Does anyone have any suggestions?

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B725097B3ACC3965
W: GPG error: http://us.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by oldos2er on 2011-11-13
For the BADSIG errors, try running these commands one at a time ```
sudo apt-get clean

cd /var/lib/apt

sudo mv lists lists.old

sudo mkdir -p lists/partial

sudo apt-get clean

sudo apt-get update
```

For the NO PUBKEY error, run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` where KEYID is the number shown in the error msg.

---

