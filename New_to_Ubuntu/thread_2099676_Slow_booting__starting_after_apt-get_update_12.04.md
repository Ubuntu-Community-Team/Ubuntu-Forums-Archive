---
title: "Slow booting / starting after apt-get update 12.04"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by wheelerruss on 2012-12-30
0     down vote          [favorite]("http://askubuntu.com/questions/234346/slow-booting-starting-after-apt-get-update-12-04#")            
                                     I have just bought a new Lenovo Ideapad Z580, which came with Windows 8.
  I have since, removed that and installed 12.04 on top. Everything  works fine. However, after I have to updated all 272 updates using  update manager, my machine now takes about 15mins to get to the  password/login page. Once I have logged in everything works fine.
  I have a before and after bootchart image if that helps (should I  save it online e.g. pastebin, or can I attach it here?). It's very odd,  in that the slow image has the opening init command taking over 1000  seconds, before the boot process kicks in.
  Since having this issue I have tried multiple things to fix it with no success. 
  Yesterday however, I did spend the entire day updating 5-10 updates  at a time, to see if I could find the culprit for the slow boot. After  going through all of them, I managed to get everything installed fine!  It worked!! Then I went to install Mate on top, and bang, back to 15  minute boot times. Uninstalling Mate, didn't fix this!
  I currently have it working because I removed the latest kernel 3.2.0-35, so now have 3.2.0-29.
  I did this by doing
  sudo apt-get purge linux-image-3.2.0-35-generic sudo update-grub2
  However, even though it is working now, I know that if I upgrade anything I will be left with the 15 minute boot times again.
  Hopefully someone out there can help.
  Thanks
  Russ

---

### Post by daslinkard on 2012-12-30
Have you uninstalled and reinstalled the Boot Optimizer provided by Lenovo?

---

