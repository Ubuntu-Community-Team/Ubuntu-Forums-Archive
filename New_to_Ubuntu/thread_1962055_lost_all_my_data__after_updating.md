---
title: "lost all my data  after updating"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by remeses on 2012-04-20
i lost all my files and stuff and all my custamizations in ubuntu after updating using terminal after typing these two commands 
sudo apt-get update 
sudo apt-get upgrade
i did the above after uninstalling wine and after updating i typed the following command
sudo apt-get autoremove 
then rebooted using "sudo reboot"
thats when i lost everything lost my pics my settings and videos everything ubuntu went back to like newly installed 
what should i do to recover these files

---

### Post by tmaranets on 2012-04-20
What updates did you install? Maybe that affected your files.

---

### Post by remeses on 2012-04-20
THESE are the recent updates i have installed 
1.linux-image-3.0.0-19-generic (3.0.0-19.32, 3.0.0-19.33)
2.linux-headers_3.0.0-19 (3.0.0-19.32, 3.0.0-19.33)
3.linux-headers-3.0.0-9-generic (3.0.0-19.32, 3.0.0-19.33)
4.linux-libc-dev(3.0.0-19.32, 3.0.0-19.33)

---

### Post by sirriffsalot on 2012-04-20
Ouch... I suppose you didn't add a seperate home partition in the previous ubuntu install? If not, it may be a long shot, but try searching for a file you are sure of it's name in your file system, or search for several if you haven't, perhaps they're stored somewhere... I suppose you've already tried, but just in case..

---

### Post by CharlesA on 2012-04-20
Upgrading the kernel would not cause you to lose all the settings and make Ubuntu "like new."

Are you sure you didn't have a livecd in your cd drive?

---

### Post by billaboy on 2012-04-20
By upgrading kernel your whole system can't become brand new as it was when you had installed ubuntu...

It may have caused due to re-installation of ubuntu...

Make sure that it hasn't happen...

& if it has happen in your case then first check your software plug-ins...

if those can tell you the best...

if by mistake you have installed ubuntu again then those will roll back to initial state...

like... while playing .mp3 songs banshee will ask for plugins to download..

I recommend you to see if all the softwares are there in the system...

let me know...

thnxx..

---

### Post by jerome1232 on 2012-04-20
another addition, If those new kernels aren't working, the old ones are still around, you can access them by smashing the shift key repeatedly during the boot process to bring up the grub menu, select the old kernel from the list and press 'b' to boot.

---

