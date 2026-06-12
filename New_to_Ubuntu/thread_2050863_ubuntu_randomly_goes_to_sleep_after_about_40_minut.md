---
title: "ubuntu randomly goes to sleep after about 40 minutes of being logged in"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by snowlizard31 on 2012-08-31
I've recently installed ubuntu on my mac and everytime I logged after a while it always starts going to sleep randomly every time I wake it. It's so annoying I really want ubuntu to work normally. I partitioned my HD like this:
These two are part of my mac I'm not sure about efi though 
/dev/sda1 efi
/dev/sda2 macHD
===============
/dev/sda3 ext4 /    13.97GB
/dev/sda4 unkown(Was linux swap but appears unknown in Gparted after install) 3.73GB
/dev/sda5 unkown(bios_grup) 96mb
/dev/sda6 ext4 /home 122.29GB

Does it have anything to do with the way I partitioned it?I tried to install it before but without the bios_grup partition but it came up with the error need reserved BIOS area

---

### Post by NikTh on 2012-08-31
Hello , 
Try to do this and see if works.

Open Dash and write **power** , press Enter. From the first drop-down menu select the "Do not suspend"
then go to "Brightness" , you will see the Tip , and from the drop-down menu on " Turn screen of when inactive for: " select "Never" 

Thanks

---

### Post by snowlizard31 on 2012-08-31
I already had those settings in :/

---

### Post by NikTh on 2012-09-01
> **snowlizard31 said:**
> I already had those settings in :/

Hi , 
and how was I supposed to know that ?  :P 

Try this command 
```

gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
```

Above command disables the screensaver. 

Thanks

---

### Post by snowlizard31 on 2012-09-01
haha sorry about that I should've put that in the first place Thank you so much!! it worked I"m so excited!!!:p

---

