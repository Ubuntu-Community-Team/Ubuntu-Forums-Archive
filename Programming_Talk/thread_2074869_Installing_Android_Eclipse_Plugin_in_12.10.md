---
title: "Installing Android Eclipse Plugin in 12.10"
date: 2012-10-22
forum: Programming Talk
---

### Post by mr john on 2012-10-22
Hi,
    I've tried to install the android eclipse plugin in my usual way by adding [https://dl-ssl.google.com/android/eclipse/](https://dl-ssl.google.com/android/eclipse/)' to the available software option and then ticking the boxes relating to Android.

After it downloaded, installed the packages and then restarted I don't have the ability to create a new android package. Am I doing something wrong? Has something changed in eclipse 3.8 on Ubuntu 12.10?

---

### Post by mr john on 2012-10-23
I resolved this issue by doing the following:

Started eclipse from terminal (as su):

> sudo eclipseIn the eclipse GUI I clicked "check for updates" and installed all the updates. You need to have started eclipse as su to have been able to do this.

When eclipse finished all the updates it asked to be restarted.  I let this happen and then checked for updates one final time, installing any suggest updates.


Then I restarted eclipse as a normal user (not with sudo) and installed the android SDK in my usual way by adding [https://dl-ssl.google.com/android/eclipse/](https://dl-ssl.google.com/android/eclipse/)' to the available software option and then ticking the boxes relating to Android.

After that everything worked as normal.

---

