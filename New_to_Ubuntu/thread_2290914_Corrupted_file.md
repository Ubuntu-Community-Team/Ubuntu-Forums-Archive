---
title: "Corrupted file"
date: 2015-08-16
forum: New to Ubuntu
---

### Post by Pierre_Corbeil on 2015-08-16
I am new to Linux. I am using Ubuntu 14.04 64bits

Trying to install Gnome Shell using "*sudo apt-get install gnome-shell*", the process ended with the error message "*file /var/lib/dpkg/available is unreadable*". I looked at the file and indeed it looks corrupted, it starts with "../../../firefox-addons/extensions/langpack-en-ZA@firefox.mozilla.org.xpi\00" followed by about 1 KB of zeros and then by the rest of the readable content. The file was last modified on August 8, 2015. I don't remember if I did anything special on that date.What do I do now ? Can I delete that file and rename the previous version "*available.old*" to replace it ?

---

### Post by Vladlenin5000 on 2015-08-16
Hi and welcome.

Yes, a corrupted file. Nothing to worry too much about because it's easily fixable and the answer - as it often happens - is just a Google search away: [http://askubuntu.com/questions/55099/dpkg-error-parsing-file-var-lib-dpkg-available-near-line-0](http://askubuntu.com/questions/55099/dpkg-error-parsing-file-var-lib-dpkg-available-near-line-0)
Try the chosen answer and post back if you have any trouble.

---

### Post by Pierre_Corbeil on 2015-08-16
Hi Vlad, and thank you, your suggestion made the repair. I had thought of deleting the file to force a reload, but I was afraid to do so, that maybe the system might forget about that non-existent file.

What is your nationality ? Romanian ? Russian ? I am French-Canadian.

---

