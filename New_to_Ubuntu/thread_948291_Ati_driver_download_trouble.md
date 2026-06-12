---
title: "Ati driver download trouble"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Kanahmal on 2008-10-15
So I'm very new here(downloaded 8.04 about 3 days ago) and I'm having some trouble. I have an ATI Radeon hd 3200 graphics accelerator and the driver I found under system>admin>hardware drivers doesn't really cut it.
 So I went to the ATI website and found Catalyst 8.6 I saved it to my desktop and now I cant figure out how to download it. I tried typing find then the file name into the terminal but it came back with nothing. 
 So if anyone can help it would be much appreciated. Also please keep in mind that my terminal abilities are pretty much cut and paste at the moment.

---

### Post by kellemes on 2008-10-15
For a cut-and-paster you're not choosing the easy way ;-)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install from ati.com (latest version of drivers)]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install from ati.com (latest version of drivers)")


What's wrong with the driver you installed the point-click way?

---

### Post by eternalnewbee on 2008-10-15
Patience is a virtue...
Just replying, because you haven't had any replies from more knowledgeable people yet.
ATI is harder to configure for Ubuntu than Nvidia cards. That's the whole issue. They are Ubuntu unfriendly in principal (or so I've heard) but hopefully there some workarounds...
Patience is a virtue...

---

### Post by Kanahmal on 2008-10-15
Well the point and click driver was ok for 2d graphics but not so much for 3d. 

Also since my last post I downloaded an update and when I restarted ubuntu it froze before the login screen, and has continued to freeze everytime I restart the computer. Right now I'm on my Windows partition.

---

### Post by kellemes on 2008-10-15
You can always revert back to defaults with the following command..
As root (from the recovery bootmode)..
```
dpkg-reconfigure xserver-xorg
```

Or as a normal user..
```
sudo dpkg-reconfigure xserver-xorg
```

Edit: Also, you may see hints of errors in the following logfile: 
/var/log/Xorg.0.log

---

### Post by Kanahmal on 2008-10-15
I entered the first code as root in recovery, and it led me through a few screens asking my preferences for things like keyboard setup, after that it brought me to a terminal screen so I hit Ctrl+Alt+Delete to restart. Now my coputer freezes at the login screen. :(

---

