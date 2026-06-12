---
title: "Rootkit Hunter Install"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by Old-un on 2011-12-10
Have been trying to install rootkit hunter-1.3.8.tar.gz but failing at each attempt. Can someone help please

---

### Post by haqking on 2011-12-10
it is in the software centre/repos

[https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter)

If you want that specific version from source then no one can help unless you say what the problem is ;-)

---

### Post by Old-un on 2011-12-10
The version of rkhunter-1.3.6 is in Synaptic but i was hoping to download and install the latest version of rkhunter which is 1.3.8 but after making my way to the folder in which rkhunter-1.3.8.tar.gz is stored and then typing: tar xvzf rkhunter-1.3.8.tar.gz an error appears?

---

### Post by haqking on 2011-12-10
> **Old-un said:**
> The version of rkhunter-1.3.6 is in Synaptic but i was hoping to download and install the latest version of rkhunter which is 1.3.8 but after making my way to the folder in which rkhunter-1.3.8.tar.gz is stored and then typing: tar xvzf rkhunter-1.3.8.tar.gz an error appears?

ahhh the age old error, i know the one you are talking about, my crystal ball is working wonders today....LOL

what is the error ?

you need to be more specific if you want help.

cheers

---

### Post by gandaran on 2011-12-10
> tar xvzf rkhunter-1.3.8.tar.gz an error appears?
right click the tar package and choose to extract here, then check if there is a readme file with instructions inside the extracted folder, there's no need to run the "tar xvzf" command as you get the same results extracting with gui.
also whats wrong with the older version in the software center?
rkhunter once installed will check for data update every week so its not necessary to have the newest version.

---

### Post by Old-un on 2011-12-10
After reading the rkhunter readme file i made the installer.sh file executable by doning the following:

sudo chmod +x installer.sh

I then typed ./installer.sh --install

But i still got, checking installation directory "/usr/local" it exists, but is not writable. Exiting

---

### Post by gandaran on 2011-12-10
> I then typed ./installer.sh --install
you need sudo on the install command

---

### Post by Old-un on 2011-12-10
That did the trick! Big thanks gandaran

---

### Post by Rubi1200 on 2011-12-10
Good support work from gandaran and others.

Please mark this Solved using the Thread Tools near the top of the page.

---

