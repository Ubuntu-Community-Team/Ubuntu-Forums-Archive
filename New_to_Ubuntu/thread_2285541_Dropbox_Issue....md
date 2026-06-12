---
title: "Dropbox Issue..."
date: 2015-07-06
forum: New to Ubuntu
---

### Post by drf2 on 2015-07-06
Hey, 

Please note, I am completely new to usage of Ubuntu Forms...

I am trying to get Dropbox up and running in 14.04 LTS but am having issues. Originally, I installed it successfully via the Software Centre. When I would launch the program, I would get the request for an adminstrator password which is normal for first time Dropbox setup, however, Dropbox would never actually start. I uninstalled it, tried reinstalling it via the Softare Center, had same issue, then uninstalled it again, and tried reinstalling it via the terminal. That didnt work as I had the same issue, so I uninstalled it via the terminal. Now when I try to install it (either by Terminal or Software Center) I get the following error and it fails to install:

"The following packages have unmet dependencies:
 nautilus-dropbox : Depends: dropbox but it is not going to be installed
 E: Unable to correct problems, you have held broken packages."

Any ideas?

---

### Post by roger_1960 on 2015-07-06
Hi

I would do this.  First in terminal

```
sudo apt-get remove nautilus-dropbox
apt-get purge nautilus-dropbox

```

Then I would open a browser and download dropbox from the dropbox website and use their instructions.  I have had lots of problems with dropbox from the repos in the past.

---

