---
title: "Ubuntu 16.04 LTS currently; Ubuntu Software won't start. How to Update LO?"
date: 2017-04-05
forum: New to Ubuntu
---

### Post by Umgb on 2017-04-05
After successfully installing Ubuntu 16.04, everything worked. Then Ubuntu Software (US) refused to start.
1) How can one re-activate US?
2) I currently have LO 5.1.6.2, but there is a newer version to which I wish to update. But HOW, when US isn't functioning?
Thank you.

---

### Post by deadflowr on 2017-04-05
Open Software Updater and run an update.

---

### Post by mastablasta on 2017-04-06
alternatively open terminal and run :

```
sudo apt-get update
sudo apt-get upgrade

```
copy and post any errors that might appear here.

---

### Post by Impavidus on 2017-04-06
Updating will give you bug fixes for LibreOffice, but no new features. Ubuntu 16.04 will stay at LibreOffice 5.1.6, unless you use a PPA, which should give you the latest release (currently 5.3.1). Generally, PPAs are a great way of destabilising your system, but I read the LibreOffice PPA is quite reliable. I never tried it myself, as I rarely use LibreOffice.

But first check your package management system. The posts above tell you how.

---

