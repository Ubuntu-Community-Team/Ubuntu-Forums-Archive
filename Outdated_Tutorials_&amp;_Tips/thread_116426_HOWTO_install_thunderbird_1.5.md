---
title: "HOWTO: install thunderbird 1.5"
date: 2006-01-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Virtual DarKness on 2006-01-12
**waiting for the backport**.. ;-) (if any):

- make sure you have thunderbird installed from ubuntu repository

- _backup your thunderbird mail archive and prefs_.

- download thunderbird from mozilla.org in a folder called for example "thunderbird"

- go inside that folder and create a script called install-thunderbird.sh and paste this as the content of the script:

```
#!/bin/sh
tar -xzf thunderbird-1.5.tar.gz
touch mozilla-thunderbird
echo cd /opt/thunderbird/ >> mozilla-thunderbird
echo ./thunderbird >> mozilla-thunderbird
chmod +x mozilla-thunderbird
sudo rm -rf /opt/thunderbird/
sudo mv thunderbird /opt/
sudo chown -R root:users /opt/thunderbird/
sudo chmod -R g+w /opt/thunderbird/
sudo rm /usr/bin/mozilla-thunderbird
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/mozilla-thunderbird
sudo mv mozilla-thunderbird /usr/bin/
sudo chown root:root /usr/bin/mozilla-thunderbird
echo Done.
```


if you want to go back to the ubuntu version of thunderbird just delete the /opt/thunderbird folder and reinstall from synaptic.

bye,
Giovanni.

---

