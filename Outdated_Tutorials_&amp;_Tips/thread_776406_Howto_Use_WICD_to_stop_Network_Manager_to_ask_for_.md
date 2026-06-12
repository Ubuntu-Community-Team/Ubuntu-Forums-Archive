---
title: "Howto: Use WICD to stop Network Manager to ask for your keyring password!"
date: 2008-04-30
forum: Outdated Tutorials &amp; Tips
---

### Post by yngens on 2008-04-30
This was already posted on [http://ubuntuforums.org/showpost.php?p=4786265&postcount=110](http://ubuntuforums.org/showpost.php?p=4786265&postcount=110), however because this method is different from the initial post in that thread, I decided to open a new how-to page. This excellent and simple tutorial is taken from [http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04](http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04)

1. Go to Administration > Synaptic Package Manager > Settings > Repositories > Third Party Software > Add...

```
deb http://apt.wicd.net hardy extras
```

(replace 'hardy' with 'dapper', 'edgy', 'feisty' or 'gutsy' according to your system's name).

2. Click Reload and wait while the package lists are downloaded, Search for "Wicd" and install it. The system will warn about that in order to install Wicd you have to uninstall NetworkManager. Response positively and finish the installation.

Don't worry about "The NetworkManager applet could not find some required resources. It cannot continue" message, just close it for now.

3. Go to Applications > Internet > Wicd.
[B]
Attention! If Wicd does not run at this stage, then have these instructions copied in some place on your Desktop or Home folder, because you will now need to restart your computer, and after the system loads back you will not have immediate Internet connection to get to these page online![/B]

- Select your wireless network, make sure to put check mark for "Automatically connect to this network".

- Then click to "Advanced Settings", mark up "Use Encryption" and put your WPA or WEP password in the field just below it. If you use MAC filter wireless security, then just omit this step.

- Press "Connect".

4. Go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "Add" button. Give it some name ("Wireless Manager" or "Wicd"). In the command field enter "/opt/wicd/tray.py".

5. Go to System > Administration > Login Window > Security and enable "Automatic Login", close and rock and roll!"

---

