---
title: "Install VLC Player on UBUNTU running from USB"
date: 2016-09-29
forum: New to Ubuntu
---

### Post by sumitpratap on 2016-09-29
Hey Guys,

I am running Ubuntu 16.04 from USB using **Try before installing feature.**
I have tried installing VLC player using following commands
sudo apt-get update
sudo apt-get install vlc browser-plugin-vlc

But I got error (screen shot attached for the same) and VLC not installed.

Can anyone suggest if it possible to install VLC on Ubuntu running from USB.

---

### Post by howefield on 2016-09-29
Open up the Software & Updates application and ensure that the universe repository is enabled.

---

### Post by deadflowr on 2016-09-29
enable the universe repository.
open Software and Updates and check the community-maintained option.
then close and let it reload. (or re-run the apt-get update command.

ninja'd

---

### Post by sudodus on 2016-09-29
Welcome to the Ubuntu Forums :-)

Please notice that you *can* install vlc into 'Try Ubuntu' alias a live session of Ubuntu. But it will not survive a reboot unless you create a *persistent* live system or an *installed* system in the USB drive.

See this link for more details: [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

